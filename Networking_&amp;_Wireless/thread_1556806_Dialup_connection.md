---
title: "Dialup connection"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by Bphillips on 2010-08-19
I'm new to Ubuntu and have just installed Ubuntu 10.04 from a DVD that a friend downloaded and copied for me to install. I have it installed and im on dialup connection and need to know how to go about setting up a connection and or software i need to do it.

Thanks in advance

---

### Post by dineshs on 2010-08-20
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)
The above site explains different methods.You may try ```
sudo pppconfig
```from a terminal after connecting modem.This will configure the connection
Now to connect use
```
pon
```and to disconnect ```
poff
```
BTW what modem are you using ? serial or USB?

---

### Post by grahammechanical on 2010-08-20
Until I got broadband a few months ago I was using the method suggested by dineshs. It works fine. The program explains what information you need to enter. It is a good little utility.

regards

---

### Post by Bphillips on 2010-08-20
> **dineshs said:**
> [http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)
The above site explains different methods.You may try ```
sudo pppconfig
```from a terminal after connecting modem.This will configure the connection
Now to connect use
```
pon
```and to disconnect ```
poff
```BTW what modem are you using ? serial or USB?

Im using a USB modem

---

### Post by dineshs on 2010-08-21
Connect your modem and post the results of
```
lsusb
```and```
dmesg | grep -e "modem" -e "tty"
```

---

### Post by Bphillips on 2010-08-21
> **dineshs said:**
> Connect your modem and post the results of
```
lsusb
```and```
dmesg | grep -e "modem" -e "tty"
```


I connected modem in USB port and it will not even power up...I have a Hiro USB modem model numberH50113 if this helps.

---

### Post by Bphillips on 2010-08-21
I dont know where to type the codes you refer to.

---

### Post by ieee488 on 2010-08-21
> **Bphillips said:**
> I connected modem in USB port and it will not even power up...I have a Hiro USB modem model numberH50113 if this helps.
Download, install, and run scanModem
and tell us what it says

[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)

---

### Post by Bphillips on 2010-08-21
Well i think i got a bad Ubuntu disk or corrupted..I couldnt get Ubuntu to recognize the cd or load it.. so i reinstalled Ubuntu and when finished and rebooted i got a whole bunch of I/O errors and it just locks up, so i'll have too see about getting another DVD.

Thanks to all

---

### Post by dineshs on 2010-08-21
The commands are to be typed in a terminal
Applications-accessories-terminal
And post the results here

---

### Post by Bphillips on 2010-08-22
> **dineshs said:**
> Connect your modem and post the results of
```
lsusb
```and```
dmesg | grep -e "modem" -e "tty"
```


Ok for the 1susb code..Bus 001 Device 003 ID 047e:2892 agere systems inc. soft modem


code for dmesg | grep -e "modem" -e "tty" is....[0.000000] console [tty0]enabled
[2.090520]serial8250: ttyso at I/0 ox3f8(irq=4) is a 16550a

[ 2.091033] 00:08: ttys0 at I/O 0x3f8 (irq=4) is a 16550A


Is this what you looking for dineshs

---

### Post by dineshs on 2010-08-22
> Is this what you looking for dineshs Yes
I think your modem is not detected.So as ieee488 suggested > Download, install, and run scanModem
and tell us what it says

[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)

---

### Post by Dinahalye on 2010-08-22
operation off dialup connection is  differcult or easy?

---

### Post by alexfish on 2010-08-22
hi

can you look in the software centre

in the search area type in " agere " see what it comes up with

---

### Post by Bphillips on 2010-08-22
I cant get scanmodem to work no matter how i type it or where i put the program at...i did it according to instructions on the site.

---

### Post by ieee488 on 2010-08-22
> **Bphillips said:**
> I cant get scanmodem to work no matter how i type it or where i put the program at...i did it according to instructions on the site.

I suspect that when running the commands in the Terminal window as directed by the instructions that you are not in the same directory as **scanModem** file.

If you are old enough to have used DOS, that's what you'll need to remember again.

---

### Post by Bphillips on 2010-08-22
> **ieee488 said:**
> I suspect that when running the commands in the Terminal window as directed by the instructions that you are not in the same directory as **scanModem** file.

If you are old enough to have used DOS, that's what you'll need to remember again.


LOL..that might be the problem...im just old...lol

---

### Post by PaulReaver on 2010-08-22
modem aside you's are all forgeting that he'll need to add himself to the dialup group

in a terminal

sudo adduser BPhillips dip



if your user name is BPhillips

---

### Post by Bphillips on 2010-08-22
From all the stuff i have been reading and trying..none of the illustrations match what i have for some reason..this is 10.04 LTS 32 bit im running. I have hardly any hardware drivers if any installed..lol

Im already an added user for dip.

---

### Post by PaulReaver on 2010-08-22
read [[COLOR="Red"]here[/COLOR]]("http://linmodems.technion.ac.il/travelmate800.ubuntu.slmodem.html")

the sl-modem source and sl-modem daemon are in the repos.  
hope it helps...:D

---

### Post by Bphillips on 2010-08-22
Thanks but i keep getting command not found file not found..i tried synaptic package manger to try and load a package and it wont mount cd ..like i said i think i got a bad copy of ubuntu.

---

### Post by dineshs on 2010-08-22
Can you try what alexfish suggested?
Also please try if this link can help
[https://help.ubuntu.com/community/DialupModemHowto/Lucent/Agere](https://help.ubuntu.com/community/DialupModemHowto/Lucent/Agere)

---

### Post by Bphillips on 2010-08-22
I dont have a software center..i have what is called software sources and you can't search anything in there.

---

### Post by alexfish on 2010-08-23
Hi

your thread say Ubuntu 10.04 if this correct

usually top panel menus

click on applications / Ubuntu Software Centre


backend  click System / Administration / Synaptic Package Manager

enter password when requested / thats the one when you log in

when investigating drivers please READ info 

check the device is listed this one is yours

Device 003 ID 047e:2892  : "agere systems inc. soft modem"
regards

alexfish

---

### Post by Bphillips on 2010-08-23
I typed in the search line of synaptic package manager "agere" and got a package known as texlive-latex-extra..i think i have another problem as well when i try to install repositories it will not mount CD.

---

### Post by alexfish on 2010-08-24
> **Bphillips said:**
> I typed in the search line of synaptic package manager "agere" and got a package known as texlive-latex-extra..i think i have another problem as well when i try to install repositories it will not mount CD.

Hi

Sorry to here about your Woes

I will look for some links as regards your problems and update the links later

But for now can you download the following:[B]Ubuntu Manual
[/B]
**About the manual**

**Getting  Started with Ubuntu 10.04** is a comprehensive beginners guide  for the Ubuntu operating system. It is written under an open source  license and is free for you to download, read, modify and share.

The  manual will help you become familiar with everyday tasks such as  surfing the web, listening to music and scanning documents. With an  emphasis on easy to follow instructions, it is suitable for all levels  of experience.

[Download now]("http://ubuntu-manual.org/download/10.04e2/en_US/screen")
[Alternative download options]("http://ubuntu-manual.org/downloads")

Regards

alexfish

---

### Post by Bphillips on 2010-08-24
I found out that Ubuntu 10.04 LTs does not have the package for Gnome ppp which is required for the dialup modem service, so i have downloaded the Gnome ppp, now im searching of how to install with out internet connection from a dvd.

Thanks to everyone for all there time and input.

---

### Post by alexfish on 2010-08-25
HI

You can try WVDIAL but maybe problems

you need to use the terminal

Code to enter from the terminal

Code:

wvdialconf

read the info carefully

from a post by George Vitas


**wvdial** and dependencies are not included into CD of **9.04**  and **9.10** (exists on DVD). You can install it if you have an  internet connection (sudo apt-get install wvdial) or download and  install the packages needed:
[wvdial offline installation]("http://ubuntuforums.org/showthread.php?p=7245790#post7245790").

Ubuntu **9.10**  initial version (liveCD) has [bug#446146]("https://bugs.launchpad.net/bugs/446146")  which affects most 3g modems. An **update using any other connection**  (ethernet or wifi) 'repairs' it.

Ubuntu **10.04** includes **wvdial**  and dependencies but are NOT installed!
To install them read [wvdial offline installation]("http://ubuntuforums.org/showthread.php?p=7245790#post7245790")

Regards,
George

---

### Post by Bphillips on 2010-08-28
Sorry i havent been on for past couple of days, the computer i was using to access internet decided the hard drive was tired and it shorted out..had to buy Windows to get back up on this computer but still want to get Ubuntu running on the other one.
 
Alexfish i will give that a try..thank you very much.

---

