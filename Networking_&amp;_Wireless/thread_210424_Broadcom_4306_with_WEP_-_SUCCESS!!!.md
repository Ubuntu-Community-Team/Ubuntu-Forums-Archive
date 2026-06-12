---
title: "Broadcom 4306 with WEP - SUCCESS!!!"
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by robstockley on 2006-07-06
Today is my second day grappling with a 4306 in my ASUS notebook. It worked fine under Breezy using the ndis driver. After a fresh install of Dapper I couldn't make it work. Both ndis and the builtin bcm43xx drivers produced the same result.

[INDENT]All drivers loaded with hardward detected.
Associated with AP no worries
Failure to complete dhcp handshake[/INDENT]

Setting a static IP made no difference. The freaky thing was that sometimes it would simply work without rhyme or reason. If I took it down then it would not start again. So then I got desperate and started tinkering and you know what? I found something.

When I set an encryption key using iwconfig the mode defaults to restricted. This makes sense, however, I've found that I need this set to open in order to get connected. The man page for iwconfig does suggest that the meaning of open/restricted is hardward dependent so perhaps this is not so strange. 

Anyway I've seen a few posts with people describing similar issues so I thought I'd share my findings. I am using the following script to connect wireless with 100% success. 

```
#!/bin/bash

sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo iwconfig eth0 essid 8khouri
sudo iwconfig eth0 rate 54MB
sudo iwconfig eth0 key open XXXXXXXXXX
sudo dhclient eth0

```

I hope this saves someone a heap of frustration. My only remaining niggle is with wireless assistant. Can anyone tell me where the default config file is? 

Rob

---

### Post by PsychicPsycho3 on 2006-07-06
This worked for me!!

I'm using a Dell Inspiron 8200 with BCM4303 firmware. I think what actually made the difference was setting the essid and rate by hand, somehow when I typed it in the networking window, it would always be different when I checked iwconfig. I also had to disable the wired connection, but this seems to be a common issue.

The only question is, am I going to have to do this on ever boot?

---

### Post by An3Azz on 2006-07-07
Well this works for me to, with a Belkin f5d7011 card. One problem that I do have is that it looses signal much easier and mor often under linux than under windooze. Any suggestions?

---

### Post by amormachine on 2006-07-07
Finally, some help with BCM4306!!!  COuld you post details of how scripting works?  I'm quite new to this ... Also, are of the options changed permenant?  Basically, I've got an external wireless card working and I'm terrified that by screwing around with the internal one, the external one will be effected.

Thanks!

---

### Post by An3Azz on 2006-07-07
you want the internal one to start up without affecting the external one, or am I wrong? I'm quite a n00b myself but I got min working just fine, except for the weak signal....is there anyway that you could boost it I wonder.

---

### Post by robstockley on 2006-07-13
> **PsychicPsycho3 said:**
> 
The only question is, am I going to have to do this on ever boot?

Probably not. To make it automatic you need to update /etc/network/interfaces. Open a console and type;

```
sudo nano /etc/nano/interfaces
```

If you prefer a gui then instead try;

```
sudo kate /etc/nano/interfaces &> /dev/null
```

The '&> /dev/null' bit simply hides the console output from the gui. Find the section the relates to your wireless interface - for me that's eth0. Make sure it looks something like this;

```
auto eth0
iface eth0 inet dhcp
pre-up ifconfig eth0 up
wireless-essid 8khouri
wireless-rate 54MB
wireless-key open XXXXXXXXXX

```

[1] The first line tells the system to configure this interface automatically at boot time.

[2] The second line defines the interface for configuration by DHCP. 

[3] The third line is important. This tells the system to run the command "ifconfig eth0 up" before configuring the interface.

[4-6] The rest is self explanatory. Make sure your essid and key details match your wireless environment.

Note that this setup assumes that you will always be connecting to the same access point as I do.

Hope this works for you.

---

### Post by robstockley on 2006-07-13
> **An3Azz said:**
> you want the internal one to start up without affecting the external one, or am I wrong? I'm quite a n00b myself but I got min working just fine, except for the weak signal....is there anyway that you could boost it I wonder.

You could try increasing the transmit power of your adapter. First check to see what it is currently set to. Type 'sudo iwconfig' and look for the following line;

```
Bit Rate=54 Mb/s   Tx-Power=15 dBm
```

As you can see, my adapter is set to 15dBm. A quick Google search showed people using values from 10 to 25dBm but that doesn't necessarily mean that your adapter can do the same. Perhaps check the setting under M$ and start by making them match.

To change the value open a console a type 'man iwconfig'. Scroll down to the section on txpower and have read. When you're ready to set the value simply type the following into a console,

```
sudo iwconfig eth0 txpower 15
```

Warning. Be very careful not to set the value higher than is necessary. If that fixes it then you should add the following line to /etc/network/interfaces

```
wireless-txpower 15
```

Hope that sorts you out.

---

### Post by wolfmaniac on 2006-07-13
do i have to install rivers first using ndis or bcmxxx first then to perfom the above action

---

### Post by robstockley on 2006-07-15
> **wolfmaniac said:**
> do i have to install rivers first using ndis or bcmxxx first then to perfom the above action

Yes. This thread assumes that either ndiswrapper or the builtin bcm43xx drivers are installed and working properly. 

When you get to the stage where you can see other access points but the connection fails due to no response from the DHCP server then this thread could help.

Rob

---

