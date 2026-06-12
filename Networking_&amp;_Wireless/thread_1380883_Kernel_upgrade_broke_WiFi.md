---
title: "Kernel upgrade broke WiFi"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by alanrlow on 2010-01-14
I'm running Ultimate Edition 2.4 on an Acer Aspire 3500 lappy, yesterday I allowed my system to upgrade the kernel (from 9.10 kernel 2.6.31-17 to 2.6.31-18 generic) as per usual but when it rebooted I had no WiFi. The NetworkManager Applet 0.7.996 has no Wireless Network shown and at the bottom section is missing the Connect to Hidden Network and Create New Wireless Network option. They're simply not there as an option. If I reboot into the earlier 2.6.31-17 kernel everything is OK. 

Alan.

---

### Post by Lutin on 2010-01-14
I have experienced exactly the same problem using an Acer Aspire 7003 with an Atheros AR2413 Wifi card. All well under kernel 2.6.31-17, but not with 2.6.31-18.

---

### Post by johann_in_uk on 2010-01-24
I had to rebuild the madwifi driver to get my wireless back. Go to 
System\Administration\Network Tools. In the first tab, Devices, there is
a dropdown list for Network device. Pop it up and check if it list a 
device called (ath0). If not, you may have the same issue I had and need 
to install the latest drivers. Compiling drivers sounds scary, but was 
really easy, thanks to the kind people at madwifi.

What I did: I downloaded the latest driver source code from this location:

[http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz]("http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz")

to a folder to my desktop and extracted it. I then opened a console 
(Applications\Accessories\Terminal), and changed to new driver directory

cd Desktop/madwifi-0.9.4-r4110-20100119/

then I followed the step by step instructions given here:

[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo]("http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo")

and hey presto! My wireless card was back and connection restored 
immediately. You need a wired connection of course to download the 
sources ;)

Btw, Acer Aspire 9300 with an Atheros AR2413

---

### Post by Lutin on 2010-01-26
I might give that a try. But I still don't understand why a kernel upgrade should wipe out my wifi connection. It worked previously, so why not now?

---

### Post by 8086 on 2010-01-26
You are not the only one! Do a search for 2.6.31-18 and there are lots of wifi problems. I have a Acer as well, and the wifi got fcked up by this last update as well.

---

### Post by 8086 on 2010-01-28
I have searched launchpad and I cannot see a single reference to this problem there. You need to post a bug report there!

The address is [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by Lutin on 2010-01-29
I have just tried twice to post a bug report through Launchpad - and failed both times.

All I got for my efforts was -

Error ID: OOPS-1490H1019  and

Error ID: OOPS-1490D1019.



Hopefully someone else has managed to report this as I apparently cannot.

---

### Post by falconindy on 2010-01-29
> **alanrlow said:**
> I'm running Ultimate Edition 2.4 on an Acer Aspire 3500 lappy, yesterday I allowed my system to upgrade the kernel (from 9.10 kernel 2.6.31-17 to 2.6.31-18 generic) as per usual but when it rebooted I had no WiFi. The NetworkManager Applet 0.7.996 has no Wireless Network shown and at the bottom section is missing the Connect to Hidden Network and Create New Wireless Network option. They're simply not there as an option. If I reboot into the earlier 2.6.31-17 kernel everything is OK. 

Alan.
Did you have to enable or compile any extra drivers to get your wireless working on 2.6.31-17? If you did, you'll need to recreate the same efforts to enable networking on 2.6.31-18 (and any subsequent kernels).

---

### Post by Lutin on 2010-01-30
One thing that I did notice, and included in my failed bug report, is that under the old kernel 2.6.31-17, my Atheros card is described as "Bus Master: Yes" in Hardware Info, PCI Devices.

However, under the updated kernel this is reported as "No".

Has something in the kernel update changed that means the card is not even being recognised?

---

### Post by drpjkurian on 2010-01-31
Hi Guys
Please do not consider it as a BUG. The driver which was in use in earlier version of Kernel has to be recompiled(Not reinstallation)

Well I have a solution for those who are on Madwifi drivers.
By following these commands, you do not have to recompile it again during Kernel upgrades.

Now type the following commands in terminal

1.

```
sudo nano /etc/apt/sources.list
```

From there make sure you uncomment anything that starts with "deb" in there. So changer it from "#deb" to "deb" Something along thoes lines. To exit and save hit "CTRL+X" the answer "YES" to do you want to save, then finally hit "ENTER"

2.
Code:

```
sudo apt-get update && sudo apt-get upgrade

```

3.
```
sudo apt-get install build-essential libssl-dev linux-headers-`uname -r` subversion
```
and instead of "linux-headers-`uname -r` I would suggest "linux-headers-generic" (or -server for server). This way the headers will be updated with the kernel. The way you have it will work but will cause confusion down the line when the kernel gets updated.

4.```
sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi-ng
```

5.```
cd madwifi-ng
```

 6.```
echo "
#Remove To Install MadWIFI Drivers
blacklist ath9k
blacklist ath5k">> /etc/modprobe.d/blacklist
```

7.```
sudo -i
```

8.```
make && make install
```

9.```
echo ath_pci >> /etc/modules
```

Reboot the machine.

You do not have to worry about the kernel updates hereafter.

---

### Post by Lutin on 2010-01-31
Thank you for posting that drpjkurian. Unfortunately, this does not help me, as I was not using the Madwifi drivers.

Ho hum.

---

### Post by Lutin on 2010-01-31
Finally managed to post a bug report on Launchpad, using another machine.

---

### Post by Lutin on 2010-02-05
Latest update has restored wireless.

Kernel 2.6.31-19.56

---

### Post by 8086 on 2010-03-15
That is really too bad. But at least it seems it was fixed in the release that followed :)

---

