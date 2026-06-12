---
title: "Atheros ar5007 quesiton"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by zmij on 2009-08-19
I'm having trouble connecting my HP dv6000 to the internet. I just installed ubuntu 8.04 and I'm dual booting with vista. The wireless works perfect in vista but I'm getting no where in ubuntu.

I've been searching all over the internet, including this site, but everything I'm supposed to download is 404d (several years old). 

Card: **Atheros AR5007**
I type in... *lspci | grep "Ethernet"*
and i get... [I]00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)[/I]

When I type in *sudo apt-get update *i just get "could not resolve us.archive.ubuntu.com" errors

Im brand new to Linux, and I know Atheros cards are a pain. Any help on connecting to the internets?

---

### Post by zmij on 2009-08-19
also, I'm not sure how i go about updating or downloading anything without being connected to the internet?

---

### Post by zmij on 2009-08-20
hmmmm

---

### Post by bobtfish on 2009-08-20
Well you should be able to get on the Internet if you used a normal wired connection. Anyway, I have the same wireless card, and I use the ath5k (was enabled from default Ubuntu installation) driver (I had trouble with ath_hal and ath_pci before). Try the command "lsmod | grep ath" (without the "s). The lsmod lists loaded drivers and such. My results are:
```
chris@chris-laptop:~$ lsmod | grep ath
Module                  Size  Used by            //added this back in for clarity
ath5k                 107520  0 
mac80211              217592  1 ath5k
led_class              12036  1 ath5k
cfg80211               38288  2 ath5k,mac80211

```

---

### Post by zmij on 2009-08-21
> **bobtfish said:**
> Well you should be able to get on the Internet if you used a normal wired connection. Anyway, I have the same wireless card, and I use the ath5k (was enabled from default Ubuntu installation) driver (I had trouble with ath_hal and ath_pci before). Try the command "lsmod | grep ath" (without the "s). The lsmod lists loaded drivers and such. My results are:
```
chris@chris-laptop:~$ lsmod | grep ath
Module                  Size  Used by            //added this back in for clarity
ath5k                 107520  0 
mac80211              217592  1 ath5k
led_class              12036  1 ath5k
cfg80211               38288  2 ath5k,mac80211

```


I typed that in and got....
[I]
ath_pci      101024      0
wlan      207728      lath_pci
ath_hal      192592      lath_pci[/I]



Are these the correct drivers to have loaded?

---

### Post by bobtfish on 2009-08-21
Well to be honest I get a bit lost around the whole driver thing, but I might be able to suggest something that is at least reversible if it doesn't help.
There is a folder at /etc/modprobe.d that contains a bunch of .conf files, in particular blacklist.conf, but I also had blacklist-ath_pci.conf which is the one I changed when I had trouble, but really you're looking for anything with ath mentioned as a place to start.
In that file I had an explanatory comment, and the line ```
blacklist ath5k
``` which basically stops the ath5k driver loading.
I changed it to: 
```

#blacklist ath5k
blacklist ath_hal
blacklist ath_pci

```
The # comments out the first line so it is ignored. For me, this allowed the first driver to be loaded, and blocked the other two, which were conflicting with it.

I guess for you, you want to look for the line "blacklist ath5k", but even if that's not there you can add the other two lines. The worst that happens is it doesn't help and you take them out again. (On second thoughts it might be worth copying the original file to your desktop just in case you accidentally change something important).
You just reboot to see if the changes worked.

On the other hand this could have been very specific to my problem, but it's a starting point. Good luck.

---

### Post by zmij on 2009-08-21
> **bobtfish said:**
> Well to be honest I get a bit lost around the whole driver thing, but I might be able to suggest something that is at least reversible if it doesn't help.
There is a folder at /etc/modprobe.d that contains a bunch of .conf files, in particular blacklist.conf, but I also had blacklist-ath_pci.conf which is the one I changed when I had trouble, but really you're looking for anything with ath mentioned as a place to start.
In that file I had an explanatory comment, and the line ```
blacklist ath5k
``` which basically stops the ath5k driver loading.
I changed it to: 
```

#blacklist ath5k
blacklist ath_hal
blacklist ath_pci

```The # comments out the first line so it is ignored. For me, this allowed the first driver to be loaded, and blocked the other two, which were conflicting with it.

I guess for you, you want to look for the line "blacklist ath5k", but even if that's not there you can add the other two lines. The worst that happens is it doesn't help and you take them out again. (On second thoughts it might be worth copying the original file to your desktop just in case you accidentally change something important).
You just reboot to see if the changes worked.

On the other hand this could have been very specific to my problem, but it's a starting point. Good luck.



So how do i go about doing all of this? Im 100% new to linux

---

### Post by bobtfish on 2009-08-21
These are only suggestions, and I'm not exactly experienced myself, so I don't know if they'll help, but I won't suggest anything that isn't reversible. If anyone who's more experienced with modules wants to jump in, please do.
It's also a lot of stuff in a row, but I hope you can follow it.

Before you start, I think the easiest way to find out if you have the ath5k module is to open a terminal and type:
modprobe ath5k
This will try to load the driver, and may cause all sorts of error messages, or simply just not work right. Doesn't matter, it shouldn't cause anything to go ballistic, and all will reload as usual next time you reboot (further down this post).
The point is, if you don't have it, you will get:
FATAL: Module ath5k not found.
In which case, I'm an idiot and there's no point carrying on.

But if  you don't get that, how I would attempt to get it working is as follows...

The folder to look in is /etc/modprobe.d
I think the files are locked so you'll need to use your admin password, so to get there, do:
Press alt+f2, this brings up a run application box.
Type in: gksudo nautilus /etc/modprobe.d

gksudo means run as admin, without the terminal window.
nautilus is the file browser program.
/etc/modprobe.d is the folder.

It'll ask for your root password. (This is not necessarily the same as your normal user password, but I can't remember how the initial setup goes, so it might be the same. Hope you can remember.)

You now have a folder open with a bunch of files with names like something.conf. Be careful what you do, you have full administration rights.
These are configuration files for modprobe, the program that deals with loading kernel modules.

In here you will have blacklist.conf, and may well have something with ath in the name.
Basically open these and look for anything with ath in it.
This would be a good time to save a copy of the file to the desktop.

If you see a line "blacklist ath5k", comment it out by putting a # at the start of the line.
Either way, it conflicts with the other ones, so add (anywhere) the other lines: "blacklist ath_hal" and "blacklist ath_pci".

Restart.

Assuming all hasn't blown up and you've decided to sue me, you can find out if ath5k has loaded (in which case wireless may be working anyway) by using the lsmod command as before.

If not, I'm at a loss for how to get it to start at boot up. You should be able to add it now by using "modprobe ath5k" as at the top, but I think then you would need to bring up wlan0 yourself, and I've never succeeded with that thing.

At this point if it's not working you should probably revert it back to how it was. Open the folder as before, remove the changes you made and save (or replace it with the backup). Reboot. You're back to square one.

That's a lot of crap to read, but I've tried to include lots of details.

---

### Post by zmij on 2009-08-23
> **bobtfish said:**
> These are only suggestions, and I'm not exactly experienced myself, so I don't know if they'll help, but I won't suggest anything that isn't reversible. If anyone who's more experienced with modules wants to jump in, please do.
It's also a lot of stuff in a row, but I hope you can follow it.

Before you start, I think the easiest way to find out if you have the ath5k module is to open a terminal and type:
modprobe ath5k
This will try to load the driver, and may cause all sorts of error messages, or simply just not work right. Doesn't matter, it shouldn't cause anything to go ballistic, and all will reload as usual next time you reboot (further down this post).
The point is, if you don't have it, you will get:
FATAL: Module ath5k not found.
In which case, I'm an idiot and there's no point carrying on.

But if  you don't get that, how I would attempt to get it working is as follows...

The folder to look in is /etc/modprobe.d
I think the files are locked so you'll need to use your admin password, so to get there, do:
Press alt+f2, this brings up a run application box.
Type in: gksudo nautilus /etc/modprobe.d

gksudo means run as admin, without the terminal window.
nautilus is the file browser program.
/etc/modprobe.d is the folder.

It'll ask for your root password. (This is not necessarily the same as your normal user password, but I can't remember how the initial setup goes, so it might be the same. Hope you can remember.)

You now have a folder open with a bunch of files with names like something.conf. Be careful what you do, you have full administration rights.
These are configuration files for modprobe, the program that deals with loading kernel modules.

In here you will have blacklist.conf, and may well have something with ath in the name.
Basically open these and look for anything with ath in it.
This would be a good time to save a copy of the file to the desktop.

If you see a line "blacklist ath5k", comment it out by putting a # at the start of the line.
Either way, it conflicts with the other ones, so add (anywhere) the other lines: "blacklist ath_hal" and "blacklist ath_pci".

Restart.

Assuming all hasn't blown up and you've decided to sue me, you can find out if ath5k has loaded (in which case wireless may be working anyway) by using the lsmod command as before.

If not, I'm at a loss for how to get it to start at boot up. You should be able to add it now by using "modprobe ath5k" as at the top, but I think then you would need to bring up wlan0 yourself, and I've never succeeded with that thing.

At this point if it's not working you should probably revert it back to how it was. Open the folder as before, remove the changes you made and save (or replace it with the backup). Reboot. You're back to square one.

That's a lot of crap to read, but I've tried to include lots of details.



I typed in **modprobe ath5k**... and got **FATAL: Module ath5k not found.**

So i did not continue with your steps, how do i go about getting this ath5k module?

---

### Post by zmij on 2009-08-24
I've tried the apt-get thing but it always tells me 'not found' 


Do I need an internet(wired) connection to get wireless, I guess i still don't understand how that works?

---

