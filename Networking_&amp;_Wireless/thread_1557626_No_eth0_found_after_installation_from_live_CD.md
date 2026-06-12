---
title: "No eth0 found after installation from live CD"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by AndesHelp on 2010-08-21
I tried searching but received hundreds of unrelated posts.

When using the Ubuntu 10.04 Live CD I had no problem connecting through my wired network connection.  After installation all I can find is the Wireless connection.

I have a Toshiba Satellite A70 laptop.  A check of the system shows no eth0 available.  What do I need to do to get the wired connection back again?

Also, if the wired worked before installation, why doesn't it work afterwards?

Thanks

---

### Post by grahammechanical on 2010-08-21
May I suggest that you run the live CD again and go to edit connections in the network manager. Right click on the icon. Make a note of the details of your wired connections. Then go back into your working installation and under Edit Connections create new wired connections using the information you have collected. It is just an idea.

regards.

---

### Post by AndesHelp on 2010-08-21
Thanks for the tip.  If I understand it, you are saying to write down the readings from the ifconfig.  

The problem is worse than just the network settings.  My Ubuntu says that there is no ethernet NIC available  The only ethernet found is the Atheros WIFI Adapter.  

I did find the NIC adapter driver, Intel e1000, but have been unble to get it to install.  Since Ubuntu does not allow me Root Sign in, I have been unable to even create the required directories for the driver installation.

---

### Post by Iowan on 2010-08-21
> **AndesHelp said:**
> ...Since Ubuntu does not allow me Root Sign in...
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by AndesHelp on 2010-08-21
Thanks for the link to the Ubuntu documentation.  Maybe I can use it in the future.

I am not familiar enough with the Linux command line syntax yet, to try the sudo entries.  And, I ran out of time.  I had to deliver the laptop this morning.  They only needed the wireless to be working.

It is still confusing why the wired NIC worked for the Live CD and then Ubuntu could not even find the NIC after it was installed to the HDD.

---

