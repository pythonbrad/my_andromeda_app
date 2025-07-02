# Andromeda Galaxy Discovery Uploader Two

### Requirements

- [Ruby on Rails](https://guides.rubyonrails.org/install_ruby_on_rails.html)
- [Postgres server](https://www.postgresql.org/download/) (*optional*)
- [Docker](https://docs.docker.com/get-started/get-docker/) (*optional*)

### Installation

Clone the repo.

```sh
git clone https://github.com/pythonbrad/my_andromeda_app
```

You will need to create three databases, one for the development and the second for the test and the last for the production.

```sh
createdb -h <hostname> -U <username> my_andromeda_app_development;
createdb -h <hostname> -U <username> my_andromeda_app_test;
createdb -h <hostname> -U <username> my_andromeda_app;
```

**Without Docker**

Install dependencies.

```sh
bundle install
```

Config your virtual environment.

```sh
export RDS_USERNAME=postgres
export RDS_PASSWORD=mysecret
export RDS_HOST=postgres
export RDS_DB_NAME=my_andromeda_app
```

Prepare the migrations

```sh
rails db:migrate
```

**With Docker**

```sh
docker build . -t my_andromeda_app
```

### Deployment

- Without docker

```sh
rails server
```

- Using docker

```sh
docker run --rm -p 80:80 -e SECRET_KEY_BASE=secret -e RDS_HOSTNAME=172.17.0.1 -e RDS_PASSWORD=mysecret -e RDS_USERNAME=postgres --name my_andromeda_app my_andromeda_app
```
