---
title: "How do I disable samba"
date: 2012-11-06
forum: Networking &amp; Wireless
---

### Post by c-m on 2012-11-06
I have samba running on Ubuntu 12.04 with a whole bunch of shares.

How do I disable the samba service (temporarily - and not have it start at boot) but still keep all my configs and settings for when I'm ready to re-enable it?

---

### Post by PowerBarry43 on 2012-11-06
Hi
 
you can quickly disable samba by running
 
```
sudo service smbd stop
```
 
or I believe you can run
 
```
 
sudo update-rc.d smb remove

```
 
to stop on boot and to start on boot again run
 
```
sudo update-rc.d smb defaults
```
 
if all else failes download and install webmin by running
 
```

sudo apt-get installperl libnet-ssleay-perl openssl libauthn-pam-perl libpam-runtime libio-pty-perl apt-show-versions
 
wget -c [http://prdownloads.sourceforge.net/webadmin/webmin_1.600_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.600_all.deb)
 
sudo dpkg -i webmin_1.600_all.deb

```
 
and if you go into a web browser and type [https://localhost:10000](https://localhost:10000) and log in you should be able to configure startup services under the system>startup and shutdown tab
 
Hope this helps!!
 
Barry

---

### Post by PowerBarry43 on 2012-11-06
Hi
 
you can quickly disable samba by running
 
```
sudo service smbd stop
```
 
or I believe you can run
 
```
 
sudo update-rc.d smb remove

```
 
to stop on boot and to start on boot again run
 
```
sudo update-rc.d smb defaults
```
 
if all else failes download and install webmin by running
 
```

sudo apt-get install perl libnet-ssleay-perl openssl libauthn-pam-perl libpam-runtime libio-pty-perl apt-show-versions
 
wget -c [http://prdownloads.sourceforge.net/webadmin/webmin_1.600_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.600_all.deb)
 
sudo dpkg -i webmin_1.600_all.deb

```
 
and if you go into a web browser and type [https://localhost:10000](https://localhost:10000) and log in you should be able to configure startup services under the system>startup and shutdown tab
 
Hope this helps!!
 
Barry

---

### Post by Lars Noodén on 2012-11-06
There should be a file 'samba4.conf' or something similar in /etc/init, edit that and comment out the line beginning with 'start'  That is done by starting the line with a pound (#) sign.

```

#start on (local-filesystems and net-device-up)

```

That will prevent it from automatically starting but you will still be able to manually invoke it when needed.

```

sudo service samba4 start

```

It's an [upstart](http://upstart.ubuntu.com/cookbook/) based service, if you want to look up more information about your options.

---

### Post by c-m on 2012-11-06
Thanks guys.

I've edited the file at :

```
sudo nano /etc/init/smbd.conf
```

as I didn't have a samaba4.conf there.

Then commented out the line

```
#start on (local-filesystems and net-device-up)
```

Hopefully that works

---

