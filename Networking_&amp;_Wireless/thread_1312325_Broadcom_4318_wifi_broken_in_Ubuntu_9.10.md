---
title: "Broadcom 4318 wifi broken in Ubuntu 9.10"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by Stewie2kill on 2009-11-03
I've searched and searched but I can't find the guide I even used in 9.04 to make my wifi work.

My broadcom 4318 (a troublesome card as I have learned) is just not working on my clean install of 9.10. I've sung the praises of Ubuntu for the past 3 months but now I want to kill it. It shows up in the lspci command so I know it's installed correctly.

I've tried enabling the b43xx-fwcutter driver and succeeded in making it show up in synaptic, but I think it's trying to install it from the 9.10 CD, trouble is that my CD drive appears to hate my copy (I've tried several different ones as well). I installed from a USB anyways and have NO idea how to make it get the repo's from the USB instead. 

I'm on Wired right now which does work (thank god) and there is nothing short of a modem in Hardware Drivers and it's enabled. I know there is a way to get it working because I did it in 9.04 but I cannot get it working in 9.10. Wireless has also mysteriously disappeared from the Gnome network manager's jump list. The tab is still open but there is no option to enable it anymore.

EDIT: I found the fix buried deep in Cannonicals documentation. I don't know how I was using fwcutter before because apparently it fails most of the time using that. I didn't want to use ndiswrapper methods because they seemed terrifyingly complicated, but I was linked to [http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/](http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/) via the support for the 4318 wireless adapter. It provides EXCELLENT support. I stuck with it and my wifi network magically appeared.  I hope this helps anyone else who is also having issues. [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom) is the place where I found the link for my drivers. 

Literally about to pull hair out here.

First time asking the community for help. Hope you guys can help me.

---

### Post by jaygo on 2009-11-14
I was working on a buddy's laptop with the BCM4318 and it's now working flawlessly. I installed fwcutter and ticked the little box that tells it to get firmware -- which it apparently then did during the installation process -- and I believe I did a quick "modprobe bcm". Bing bing!

This got it working for both his internal dell card and his external linksys PCMCIA, which both use the same chip ... well now he's getting rid of the external.

---

### Post by brookie on 2009-11-15
Hi Stewie,

So did you get it to work using Sambar's blog? I have tried sll kinds of ways similar to his post using ndiswrapper and could not get it to work on a Compaq v5000 with the same wireless card. This is nuts! 

Got a fresh install lf Karmic on it and the popup for proprietary drivers came up. I enabled B43 driver but still cannot connect to my hidden wireless network w/WPA-WPA2 encryption. 

Let me know how you fixed it okay.
Cheers, 
brook

---

### Post by SpectralDesign on 2010-02-24
Well....

When I click System... Administration... Hardware Drivers I get a dialogue that informs me that the Broadcom STA wireless driver is "activated but not currently in use".  (It goes on to mention that the driver is for blah blah **BCM4311-** blah blah blah).

When I do the `lspci` command in an xterm it happily tells me that I have the **BCM4311** 802.11b/g network controller.

Meanwhile the status light for the adaptor is amber instead of green, and I can't get the thing connected wirelessly...

:(

Ideas would be great but I'll post if I get any solutions working...

---

### Post by SpectralDesign on 2010-02-24
[I]THIS WORKED WITH MY BCM4311
[/I]
okay - I found my old notes... I'm positive some of this is not really required but I don't have the time or energy to pare it down... suffice to say that after doing the following my wireless went back to auto-connecting and there was no reboot required:

1. I used Synaptec Package Manager to search "ndiswrapper" and installed all 3 items that came up, though simply installing ndiswrapper-common would probably be sufficient:

```
sudo apt-get install ndiswrapper-common
```

next I pasted all this from my old notes, and it was working immediately afterward:

```

cd
mkdir broadcom_fix
cd broadcom_fix
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy #this step added Apr 27 2008
sudo rmmod wl #this step added Sep 20 2008
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44 #this step added May 1 2008
echo -e '#Karmic Koala ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper


```

---

