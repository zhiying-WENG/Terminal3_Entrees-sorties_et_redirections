# Terminal3_Entrees-sorties_et_redirections  
## **les commands:**  

**Télécharge CSV:**  
```
curl -L -o wilders.csv "https://gist.githubusercontent.com/bhubr/bc3a21a0202109beeb31c4a677e0461b/raw/d8805eb82e8aabffab3b0163596c734f376617d0/wilders.csv"  
```  
or  
```
wget "https://gist.githubusercontent.com/bhubr/bc3a21a0202109beeb31c4a677e0461b/raw/d8805eb82e8aabffab3b0163596c734f376617d0/wilders.csv"  
```  
**Créer un fichier <kbd>php_france_2019.csv</kbd> contenant uniquement le nombre de wilders ayant fait du PHP, sur un campus en France, en 2019:**
```
grep -c "France,2019,PHP"  < wilders.csv | > php_france_2019.csv
```
or  
```
grep -c "France,2019,PHP"  < wilders.csv > php_france_2019.csv
```
or
```
grep "France,2019,PHP"  < wilders.csv | wc -l > php_france_2019.csv
```

**Créer un fichier <kbd>php_france_2019.csv</kbd> contenant uniquement les wilders ayant fait du PHP, sur un campus en France, en 2019:**
```
grep "France,2019,PHP"  < wilders.csv | > php_france_2019.csv
```
**Créer un fichier <kbd>javascript_biarritz_toulouse.csv</kbd> contenant uniquement les wilders ayant fait du JavaScript, sur les campus de Toulouse et Biarritz**  

Solution 1:  
```
grep "Biarritz\|Toulouse" <  wilders.csv | grep "JavaScript" | > javascript_biarritz_toulouse.csv
```
or
```
grep "Biarritz\|Toulouse" <  wilders.csv | grep "JavaScript" > javascript_biarritz_toulouse.csv
```
  
Solution 2:

```
grep "Biarritz"  < wilders.csv | grep "JavaScript" | > biarritz_javascript.csv
```
```
grep "Toulouse"  < wilders.csv | grep "JavaScript" | > toulouse_javascript.csv
```
```
cat biarritz_javascript.csv toulouse_javascript.csv javascript_biarritz_toulouse.csv | sort -u
```
Solution 3:
```
grep "JavaScript"   < wilders.csv | > javascript.csv
```

```
grep "Biarritz\|Toulouse"   javascript.csv | > javascript_biarritz_toulouse.csv
```
verifier:
```
wc -l javascript_biarritz_toulouse.csv
cat javascript_biarritz_toulouse.csv
```

**Combiner les commandes history et tail (en ajustant le nombre de lignes) pour produire un fichier <kbd>history.txt</kbd> :**
```
history | tail -n 23 > history.txt
```