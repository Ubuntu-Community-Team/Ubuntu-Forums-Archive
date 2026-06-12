---
title: "Wpa_supplicant &amp; Wired networking"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by 71GA on 2010-03-04
Hello i am a Ubuntu 9.10 user and have a problem. I want to access network that is protected by a wpa_supplicant. I first tried using these instructions (it is in Slovene language, so only look at pictures) 

[http://prijava.sd.uni-lj.si/navodila/linux/nm0.7/](http://prijava.sd.uni-lj.si/navodila/linux/nm0.7/) 

which worked fine for a while, but then it didn't connect anymore so i uninstalled network manager because i decided to setup my conection manually using Terminal (#).

**sudo apt-get remove network-manager-gnome** 

Then i tried to manually setup connection. I first installed latest version of wpa_supplicant on **Ubuntu packakge page** (picture below).

[[img]http://www.shrani.si/t/2q/Cg/3otWbRVd/screenshot-2.png[/img]](http://www.shrani.si/?2q/Cg/3otWbRVd/screenshot-2.png)

I used command **dpkg -i /.../wpasupplicant_0.6.9-3ubuntu1_amd64.deb** to install. 

To check it i used command **which/wpa_supplicant** and get what is listed in picture below:

[[img]http://www.shrani.si/t/10/12q/31FCn6f5/screenshot-1.jpg[/img]](http://www.shrani.si/?10/12q/31FCn6f5/screenshot-1.png)

Then i downloaded certificate **stud-dom.pem** from internet and put it in a folder which i created myself (picture below).

[[img]http://www.shrani.si/t/3F/Mz/2S7jwt3A/screenshot-4.jpg[/img]](http://www.shrani.si/?3F/Mz/2S7jwt3A/screenshot-4.png)

It was time to do some editing in some files so i used command  **gedit /etc/wpa_supplicant.conf** and edited this document like in a picture below (red text is where i inserted my **username** and **pasword**):

[[img]http://www.shrani.si/t/1w/111/22sDVBK9/screenshot-5.jpg[/img]](http://www.shrani.si/?1w/111/22sDVBK9/screenshot-5.png)

I then edited next file using command: **gedit /etc/network/interfaces** and added lines (shown in picture below) under a **eth0**.

[[img]http://www.shrani.si/t/3o/10k/4f7BGpw0/capture.jpg[/img]](http://www.shrani.si/?3o/10k/4f7BGpw0/capture.png)

the last one to edit was **/etc/default/wpasupplicant** and i added lines in a picture below. *(When i opened this file it was totaly empty so these lines are now only lines within a document)*

[[img]http://www.shrani.si/t/28/AE/4XoUIXmr/capture1.jpg[/img]](http://www.shrani.si/?28/AE/4XoUIXmr/capture1.png)

So it should work now right and when i try to use command sudo **/etc/init.d/wpasupplicant restart** to start wpa_supplicant i get this [COLOR="Red"]error:[/COLOR]

[[img]http://www.shrani.si/t/2j/qw/26oO5gbc/screenshot-8.jpg[/img]](http://www.shrani.si/?2j/qw/26oO5gbc/screenshot-8.png)

and if i use command **ifup eth0** i cant connect to network.

so i now decided to check **eth0** to see if anything is wrong and i type command **ifconfig -a** and get a list of interfaces (picture below).

[[img]http://www.shrani.si/t/y/el/3RmldTWc/screenshot-3.jpg[/img]](http://www.shrani.si/?y/el/3RmldTWc/screenshot-3.png)

I noticed it is something wrong... i have two eth0 connections. My internet provider told me my eth0 interface should look something like this: 

[B]eth0      Link encap:Ethernet  HWaddr 00:11:22:33:44:55
          inet addr:13.2.15.190  Bcast:13.2.15.191   Mask:255.255.255.192
          UP BROADCAST NOTRAILERS RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:226746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:100342043 (95.6 Mb)  TX bytes:23785810 (22.6 Mb)
          Interrupt:18 Base address:0x7800
[/B]
but mine is totaly different. 

[SIZE="5"]Does anyone know how to connect my computer online?[/SIZE]

---

