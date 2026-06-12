---
title: "can't detect wireless networks"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by SrEstroncio on 2008-12-21
Hello Ubuntu community, I have a little problem and I was wondering if I could ask for a little advice.

I just bought a new laptop and I installed Ubuntu 8.10 for 64 bit architectures and I believe I have an issue with my network settings, specially in the wireless department. I have only used Ubuntu 6.06 and 7.10 before trying out 8.10, but I shocked me when I didn't see my laptop automatically connect (or at least detect) my wireless internet signal or that of my neighbors.

To be more precise, I don't think my laptop recognizes wireless signals when in Ubuntu: if I right click the Networking icon in the upper bar every option is grayed-out and the only thing I can modify is the menu in which you manually configure your connections. On that point, I tried manually configuring the access to my wireless network, with no apparent results.

It might be a useful to know my computer's connection device is listed under the restricted drivers list, and it is activated.

I humbly ask for a little help here, as I am a little rusted in my use of ubuntu and I am not an erudite in it's workarounds.

Sorry for not providing any screenshots, it didn't occur to me to take any and I can't take them now as I am using Vista right now. Also, sorry if my English seems kind of unnatural, it is not my mother-tongue.

Here are the specs of the computer which I am currently using (and I am having the issues with):

HP Pavillion dv5 Notebook PC

Processor: AMD Turion X2 Ultra Dual-Core Mobile ZM-80 2.10GHz
RAM: 4GB
Videocard: ATI Radeon HD 3200
Wireless device: Atheros AR5007 802.11b/g WiFi Adapter

Again, thank you all for your attention.

---

### Post by grandmaster on 2008-12-21
Is there a physical wireless switch on the computer?
I have a dv6000 and intrepid and the wireless worked out of the box.

*edit

If not try this for atheros cards as it worked for me on my acer aspire one.

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)


Wireless module

    *

      Seems to work out of the box for some. If not:
      disable ath_pci( use ath5k )

  sudo rmmod ath_pci

    *

      System->HardwareDrivers-> ( disable Atheros 802.11 wireless lan cards )

  sudo apt-get install linux-backports-modules-intrepid-generic <<BR>>

    * If this doesn't work, try enabling the backports repositories in /etc/apt/sources.list (remove the # signs in front of them)

      System->HardwareDrivers-> ( enable 5xxx series of Atheros 802.11 wireless lan cards )

  sudo modprobe ath5k

    * For some reason it seems to be necessary to add the following line to /etc/modules, so Ubuntu will automatically load the driver when the system comes up: 

ath5k

---

### Post by SrEstroncio on 2008-12-21
There is a "Physical" wireless switch, which is more kind of a led indicator which turns blue when wireless is on and red when it is off, the indicator is not a button but "pressing" it turns the wireless on/off.
The led stays red when in ubuntu, and does not change even if I press it.

Also, thanks for the help, I'm gonna go try it out, I'll drop by to say how it went. If anyone has some more ideas they'll be really appreciated.

---

### Post by superprash2003 on 2008-12-21
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by acreech on 2008-12-21
> **SrEstroncio said:**
> There is a "Physical" wireless switch, which is more kind of a led indicator which turns blue when wireless is on and red when it is off, the indicator is not a button but "pressing" it turns the wireless on/off.
The led stays red when in ubuntu, and does not change even if I press it.

Also, thanks for the help, I'm gonna go try it out, I'll drop by to say how it went. If anyone has some more ideas they'll be really appreciated.

Make sure that your "Physical" switch is on while trying to work on this problem. I would suggest that you install the backports as suggested in the link below (post #21). I however get it to work on my machine using the suggestion in post #4. Either of these ways should get the wireless to work for you. good luck. 

[http://ubuntuforums.org/showthread.php?t=1007434&page=3]("http://ubuntuforums.org/showthread.php?t=1007434&page=3")

---

### Post by SrEstroncio on 2008-12-21
> **superprash2003 said:**
> [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

Nothing in here helps, I don't have the "madwifi" file in modprobes.d, nor I can find the ath5k line to comment, and I went through all the files there.

---

### Post by jfernyhough on 2008-12-21
I'd think that blacklisting the ath_pci driver will make your wireless card work.

$ gksudo gedit /etc/modprobe.d/blacklist

Add
blacklist ath_pci 

to the end of the file and reboot.

---

### Post by SrEstroncio on 2008-12-21
I tried the suggestion grandmaster said and I got this in the very first step.

srestroncio@lucifer:~$ sudo rmmod ath_pci
ERROR: Module ath_pci does not exist in /proc/modules
srestroncio@lucifer:~$

I tried installing sudo apt-get install linux-backports-modules-intrepid-generic but a message came out saying there is no package with that name (I did enable the repositories) dang, I might be too dumb or nothing seems to work.

I also tried what jfernyhough said and I don't see any change.

---

### Post by SrEstroncio on 2008-12-21
Dang, and now the Atheros driver in Hardware Drivers is disabled by default and can't be turned on T__T.

I tried what was suggested in the thread posted by acreech, but even with all the repositories enabled I still get no hits when I search for "backports" in the synaptic package manager, I might be doing something wrong because nothing seems to work.

---

### Post by superprash2003 on 2008-12-23
try do apt-get install linux-backports-modules-intrepid without generic

---

### Post by jfernyhough on 2008-12-23
Not being daft, but is the card enabled in the BIOS?

What's the output of nm-tool ?

---

