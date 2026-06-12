---
title: "How do I connect to a wireless internet connection?"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by JoeCenedella on 2010-02-12
I've been using this network forever With windows and I can't figure out how to connect to it now with ubuntu...I have a build-in wireless card and I know the name/password of the connection, but my computer cannot seem to locate it. I've looked through guides and none of them work... Lcan anyone help?

---

### Post by Luisnux on 2010-02-12
What version of Ubuntu are you using?  It's just that there are a few differences in the procedure for installing and configuring the drivers.  I've used Ubuntu 8.04, 8.0, 9.04 and now 9.10 and the installation and configurations has always been a bit different.  However, if you could put that as well as what type of card you have I'll be able to give you more specific info.

---

### Post by JoeCenedella on 2010-02-12
I'm using 9.10... I don't know how to determine my wireless card,though.

---

### Post by chewearn on 2010-02-12
Make sure wifi hardware is turned on.

Open a terminal, enter this command:
```
lshw -c network
```This should tell us the network hardware info.

---

### Post by lyall on 2010-02-12
see the following link 
[https://help.ubuntu.com/community/NetworkDevices]("https://help.ubuntu.com/community/NetworkDevices")

then look at Wireless networking

it is a place to start

good luck and have fun learning

---

### Post by Xog on 2010-02-12
if there isn't anything useful from that, give the results of these

```
lspci
```

and

```
iwconfig
```

---

### Post by JoeCenedella on 2010-02-12
> **Xog said:**
> if there isn't anything useful from that, give the results of these

```
lspci
```

and

```
iwconfig
```

It says"no wireless extentions"

---

### Post by Xog on 2010-02-12
copy+paste the results from the lspci command

---

### Post by JoeCenedella on 2010-02-12
I can't. I'm using my cell phone. I don't have Internet on the computer I'm trying to get Internet on...

---

### Post by Xog on 2010-02-12
You don't have a flash drive? Or a partition?

Anyways, I'm not sure about you but on mine, it says Network controller: NAME OF YOUR PCI CARD

mine are:

09:07.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
09:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

---

### Post by JoeCenedella on 2010-02-12
Broadcom corperation BCM4311 802.11b/g WLAN ( rev 01)

---

### Post by Xog on 2010-02-12
here u go, jump to post 4 (not page 4)

[http://ubuntuforums.org/showthread.php?t=346083](http://ubuntuforums.org/showthread.php?t=346083)

---

### Post by Luisnux on 2010-02-12
On Ubuntu 9.10 the tools required for wireless are already installed, so more than likely you're having a little bit of issues with the drivers.  You can either connect to the internet and download the drivers by doing System-->Adminstration-->Harware drivers, or you can connect to the internet (we're talking about Ethernet of course) and install "broadcom" drivers through synaptic package manager.  Now if you don't have that option (ethernet), then you can use the guide that I found at the following website:  [http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/](http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/).   It worked just fine with my rather problematic wireless card.  It was dropping signal all the time, and it would not give me great range, not it works better than ever.  Keep in mind that you will need the drivers to be able to use that guide.  You can find the drivers among the disks that came with your laptop.

---

### Post by PRC09 on 2010-02-12
The following link should enable you to connect.......





[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by JoeCenedella on 2010-02-13
Thanks for the help and links... But they both require Internet connection already... I can get an Ethernet connection in a few days, but I really would like to have it sooner.

Is there any way to solve this without a connection?

---

### Post by PRC09 on 2010-02-13
The link I posted has how to install from the cd under .....2.IF WIRED CONNECTION DOES NOT WORK:

---

### Post by JoeCenedella on 2010-02-13
> **PRC09 said:**
> The link I posted has how to install from the cd under .....2.IF WIRED CONNECTION DOES NOT WORK:

Yeah, I know. The CD is at home, so I'd need a connection to burn another one, anyway...ugh. I'm in a horrible position computer-wise right now..

---

### Post by PRC09 on 2010-02-13
Sorry,you would need the CD or an internet connection to enable the wireless...

---

