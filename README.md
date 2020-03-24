# docker-diving-lessons
An amassing of infos, shortcuts, text about Docker


### Shortcuts
Ctrl+P+Q     (Gracefully get out of container)


### Misc
docker service create --name psight1 -p 8080:8080 --replicas 5 nigelpoulton/pluralsight-docker-ci

docker swarm join --token SWMTKN-1-XXXXXX 192.168.0.8:2377 --advertise-addr 192.168.0.7:2377 --listen-addr 192.168.0.7:2377

docker service ps psight1

docker service update --replicas 10 psight1

docker service create --name psight2 --network ps-net -p 80:80 --replicas 12 nigelpoulton/tu-demo:v1

docker service update --image nigelpoulton/tu-demo:v2 --update-parallelism 2 --update-delay 10s psight2

docker service ps psight2 | grep :v2


### Misc 2
docker history redis

docker image inspect redis

docker image rm redis

docker image ls --digests

docker image pull nigelpoulton/tu-demo -a

docker image build -t psweb1 .       (Note the dot, current dir as context, where the code is,    -t  => tag)

docker image build -t psweb1 https://github.com/nigelpoulton/psweb.git

docker container run -d --name psweb_1 -p 8080:8080 psweb

docker container run -it alpine sh

docker container exec 06a535a69461 ls -l

docker container rm $(docker container ls -aq) -f

docker logs 06a535a69461

### Swarm
docker swarm init --advertise-addr 192.168.0.23:2377 —listen-addr 192.168.0.23:2377

docker swarm join-token manager      (or worker)

docker node ls

docker swarm join --token SWMTKN-1-XXXXXX 192.168.0.21:2377 --advertise-addr 192.168.0.19:2377 --listen-addr 192.168.0.19:2377

docker swarm join-token --rotate worker

docker swarm update --autolock=true

service docker restart

docker swarm unlock (-> then pass in key)

docker swarm update --cert-expiry 48h

docker swarm leave --force

