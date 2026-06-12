---
title: "Online video problem"
date: 2010-05-17
forum: Multimedia Software
---

### Post by batarya on 2010-05-17
Hi,

Upgraded to 10.4. After the upgrade can't watch on-line content neither on Firefox nor on Chrome.

On YouTube I get an "error" message, on Facebook the infamous "video not available" screen shows up, on NBC the video just keeps buffering with sound button crossed.

What is wrong? I kept installing all swf, flash, gnash codecs over and over, additionally even installed various movie players like SM. I do not think the issue is browser-related, either a video codec or library is corrupt or something related with Java. How can I detect the problem? Even detection would help me solve it (I believe).

Thanks in advance,

BaTarYa

---

### Post by batarya on 2010-06-08
Resolved. Related to Flash and Java plug-ins. Step by step measures I have taken:

sudo echo deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free | sudo tee -a /etc/apt/sources.list

 wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

 wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -sudo apt-get updatesudo apt-get updat

sudo apt-get update

sudo apt-get install sun-java6-jre

sudo update-alternatives --install  /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so  /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so 50

sudo update-java-alternatives --set java-6-sun

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts sun-java6-jdk

sudo update-java-alternatives --set java-6-sun

 locate libflashplayer.so

sudo add-apt-repository ppa:sevenmachines/flash

Basically it's installing java and flash 64 bit and then linking it to Firefox!!! It is not enough just to install them but you also need to link.

---

