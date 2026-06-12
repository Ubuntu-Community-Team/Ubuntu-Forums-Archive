---
title: "Java not working"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by ronbrooks on 2007-05-20
OK I have java installed into my system Ubuntu 7.04 and after I installed it a window came up and said to have the admin. remove this file XPTI.DAT from the component dir. of mozilla. 

I wanted to know is this why Java will not work because I have not removed it yet.  

Can I just rename the file so if I should need it again I could put it back by adding the name again. 

I am not sure on this so could someone help me on this.

---

### Post by taurus on 2007-05-20
If you don't want to overwrite the old file with the new file, you can move the old one somewhere else in case you need it later.

```
mv filename ~
-or-
sudo mv filename ~
```

---

### Post by ronbrooks on 2007-05-20
Well I moved the file but Java is still not working.  It keeps asking me to install the program. 

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        3    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.

I sure don't know why it is not working

---

### Post by taurus on 2007-05-20
Did you also install java6 plugin when you installed the latest version of java?  

Open synaptic again and search for sun-java6.  Then, install the plugins and the font for it.

---

### Post by ronbrooks on 2007-05-20
No I didn't but I just did and it still is not working.  I closed firefox and started it again but no luck.

I will try and do a system restart to see if that will help.

---

### Post by ronbrooks on 2007-05-20
Well a reboot didn't work either. So I am not sure where to go from here. I was thinking about uninstalling it and then reinstalling it again but on 56K dial up it takes a long time to down load it again. I am sure it is something that just needs to be tweeked. 

Taurus you have helped me in the past and I was able to get my problem fixed so i sure hope you can do the same here. 

Thanks again for your help.

---

### Post by taurus on 2007-05-20
In the URL field, type

```
about:plugins
```
and see if java plugin is on the list.  What website have you visited that report you don't have java plugins for your firefox?

---

### Post by ronbrooks on 2007-05-20
No it is not listed in the plugins and the the web site that I am going to is this on

[http://www.virginiaelks.org/]("http://www.virginiaelks.org/")

---

### Post by ronbrooks on 2007-05-20
I don't know if this will help but I saw it on another post
ronbrooks@ronbrooks-desktop:~$ ls -l /usr/lib/firefox/plugins
total 152
-rw-r--r-- 1 root root 137085 2006-11-29 04:51 libjavaplugin_oji.so
lrwxrwxrwx 1 root root     39 2007-05-20 12:16 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root     36 2007-05-18 09:01 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root     37 2007-05-18 09:01 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root     34 2007-05-18 09:01 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root     35 2007-05-18 09:01 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root     36 2007-05-18 09:01 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root     37 2007-05-18 09:01 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root     42 2007-05-18 09:01 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root     43 2007-05-18 09:01 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root   8936 2007-04-03 11:44 libunixprintplugin.so

---

