---
title: "D-Link G120"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by tronica on 2006-06-06
I have a usb G120 and ubuntu dapper reconizes it but when i enable it, and i try to browse the net, its a no go.  I've never messed with wi-fi stuff on linux so this is new to me. can some help me get this going. i think i'm close but just can't figure out the last bit.

> lyle@ubuntu:~$ lsusb
Bus 002 Device 004: ID 2001:3701 D-Link Corp. [hex] DWL-G120 Spinnaker 802.11b
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 001 Device 002: ID 046d:c30a Logite[COLOR="Black"][/COLOR]ch, Inc.
Bus 001 Device 001: ID 0000:0000


---

### Post by jml on 2006-06-06
Check out this site.  You may find the help you need.  I have not had much success with USB wireless devices personally.

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Joe

---

### Post by tronica on 2006-06-06
well i followed the stuff on that link, but still not having any luck. Ubuntu detects it and sees it and make the power light on it come on. Any other ideas.

---

### Post by tronica on 2006-06-08
anybody else have ideas on making this work. i really need it. Thanks

---

### Post by barrmulio on 2006-06-08
i have a similiar thread over at [http://ubuntuforums.org/showthread.php?p=1114413#post1114413](http://ubuntuforums.org/showthread.php?p=1114413#post1114413) for the same card

ubuntu can recognize the card in network configuration, as can ndisgtk, but no link to my router

---

### Post by tronica on 2006-06-08
can you post the driver you installed. i really would like to try that on mine. but can't find a driver and can't get the ones of the disk using cabextract or unshield.

---

### Post by tronica on 2006-06-08
nevermind i got on but didn't work. hmm. maybe i will just wait to buy a pci card.

---

### Post by dthomp325 on 2006-06-17
I just got the G120 B1 working no problem. 1st I disabled WEP encryption on my network.

1. I used Automatix to install wifi packages including ndis-tools.
2. Downloaded drivers from the D-Link site labeled as version 1.12.
3. Extracted .inf file by using the command 'unshield x ' for both 'cab' files in from the download.
4. Installed .inf driver files with ndisgtk.
5. Deactivated Etherent card (eth1 on my system) with system->admin->networking tool.
6. Selected wireless network and activated wireless card (wlan0 on my system) with system->admin->networking. 

It Works!
Then I entered the WEP key in system->admin>networking and re-enabled WEP. Then ran the command ndiswrapper -m to autostart ndiswrapper at start-up.

Hope this Helps

---

### Post by dthomp325 on 2006-06-17
Ok, I'm getting a very weird problem. If I start my computer with the card unplugged, and then plug the wireless card into the usb port after I am in Gnome, everything works great. However, if I start the computer with the card already plugged in, it lists the cards as 'eth1' instead of 'wlan0' and does not work correctly. Any suggestions?

---

### Post by Sam Liu on 2006-08-21
Ok guys heres the solution to that;

Go to shell,

```

sudo -s
```

type your password

```
vi -e /etc/modprobe.d/blacklist
```

type visual.

ok now, using vi, press the letter "I" on the keyboard (it lets you add to the file)

go and make these lines at the end of the file

```

blacklist islsmusb
blacklist islsm
blacklist islsm-usb

```

and reboot. should work if you have your prisma02 and ndiswrapper already installed. anyone need the files for prisma02 just email me

---

### Post by libertyforever on 2006-08-30
OH MY GOODNESS GRACIOUS!!!  Sam Liu, you are a genius!  =D>   I have been having problems with my DWL-G122, ver. B1 locking up.  I tried your suggestions and it works like a charm!!!

In the event other newbies come along this thread, after pulling my hair out in vi, I finally figured out that after you do this . . .


> **Sam Liu said:**
> 
blacklist islsmusb
blacklist islsm
blacklist islsm-usb


. . . the way I got out of vi and saved my changes was to hit control+c, and then type a ":" and right after it an "x" <enter>.  For those of you that know more, please update this info if there is a more proper way of getting out of vi.

It was also necessary for me after booting up to type in:

**sudo dhclient rausb0 <enter> **

This would get me totally up and running.  But, at some other posts, I figured out something else.

**gksudo gedit /etc/network/interfaces <enter>**

This will open the interface file in gedit.  I added to the bottom of the file:

[B]iface rausb0 inet dhcp

auto rausb0[/B]

I saved the changes and closed out gedit.  Now, when I reboot, after about 1 minute, my entire internet comes up and works great with no tweeking!  Hope this helps others.

---

### Post by ala.frosty on 2007-06-29
I'm an ubuntu newbie. I've been scouring the i'net looking for step-by-step instructions on how to set up this #!^$ DWL-G122 B1 USB wirelese dongle. There seem to be all sorts of "just do that thing" comments without steps that let it work for me. I've been at this for literally days!

I've reinstalled Feisty Fawn .. for about the fifth time. At one point, I think I was using an rt2500 driver that actually got the lights to work. Unfortunately, I could not get it to connect to my wpa network. I then went back to the rt2570. No lights and no connection. :-(

I've tried blacklisting stuff and unblacklisting and adding to /etc/network/interfaces but none of it works.

Can anyone please walk me through steps I should take to get this puppy working? I have had it working on this same computer (Dell Inspiron 3500 PII-400 w. 128MB RAM) under Windoze 2000 so I know the hardware works. It's just this OS that's bringing me down.

iwconfig shows the rausb0. My mode is managed. dhclient gets me nothing. After I run dhclient, then iwconfig, it looks like I'm not broadcasting. 

I've been through the Ubuntu wireless troubleshooting .. which I'm sure works great if you don't have any troubles, but when you do, it leaves you completely in the dust .. not exactly high praise for a troubleshooting guide.

Anyway, I'd really like to try to get Ubuntu working so if anyone here in Ubuntu-land can give me some really direct instructions, I (and clearly a lot of other people judging from all the posts about this) would really really appreciate it.

Thank you very much.

---

### Post by tronica on 2007-06-30
I never got it to work. i just gave up and bought a pci card. But I found a guide, its for dapper but i imagine it will work for feisty.

[http://www.linuxforums.org/forum/linux-networking/68864-howto-install-d-link-dwl-g120-ubuntu-linux-6-06-lts-guide.html](http://www.linuxforums.org/forum/linux-networking/68864-howto-install-d-link-dwl-g120-ubuntu-linux-6-06-lts-guide.html)

---

