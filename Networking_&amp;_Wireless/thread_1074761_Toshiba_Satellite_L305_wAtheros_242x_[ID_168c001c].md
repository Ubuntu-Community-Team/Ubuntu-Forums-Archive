---
title: "Toshiba Satellite L305 w/Atheros 242x [ID 168c:001c]"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by Testrum on 2009-02-19
Hello Ubuntu-ians,
 After a complete fresh install of Ubuntu I'm having trouble's setting up my wireless :(

I've executed the following commands:
```
sudo aptitude install linux-backports-modules-intrepid
```
```
sudo aptitude install linux-backports-modules-intrepid-generic
```

Here's my wireless card info:
```
Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c]
```

I have Ndiswrapper installed but can't find the correct Windows driver :???:

Here's a picture of packages I have available:
[img]http://i43.tinypic.com/ml5bg8.png[/img]

---

### Post by Ketara on 2009-02-19
Before we get started, are you running Hardy or Intrepid?

Ndiswrapper is a tool that attempts to make windows drivers work in a Unix based operating system. You won't find windows drivers in Synaptic because Synaptic is going to give you files designed to work in Ubuntu.

There are multiple ways to make an Atheros 242x card work (not all of the fixes work for everybody), but lets start with ndiswrapper since you have it installed, and any other fix will generally want you to remove ndiswrapper.

If you still have your windows partition (assuming this Toshiba came with windows pre-installed) you should be able to find your Atheros driver. It will be a .inf file named something like "netathwx.inf" or "net5211.inf" If you cannot find it you should be able to find downloads for those files on google.

Once you have the driver, go to System->Administration->Windows Wireless Drivers and set it to use that driver with "Install New Driver" You will have to locate the driver on your hard drive but it doesn't matter what folder it's in.

Then you want to disable your existing drivers, so there aren't multiple drivers attempting to claim the card. (this usually makes none of them work) Go into System->Administration->Hardware Drivers and disable HAL access layer, ath5k or ath9k. If they're not there that's fine.

After that, just to be safe open up a terminal (applications->accessories->terminal) and type:

sudo modprobe ndiswrapper

And then reboot. If that doesn't work, we'll keep going from there.

---

### Post by Testrum on 2009-02-19
> **Ketara said:**
> Before we get started, are you running Hardy or Intrepid?

Ndiswrapper is a tool that attempts to make windows drivers work in a Unix based operating system. You won't find windows drivers in Synaptic because Synaptic is going to give you files designed to work in Ubuntu.

There are multiple ways to make an Atheros 242x card work (not all of the fixes work for everybody), but lets start with ndiswrapper since you have it installed, and any other fix will generally want you to remove ndiswrapper.

If you still have your windows partition (assuming this Toshiba came with windows pre-installed) you should be able to find your Atheros driver. It will be a .inf file named something like "netathwx.inf" or "net5211.inf" If you cannot find it you should be able to find downloads for those files on google.

Once you have the driver, go to System->Administration->Windows Wireless Drivers and set it to use that driver with "Install New Driver" You will have to locate the driver on your hard drive but it doesn't matter what folder it's in.

Then you want to disable your existing drivers, so there aren't multiple drivers attempting to claim the card. (this usually makes none of them work) Go into System->Administration->Hardware Drivers and disable HAL access layer, ath5k or ath9k. If they're not there that's fine.

After that, just to be safe open up a terminal (applications->accessories->terminal) and type:

sudo modprobe ndiswrapper

And then reboot. If that doesn't work, we'll keep going from there.

I'm on Intrepid Ibex brand new fresh install.

I don't have my Vista partition anymore but I will google the files you mentioned, will edit my post after I've located and installed it.

***Edit*** I've googled both files and tried to install them both ndiswrapper and it said gave me an error stating "invalid driver" for both files :???:

---

### Post by Ketara on 2009-02-19
Okay, time to troubleshoot.

Check out this thread: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

When you got the downloads it should have been zipped folders with a number of files, not just the .inf

Try this guy: [http://www.mediafire.com/?emektlygdif](http://www.mediafire.com/?emektlygdif)

---

### Post by Testrum on 2009-02-19
> **Ketara said:**
> Okay, time to troubleshoot.

Check out this thread: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

When you got the downloads it should have been zipped folders with a number of files, not just the .inf

Try this guy: [http://www.mediafire.com/?emektlygdif](http://www.mediafire.com/?emektlygdif)
Okay downloaded, extracted, and this time ndiswrapper says the hardware is present :D

---

### Post by Ketara on 2009-02-19
Does it work?

---

### Post by Testrum on 2009-02-19
> **Ketara said:**
> Does it work?
I truned my wireless switch on and it's picked up Canyon's Restaurant and Summit 4 WLAN Connection's :D

Thank you soooo much for the help!

---

