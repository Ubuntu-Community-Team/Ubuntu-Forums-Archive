---
title: "Acer Aspire One Wireless Stopped Working"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by jcb081584 on 2009-05-18
I have an Acer Aspire One and upgraded to 9.04 a few weeks ago and yesterday my wireless suddenly stopped working.  I open the menu to connect to a network and it shows a wired connection and a wireless connection but is grayed out and does not show any networks.  Any idea what could have happened?  I've been trying to bridge my interfaces but a few days ago put the interfaces file back to how it originally was and it has worked since then.  Any help would be greatly appreciated.  Thanks in advance.

---

### Post by sloggerkhan on 2009-05-18
Configuring your wireless via config file will overide the default settings at make it so that NetworkManager can no longer control your networking configuration.

If NetworkManager can't control your wireless, then it will see no wireless networks.

---

### Post by superprash2003 on 2009-05-18
do you get any "unmanaged" error?

---

### Post by jcb081584 on 2009-05-19
> **sloggerkhan said:**
> Configuring your wireless via config file will overide the default settings at make it so that NetworkManager can no longer control your networking configuration.

If NetworkManager can't control your wireless, then it will see no wireless networks.

How do I make it to where network manager can control it again?  Can I copy the interfaces file off the install cd?

---

### Post by jcb081584 on 2009-05-19
> **superprash2003 said:**
> do you get any "unmanaged" error?

No I'm not getting any error message.

---

### Post by ebcovert3 on 2009-05-21
I am having the exact same problem. Please assist.

---

### Post by ebcovert3 on 2009-05-21
Ok, apparently installing the updates came across the wire last night removed the permissions for connecting to wireless networks etc from my account. Interesting. I have since rechecked that box; however, still no joy. 

I can see my wireless device but it doesn't see any networks. And I know they are there. If anyone has any ideas, I am open to them.  Thanks

---

### Post by ebcovert3 on 2009-05-21
I have uploaded three files that are the output from:
```
lshw -C network
iwconfig
ifconfig
```

---

### Post by Jose Catre-Vandis on 2009-05-21
Have you tried things manually?

```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
(and assuming no security (turn it off if on - for now)
sudo iwconfig wlan0 essid "your-essid"
sudo dhclient wlan0
```

Any luck?

On my AA0 I used a minimal install and installed wicd to look after my networking, given the need to switch from wired to wireless.

---

### Post by raymondh on 2009-05-21
This may be silly but ... I do get a "grey-out" when my wifi switch is off.

---

### Post by ebcovert3 on 2009-05-21
Well, to make matters worse, I have some how managed to uninstall the wireless drivers now. Now I have NO wireless. When I run ifconfig, wlan0 does show up. I have run a restore from a backup I made last week when everything worked, but no joy. I ran the restore on /etc/modprobe.d and /etc.

Open to ideas once again.

---

### Post by ebcovert3 on 2009-05-24
> **Jose Catre-Vandis said:**
> Have you tried things manually?

```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
(and assuming no security (turn it off if on - for now)
sudo iwconfig wlan0 essid "your-essid"
sudo dhclient wlan0
```

Any luck?

On my AA0 I used a minimal install and installed wicd to look after my networking, given the need to switch from wired to wireless.
Jose,
I tried all of the above. I get "no such device."

---

### Post by Jose Catre-Vandis on 2009-05-25
OK, ebcovert3. Back to basics :)

1. Please report back with output from the following:
```
lspci -v
ifconfig
iwconfig (from the sound of it, nothing likely here)
contents of /etc/network/interfaces
dmesg (after a boot, and only anything related to the atheros adapter)
```
Yes, I know you put up some of these before, but things are different now?

2. The wireless network adapter is in the kernel, (9.04), so I am not sure how you uninstalled the drivers. What was you driver setup - madwifi? Your first lshw - network indicated that the ath5 module was present.

3. Also, are you trying to run wired and wireless at the same time - without network manager - this seems to kill everything, so run "sudo ifconfig eth0 down" to stop the wired connection (it will come back up on reboot, or simply run "sudo ifconfig eth0 up" to bring it back)

---

### Post by ebcovert3 on 2009-05-26
Ok all. Good news. I found a website ([https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L)) and that got me thinking about the kernel. On a whim (with no backing up; I know, I know...like I said: a whim), I installed kernel version .12-43. I then removed and re-installed the linux backports for Jaunty and lo and behold...


It worked!!!


Thanks to everyone for all of the suggestions.

---

