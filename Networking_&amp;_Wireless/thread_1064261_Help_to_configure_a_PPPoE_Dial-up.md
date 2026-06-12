---
title: "Help to configure a PPPoE Dial-up"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by toopho on 2009-02-08
In order to get surfing I have tried to follow my provider's instructions but I soon get lost. Following is a translation of what is said in my provider’s web page: 

Dialling under Linux and Unix 

At the moment we can offer to you no direct support by the installation of your Alice Anschlusses with Linux-or Unix-been based operating systems. 

At the market there are many different, constantly changing Linux distributions which partly very deviating settings require. 

Special Alice Software is not necessary for the use of your DSL connection. As a rule the distributions offer suitable easy configuration assistants DSL. Please, find out in addition in the operating instructions or on the on-line help sides of your operating system manufacturer. 

Under Suse Linux from version 7.3, for example, you configure the ADSL access quite comfortably with the provided programme YaST. 

To the equipment you need Login and password (access data) which you find in the welcome writing which you have received after your registration from Alice. 

The following settings are possibly necessary: 

1- A PPPoE driver must be installed 
2- The MTU value of the operating system must be put on 1492. 
3- DNA server: 
name1: 213.191.74.18 
name2: 213.191.74.19 
name3: 213.191.92.87 
name4: 213.191.92.86 
name5: 213.191.74.11 
name6: 213.191.92.84 
name7: 213.191.74.12 
name8: 213.191.92.82 
Please, use always the pairs name1 / name3, name2 / name4, name5 / name7 and name6 / name8. 

4- Authentication method: Chap 

- I would appreciate any comment.

---

### Post by ieee488 on 2009-02-08
DSL is **not** dial-up.


You need to connect your Ethernet card to the DSL modem that they supplied.

---

### Post by x33a on 2009-02-08
firstly, it's not a dial-up connection as ieee4888 said. though you can use a dialer to connect through dsl.

to get your connection working, open a terminal and type

1. sudo pppoeconf.
2. follow the instruction and stick to the defaults.
3. your connection will be ready in a minute.

---

### Post by toopho on 2009-02-09
I tried with pppoeconf on the liveCD before installing Kubuntu and it seemed to get working, but it did not really. I tried the same with Xubuntu and did perfectly work. Somehow I would like to install KDE4.1 not Xfce.

Thanks for the attention

---

### Post by x33a on 2009-02-09
pppoeconf should perfectly work on any distro. maybe, it's an issue with the live cd.

first try installing kubuntu to the hard drive, after that run pppoeconf and you should be able to connect to the net. other than that you can use the knetworkmanager. 

if you are connecting through the ethernet port then you don't have to do anything further, but if you are using a usb modem, then you'll have to install drivers for that.

---

### Post by toopho on 2009-02-10
The package knetworkmanager has to be downloaded from Internet. And I don't have access to Internet yet. 
Somehow I don't know what I have done differently today but I am surfing with the Kubuntu LiveCD (Using pppoeconf). I am going to proceed to install it.

Thanks

---

### Post by superprash2003 on 2009-02-10
it could have been an ip address issue the previous time.. just type ifconfig in the terminal and see if you get an ip always..

---

### Post by khushalb on 2010-07-19
Well i used sudo pppoeconf this thing configures permanently and internet is working.
But what If I want to create a PPPOE Dialer to connect to the internet just like in Windows you can create a connection. Any help guys?

---

### Post by dineshs on 2010-07-20
If you are using NM
[http://ubuntuforums.org/showpost.php?p=9611335&postcount=9](http://ubuntuforums.org/showpost.php?p=9611335&postcount=9)
If you are using  *pon / poff* commands to connect/disconnect,install [COLOR="Blue"]gpppon[/COLOR]  then create a launcher
```
sudo apt-get install gpppon
```
to create launcher 
Right click on the desktop and click create launcher
type-Application in terminal
name-internet(say)
command-sudo gpppon
then click on the icon- if you want to change the default icon
and click OK

---

### Post by khushalb on 2010-07-20
Yes Dinesh I am using the pon and pof button to activate my pppoe connection. And I will certainly try to download that app to suggested and let you know.

I configured my internet using sudo pppoeconf but once you restart your comp u have to again use pon to restart the pppoe connection. Also Dinesh can you give me your email id I am just new to Linux Ubuntu and since you are from India as well I can probably learn alot about Linux.

---

### Post by khushalb on 2010-07-20
Well I am just struck again with another issue my pon and poff aint working. I just used pon to enable my connection to it aint working? What should I do to get back my internet service back on.

---

### Post by dineshs on 2010-07-20
If you have network manager pl try this link
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
> Also Dinesh can you give me your email id I am just new to Linux Ubuntu and since you are from India as well I can probably learn alot about Linux. You can send private message to anyone in the forum by clicking on the user id

---

