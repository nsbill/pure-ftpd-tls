Docker Pure-ftpd-tls Server

#docker-compose build  
#docker-compose up -d

``` root@e21c3686f2dc:/# mkdir -p /etc/ssl/private ```
``` root@e21c3686f2dc:/# openssl dhparam -out /etc/ssl/private/pure-ftpd-dhparams.pem 2048 ```
``` root@e21c3686f2dc:/# openssl req -x509 -nodes -newkey rsa:2048 -sha256 -keyout \
                      /etc/ssl/private/pure-ftpd.pem -out /etc/ssl/private/pure-ftpd.pem ```
``` root@e21c3686f2dc:/# chmod 600 /etc/ssl/private/*.pem ```

``` root@e21c3686f2dc:/# pure-pw useradd user1 -f /etc/pure-ftpd/passwd/pureftpd.passwd -u 1002 -g 1002 -n 1000 -N 5000 -d /home/ftpusers/user1 ```
``` root@e21c3686f2dc:/# pure-pw mkdb /etc/pure-ftpd/pureftpd.pdb -f /etc/pure-ftpd/passwd/pureftpd.passwd ```
