# genotypeMatcher
Matching vireo genotypes between pools


matcher.py correlates genotypes between donors of different pools from vireo output.


Example run
-----------
python3 matcher.py /path/to/vireo/dir/ /path/to/outdir/


**/path/to/vireo/dir/** is a directory containing vireo output for multiple pools with the following structure. 

<pre>
├── pool1
│   └── vireoOutput
│       └── pool1
│           ├── GT_donors.vireo.vcf.gz
├── pool2
│   └── vireoOutput
│       └── pool2
│           ├── GT_donors.vireo.vcf.gz
</pre>


Optional parameters
----------

**--samplesheet**:
The last directory name is used as pool name. If you would like to convert this to a different ID,
you can give --samplesheet <file> option, where the
first column matches with the directory name,
and 4th column with the new name you want to give

**--min\_cor\_threshold option.**: By default donors are matched if they have a genotype correlation > 0.8. This can be adjusted with the --min_cor_threshold option.

Output
------

Two outputs written to the  /path/to/outdir/ directory:  

-  **matched\_donors.txt**: tab delimited file with 3 columns: new\_donor, sample, and old\_donor. 
<br>**new\_donor**: is matched between pools (e.g. if new\_donor is donor1 for pool1 and pool2, then this is the same donor in both pools)  
**sample**: the name of the pool  
**old\_donor**: the donor as recorded by vireo

- **correlations.png** Correlation heatmap between all donors of all pools. Double check this to see if --min\_cor\_threshold is set correctly