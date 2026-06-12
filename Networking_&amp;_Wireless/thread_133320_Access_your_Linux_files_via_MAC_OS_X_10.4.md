---
title: "Access your Linux files via MAC OS X 10.4"
date: 2006-02-20
forum: Networking &amp; Wireless
---

### Post by MAbans on 2006-02-20
I know I wasn't the only one having trouble sharing files between Mac OS X and Linux. Sure linux could get into the OS X 10.4 (Referred to as Tiger from here on) but the other way was just plum broken for some reason. Keep in mind these are my experiences with setting this up and if there was a much easier way then the way I'm about to explain please by all means share this information..

	Now research led me to believe that there was something "broken" with Samba in the way its implemented in Tiger. I tried creating a new smb.conf, tried the command "smbpasswd" to no avail. But I did discovered was a package manager called "Darwin port". This was new to me and I was somewhat familiar with more advanced version like what comes in stock in Ubuntu and Automatix when I came across it. So get a copy of Darwin ports here. 

Darwin Ports
[http://www.darwinports.org/](http://www.darwinports.org/)

	Download and install darwin ports and open your terminal. From there I just ran:

	```
sudo port install samba3
```

	Poof.. All of the samba + any dependencies were downloaded and promptly installed. Afterwards I was properly able to log into my linux box and do as I wished.. (Given that you have shared folders setup as well) I have no idea what exactly got fixed or how it fixed it since my knowledge of Samba3 is near nil. Then again my very experience using command-line "stuff" is just +1 higher.. Try it and if it works let me know. Lets hope that no Tiger updates re-breaks this fix..

---

