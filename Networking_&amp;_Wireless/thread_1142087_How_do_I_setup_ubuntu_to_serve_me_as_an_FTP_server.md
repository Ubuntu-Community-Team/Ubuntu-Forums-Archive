---
title: "How do I setup ubuntu to serve me as an FTP server."
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by Extol11 on 2009-04-28
Hi! I'm new to using Ubuntu as a server so I need a bit of help here. I installed Apache, Mysql and PHP on a spare computer I plan to use as a server for a forum. I have very few experience on how to do this stuff and the last time I actually tried it was a long time ago when I setup joomla. What I want to do is setup a Phpbb forum on this computer and I asked a friend of mine for help. He told me that he could help me but he wants me to make the pc accept transfers via ftp. I looked in synaptics for any package that did this and got confused with everything I saw. So how do I setup Ubuntu 9.04 to let me upload files to this pc via say.... filezilla? I also want it to be safe. I just want to be able to upload files to the site from anywhere to change the content of the site when needed. I don't have too much time to research this as I'm nearing finals and I have a couple of projects, so please bear with me. Thanks in advance for any help.

---

### Post by tricolorpoa on 2009-04-28
I use proftpd as server and GProftpd as GUI-config
```
# sudo apt-get install proftpd gproftpd
```

:popcorn:

---

### Post by Extol11 on 2009-04-29
Am I not suppose to choose one of those packages or the other? Also, is there any setup needed after that? And is whatever firewall that ubuntu has ready for it? Meaning it will let only that program get accessed through the ftp port? And thanks for telling me.

---

### Post by tricolorpoa on 2009-04-29
Install the 2 packages

proftpd - the server
gproftp - the configuration interface in Application > Internet > GProftpd

after that the service are working for all users that you have in your system...
maybe you want to change the Home Dir of some users in GProftpd to use /var/www but this is very easy if you use GProftp

---

### Post by Extol11 on 2009-04-29
> **tricolorpoa said:**
> Install the 2 packages

proftpd - the server
gproftp - the configuration interface in Application > Internet > GProftpd

after that the service are working for all users that you have in your system...
maybe you want to change the Home Dir of some users in GProftpd to use /var/www but this is very easy if you use GProftp
Everything worked perfectly untill I tried to use gproftpd. It said that some regular configuration had to be done, if one was unsure about it you should select yes. I did and now filezilla no longer connects to it. It says that econ, or something like that, was refused. I tried to fix things up in gproftpd but it didn't work. Can you tell me some regular set ups that work? I'm going to set the directory to var/www and it asked me to select a group then said that the group I had selected didn't exist. Also, is it ok if I set the server ip to 192.168.1.XXX even for accessing from outside my network? And what is the nat option for and the lookup user one? Sorry for my noobishness. :confused:

---

### Post by Kareeser on 2009-04-29
You've overcomplicated things. In fact, you don't even need gProFTPd to configure proftpd.

Start over, please:
```
sudo apt-get purge proftpd
sudo apt-get install proftpd
```

From there, the only modification you need should be in the file /etc/proftpd/proftpd.conf, to change the directive "ServerType" from "inetd" to "standalone".

That should be all you need.

Default behaviour is to let all users with login credentials log into the FTP server with their same credentials.

---

### Post by Extol11 on 2009-04-29
> **Kareeser said:**
> You've overcomplicated things. In fact, you don't even need gProFTPd to configure proftpd.

Start over, please:
```
sudo apt-get purge proftpd
sudo apt-get install proftpd
```

From there, the only modification you need should be in the file /etc/proftpd/proftpd.conf, to change the directive "ServerType" from "inetd" to "standalone".

That should be all you need.

Default behaviour is to let all users with login credentials log into the FTP server with their same credentials.

Ok, thanks. I just restarted the computer and as I logged in it told me that "/home/.,dmrc" or something like that, was being ignored. The default values of that file should be 644 and that it was responsible for loading my prefered settings or something like that. Will this fix it too?

---

### Post by Extol11 on 2009-04-29
I just reinstalled Ubuntu 9.04. So how do I change the location of the ftp to "/var/www" without messing anything? Is it in that same directory?

---

### Post by MontelEdwards on 2009-04-29
Umm,  i am not sure about proftpd but I know that if you just make a hyperlink to /var/www  you can access all the files that way

---

### Post by Extol11 on 2009-04-29
> **monteledwards said:**
> Umm,  i am not sure about proftpd but I know that if you just make a hyperlink to /var/www  you can access all the files that way

Nice! How do I do that?

---

### Post by MontelEdwards on 2009-04-29
> **Extol11 said:**
> Nice! How do I do that?
Well it depends on what files/folders you want to access.  I am not sure how to do it shell, but with Nautilus.
Just ```
gksudo nautilus 
``` and then go to the folder/file, right click and click make link.
Then move the link to /var/www

You need Nautilus with root permissions that is why we run gksudo
so for example you want to acess your home directory via FTP just run gksudo nautilus, go  /home and the right click your username, click make link, right click on the link, copy, and paste it to /var/www

---

### Post by tricolorpoa on 2009-04-29
> **Extol11 said:**
> Nice! How do I do that?

this create a link to /var/www in your home dir
```
$ ln -s /var/www ~/link-to-www
```But this can cause some issues about permissions for apache to read these files because the files will be owned by your user and not by the apache's user., so remember to do
```
$ sudo chmod -Rv 777 /var/www
```This trick is very insecure but... It is a way..

:guitar:

---

### Post by Kareeser on 2009-04-30
Correct. By default, FTP logins work similar to SSH logins. Because you log in with your system credentials, you have the same permissions as if you were sitting at the computer yourself.

Therefore, by default, /var/www can be accessed by anyone, although write permissions are limited to whoever owns the directory (which I believe is root).

You can change it if you'd like, with the commands chown and chmod.

---

### Post by Extol11 on 2009-04-30
OK. I think I just want to make the ftp server take you to the /var/www directory by default instead of /home/me Will I have all the privileges needed to write into that folder? How can I do that without "screwing" up the setup that I already have? I only installed proftpd and not gproftpd this time. I think with being able to access the apache folder would be enough for what I want to do at the moment. And thanks for all of the help, guys. It is really appreciated.

---

### Post by tricolorpoa on 2009-04-30
Create a link to /var/www in your home dir like I said before, then connect to ftp, open the link and put your files. After that, change the permissions of these files.```
$ sudo chmod -Rv 777 /var/www
```
So access [http://localhost/](http://localhost/)
Remember that apache put a index.html file in /var/www so you need to replace or move it.

---

### Post by coutts99 on 2009-04-30
> **tricolorpoa said:**
> Create a link to /var/www in your home dir like I said before, then connect to ftp, open the link and put your files. After that, change the permissions of these files.```
$ sudo chmod -Rv 777 /var/www
```
So access [http://localhost/](http://localhost/)
Remember that apache put a index.html file in /var/www so you need to replace or move it.

chmod 777 on /var/www = bad!

---

### Post by Extol11 on 2009-04-30
Cab't I just put the files straight into /var/www with the rights of my account? After all, it's the same rights the ftp is using, right? I think I want to go straight to the folder and not through a link. And why do I have to keep changing the ownership of those files? Apache will not let anything else change them? This pc is going to be exclusively a server. The only reason it's got a GUI is because I don't have experience doing this. Is there anyway I can just throw files directly into var/www and not have change ownerships or make a link?


And something that doesn't have to do much with this, but I don't think it deserves a thread just for this. I installed SSLEAY the first time in the server and when I installed webmin, it still wouldn't let me access it through https:// but through http:// how can I make webmin use the https protocol instead?

---

### Post by tricolorpoa on 2009-04-30
For this you need to do some changes in your /etc/proftpd/proftpd.conf
You can use the umask parameter to save the files with a right permission to apache

---

### Post by Extol11 on 2009-04-30
Can't I just make the admin log in through the actual admin account (there's an option somewhere to log in as admin) and access the ftp with that account? I think this should give me privileges to access /var/www and since I don't want to do anything but access that folder I don't think I'll mess anything up. And how can I solve that webmin problem?

---

### Post by Extol11 on 2009-04-30
Up up! Go up I say!!!! Dang it, man. These threads are sinking way to quickly.

---

### Post by tricolorpoa on 2009-05-04
Please,

post the output of the following command:
```
egrep -v "^$|^#" /etc/proftpd/proftpd.conf
```

---

