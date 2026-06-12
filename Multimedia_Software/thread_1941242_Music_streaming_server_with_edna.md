---
title: "Music streaming server with edna"
date: 2012-03-15
forum: Multimedia Software
---

### Post by sp-1070 on 2012-03-15
Its been a long time but here we go once again a new tutorial, What about you ask ?

About making a Music streaming server using apache mysql and edna.

Just follow the steps and you will have a new working music server.
Reachable from the inside and if ports are open also from the outside.

Im going to write this thinking you know how to start a terminal and work in it.

This will work for 10.04 and higher.

First we install apache2 webserver
```
sudo apt-get install apache2
```

Then restart the service
```
sudo /etc/init.d/apache2 restart
```

Then see if it works 

```
Open a browser and navigate to http://localhost  if you read "It works!", which is the content of the file /var/www/index.html , this proves Apache works.
```

If it doesnt try the trouble shooter at

```
https://help.ubuntu.com/community/ApacheMySQLPHP
```

Then navigate to youre www folder wich is the folder apache shows on [http://localhost](http://localhost)

```
cd /var/www
```

Now download edna and put it in youre Downloads file.

```
http://sourceforge.net/projects/edna/files/latest/download?source=files
```

extract it and open a new terminal and move the extracted file to /var/www.

Make sure you rename the extracted directory to edna.

```
[LIST=1]
[*]cd /home/Downloads
[*]sudo mv edna /var/www/
[/LIST]
```

Now go and edit the edna.conf

```
sudo gedit /var/www/edna edna.conf
```

First change the port to something you like.

```
[server] port = 7007
```

go down and edit the path to your music.
Saying youre directory is the music folder we change it to:

```
# Unix example:
dir1 = /mnt/cdrom = MP3 CDROM
dir2 = /mp3/all-albums = Jukebox<----to---->dir2 = /home/Music

```


Save and close.

Now we start edna by doing the following

```
[LIST=1]
[*]cd /var/www/edna
[*]sudo python edna.py
[/LIST]
```

now its running on youre internal ip adres you can see it bij going to.

```
http://YoureIp:7007(depending on the port you chose it might be :8080 or whatever
```

Now to open it to the world or so you can reach it from annywhere you  have to open the port specified in the edna.conf in your router and forward it to your ip and restart edna.

Hope it helped, have fun and ROCK ON !:guitar::-({|=

---

