---
title: "JRE Firefox Plugin"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by CarlosinFL on 2007-10-10
Guys - I am attempting to look at the surf report via my Firefox browser & it tells me I need JRE plugin however I am unable to install them automatically. Is there a way I can verify if I have this plugin installed or can someone please help me and advise how this can be installed.

Thanks for any assistance.

I did make sure I have the "sun-java6-jre" package installed and all of its dependencies. 

```
cwilliams@cwilliams:~$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  java-common libltdl3 odbcinst1debian1 sun-java6-bin unixodbc
Suggested packages:
  equivs sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts ttf-sazanami-gothic ttf-sazanami-mincho
  libmyodbc odbc-postgresql libct1
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  java-common libltdl3 odbcinst1debian1 sun-java6-bin sun-java6-jre unixodbc
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 33.1MB of archives.
After unpacking 94.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com feisty/main java-common 0.25ubuntu2 [76.9kB]
Get:2 http://us.archive.ubuntu.com feisty/main libltdl3 1.5.22-4 [168kB]
Get:3 http://us.archive.ubuntu.com feisty/main odbcinst1debian1 2.2.11-13 [64.1kB]
Get:4 http://us.archive.ubuntu.com feisty/main unixodbc 2.2.11-13 [269kB]
Get:5 http://us.archive.ubuntu.com feisty/multiverse sun-java6-bin 6-00-2ubuntu2 [26.2MB]
Get:6 http://us.archive.ubuntu.com feisty/multiverse sun-java6-jre 6-00-2ubuntu2 [6324kB]                       
Fetched 33.1MB in 2m26s (226kB/s)                                                                               
Preconfiguring packages ...
Selecting previously deselected package java-common.
(Reading database ... 113656 files and directories currently installed.)
Unpacking java-common (from .../java-common_0.25ubuntu2_all.deb) ...
Selecting previously deselected package libltdl3.
Unpacking libltdl3 (from .../libltdl3_1.5.22-4_i386.deb) ...
Selecting previously deselected package odbcinst1debian1.
Unpacking odbcinst1debian1 (from .../odbcinst1debian1_2.2.11-13_i386.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.11-13_i386.deb) ...
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6-00-2ubuntu2_i386.deb) ...
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-00-2ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Setting up java-common (0.25ubuntu2) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

Setting up sun-java6-jre (6-00-2ubuntu2) ...

Setting up sun-java6-bin (6-00-2ubuntu2) ...

```

---

### Post by w4ett on 2007-10-11
Try this:

```
sudo apt-get install flashplugin-nonfree
```

please see:  [https://help.ubuntu.com/7.04/internet/C/web-plugins.html](https://help.ubuntu.com/7.04/internet/C/web-plugins.html)

---

### Post by CarlosinFL on 2007-10-11
That is adobe flash which works fine. I need the Java JRE plugin.

---

### Post by nzadLithium on 2007-10-11
are you using 64bit ubuntu?

---

### Post by CarlosinFL on 2007-10-11
No. 32.

---

### Post by nzadLithium on 2007-10-11
thats odd then.

You can check to see if its installed by typing "about : plugins" into the url box in firefox take the spaces out of that. I did likethat coz i couldnt figure out how to get rid of the smiley.

Look for the one that says java.

I got to do some study for my exams now. but when i finish i'll go on my machine running 32 bit and find all the java packages i have.

---

### Post by nzadLithium on 2007-10-11
k these are the packages i have.

java-common, sun-java6-bin, sun-java6-fonts, sun-java6-jre, sun-java6-plugin

i think thats all you will need

if you look at your post from you installation it says: 'suggested pacakages' in that list is the other packages that you may need but are not critical to run java.

i would add the fonts one sun-java6-fonts
but the one you need to get it going in mozilla-firefox is sun-java6-plugin

---

### Post by PCZahra on 2008-01-12
> **nzadLithium said:**
> k these are the packages i have.

java-common, sun-java6-bin, sun-java6-fonts, sun-java6-jre, sun-java6-plugin

i think thats all you will need

if you look at your post from you installation it says: 'suggested pacakages' in that list is the other packages that you may need but are not critical to run java.

i would add the fonts one sun-java6-fonts
but the one you need to get it going in mozilla-firefox is sun-java6-plugin

I have all of them, but no java plugin in the list. I have the same problem with the mplayer plugin, the plugin package is selected and installed but doesn't show up in the list and it still wants me to download an install it manually.

---

### Post by ShelJ on 2008-01-13
Same prob,  HELP please!!  I have Xubuntu on a Athelon 64.

---

### Post by comandrei on 2008-01-13
did you try this : [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins) ?

---

### Post by PCZahra on 2008-01-17
yes. here's something odd. all of those install into /usr/lib/mozilla/plugins. if I put symlinks to all of them into ~/.mozilla/plugins they all appear in the list. for some reason it just didn't recognise its own global folder. though I am using ff3b2, maybe it's a bug

---

### Post by reginabally on 2008-04-01
I've recently upgraded my Kubuntu 7.10 to 8.04 beta. I removed the pre-installed Firefox 3 beta and installed Firefox 2 through Adept Manager.

I've verified that I've installed the latest and complete JRE but it's not shown in the list while I typed "about:plugins" in firefox.

I tried the instructions given by Sun Java but it's not working too.

Please help.

---

### Post by lesergi on 2008-04-01
Hi!

The only you need is the package sun-java6-plugin, if you says you can't install it, try to download from here: [http://mirror.switch.ch/ftp/mirror/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-03-0ubuntu2_i386.deb](http://mirror.switch.ch/ftp/mirror/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-03-0ubuntu2_i386.deb)

Download it, and install it with sudo dpkg -i sun-java6-plugin_6-03-0ubuntu2_i386.deb

Regards!

---

### Post by russ18uk on 2008-04-01
> **PCZahra said:**
> yes. here's something odd. all of those install into /usr/lib/mozilla/plugins. if I put symlinks to all of them into ~/.mozilla/plugins they all appear in the list. for some reason it just didn't recognise its own global folder. though I am using ff3b2, maybe it's a bugShouldn't that be /usr/lib/firefox/plugins?

---

