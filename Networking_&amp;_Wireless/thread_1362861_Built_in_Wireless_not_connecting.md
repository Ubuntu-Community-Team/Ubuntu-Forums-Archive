---
title: "Built in Wireless not connecting"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by phahtrox on 2009-12-23
I have a a505-s6985 Toshiba laptop. The wired internet access is working. Sadly the wireless does not. I've downloaded the Ndiswrapper program but I get lost in some of the tutorials. I'm extremely new to Ubuntu and Linux systems, I'm willing to stick it threw to get it working. 

The WiFi card is built in. It's the RealTek Brand (the exact type I'm not sure of).

I've tried to get the drivers from my W7 setup but something just doesn't work right. I went into my W7 partition and tried to find the drivers, but all I could find was the DLL's. Then I tried to download the drivers from the Toshiba site. It installs as soon as I open it so I can't get to the actual drivers. Then I tried to open it up in Ubuntu then I just couldn't open it because it was .exe.

---

### Post by dvlchd3 on 2009-12-23
Please run this command.  This will give us the exact wireless card in your computer:

```

lspci | grep Network

```

---

### Post by =not4prophet= on 2009-12-23
the exe from Toshiba is a self-extracting zip file.  You can open it using the archive manager and extract the files you need that way.

---

### Post by phahtrox on 2009-12-23
> **dvlchd3 said:**
> Please run this command.  This will give us the exact wireless card in your computer:

```

lspci | grep Network

```

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
> **=not4prophet= said:**
> the exe from Toshiba is a self-extracting zip file. You can open it using the archive manager and extract the files you need that way. 

I don't know how to do that, sir.

---

### Post by phahtrox on 2009-12-26
Can anyone help me??

---

### Post by Valon Majere on 2009-12-30
I've got this problem with the Toshiba A505-s6985 as well, haven't had any luck with it either.

p.s.: Just right click on the .exe and hit "extract here"

---

### Post by Valon Majere on 2010-01-14
bump: Anybody out there?

---

### Post by bkratz on 2010-01-14
> **phahtrox said:**
> 03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
 

I don't know how to do that, sir.




Here is an interesting thread about the 8172, hopefully it helps

[http://ubuntuforums.org/showthread.php?t=1367871&highlight=8172](http://ubuntuforums.org/showthread.php?t=1367871&highlight=8172)

---

