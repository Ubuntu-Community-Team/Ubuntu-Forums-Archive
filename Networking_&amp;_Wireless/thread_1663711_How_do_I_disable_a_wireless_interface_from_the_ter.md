---
title: "How do I disable a wireless interface from the terminal, permanently?"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2011-01-10
I have a small computer (Zotac Mag Mini All-in-One Giant) that has a built in wireless adapter that barely works (poor signal), so I'm using an external USB adapter instead, which performs far better by comparison.  I would like to disable the adapter inside the PC so that in the future the computer doesn't try to reconnect to the network using the "wrong" interface.

Is there a way to disable a networking interface (Ethernet or Wireless for that matter) from terminal in such a way so that it will remain "off" or ignored after rebooting?

---

### Post by sj1410 on 2011-01-10
yes you can do it

ifconfig wifi0 down

or whatever the internet name is.

---

### Post by diablo75 on 2011-01-20
> **sj1410 said:**
> yes you can do it

ifconfig wifi0 down

or whatever the internet name is.

Tried this.  All it does is take the interface down for the current session, but after rebooting the system, it comes right back.  This is not what I was looking for.  

I want the interface to remain down after reboot; to not even attempt to connect to anything.

---

### Post by Rebelli0us on 2011-03-16
Zotac? Disable wireless through the BIOS or even remove the mini card.

---

### Post by dmizer on 2011-03-17
> **diablo75 said:**
> Is there a way to disable a networking interface (Ethernet or Wireless for that matter) from terminal in such a way so that it will remain "off" or ignored after rebooting?

I have a computer with the same problem so I found a solution.

According to: /usr/share/doc/network-manager/README.Debian
> Only devices that are not listed in /etc/network/interfaces or which have been configured "auto" and "dhcp" (with no other options) are managed by NM.

So you just need to edit /etc/network/interfaces and add a non-auto entry for your weak network adapter like so (where wlan0 is your weak adapter):
```
auto lo
iface lo inet loopback

iface wlan0 inet manual
```

Edit:
Humm, this has some problems. I had to delete all of the configs in ./gconf and then nm-applet only shows up if I restart network-manager.

Edit 2:
Seems the above was only a problem with one machine.

---

### Post by flash63 on 2011-03-17
Hello,
why not just disable the module permanently (blacklist)?

Hardware and loaded Modules?
```
lspci -nnk | grep -i net -A2
lsusb
lsmod
```

---

### Post by grants on 2011-06-02
Curious as well. I dont use wi-fi but I can't disable it either. 

I'd like to just have the device powered off unless I needed it for a particular session.

Help please!

---

### Post by dmizer on 2011-06-03
> **grants said:**
> Curious as well. I dont use wi-fi but I can't disable it either. 

I'd like to just have the device powered off unless I needed it for a particular session.

Help please!

It's usually possible to do this via a few ways:
[LIST=1]
[*]Disable the card in BIOS. (This may or may not be possible)
[*]Use the on/off switch to disable it. Check your computer's users manual for the correct key combination.
[*]Use the edit I suggested above in [post #5]("http://ubuntuforums.org/showpost.php?p=10569222&postcount=5").
[*]Blacklist the module driving the card as suggested in [post #6]("http://ubuntuforums.org/showpost.php?p=10569271&postcount=6")
[/LIST]

---

### Post by nm_geo on 2011-06-03
> **flash63 said:**
> Hello,
why not just disable the module permanently (blacklist)?

Hardware and loaded Modules?
```
lspci -nnk | grep -i net -A2
lsusb
lsmod
```

+1 I like that idea flash it is elegant.  Find the driver or module and blacklist it.

---

### Post by dmizer on 2011-06-04
> **nm_geo said:**
> +1 I like that idea flash it is elegant.  Find the driver or module and blacklist it.

Yes and no. This could cause problems if both your wireless and your wired network cards are Broadcom. It could also cause problems because many different cards share the same modules, so it's possible that (in a situation where you want to use a wireless card other than the factory card) both the factory card and your spare card may use the same module.

---

### Post by lz1dsb on 2013-01-29
> **dmizer said:**
> It's usually possible to do this via a few ways:
[LIST=1]
[*]Disable the card in BIOS. (This may or may not be possible)
[*]Use the on/off switch to disable it. Check your computer's users manual for the correct key combination.
[*]Use the edit I suggested above in [post #5]("http://ubuntuforums.org/showpost.php?p=10569222&postcount=5").
[*]Blacklist the module driving the card as suggested in [post #6]("http://ubuntuforums.org/showpost.php?p=10569271&postcount=6")
[/LIST]

That surely did it for me, exactly what I was looking for :lolflag: Thank you ;)

---

