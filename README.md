# Como usar o Laravel com o Docker 

Para poder rodar este projeto com o docker e docker compose é necessário ter tanto o docker quanto o docker compose instalado na 
sua máquina. 

1. Tenha gere um arquivo .env na raíz do projeto com as credenciais de banco de dados conforme as variáveis de ambiente do serviço de banco de dados do **docker-compose.yml**

2. Rode o comando **docker-compose up -d --build** na raíz do projeto, o mesmo irá subir os três serviços configurados no **docker-compose.yml**

3. Entre no seu container de aplicação digitando o comando **docker composer exec lara_docker_env_app bash**, caso dê algum erro tento de outra forma vendo o nome do container e utilizando o comando: **docker exec -it <nome-do-container> bash** 

4. Na pasta corrente /var/www que é onde você estará ao entrar no container, instale o laravel utilizando o comando: **composer create-project laravel/laravel my-app** 

Obs: O composer irá criar este diretório: **/var/www/my-app** e instalará o laravel dentro dele

5. Ainda em /var/www digite o comando **cp -r /my-app/* .** , isso irá copiar todo o projeto para /var/www

Obs: Verifique se as pastas existem dentro de /storage/framework: cache, views e sessions, se não existem crie essas pastas. Exemplo: 

 - storage
    - framework 
        - cache
        - views
        - sessions

6. No seu container , estando na raiz /var/www/ digite o comando: **chmod 777 -R *** para dar permissão. Você pode resolver este problema de permissão com alguma alternativa no Dockerfile também, fica a seu critério. 

Obs: A Aplicação estará rodando na porta HTTP 8088