---
title: "New to Ubuntu, need help Configuring internet"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by coreys.pc.repair on 2009-08-16
Hi everyone,  I am a complete noob when it comes to any Linux distro, but I really want to learn it that is why I did a dual boot with XP Pro.  I'm learning everything slowly but one thing I can't figure out is how to configure my internet.  I am using CenturyTel as my ISP and am using the Westell D90-327W-06 Modem/Router.  I have it hooked up via USB connection.  Any help is greatly appreciated.

Thank You,
Corey

---

### Post by ibutho on 2009-08-16
Hi and welcome to the forum.

Is there a way to switch the connection to ethernet instead of USB? If its an option, go with Ethernet because it usually just works with most operating systems without any additional configuration.

---

### Post by coreys.pc.repair on 2009-08-16
No can do, I have an ancient Sony Vaio desktop and it has some no name ethernet card in it and I don't have the back up disc with the driver anymore and I cannot find it online anywhere.

---

### Post by dlmarti on 2009-08-16
> **coreys.pc.repair said:**
> No can do, I have an ancient Sony Vaio desktop and it has some no name ethernet card in it and I don't have the back up disc with the driver anymore and I cannot find it online anywhere.

My suggestion would be to just plug both the ethernet and USB in.  Linux will use the Ethernet, and your Windows can use the USB.

As to the drivers, I'm very surprise you can't find them online (Linux probably doesn't need them anyways).

---

### Post by Ranko95 on 2009-08-16
it took me a while to get the internet working on my computer too. You can use ndiswrapper to install the .inf file if you need to. Do you have the installation cd? the driver could be found within that cd

---

### Post by coreys.pc.repair on 2009-08-16
The internet install disc or the Ubuntu Install Disc?

---

### Post by ibutho on 2009-08-19
> **coreys.pc.repair said:**
> No can do, I have an ancient Sony Vaio desktop and it has some no name ethernet card in it and I don't have the back up disc with the driver anymore and I cannot find it online anywhere.

You usually do not need to install additional drivers in order to get an ethernet card working on Linux. Most will just work out of the box without you having to do anything. If you want to enable ethernet for Windows as well, run your Linux installation go to Applications -> Accessories -> Terminal and enter
```
sudo lspci | grep -i net
```
That will show you what network cards are installed on your computer and you can then search for the Windows drivers online.

---

