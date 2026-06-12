---
title: "unable to access internet .DSL connection"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by pushkar_k on 2010-07-25
Hello ,
   I have recently installed ubuntu 9.10. Earlier I had ubuntu 9.04 . On that my internet was running perfectly well.
           After installation I created new connection as I had done for 9.04 version using "Network connections , Edit connections" . However , after configuring connection(uname , password etc.) I wasn't able to access Internet. 
              So I tried using "**pppoeconf**" utility. After using this now whenever I click on network connections applet on top panel , it shows in menu "**device not managed**".
  Can somebody point out what went wrong and what to do so as to be able to acess Internet in ubuntu ? Thank you in advance .

---

### Post by Iowan on 2010-07-25
Check */etc/network/interfaces* - interfaces defined there are not managed by Network Manager (although this can be changed).**ppoeconf** may have made changes.

---

### Post by dineshs on 2010-07-25
> However , after configuring connection(uname , password etc.) I wasn't able to access Internet. 
May be bug in 9.10
[http://techtitbits.com/2010/04/resolving-the-network-manager-bug-in-ubuntu-9-10/](http://techtitbits.com/2010/04/resolving-the-network-manager-bug-in-ubuntu-9-10/)
> So I tried using "pppoeconf" utility.If you have run pppoeconf try
 ```
pon dsl-provider
``` (in a terminal) to connect and```
poff dsl-provider 
```to disconnect

---

### Post by pushkar_k on 2010-07-26
> **Iowan said:**
> Check */etc/network/interfaces* - interfaces defined there are not managed by Network Manager (although this can be changed).**ppoeconf** may have made changes.
      Thank you for your reply . I don't understand contents of /etc/network/interface file. So I am pasting it here for reference. Also I was able to access internet using pon but still network manager applet is not showing configured connection.
> 
[B]auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual[/B]


---

### Post by dineshs on 2010-07-26
If you want Network manager to manage your connections,the file should contain only
```
auto lo
iface lo inet loopback
```
But you have these additional lines as lowan said```
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
```caused by running pppoeconf.pl refer this
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
But as I said I am not sure this will work because of the bug in NM  ubuntu 9.10

---

### Post by pushkar_k on 2010-07-26
> **dineshs said:**
> May be bug in 9.10
[http://techtitbits.com/2010/04/resolving-the-network-manager-bug-in-ubuntu-9-10/](http://techtitbits.com/2010/04/resolving-the-network-manager-bug-in-ubuntu-9-10/)
If you have run pppoeconf try
 ```
pon dsl-provider
``` (in a terminal) to connect and```
poff dsl-provider 
```to disconnect
         Thank you for your reply. I can access Internet using pon ! However , network manager applet is still showing "device not managed" error. However , I was unable to install fix using url that you posted.

---

### Post by dineshs on 2010-07-26
My suggestion is
1)Continue with pon (you may install gpppon for a gui)if you are OK with it
```
sudo apt-get install gpppon
```
and create launcher 
Right click on the desktop and click create launcher
type-Application in terminal
name-internet(say)
command-sudo gpppon
then click on the icon- if you want to change the default icon
and click OK
Or
2)Upgrade to 10.04 and use DSL tab in NM

---

### Post by Iowan on 2010-07-26
Dunno if [this]("http://ubuntuforums.org/showpost.php?p=7041625&postcount=4") will help for a DSL connection...
(only offered as an option )

---

### Post by pushkar_k on 2010-07-27
> **dineshs said:**
> My suggestion is
1)Continue with pon (you may install gpppon for a gui)if you are OK with it
```
sudo apt-get install gpppon
```and create launcher 
Right click on the desktop and click create launcher
type-Application in terminal
name-internet(say)
command-sudo gpppon
then click on the icon- if you want to change the default icon
and click OK
Or
2)Upgrade to 10.04 and use DSL tab in NM
I can access internet using pon although it didn't work a few times. Upgrading to 10.04 is not an option right now . I will definitely try GUI you recommended. Thanks for your reply . I will also try commenting those line in "interface" files

---

### Post by pushkar_k on 2010-07-27
> **Iowan said:**
> Dunno if [this]("http://ubuntuforums.org/showpost.php?p=7041625&postcount=4") will help for a DSL connection...
(only offered as an option )
    It partiallty worked for me , in the sense. Now its not showing "Device not managed" and showing dsl connection but I am still unable to connect using that. I have to use "pon" to connect to internet. Thanks for  your reply .

---

### Post by naveen9885 on 2010-07-28
Can some one help me with this issue in the link.[ http://ubuntuforums.org/showthread.php?t=1537782]("http://ubuntuforums.org/showthread.php?t=1537782")

---

### Post by dineshs on 2010-07-28
> **pushkar_k said:**
> It partiallty worked for me , in the sense. Now its not showing "Device not managed" and showing dsl connection but I am still unable to connect using that. I have to use "pon" to connect to internet. Thanks for  your reply .
I think now you can edit /etc/network/interfaces so that it contains only those 2 lines.Then reboot and try DSL connection via NM

---

### Post by pushkar_k on 2010-07-28
> **dineshs said:**
> I think now you can edit /etc/network/interfaces so that it contains only those 2 lines.Then reboot and try DSL connection via NM
                Yes , I tried that once , it did not connect after rebooting. I will try once again. For now , I am able to access Internet through pon.

---

