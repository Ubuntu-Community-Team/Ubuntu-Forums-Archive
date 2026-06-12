---
title: "xmms2 client"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by ASPCartman on 2007-10-24
Hi all. So i wanna install xmms2 with abraca client. But when i compile abraca (as it said on  web site of project) i got message: xmms2-client package not found. WTF? I installed everything that has xmms2 title in gutsy repos! What to do? (Searching xmms2-client in google doesnt help)

---

### Post by cafe2 on 2007-10-25
I installed all of libxmmsclient packages and it worked.

---

### Post by ASPCartman on 2007-10-25
thx but now other **** =( 

```

aspcartman@ASP:~/Desktop/abraca-0.2$ sudo ./waf configure && ./waf && ./waf install
[sudo] password for aspcartman:
Checking for program gcc                : ok /usr/bin/gcc 
Checking for program ar                 : ok /usr/bin/ar 
Checking for program ranlib             : ok /usr/bin/ranlib 
Checking for program cpp                : ok /usr/bin/cpp 
Checking for compiler could create pragramms : ok  
Checking for compiler could create shared libs : ok  
Checking for compiler could create static libs : ok  
Checking for flags -Wall                       : ok  
Checking for flags -O2                         : ok  
Checking for flags -g -DDEBUG                  : ok  
Checking for flags -g3 -O0 -DDEBUG             : ok  
Checking for package gtk+-2.0 >= 2.8.0 (cached)  : ok  
Checking for package libglade-2.0 >= 2.6.0 (cached)  : ok  
Checking for package glib-2.0 >= 2.12.0 (cached)     : ok  
ERROR:  == Build ==  cannot find config.h
Compilation finished successfully 
ERROR:  == Build ==  cannot find config.h
Cannot create folder /usr/local/share/abraca/. 


```

---

### Post by cafe2 on 2007-10-25
have you "libxmmsclient++-dev" installed?

---

### Post by cafe2 on 2007-10-25
+ put sudo before each step:

```
sudo ./waf configure && sudo ./waf && sudo ./waf install
```

---

### Post by ASPCartman on 2007-10-25
ERROR: ../src/xmms/xform.c:1311: Couldn't get url for entry (17)


This is what i got in log when i click play button (and i cant add music to playlist. I click add and nothing happens. 

Only

 INFO: ../src/xmms/xform.c:1295: Successfully setup chain for 'file:///home/aspcartman/Desktop/1.wma' (919) containing file:magic:avformat:avcodec

in log of xmms2d

---

### Post by ASPCartman on 2007-10-25
And log is full of 
```

ERROR: ../src/plugins/alsa/alsa.c:271: Sample format (16) not available for playback.

```

---

### Post by damnum on 2007-11-04
You must launch xmms2-launcher.

---

### Post by darck on 2007-12-06
Which xmms2 client support Winamp skins?

---

