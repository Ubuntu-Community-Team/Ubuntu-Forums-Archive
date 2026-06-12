---
title: "Wecamserver"
date: 2011-01-31
forum: Multimedia Software
---

### Post by bigmos on 2011-01-31
I have installed the web cam server from the site below. How do**[COLOR=Red] i uninstall it completely?[/COLOR]** I need the command line. I am running Ubuntu server 10.10. 

The website is:

[http://webcamserver.sourceforge.net/](http://webcamserver.sourceforge.net/)

I
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		 		 		 Thanks

	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=2208172")

---

### Post by mpnordland on 2011-01-31
probably go to the directory where you unpacked it and run
```
sudo make uninstall
```
NOTE: I have not used this program, and it looks old, but this is generally what you do if you want to remove a program that you compiled yourself

---

### Post by heracles on 2011-01-31
I have been trying to install this for ages can you tell me EXACTLY how you did it?

---

### Post by bigmos on 2011-02-01
> **mpnordland said:**
> probably go to the directory where you unpacked it and run
```
sudo make uninstall
```note: I have not used this program, and it looks old, but this is generally what you do if you want to remove a program that you compiled yourself

thanks it worked I hate when i forget the simple things

---

### Post by bigmos on 2011-02-01
> **heracles said:**
> I have been trying to install this for ages can you tell me EXACTLY how you did it?

I downloaded it unpacked it with tar -zxvf <tarfile>
Go to the directory when it unpacked it
cd <Directory>
./configure
make install

I got it to install but couldn't get it to work with my cam.
  I'musing the apt-get install webcam-server on ubuntu server.

;)

---

### Post by heracles on 2011-02-01
When i try this I get Unable to locate package webcam-server

---

### Post by bigmos on 2011-02-05
You need to add repositories 
here is the Link
:phttps://help.ubuntu.com/community/Repositories/CommandLine

add these below to the source list file
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

For the Multiverse: 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

---

