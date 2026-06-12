---
title: "Network configuration, aircrack, bcm4312"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by Hospadar on 2008-12-23
I'm trying to get aircrack working on my laptop, but I've never done it before and while I know what tools are generally involved, I don't know how to use them.

My biggest question is that every tutorial I find assumes I have a nice setup, but as I'm starting with a stock ubuntu install, I have this network manager business managing my connection, which is great, but not that useful for aircrack (I gather?)

I was just hoping someone could fill me in on what I need to do.
Mainly:
Do I need to patch my kernel/driver, if so, how do I do that?
How do I remove network-manager and get a manual configuration setup
How do I manually configure my wireless network to an essid (so I can be looking at websites while I try to get this stuff working)

My network card is a BCM 4312

---

### Post by pytheas22 on 2008-12-23
> Do I need to patch my kernel/driver, if so, how do I do that?

I'm not positive because I've never used a Broadcom 4312, but in general, the b43 driver that's built into Ubuntu 8.04 and up should be able to handle aircrack on most Broadcom cards without a problem.  So you should not need to do any patching.

> 
How do I remove network-manager and get a manual configuration setup

When you want to use aircrack, type this command first to kill Network Manager:
```

sudo killall NetworkManager
```

This way you don't have to uninstall it; you just stop it when you need to.  You can type 'sudo NetworkManager' to start it again when you're done.
> 
How do I manually configure my wireless network to an essid (so I can be looking at websites while I try to get this stuff working)

The answer above makes this a moot point, I think.  But just keep in mind that you can't actually browse websites while you're using aircrack, even if you connected to a network manually, because aircrack needs your card to be in monitor mode, and you can't browse the web while it is.

Another important point to note is that your 4312 card may be driven by the wl driver currently.  If you post the output of the command:
```

lshw -C Network
```

we can check.  wl probably won't work with aircrack; you need to switch to the b43 driver.

---

### Post by Hospadar on 2008-12-24
It is driven by the wl driver as it turns out, how can I remedy that?
Can I just blacklist wl and load b43?
Will b43 still work with networkmanager?

After playing around for a while, I tried a few things:
I tried:
rmmod wl
modprobe b43
/etc/init.d/networking restart

If I did this, I got no networks other than my loopback (for some reason even my wired connection disappeared

Also, for some reason, I can't scan for networks from the command line with my network card (using the wl driver, since I can't make it even show up with anything else)  I can see it in iwconfig as definately being a wireless card, but "iwlist scan eth1" just tells me that eth1 doesn't support scanning.  (my wireless adapter shows up as eth1).

Is there any way I can just totally wipe out network manager and do all my configuration by hand in the /etc/network/interfaces file?  I never had any trouble with things when I did all this that way in the past.


Thanks much for the help,
L-tron

---

### Post by pytheas22 on 2008-12-24
> It is driven by the wl driver as it turns out, how can I remedy that?
Can I just blacklist wl and load b43?
Will b43 still work with networkmanager?

Yes, blacklisting wl and modprobing b43 should do the trick.  b43 will work fine with Network Manager.
> 
After playing around for a while, I tried a few things:
I tried:
rmmod wl
modprobe b43
/etc/init.d/networking restart

If I did this, I got no networks other than my loopback (for some reason even my wired connection disappeared

You need to download firmware before b43 can actually see networks.  To do that, just run these commands once:
```

sudo apt-get update
sudo apt-get install b43-fwcutter
```

Then restart your computer and b43 should be working and allow you to see networks.
> 
Also, for some reason, I can't scan for networks from the command line with my network card (using the wl driver, since I can't make it even show up with anything else) I can see it in iwconfig as definately being a wireless card, but "iwlist scan eth1" just tells me that eth1 doesn't support scanning. (my wireless adapter shows up as eth1).

I don't know what could be going on here--if you can see a list of networks in Network Manager, you should also be able to see it by typing 'sudo iwlist scan'.  But the wl driver is proprietary, closed-source and undocumented, so it's hard to understand how it works.  b43 is open-source.
> 
Is there any way I can just totally wipe out network manager and do all my configuration by hand in the /etc/network/interfaces file? I never had any trouble with things when I did all this that way in the past.

You can uninstall NM permanently by typing:
```

sudo apt-get remove network-manager
```

To reinstall later:
```

sudo apt-get install network-manager-gnome
```

As for managing connections manually: there's a nice guide to command-line wireless [here]("http://ubuntuforums.org/showthread.php?t=571188").

But I'm pretty sure that Network Manager isn't the source of your problem; getting the drivers straightened out is.  Once you make sure wl is blacklisted and install firmware for b43, things should work.

NM can interfere with airodump because it tries to put cards into managed mode when they need to be in monitor mode, but as long as you run 'sudo killall NetworkManager' before starting airodump, NM should never be a problem.

---

