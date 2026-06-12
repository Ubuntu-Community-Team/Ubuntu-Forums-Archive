---
title: "Anybody! Wireless gurus? Help"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by Rickkm on 2009-05-02
[SIZE=3]Is there a wireless ](*,)[SIZE=6][COLOR=DarkRed] .inf[/COLOR][/SIZE] file available for an EVO610C laptop with a W200 Wireless card. I would like to feed the file to the NDISwrapper as directed by the Ubuntu manual.[/SIZE]

---

### Post by chili555 on 2009-05-02
Wow! I need to turn down the lights so I can read your blinding post! Seriously, bigger fonts and bright colors do nothing to enhance your message and may actually turn off some gurus that don't have my incredible patience.

Compac reputedly changed the chipset a few times so that one W200 chipset may not be the same as another. Let's see which one you actually have. Please open a terminal and do:```
lspci | grep -i wireless
```Please post the result.

At least one of the W200 chipsets will work out of the box, that is, without ndiswrapper, with the addition of firmware.

---

### Post by Rickkm on 2009-05-02
[COLOR=DarkSlateBlue]> **chili555 said:**
> Wow! I need to turn down the lights so I can read your blinding post! Seriously, bigger fonts and bright colors do nothing to enhance your message and may actually turn off some gurus that don't have my incredible patience.

Compac reputedly changed the chipset a few times so that one W200 chipset may not be the same as another. Let's see which one you actually have. Please open a terminal and do:```
lspci | grep -i wireless
```Please post the result.

At least one of the W200 chipsets will work out of the box, that is, without ndiswrapper, with the addition of firmware.[/COLOR]  

Sorry about the font - O replies on 1st post. Would have used a seachlight if I thought it might get me past this last hurdle.  Suggested command shows nothing. Could you peek at my 1st posting? ...as follows:

Have installed Unbuntu 9.04 ... it all looks great. My 1st Linux. WIRED LAN WORKS >>>But no wireless. What I know is:

lsusb (shows)
rick@rick-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

After I hit an "Fn" plus the "F2" keys the lsusb shows:

rick@rick-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 049f:0076 Compaq Computer Corp. Wireless LAN MultiPort W200
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I've installed the ndisgtk package ... it's ready to go. The "Using Windows Wireless Drivers" doc says simply point the ndisgtk program at the correct Windows .inf file. [COLOR=Red]And there is the rub[/COLOR]. I cannot find such a file anywhere on the web. I did find the Windows EXE driver for a Wireless LAN MultiPort W200. I even installed the "WINE" program to look at all of the files in the Windows EXE prog...no files were an .inf file.

Also:
rick@rick-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:02:a5:c3:be:ed
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=full firmware=N/A ip=192.168.2.103 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
 [COLOR=Red] *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f2:ae:28:fa:2e:4c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[/COLOR]
ANY IDEAS HOW I MIGHT LOCATE THE RIGHT *.inf FILE? IS THAT ALL I NEED? 

Thanks from the newest guy on this forum.
Thanks for the reply.

---

### Post by chili555 on 2009-05-02
May I assume the file you have is *sp28252.exe*? Hook up your laptop to an ethernet cable and do:```
sudo apt-get install cabextract
cabextract sp28252.exe
cd Driver/w2kxp
ls | grep .inf

```I think you will find *WLCOMALL.inf*. You should then be able to fire up ndisgtk, point it to the Driver/w2kxp folder and be off and running.

We don't need no stinking wine!

---

### Post by Rickkm on 2009-05-02
Thanks ... got all that done ok. But sys won't reboot with "active" (light on) wireless. Have to do a couple of ALT-CNTL-DEL to get up. Guess this Evo refuses to run wireless. Bummer. Boots ok if I remove the wireless hw driver. I'll ask the form if there is anyone _actually_ using a Multiport W200 Wireless otion on an EVO610C laptop with Ubuntu 9.04. It "saw" my Linksys router w/Windows. Thamks again.

---

### Post by chili555 on 2009-05-02
May we please see, with the device inserted:```
sudo ndiswrapper -l
```Thanks.

---

