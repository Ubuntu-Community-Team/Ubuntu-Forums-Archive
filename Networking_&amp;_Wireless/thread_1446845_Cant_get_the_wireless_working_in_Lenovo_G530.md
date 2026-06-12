---
title: "Cant get the wireless working in Lenovo G530"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by albanee on 2010-04-04
[FONT=Century Gothic][SIZE=2]Hi, I am new to linux/ubuntu. Please give me step by step directions. I just installed Ubuntu 9.10 in my Lenovo G530. However the wifi is not working. I have a dual operating system with windows xp where the wifi is working fine though. [/SIZE][/FONT][FONT=Century Gothic][SIZE=2]Broadcom WiFi (802.11b/g), 10/100  Ethernet is the card im using. 
Please help me install this. if more information is needed please let me know and how to get it perhaps.
Thanks for your time and patience. [/SIZE][/FONT]

---

### Post by albanee on 2010-04-04
7 hours no reply yet .....

---

### Post by bahubindu on 2010-04-04
Have you tried installing:
linux-backports-modules-wireless-[OS_ubuntu]-generic

If that also didn't worked then:
move to "/etc/modeprobe.d/"
open this file as root in your text editor:
sudo gedit blacklist-ath_pci.conf

PUT a "#" in front of the "blacklist ath_pci" in my case.

then reboot

If not worked:

move to "/etc/modeprobe.d/"
open this file as root in your text editor:
sudo gedit bcm**?????.conf
I forgot the file name for that. you can easily understand that you have a broadcom like text in the filename.

repeat the same, that should work.

---

### Post by albanee on 2010-04-05
> **bahubindu said:**
> Have you tried installing:
linux-backports-modules-wireless-[OS_ubuntu]-generic

If that also didn't worked then:
move to "/etc/modeprobe.d/"
open this file as root in your text editor:
sudo gedit blacklist-ath_pci.conf

PUT a "#" in front of the "blacklist ath_pci" in my case.

then reboot

If not worked:

move to "/etc/modeprobe.d/"
open this file as root in your text editor:
sudo gedit bcm**?????.conf
I forgot the file name for that. you can easily understand that you have a broadcom like text in the filename.

repeat the same, that should work.

thanks for your reply... i dont know where i can install backport modules from and how do i do them ... regarding everything else you just said i have no idea what they mean...
i am new to linux please give me step by step directions...
thanks for your time and patience.

---

### Post by bkratz on 2010-04-05
The first thing to do is to determine which Broadcom card you have. This can be done by entering the following in the terminal ( Applications>>Accessories>>Terminal):

lspci | grep Network

That is LSPCI in lowercase, N in upper, | is shift \ on my US keyboard
and copy/paste the output back here or simply type the response. If no response is received just try 

lspci

and manually look through it for something that looks like BCM43xx. Post the response back here.

---

### Post by albanee on 2010-04-05
> **bkratz said:**
> The first thing to do is to determine which Broadcom card you have. This can be done by entering the following in the terminal ( Applications>>Accessories>>Terminal):

lspci | grep Network

That is LSPCI in lowercase, N in upper, | is shift \ on my US keyboard
and copy/paste the output back here or simply type the response. If no response is received just try 

lspci

and manually look through it for something that looks like BCM43xx. Post the response back here.
thanks for your reply...here are the results

lspci|grep Network
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Please lemme know what to do next...thanks for your time and patience

---

### Post by mcoleman44 on 2010-04-05
If your ethernet works then just go to system>admin>hardware drivers and install STA
If no drivers are listed then  go to a terminal and type
sudo apt-get update
sudo apt-get upgrade
sudo reboot
When you log back in the driver should be listed.

---

### Post by bkratz on 2010-04-05
> **albanee said:**
> thanks for your reply...here are the results

lspci|grep Network
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Please lemme know what to do next...thanks for your time and patience

It should be as easy as having a wired connection and putting in, from the terminal

sudo apt-get install bcmwl-kernel-source

If you don't have a wired connection see this post

[http://ubuntuforums.org/showpost.php?p=9068009&postcount=11](http://ubuntuforums.org/showpost.php?p=9068009&postcount=11)

---

### Post by albanee on 2010-04-05
> **bkratz said:**
> It should be as easy as having a wired connection and putting in, from the terminal

sudo apt-get install bcmwl-kernel-source

If you don't have a wired connection see this post

[http://ubuntuforums.org/showpost.php?p=9068009&postcount=11](http://ubuntuforums.org/showpost.php?p=9068009&postcount=11)

thanks for your reply.....i tried pluggin it into the wired connection but after trying for a while with auto eht0 it says disconnected ...i dont know why that is happening but it seems it is not working on either wired connection
here are the results of the output


mohammed@mohammed-laptop:~$ sudo apt-get install bcmwl-kernel-source

[sudo] password for mohammed: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Couldn't find package bcmwl-kernel-source

mohammed@mohammed-laptop:~$

i restarted the computer like it says in the article you gave me no success...
please help me ....lemme know if im doing something wrong or i need to do something else
thanks for your time and patience

---

### Post by albanee on 2010-04-06
> **mcoleman44 said:**
> If your ethernet works then just go to system>admin>hardware drivers and install STA
If no drivers are listed then  go to a terminal and type
sudo apt-get update
sudo apt-get upgrade
sudo reboot
When you log back in the driver should be listed.
the ethernet is not working

---

### Post by albanee on 2010-04-06
> **bkratz said:**
> It should be as easy as having a wired connection and putting in, from the terminal

sudo apt-get install bcmwl-kernel-source

If you don't have a wired connection see this post

[http://ubuntuforums.org/showpost.php?p=9068009&postcount=11](http://ubuntuforums.org/showpost.php?p=9068009&postcount=11)
any idea how to get the wired connection working ? the post on page 11 i dont understand...
thanks for your time

---

### Post by bkratz on 2010-04-06
> **albanee said:**
> any idea how to get the wired connection working ? the post on page 11 i dont understand...
thanks for your time

Regarding the wireless section--did you install Ubuntu from a disk, if so that is called a live CD. Dr. Chili555 was saying to put that disk in the tray and type in terminal (applications>>Accessories>>terminal) 

```
sudo apt-cdrom add
sudo apt-get update
```

The commands that start with sudo will require your password, which will not be echoed to you during entry, just press enter.

"It will complain when it can't find the on-line repositories, but it will index the CD contents as a source."

Ignore the fact that it will complain about the on-line repositories, it will find what you want on the CD.

After that has been completed then type the following in the terminal

```
sudo apt-get install bcmwl-kernel-source
```

Then hopefully,the wireless will work and time can be spent on the wired ( which honestly other people are better able to handle but we will see).

When you post next it would be helpful for you to copy/paste the ouput of 

```
lspci -nn
```

(that is LSPCI in lower case) it will describe your hardware.

---

### Post by albanee on 2010-04-07
> **bkratz said:**
> Regarding the wireless section--did you install Ubuntu from a disk, if so that is called a live CD. Dr. Chili555 was saying to put that disk in the tray and type in terminal (applications>>Accessories>>terminal) 

```
sudo apt-cdrom add
sudo apt-get update
```The commands that start with sudo will require your password, which will not be echoed to you during entry, just press enter.

"It will complain when it can't find the on-line repositories, but it will index the CD contents as a source."

Ignore the fact that it will complain about the on-line repositories, it will find what you want on the CD.

After that has been completed then type the following in the terminal

```
sudo apt-get install bcmwl-kernel-source
```Then hopefully,the wireless will work and time can be spent on the wired ( which honestly other people are better able to handle but we will see).

When you post next it would be helpful for you to copy/paste the ouput of 

```
lspci -nn
```(that is LSPCI in lower case) it will describe your hardware.

thanks for your reply. yes i installed it from a cd however the cd had 3 os... opensuse, ubuntu and another one (cant remember the name)
does that really matter ?

---

### Post by albanee on 2010-04-09
> **bkratz said:**
> Regarding the wireless section--did you install Ubuntu from a disk, if so that is called a live CD. Dr. Chili555 was saying to put that disk in the tray and type in terminal (applications>>Accessories>>terminal) 

```
sudo apt-cdrom add
sudo apt-get update
```The commands that start with sudo will require your password, which will not be echoed to you during entry, just press enter.

"It will complain when it can't find the on-line repositories, but it will index the CD contents as a source."

Ignore the fact that it will complain about the on-line repositories, it will find what you want on the CD.

After that has been completed then type the following in the terminal

```
sudo apt-get install bcmwl-kernel-source
```Then hopefully,the wireless will work and time can be spent on the wired ( which honestly other people are better able to handle but we will see).

When you post next it would be helpful for you to copy/paste the ouput of 

```
lspci -nn
```(that is LSPCI in lower case) it will describe your hardware.
 
GRT NEWS......... my wireless internet is working now ....thank you ..... i really appreicate your time and patience...
now the only thing is that at my work i have to connect to a wired connection...anyone has any idea how to get that working ?
thanks once again

---

### Post by bkratz on 2010-04-09
Sorry, i have been without internet for 2 days and have been unable to respond, but it looks like you have made progress, congratulations, unfortunately, I will not have a connection until Monday, other than this temporary one.  I will check then on your progress having added yours to my subscribed list. If no one else jumps in and fixes you before, I will attempt to help then.

---

### Post by albanee on 2010-04-11
any one knows how to get the wired internet working?

---

