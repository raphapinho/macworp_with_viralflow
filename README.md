# instalação do macworp
```
$ git clone https://cubimedrub.github.io/macworp/latest/
  ```
# Preparando abiente de desenvolvimento
  ```S cd ./macworp ```
  ```$ conda env create -f environment.yml ```
  ```$ conda env update -f environment.yml --prune ```
  ```$ conda activate macworp ```
  ```$ yarn --cwd ../frontend install ```

# Com o conda macworp ativado em cada prompt
## Shell 1
  ```$ docker-compose up ```
## Shell 2
  ```$ python -m macworp_backend database migrate```
  ```$ python -m macworp_backend utility rabbitmq prepare```
  ```$ honcho -e dev.env start```
## Shell 3
  ```
$ env PYTHONUNBUFFERED=1 python -m macworp_worker -n ./nextflow -s $(which snakemake) -c http://localhost:3001 -r amqp://admin:developer@127.0.0.1:5674/%2f -q project_workflow -d ./uploads -u worker -p developer -vvvvvvvv
```

## Frontend
  - http://localhost:5001
## API
  - http://localhost:3001	
## Fusionauth
  - http://localhost:9011	
  - usuário: developer@example.com
  - senha: developer
