---
title: "Server Uploads"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by badmelon on 2008-12-27
Hello,

I have a small server setup and I would like to be able to upload files from my Ubuntu 8.10 laptop to it via the internet using a username and password. Basically my own private online backup service. Are there any programs available that will let me do this? 

Thoughts and Ideas please....
Cheers!

---

### Post by tuskenraider on 2008-12-27
yeah [http://www.rejetto.com/hfs/](http://www.rejetto.com/hfs/) you have to use wine.. but it will work like a champ.  

hfs + wine + dyndns + forwarded port = your home server on the internet


tusken

thats what i use btw.

---

### Post by htmlland on 2008-12-27
or even a basic FTP server could work too as thats client platform independant and does not need wine installed. Personally i use ProFTPD.

---

### Post by badmelon on 2008-12-27
oh yeah ftp, i forgot that. Does Apache run on ubuntu anyone? or are there better alternatives?

---

### Post by htmlland on 2008-12-27
Of course! Apache can be installed with "apt-get install apache2" I belive.

Michael

---

### Post by badmelon on 2008-12-27
Can I set up multiple accounts with it, so my family can use it too?

---

### Post by htmlland on 2008-12-27
do you mean with proFTPd? Not sure :( sorry I only use it for me :P. This topic might help though [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by badmelon on 2008-12-27
No, I meant in Apache.....

---

### Post by htmlland on 2008-12-27
what do you mean by users? Apache is nothing but a webserver which just displays pages or files in its htdocs! It is a read-only thing in the sameway that a website is. Are yuo thinking of mabye Apache wit hmabye PHP and some file manegment software? In which case the sfotware might come with multiple users.

---

### Post by badmelon on 2008-12-27
I'm trying to make a basic home server that will give multiple users disk space. So if I logon with my username/password I get the files I uploaded but if someone else logs on they get the files they uploaded but not mine. I want to use Ubuntu 8.10 as the client system and preferably as the host.

---

### Post by badmelon on 2008-12-27
I just found a useful walkthrough, I'm gonna play with this for a while.

[HTML]http://www.instructables.com/id/Set-up-your-very-own-Web-server/?ALLSTEPS[/HTML]

---

### Post by htmlland on 2008-12-27
Then an FTP server software is what would be good for that job :).

There is several FTP server software variations out there its really about picking the one you like. 

Just so you know; in case you dont; with ftp the user will simply be able to type into an FTP client (or firefox/windows explorer/internet explorer etc) [ftp://server.address](ftp://server.address) and it will ask for a login. If set up right that will then take them to their "space".

Hope it all works :)

Michael

---

### Post by badmelon on 2008-12-27
What are my choices when it comes down to this sort of thing?

---

### Post by htmlland on 2008-12-27
Well personally i use proFTPd but i am not usre if this has multiple users. Try googleing "ubuntu 8.10 ftp server software" and see what comes up :). 

Sorry i can't be anymore help :)

Michael

---

### Post by tuskenraider on 2008-12-28
or like i said before... you can use the hfs program if you want.. oh idk your grandma to go to your site and look at pictures or what ever.  IDK about your grandma but mine doesnt know what FTP is but she can check her email and follow a link that i sent her.   HFS will do that for you.  mulitiple users upload and download  double click the icon and you have a HTTP server up and running.  

but thats my 2 cents.


tusken

---

