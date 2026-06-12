---
title: "Proxy Authentication Required"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by Makyl on 2010-09-12
I have a ethernet enabled network access at my college through a proxy server which requires authentication.The browser when started prompts for a username and password which when entered correctly runs smoothly but whenever I try to download something from Ubuntu software center I am unable to do so with an error message "Failed to download files Check your network connection"
The details in it are:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/b/bibledit/bibledit-data_3.8-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/b/bibledit/bibledit-data_3.8-1_all.deb) 407  [COLOR="Red"]Proxy Authentication Required[/COLOR]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/b/bibledit/bibledit_3.8-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/b/bibledit/bibledit_3.8-1_i386.deb) 407  [COLOR="red"]Proxy Authentication Required
[/COLOR]
What should I do?
And Is there any software like proxy cap or proxifier available in ubuntu..?

---

### Post by Makyl on 2010-09-12
Solution:
In both :
1. System->Preferences->Network Proxy-> Set : Direct Internet Connection.
2. System->Administration->Synaptic Package Manager->Settings->Preferences->Network-> Set : Direct Internet Connection.

Then create a filename in:
/etc/apt/apt.conf

add the following lines:
Code:

Acquire::http::Proxy "http://username:password@proxy:port";
Acquire::ftp::Proxy "ftp://username:password@proxy:port";

and save the file.

In the terminal run:
Code:
sudo apt-get update


I tried the whole thing but it still doesn't work.

---

### Post by Makyl on 2010-09-12
Now when I try to download something from ubuntu software update it displays:

"Requires installation of untrysted packages.
The action would require the installation of packages from not authenticated sources."

Help me out.

---

### Post by sikander3786 on 2010-09-12
> **Makyl said:**
> Now when I try to download something from ubuntu software update it displays:

"Requires installation of untrysted packages.
The action would require the installation of packages from not authenticated sources."

Help me out.
Try changing the update server from System >>> Administration >>> Software Sources. Select Main and then

```

sudo apt-get update

```

And then go on installing any package you want to.

---

### Post by Makyl on 2010-09-12
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/..._3.8-1_all.deb](http://in.archive.ubuntu.com/ubuntu/..._3.8-1_all.deb) 407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...3.8-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/...3.8-1_i386.deb) 407 Proxy Authentication Required


Still getting this error..

---

### Post by sikander3786 on 2010-09-12
Did you try setting up proxy in Synaptic? System -> Administration -> Synaptic Package Manager -> Settings -> Preferences -> Network and configure proxy for your machine.

---

### Post by sobrimohamad on 2010-09-28
i am having the same problem. in the browser, the proxy setting is like this
 
proxy adress 172.23.3.234
port 8080
username    student\AA1234     (domain\username if im not mistaken)
password ******
 
so how to use 
 
Acquire::http::razz:roxy "http://username:razz:assword@proxy:razz:ort"
 
in this type of authentication.
thanks

---

### Post by sankara09 on 2010-11-09
check this file out :

pour le software center via proxy avec user password

sudo gedit /etc/bash.bashrc

in mine i had put those line at work to go through the proxy but forgot to remove them at home. So synaptic was working well but not the software center !

the line in the file were :
#export http_proxy=http://user:pwd@adr:8080/
#export ftp_proxy=http://user:pwd@adr:8080/

after i remove them i was  again able to install software via software center

---

### Post by rajhanschinmay on 2012-05-05
This worked for me in Ubuntu 12.04:

You can use the following commands in the termial.
sudo export http_proxy=”http://$username:$password@proxyserver:port/”
sudo export ftp_proxy=”ftp://$username:$password@proxyserver:port/”
sudo export https_proxy=”https://$username:$password@proxyserver:port/”
sudo export socks_proxy=”socks://$username:$password@proxyserver:port/”


eg.
sudo export http_proxy="http://abc:def@ghi.com:8080/";

Here abc is username, def is password and ghi.com is the proxy server, 8080 is the port.

where username and password are authentication details of the proxy server (use without $) and proxyserver is the address followed by the port number.
eg. 
Typical port no. is 80 or 8080.


Then run sudo apt-get update

This will update ur software versions database from the respositories you selected. Then u can use
sudo apt-get install package_name to install any of the packages you need.

Hope this info. is useful.
Thank you.

---

### Post by rajhanschinmay on 2012-05-05
If the previous method does not work then u can manually edit the configuration file as follows

sudo gedit /etc/apt/apt.conf

In this file add the following line(s):

Acquire::http::proxy "http://$username:$password@proxyserver:port/";
Acquire::socks::proxy "socks://$username:$password@proxyserver:port/";

also for https and for ftp.

eg.
Acquire::http::proxy "http://abc:def@ghi.com:8080/";
Here abc is username, def is password and ghi.com is the proxy server, 8080 is the port.

where username and password are authentication details of the proxy server (use without dollar sign) and proxyserver is the address followed by the port number.
eg.
Typical port no. is 80 or 8080.

Then save and exit.

Then run sudo apt-get update

This will update ur software versions database from the repositories you selected. Then u can use
sudo apt-get install package_name to install any of the packages you need.

Hope this info. is useful.
Thank you.

---

