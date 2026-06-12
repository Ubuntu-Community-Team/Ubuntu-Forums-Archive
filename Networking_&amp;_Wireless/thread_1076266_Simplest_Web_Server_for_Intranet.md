---
title: "Simplest Web Server for Intranet?"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by LaneLester on 2009-02-21
I'm setting up a 9-computer network in my science classroom where I teach at a very small K-12 school. All the computers are connected to the router, but I'm still trying to decide how to connect the computers to each other. Other threads have suggested either samba or nfs, and experiments are progressing.

This question is for the times when Internet service may be down for an ISP problem or whatever. I would like to have a web server on my desk computer to which students could connect with Firefox and use web pages that I have on my machine.

Is LAMP (it's been a long time since I've thought about this) the easiest way to have a web server or is something simpler available?

Lane

---

### Post by superprash2003 on 2009-02-21
samba , nfs is for file sharing. for your case LAMP would be best!!

---

### Post by LaneLester on 2009-02-21
> **superprash2003 said:**
> samba , nfs is for file sharing. for your case LAMP would be best!!
OK, I've installed it before; I guess I can do it again. Thanks for letting me know.

I did a little investigation and it looks like this command will install what I need:
sudo tasksel install lamp-server

Of course, then there's configuration. Ugh.

Lane

---

### Post by LaneLester on 2009-02-23
Christer Edwards in his blog reports moving his site to a new server and using lighttpd as the web server. Have you had any experience with this one? It claims to have low overhead. I'd be interested in reports of how hard it is to set up and maintain.

I don't expect to need MySQL and probably not PHP. So I guess if I don't use lighttpd, apache by itself would be the way to go.

Lane

---

### Post by mpokrywka on 2009-02-23
Your key requirement is:
> I would like to have a web server on my desk computer to which students could connect with Firefox and use web pages that I have on my machine.
Apache would work in this case perfectly because of userdir and autoindex mods - install apache, enable mentioned modules (sudo a2enmod userdir; sudo a2enmod autoindex)
Now you can create ~/public_html directory and keep there pages to view
address will be [http://ip.of.your.machine/~youruser/](http://ip.of.your.machine/~youruser/)

---

### Post by albinootje on 2009-02-23
> **LaneLester said:**
> 
This question is for the times when Internet service may be down for an ISP problem or whatever. I would like to have a web server on my desk computer to which students could connect with Firefox and use web pages that I have on my machine.

Is LAMP (it's been a long time since I've thought about this) the easiest way to have a web server or is something simpler available?


If you want simple to configure and easy to use web server software  to serve just static html pages, or images, documents or other data, consider installing lighttpd instead of apache.
Lighttpd has only one configuration file which is easy to understand.
```

sudo apt-get install lighttpd

```

---

### Post by LaneLester on 2009-02-25
> **albinootje said:**
> If you want simple to configure and easy to use web server software  to serve just static html pages, or images, documents or other data, consider installing lighttpd instead of apache.
I took your advice and have made some good progress. I have lightftd running on the server, and students can reach the html files with Firefox.

One strangeness (to me) is that when Firefox accesses the server, a message comes up saying it's not a good URL and can't be loaded. But it's already been loaded! Is there a way to turn off that error message?

This probably isn't related to lightftd, but it's a problem keeping lightftd from working the way I want. I have three partitions on the server: Win2K, Ubuntu Intrepid, and a vfat partition so I can get to data from either OS. I want to have lightftd's HTML pages on the vfat partition, but I can't get it to work from there. I get an error message about error.log's permission denied. It seems the permissions need to be read/write for everybody, but Others is stuck at no permission at all. I'm using Ubuntu's file manager to try to make the change, and if I change it to read/write, it jumps back to none. I don't have this problem when I the HTML directory on the Ubuntu partition.

Lane

---

### Post by albinootje on 2009-02-25
> **LaneLester said:**
> I took your advice and have made some good progress. I have lightftd running on the server, and students can reach the html files with Firefox.

One strangeness (to me) is that when Firefox accesses the server, a message comes up saying it's not a good URL and can't be loaded.

See attached screenshot, you mean the default lighttpd message ? 
That is from the index.lighttpd.html file in /var/www (At least it is called like that in Ubuntu Hardy).
You can rename that file to index.html.old or something.
> 
I want to have lightftd's HTML pages on the vfat partition, but I can't get it to work from there. I get an error message about error.log's permission denied.
Hmmm, weird.
For the record, the permissions of the lighttpd log files should be like this :
> 
ls -la /var/log/lighttpd/
total 12
drwxr-x---  2 www-data www-data 4096 2009-02-25 20:33 . 
drwxr-xr-x 15 root     root     4096 2009-02-25 20:33 ..
-rw-r--r--  1 www-data www-data    0 2009-02-25 20:33 access.log
-rw-r--r--  1 www-data www-data   48 2009-02-25 20:33 error.log

How exactly are you serving the html files from the fat-partition to lighttpd ?
Through a symbolic link ? 
Or using mount with the --bind option ?

---

### Post by LaneLester on 2009-02-25
> **albinootje said:**
> See attached screenshot, you mean the default lighttpd message ? 
Thanks for the reply. No, it's not an html page; it's a popup error message: The URL is not valid and cannot be loaded.

But as I say, this pops up after the page is correctly displayed!

Later: I just loaded an html file into Firefox from the hard drive, and I got the same error message. It looks like a bug iin the new verion of FF, because I've never seen this before.

> Hmmm, weird.
For the record, the permissions of the lighttpd log files should be like this :
I'll check those tomorrow when I'm at school.

[QUOTE]How exactly are you serving the html files from the fat-partition to lighttpd ?
Through a symbolic link ? 
Or using mount with the --bind option ?
I'm mounting the partition in fstab, and I just put the mounted directory in lighttpd.conf as "/mnt/extra/html". extra is the mounted partition.

I'm not familiar with the --bind option.

Lane

---

### Post by LaneLester on 2009-02-25
Forget the Firefox error problem, I think there was something wrong with the quick-and-dirty html file I was using. It didn't have anything to do with a URL, which threw me off. But when I used a different html file, the error was not generated.

But I still hope to use the vfat partition.

Lane

---

### Post by cannonfodder on 2009-03-27
> I want to have lightftd's HTML pages on the vfat partition, but I can't get it to work from there. I get an error message about error.log's permission denied.

When it comes to permissions, VFAT is not as versatile as Unix-like filesystems. Some features present in Unix-like filesystems are not available in some Microsoft-endorsed filesystems, like switching permissions.

The MAN pages of the respective filesystems go into good detail about what functions are available to them, and, conversely, what their limits are.

I faced this problem last year and that's what I retained from it. Hope my explanation helps. 

BTW, I also recently installed lighttpd with the intention of using it to serve web pages on an Intranet. I'm in the process of configuring lighttpd.conf. 

The machine running lighttpd is 192.168.1.113. If I understand correctly, ***server.bind = "server-ip-address"*** should be modified to read ***server.bind = "192.168.1.113"***, correct?

---

### Post by coutts99 on 2009-03-27
> **cannonfodder said:**
> The machine running lighttpd is 192.168.1.113. If I understand correctly, ***server.bind = "server-ip-address"*** should be modified to read ***server.bind = "192.168.1.113"***, correct?

Yep

---

### Post by sv1cdn on 2009-03-27
> **LaneLester said:**
> I'm setting up a 9-computer network in my science classroom where I teach at a very small K-12 school. All the computers are connected to the router, but I'm still trying to decide how to connect the computers to each other. Other threads have suggested either samba or nfs, and experiments are progressing.

This question is for the times when Internet service may be down for an ISP problem or whatever. I would like to have a web server on my desk computer to which students could connect with Firefox and use web pages that I have on my machine.

Is LAMP (it's been a long time since I've thought about this) the easiest way to have a web server or is something simpler available?

Lane

How about using XAMP?
Take a look at:

[http://www.apachefriends.org/en/index.html](http://www.apachefriends.org/en/index.html)

Apache web server plus more.

---

### Post by LaneLester on 2009-03-27
I was not happy with my progress with lightftd for a number of reasons. I saw an announcement on freshmeat about cherokee, an apache alternative with a GUI interface. That sounded good to me, so I installed it. It has been serving me well for several weeks, and I was particularly pleased to find the users on the mailing list very helpful.

I'm using html pages on my cherokee system to give the students assignments and supporting material. They upload their finished work to me via a dropbox (DropBocks). They mostly use the Internet for information and for websites that offer useful exercises.

Thanks to all on here who suggested various approaches.

Lane

---

