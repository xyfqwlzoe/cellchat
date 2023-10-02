# How to use cellchat_wrapper<br /> 
<p align="center">
  <img width="200"  src="https://github.com/sqjin/CellChat/blob/master/CellChat_Logo.png">
</p>


# Extract the CellChat input files from a Seurat object
The normalized count data and cell group information can be obtained from the Seurat object by

## If you're using "NormalizeData" function from seurat
```R
data.input <- GetAssayData(seurat_object, assay = "RNA", slot = "data") # normalized data matrix
labels <- Idents(seurat_object)
meta <- data.frame(group = labels, row.names = names(labels)) # create a dataframe of the cell labels
```
## If you're using "SCTransform" function from seurat
```R
data.input <- GetAssayData(object = seuratObj, assay = 'SCT', slot = "data")
labels <- Idents(seurat_object)
meta <- data.frame(group = labels, row.names = names(labels))
```
## Save as "data.input.rds" and "meta.rds"

# Run cellchat_wrapper.r
```
cellchat_wrapper.r \
#normalized data 
normdata_path \
# meta data 
metadata_path \
#group variable for cellchat, one column name from meta data 
group_var \
# human or mouse
species \
outputdir 
```
# example
```
cellchat_wrapper.r data.input.rds meta.rds group human outputdir
```
