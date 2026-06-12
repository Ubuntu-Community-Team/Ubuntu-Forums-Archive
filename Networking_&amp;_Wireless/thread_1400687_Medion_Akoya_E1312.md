---
title: "Medion Akoya E1312"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by Glyn Hughes on 2010-02-07
There are a lot of threads reporting problems with wireless, camera and microphone on this popular small laptop, has anybody solved any of them? Especially, for me, the wireless. 

 There are now a large number of helpful guesses and suggestions about this,  but may I strongly enjoin no-one to reply to this thread unless **they actually have **a Medion Akoya E1312 and have made it work with Ubuntu.

---

### Post by erik2912 on 2010-02-07
I made it work with Debian. I had to compile in wireless card driver. But if you google enough, you will find an howto.
If it's there for debian, it sure is there for ubuntu. Remember (especialy in this case) google is your best friend.

---

### Post by bkratz on 2010-02-07
No i don't have one but there was a similar post about 1 or 2 days ago.
[http://ubuntuforums.org/showthread.php?t=1399123](http://ubuntuforums.org/showthread.php?t=1399123)


You  probably have a Realtek 8172 and should see this posting
[https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172](https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172)

Just to check though go to the terminal Applications>>Accessories>>terminal
and type in 
lspci (LSPCI in lowercase) and check before proceeding

---

### Post by chili555 on 2010-02-07
> Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

[https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172](https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172)

I do not believe they have the latest version of the driver referenced. I think it's: [http://launchpadlibrarian.net/36688638/rtl8192se_linux_2.6.0010.1211.2009.tar.gz](http://launchpadlibrarian.net/36688638/rtl8192se_linux_2.6.0010.1211.2009.tar.gz)

[http://ubuntuforums.org/showpost.php?p=8754255&postcount=5](http://ubuntuforums.org/showpost.php?p=8754255&postcount=5)

It's a bit difficult, but not that hard. Although I get people's wireless, including a few Realtek 8172s, going literally several times a day, I do not actually have a Medion Akoya E1312, so I will go away now.

Just kidding; post back if you get stuck.

---

### Post by Glyn Hughes on 2010-02-07
Thank you very much for that, but I've been through all this.

I was rather hoping that **someone who actually has made a Medion Akoya E1312 work with Ubuntu **might perhaps reply.

---

### Post by chili555 on 2010-02-07
And it didn't work and you can't figure out why and I guess you figure we can't either. Maybe so or maybe not. You'll never know if you don't ask. We are just a PM away.

Good luck.

---

### Post by Glyn Hughes on 2010-02-07
> **chili555 said:**
> And it didn't work and you can't figure out why and I guess you figure we can't either. Maybe so or maybe not. You'll never know if you don't ask. We are just a PM away.

Good luck.
Thank you for trying, I've carefully followed your suggestions several times each. I have also tried to follow the suggestuions at:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[http://ubuntuforums.org/showthread.php?t=249889&highlight=akoya](http://ubuntuforums.org/showthread.php?t=249889&highlight=akoya)
[http://ubuntuforums.org/showthread.php?t=820026](http://ubuntuforums.org/showthread.php?t=820026)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126)
[http://ubuntuforums.org/showthread.php?t=1182457](http://ubuntuforums.org/showthread.php?t=1182457)
[http://ubuntuforums.org/showthread.php?t=1209710](http://ubuntuforums.org/showthread.php?t=1209710)
[http://ohioloco.ubuntuforums.org/showthread.php?t=1190996](http://ohioloco.ubuntuforums.org/showthread.php?t=1190996)
[http://forums.lenovo.com/t5/T400-T500-and-newer-T-series/Replacing-T400-wireless-card/m-p/134159](http://forums.lenovo.com/t5/T400-T500-and-newer-T-series/Replacing-T400-wireless-card/m-p/134159)
[http://lnv.lithium.com/t5/Linux-Discussion/New-T500-no-wifi-drivers/m-p/148683](http://lnv.lithium.com/t5/Linux-Discussion/New-T500-no-wifi-drivers/m-p/148683)
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2004697.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2004697.html)

... but it definitively does not work. 

Is there anyone who has **ever made a Medion Akoya E1312 work with Ubuntu? **

---

### Post by chili555 on 2010-02-07
After you do:```
sudo apt-get install linux-headers-`uname -r` build-essential
```Which step here failed?

[http://ubuntuforums.org/showpost.php?p=8754255&postcount=5](http://ubuntuforums.org/showpost.php?p=8754255&postcount=5)

---

### Post by Glyn Hughes on 2010-02-07
> **chili555 said:**
> After you do:```
sudo apt-get install linux-headers-`uname -r` build-essential
```Which step here failed?

[http://ubuntuforums.org/showpost.php?p=8754255&postcount=5](http://ubuntuforums.org/showpost.php?p=8754255&postcount=5)
sed -i 's/install: modules/install:/g' ./ieee80211/Makefile

returns:

sed: couldn't open temporary file ./ieee80211/sed4nHI6V: Permission denied

---

### Post by chili555 on 2010-02-07
Please try with *sudo*:```
sudo sed -i 's/install: modules/install:/g' ./ieee80211/Makefile

etc.

```

---

### Post by Glyn Hughes on 2010-02-07
> **chili555 said:**
> Please try with *sudo*:```
sudo sed -i 's/install: modules/install:/g' ./ieee80211/Makefile

etc.

```
Well, a box appeared saying wireless was connected. But I couldn't connect to anything. On re-start, the wireless connection had completely dissapeared.

---

### Post by chili555 on 2010-02-07
Please try:```
sudo modprobe r8192se_pci
```If that does it, let's see:```
cat /etc/modules
```

---

### Post by Glyn Hughes on 2010-02-07
> **chili555 said:**
> Please try:```
sudo modprobe r8192se_pci
```If that does it, let's see:```
cat /etc/modules
```
Having obtained the file [COLOR=Indigo]rtl8192se_linux_2.6.0010.1211.2009.tar.gz[/COLOR] and saved it to the desktop, I've started the Terminal, and, ona-at-a-time entered the lines

[COLOR=Red]cd ~/Desktop
tar xzf rtl8192se_linux_2.6.0010.1211.2009.tar.gz
cd rtl8192se_linux_2.6.0010.1211.2009
sudo make
sudo sed -i 's/install: modules/install:/g' ./ieee80211/Makefile
sudo sed -i 's/install: modules/install:/g' ./HAL/rtl8192/Makefile
sudo make install
sudo echo "r8192se_pci" > /etc/modules
sudo modprobe r8192se_pci[/COLOR]

At the end of this I do have a working wireless connection, but it dissapears on resrart.

[COLOR=Red]cat /etc/modules[/COLOR]   gives

glyn@ubuntu:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
lp
glyn@ubuntu:~$

---

### Post by chili555 on 2010-02-07
> sudo echo "r8192se_pci" > /etc/modulesThis part didn't take, for some reason. Please do:```
sudo gedit /etc/modules
```Add a line:```
r8192se_pci
```Proofread, save and close gedit. Now, before you restart, please do:```
sudo modprobe r8192se_pci
```Does your wireless come to life?

Now restart and let us know the outcome. Thanks.

---

### Post by Glyn Hughes on 2010-02-07
> **chili555 said:**
> This part didn't take, for some reason. Please do:```
sudo gedit /etc/modules
```Add a line:```
r8192se_pci
```Proofread, save and close gedit. Now, before you restart, please do:```
sudo modprobe r8192se_pci
```Does your wireless come to life?

Now restart and let us know the outcome. Thanks.
Well! I'll be squizzled. That seems to work perfectly, thank you so much.
 

 So, its...
 

 Download the file [COLOR=#4b0082][/COLOR]

[http://launchpadlibrarian.net/36688638/rtl8192se_linux_2.6.0010.1211.2009.tar.gz ]("http://launchpadlibrarian.net/36688638/rtl8192se_linux_2.6.0010.1211.2009.tar.gz")


and save it to the desktop  
 

 Then, open Applications>Accessories>Terminal, and one-line-at-a-time, followed by 'return' enter these lines..
 

 [COLOR=#ff0000]cd ~/Desktop
tar xzf rtl8192se_linux_2.6.0010.1211.2009.tar.gz
cd rtl8192se_linux_2.6.0010.1211.2009
sudo make
sudo sed -i 's/install: modules/install:/g' ./ieee80211/Makefile
sudo sed -i 's/install: modules/install:/g' ./HAL/rtl8192/Makefile
s[COLOR=Red]udo make install
sudo modprobe r8192se_pci[/COLOR][/COLOR]  
 [COLOR=Red]sudo gedit /etc/modules[/COLOR]
 

 which will open a text editor, add to it the line
 

 r8192se_pci
 

 ..close the editor. That's it. Is it?

---

### Post by chili555 on 2010-02-07
As we used to say back in East Texas, yup!

Glad it's working and thanks for giving the searchers a HOWTO. They'll appreciate it.

---

### Post by Glyn Hughes on 2010-02-07
Well, thanks for all your help. All we need now is to get the sound and the camera working - but I think that can wait for another day.

---

### Post by chili555 on 2010-02-07
By the way, when Update Manager gives you a newer kernel, also known as linux-image, you (and the searchers) will have to build the module anew against the new kernel with the addition of a step:```
cd ~/Desktop
tar xzf rtl8192se_linux_2.6.0010.1211.2009.tar.gz
cd rtl8192se_linux_2.6.0010.1211.2009
[COLOR="Blue"]sudo make clean[/COLOR]
sudo make
sudo sed -i 's/install: modules/install:/g' ./ieee80211/Makefile
sudo sed -i 's/install: modules/install:/g' ./HAL/rtl8192/Makefile
sudo make install
sudo modprobe r8192se_pci
sudo gedit /etc/modules

```Also, eventually, a later version than 1211.2009 will come out. 

Also, kernel version 2.6.32, now under development for Lucid, is supposed to include r8192se_pci from, as we used to say in East Texas, the gitgo.

---

### Post by Glyn Hughes on 2010-02-09
Thank you very much for that, an enormous help.

---

### Post by crid on 2010-05-05
For anyone else struggling with this laptop

quote:-
Download the file 

[http://launchpadlibrarian.net/36688638/rtl8192se_linux_2.6.0010.1211.2009.tar.gz](http://launchpadlibrarian.net/36688638/rtl8192se_linux_2.6.0010.1211.2009.tar.gz)


and save it to the desktop  
 

 Then, open Applications>Accessories>Terminal, and  one-line-at-a-time, followed by 'return' enter these lines..
 

 [COLOR=#ff0000]cd ~/Desktop
tar xzf rtl8192se_linux_2.6.0010.1211.2009.tar.gz
cd rtl8192se_linux_2.6.0010.1211.2009
sudo make
sudo sed -i 's/install: modules/install:/g' ./ieee80211/Makefile
sudo sed -i 's/install: modules/install:/g' ./HAL/rtl8192/Makefile
s[COLOR=Red]udo make install
sudo modprobe r8192se_pci[/COLOR][/COLOR]  
 [COLOR=Red]sudo gedit /etc/modules[/COLOR]
 

 which will open a text editor, add to it the line
 

 r8192se_pci
 

 ..close the editor. That's it. Is it?

unquote


This didn't work for me (a complete novice) somehow.
However putting the 
[COLOR=#ff0000][COLOR=Red]sudo modprobe r8192se_pci

command after the edit did work
Thanks for the help

[/COLOR][/COLOR]

---

