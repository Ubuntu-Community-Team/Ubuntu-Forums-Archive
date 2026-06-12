---
title: "Ndiswrapper Problems..."
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by Thikr on 2009-07-09
I made a couple of posts elsewhere that started at some base problems and evolved... Here is the problem in its crudest form (I will edit Later for more details) I am using a Belkin Wireless N F5D8053 which has no drivers on linux. I downloaded and (I think) installed Ndiswrapper. When I extract the contents of the windows Driver I use one of two .inf files (both of which have the problem) and do the "sudo ndiswrapper -i path/to/file.inf" command and get some error like "could not find path/to/file.inf at usr/sbin/ndiswrapper line 219" which is quite annoying. I tried to put them in usr /sbin but to no avail. Anyone got any ideas? Thanks a million guys, I will update this and clean it up...

---

### Post by Crafty Kisses on 2009-07-09
Now to my knowledge the Belkin F5D8053 uses the "rt2870" driver. Which the driver again to my knowledge is Linux native. Before I go any further though, you're going to need build essential, so run the following:
```
sudo apt-get install build-essential
```
Now that you have build essential, you can now compile the driver. So you can now fetch the driver by running the following:
```
wget http://www.ralinktech.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2
```
Then once you have it downloaded, you can extract the file by running the following:
```
tar xvfj RT2870_Linux_STA_v1.4.0.0.tar.bz2.tar.bz2
```
So now enter the directory, you can do this by running:
```
cd RT2870_Linux_STA_v1.4.0.0
```
Now once you're in the directory, you **might** have to do a couple of things, open a Terminal and run:
```
sudo gedit config.mk
```
Go down until you see the following in the configuration file:
```
HAS_WPA_SUPPLICANT=n
```
You need to change that to the following:
```
HAS_WPA_SUPPLICANT=y
```
Then go down a bit further until you see the following line:
```
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
```
Then you obviously need to change that to:
```
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```
Save your changes, then you need to run as root:
```
make
```
Then if needed, as root:
```
make install
```
Then if needed you may need to load the module manually, it's very easy to do, now as root, run:
```
modprobe rt2870sta
```
To make sure the module is loaded, you can run:
```
lsmod | grep rt2
```
Then the module should appear, now once you have done this. You can now reboot and hopefully your card works perfectly. You can reboot by running:
```
shutdown -r now
```
This in essence should get you up and running, if you have any problems please let me know.

---

### Post by Thikr on 2009-07-09
> **Codename said:**
> Now to my knowledge the Belkin F5D8053 uses the "rt2870" driver. Which the driver again to my knowledge is Linux native. Before I go any further though, you're going to need build essential, so run the following:
```
sudo apt-get install build-essential
```


Unfortunately, Linux does NOT have my driver native to it to my knowledge and I can't apt-get when the driver I need is for my internet Connection :). I don't mean to sound like a jerk, if I did because I have a habit of misleading people with the tone of my text. Thank you for trying to help but I need offline help... ;)

---

### Post by Crafty Kisses on 2009-07-09
This is the driver for your Belkin. [http://www.ralinktech.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2). 

You could always put the files you need on a flash drive with the machine that has a network connection. Then install the drivers like that.

---

### Post by Thikr on 2009-07-09
> **Codename said:**
> This is the driver for your Belkin. [http://www.ralinktech.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2). 

You could always put the files you need on a flash drive with the machine that has a network connection. Then install the drivers like that.

Thank you, I couldn't extract the original archive I was using (On Linux, I have winRAR though...) Also, what do you mean by "You could always put the files you need on a flash drive with the machine that has a network connection. Then install the drivers like that." I don't quite understand... ;)

---

### Post by Crafty Kisses on 2009-07-10
> I can't apt-get when the driver I need is for my internet Connection
Correct me if I'm wrong, but it sounds like you can't connect via Ubuntu at all. So first, try and plug the machine in with an Ethernet cord, or whatever you may use, and what I meant about putting your files on a USB drive is you can go on the machine that has a working net connection and put the files on a USB drive. Then put them on your Linux machine. If you want to install the driver that I gave you, you are going to need the "build essential" package. So read this thread on how to get packages without a net connection. [http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819). You also said you can't extract the file? Just copy and paste the command I provide:
```
tar xvfj RT2870_Linux_STA_v1.4.0.0.tar.bz2.tar.bz2
```
That should extract the driver. Then you can go along with the initial compile. The other way of doing this, is downloading ndisgtk, which is a graphical front end of ndiswrapper. Which you can grab right here: [http://linuxappfinder.com/package/ndisgtk](http://linuxappfinder.com/package/ndisgtk). Once you have done that, you need to download the "inf" for your card. I've already found the inf for you, so download the this [**file.**]("http://77.91.202.10/~alpoimco/Satanas/belkin_pre-n.tar.gz") Once you have done that, find the .inf file and open ndisgtk, ndisgtk is pretty straight forward but if you have problems let me know.

---

### Post by Thikr on 2009-07-10
> **Codename said:**
> Correct me if I'm wrong, but it sounds like you can't connect via Ubuntu at all. So first, try and plug the machine in with an Ethernet cord, or whatever you may use, and what I meant about putting your files on a USB drive is you can go on the machine that has a working net connection and put the files on a USB drive. Then put them on your Linux machine. If you want to install the driver that I gave you, you are going to need the "build essential" package. So read this thread on how to get packages without a net connection. [http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819). You also said you can't extract the file? Just copy and paste the command I provide:
```
tar xvfj RT2870_Linux_STA_v1.4.0.0.tar.bz2.tar.bz2
```
That should extract the driver. Then you can go along with the initial compile. The other way of doing this, is downloading ndisgtk, which is a graphical front end of ndiswrapper. Which you can grab right here: [http://linuxappfinder.com/package/ndisgtk](http://linuxappfinder.com/package/ndisgtk). Once you have done that, you need to download the "inf" for your card. I've already found the inf for you, so download the this [**file.**]("http://77.91.202.10/~alpoimco/Satanas/belkin_pre-n.tar.gz") Once you have done that, find the .inf file and open ndisgtk, ndisgtk is pretty straight forward but if you have problems let me know.

Ok, thank you very much...  I'll try it soon as I can :p

---

