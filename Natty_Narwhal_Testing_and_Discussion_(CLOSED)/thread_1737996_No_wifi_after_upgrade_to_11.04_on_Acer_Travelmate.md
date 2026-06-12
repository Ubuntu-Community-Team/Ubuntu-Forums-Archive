---
title: "No wifi after upgrade to 11.04 on Acer Travelmate"
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jacki on 2011-04-24
Hi all,

after upgrading to Ubuntu 11.04 (beta2) the wireless connection on my Acer notebook is not working any more. The cable connection works fine. Looking around the web I saw that many people have this or similar problems, but didn't yet manage to solve it in my case. 


If I put acer-wmi in the blacklist.conf, I do see wireless connections listed in the networkmanager, but connecting fails. If I don't put acer-wmi in the blacklist, I can't even activate wireless.

Is there some kind soul out there who could give me some advice on this problem or maybe even suggest a solution? Wireless is really essential for me on the netbook, so any help is greatly appreciated. I also don't know what more information I could offer to clarify what's really wrong here, but if you tell me I'll post it right away.

---

### Post by coffeecat on 2011-04-24
Hi.

It would be useful to know what wireless chipset you have. Open a terminal and post the output of:

```
lspci | grep -i wireless
```It's interesting that you found that  acer-wmi seems to be interfering with wireless. Here's a thread from over a year ago about acer-wmi  interfering with wireless. They may be something useful for you there.

[http://ubuntuforums.org/showthread.php?t=1333700](http://ubuntuforums.org/showthread.php?t=1333700)

By the way, ignore post #19. I have the same Acer Aspire 7540 as the poster. Wireless has worked for me in Karmic, Lucid, Maverick and continues to work just fine in Natty. I haven't had to uninstall smartdimmer, neither have I had problems with network-manager.

---

### Post by jacki on 2011-04-24
Hi coffeecat, thanks for the reply. The "lspci | grep -i wireless" doesn't return anything, but scrolling through the unfiltered lspci output, this is probably what you were asking for: 

```

01:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57760 Gigabit Ethernet PCIe (rev 01)

```

Regarding the old thread: Wireless worked just fine here before the update, so I'm not sure if the older discussion will be helpful. I'll have a look, tough.

---

### Post by Vaun on 2011-04-24
The open source brcm80211 driver should work fine.  I have the same card in my HP-DV6 2170.  Ensure you have the latest linux-firmware installed 1.52.

```
sudo rmmod wl brcm80211

sudo modprobe brcm80211

sudo depmod -a
```

---

### Post by jacki on 2011-04-24
> **Vaun said:**
> The open source brcm80211 driver should work fine.  I have the same card in my HP-DV6 2170.  Ensure you have the latest linux-firmware installed 1.52.


I do have the latest linux-firmware installed. Unfortunately, after following your instructions I still get no wireless connection. Is there some place/log where I can look up what's wrong here?

---

### Post by coffeecat on 2011-04-24
Unlike Vaun, I have no direct experience of your Broadcom chipset, but I do have an alternative suggestion. According to this page:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

... your BCM43225 can use the proprietary STA driver. Because you upgraded from 10.10, I wonder if the driver didn't get upgraded properly. Perhaps a re-installation of the STA driver might help.

---

### Post by Vaun on 2011-04-24
This may sound like a ridiculous question, but is your wifi kill switch somehow activated?

---

### Post by Vaun on 2011-04-24
Yes, both the proprietary and open source driver work well with this card.  The open source is just much faster at connecting / resuming.

Try:

```
sudo apt-get install --reinstall bcmwl-kernel-source
```

---

### Post by jacki on 2011-04-24
> **Vaun said:**
> This may sound like a ridiculous question, but is your wifi kill switch somehow activated?

Yes, it's on: I do see the available wifi networks listed in the network manager. But when I select for example my home wifi network, it first says that the interface is configured, then moves on to getting a network address (the mini progress bar in the wifi icon proceeds a little at this step, I'm on kubuntu here atm but it was the same in gnome), but then is stuck without connecting. Shortly afterwards the status changes to "not connected".

This behaviour seems to be identical, no matter if the listed driver is "wl" or "brcm80211". Also reinstalling bcmwl-kernel-source didn't change that.

Browsing through the package list, I also found that I do have b43-fwcutter and firmware-b43-installer installed. Are these further optional drivers for the wifi? Which packages should be installed, and which removed? Or doesn't that matter for my connection? :confused:


Edit: I just found I have a file /etc/modprobe.d/blacklist-bcm43.conf, which contains

blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211

plus a comment that it is auto generated by bcmwl and should not be edited manually. Is blacklisting brcm80211 the correct thing to do or is this somehow overridden by other settings? I really have no idea where to change what here ....

---

### Post by ibrrfarr on 2011-04-24
I'm not really a coder; however, I have an AAO D255.  When I installed 10.10 I had to go into the Admin section and toggle the feature manually.  I do not know how this occurs in 11.04, but perhaps there is a similar feature in 11.04?  All features work out-of-the-box for me.  I am using Ubuntu Tweak to both Update and Clean Up redundant stuff.

Wish you the best!

---

### Post by Vaun on 2011-04-24
Try uninstalling those b43-fwcutter and firmware-b43-installer packages.  Uninstall the proprietary wl driver and modprobe for brcm80211. I have a feeling those packages may be the issue.

Under connection information in network-manager, what driver is displayed?

---

### Post by jacki on 2011-04-24
It's working now :-) !! Thanks for the help! :D

If someone has the same problem, this is what I did: I uninstalled everything with b43 in its name, removed also the packages broadcom-sta-common and broadcom-sta-source, and to be on the save side, reinstalled bcmwl-kernel-source. Then followed the instructions in #4 in this thread to load the brcm80211 module. Now the wireless works as in 10.10, using the brcm80211 driver. Great! :D

---

### Post by Vaun on 2011-04-24
No problem.  Glad I could help.  The driver has been working flawlessly for me.

---

### Post by jacki on 2011-04-25
Hmmm ... apparantly I was a little too optimistic here. After a restart I'm back to the same problem again. :(

I didn't remove or install any packages, but cannot connect to wifi networks anymore. Any ideas left? :confused:

---

### Post by ozorba on 2011-04-25
> **Vaun said:**
> This may sound like a ridiculous question, but is your wifi kill switch somehow activated?

Actually, the problem may stem from not detecting the WiFi kill switch. I have a HP Pavillion and had a similar problem. Whatever I did I could not turm the WiFi on. The only way to do this was to revert to windows and tur wifi on with the app supplied by HP. :-(

---

### Post by jacki on 2011-04-25
> **ozorba said:**
> Actually, the problem may stem from not detecting the WiFi kill switch. I have a HP Pavillion and had a similar problem. Whatever I did I could not turm the WiFi on. The only way to do this was to revert to windows and tur wifi on with the app supplied by HP. :-(

Well, I do see the available networks, so I suppose the wifi hardware is activated.

---

