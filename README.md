## Instruction to create environment and install packages necessary for working with GEE in windows maching

### Create a new invironment

### Update conda
```
conda update -n base conda
conda config --add channels conda-forge
conda update --all
```

### Create environment
```
conda create --name gee python=3.7.5
activate gee
```

### Install pyCrypto
* ``pip install pyCrypto``
* I was getting error in my windows maching with python 3.7 in the environment. Later found the code ''``pip install pyCrypto``'' https://stackoverflow.com/questions/54142430/how-to-install-pycrypto-for-python-3-7-2 as solution


### Install google api
```
pip install google-api-python-client
pip install earthengine-api
```

### Initialize API
```
python -c "import ee; ee.Initialize()"
earthengine authenticate
```
This will open web browser. Copy the code and paste in the command line. This will authorize.


### Install packages
```
conda install gdal
conda install rasterio
conda install geopandas
```

### Including the virtual environment in jupyter notebook
To make sure the environment is show in jupyter notebook, follow the steps
```
pip install --upgrade ipykernel
conda install -c anaconda ipykernel
# conda install ipython_genutils
python -m ipykernel install --user --name=gee

```
### Listing jupyter kernals
```
jupyter kernelspec list
```

### check if ee can be imported
```
python
import ee
ee.Initialize()
image = ee.Image('srtm90_v5')
print(image.getInfo())
exit()
```
For some reason, it wasn't importing. So, I installed api again using following codes

### Install google api
```
pip install google-api-python-client
pip install earthengine-api
```

### Open jupyter notebook
```
jupyter notebook
```
### start ee in jupyter notebook
```
import ee
ee.Authenticate()
ee.Initialize()
```

### Install few packages
```
conda install rasterio pandas pygeos geopandas tqdm

```

### For some reason the created python environment wasn't showing in jupyter notebook. Tried following codes and worked.
To make sure the environment is show in jupyter notebook, follow the steps
```
pip install --upgrade ipykernel
conda install -c anaconda ipykernel
# conda install ipython_genutils
python -m ipykernel install --user --name=gee

```

### removing a kernal from jupyter notebook
```
jupyter kernelspec uninstall gee
```
### Delete python environment [if needed]
conda env remove -n gee