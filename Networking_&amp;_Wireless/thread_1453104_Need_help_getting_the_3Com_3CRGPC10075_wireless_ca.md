---
title: "Need help getting the 3Com 3CRGPC10075 wireless card to work"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by rdunton on 2010-04-12
I have looked for information regarding this card.  I have tried to install it using ndisgtk and ndiswrapper.  I have the green light on the card but it won't work.  When I have tried using ndiswrapper to install this card, I can get the driver to install but then the instructions say to type the following line which I do, but then it gives me an error message:

 sudo modprobe ndiswrapper

The error message is:

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

Please help me install this wireless card.  Any help will be greatly appreciated.  I am running Ubuntu 9.10.

---

### Post by chili555 on 2010-04-12
That's not an error, it's a warning. Did ndiswrapper load?```
lsmod | grep ndiswrapper
ndiswrapper -l
```Was a wireless interface created?```
iwconfig
```Does clicking the Network Manager icon show networks? Can you connect (he asked with optimism)?

---

### Post by rdunton on 2010-04-12
I entered: lsmod | grep ndiswrapper

Output:
ndiswrapper          185532 0

I entered:  ndiswrapper -l

Output:
WARNING:  All config files need .conf:  /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING:  All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release
mrv8335x : driver installed
           device:  (11AB:1FAA) present

I entered:  iwconfig

Output:
NONE.  System just hangs.  Have let it go for several minutes with no response.

---

### Post by chili555 on 2010-04-13
> System just hangs. Have let it go for several minutes with no response.That sounds like a bigger problem than wireless. Let's see what's going on under the hood. Please do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```You will find a file in your user directory called dmesg.zip. Attach it as an attachment to your reply. I'll look it over and we'll see what the kernel messages are.

---

### Post by rdunton on 2010-04-13
I had to take the wireless card out before it would even open the file manager so I could find the dmesg.zip file.  For some reason, when this driver I am using for the card is in the computer (and the hardware is present), it prevents me from opening file manager, using anything that requires a password, and even prevents firefox from loading correctly.

When I take the card out, everything works just as it should with my wired connection.  I have entered the commands that you asked me to enter (with the card installed) and have attached that as a zip file.  Thanks a lot for the help that you have given me so far.

In addition, and I am not sure if this would make any difference or not, but I had to shut off ACPI to even get it to install on this laptop which is a Dell Inspiron 2650.

---

### Post by chili555 on 2010-04-13
While I study, would you please post:```
cat /etc/hosts
cat /etc/network/interfaces
```Thanks.

---

### Post by chili555 on 2010-04-13
Also:```
lsmod | grep dell
```Thanks.> I am not sure if this would make any difference or not, but I had to shut off ACPI to even get it to install It certainly does.

---

### Post by rdunton on 2010-04-13
Regarding the last two postings, do these commands need to be entered with the wireless card in the PCMCIA slot.

---

### Post by chili555 on 2010-04-13
None of the three need the card installed.

---

### Post by rdunton on 2010-04-13
```
cat /etc/hosts

```

127.0.0.1	localhost
127.0.1.1	raymond-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
cat /etc/network/interfaces
```

auto lo
iface lo inet loopback

```
lsmod | grep dell
```

dell_wmi                2564  0 

I wanted to clarify a previous posting regarding shutting ACPI off.  I meant that I had to shut off ACPI to install Ubuntu, not to install the wireless card.

---

### Post by chili555 on 2010-04-13
I saw this forum post concerning your exact model: [http://208.109.22.214/puppy/viewtopic.php?t=52429&sid=58f721c86feaee5cdd0c96f464f1dcab](http://208.109.22.214/puppy/viewtopic.php?t=52429&sid=58f721c86feaee5cdd0c96f464f1dcab)

The last post suggests changing the boot parameter from acpi=off to pci=noacpi. He says:> That's not the same than acpi=off/noacpi/nolapic; the computer boots fine, ACPI is partially loaded,I suggest you change the boot parameter in Grub. Do you know how to do that?

---

### Post by rdunton on 2010-04-13
yes, I will try that. also, i just upgraded to the latest BIOS for my laptop and that seems to help somewhat.  i can run it now with out acpi=off, but touchpad doesn't function. I have to use an external mouse.  I'll try pci=noacpi, as suggested.

---

### Post by rdunton on 2010-04-13
touchpad won't function with pci=noacpi

pci=noacpi or deleting acpi=off sometimes prevents the keyboard from working too.

I'll try acpi=off again to see if I am having any troubles with the touchpad.

i have seen another option that someone tried on this model laptop too and that is acpi=ht.  I'll give that a try too.

---

### Post by rdunton on 2010-04-13
acpi=ht makes the touchpad and keyboard work again

pci=noacpi is makes the keyboard work intermittently on the keyboard and very seldom makes the touchpad work.

I haven't tried the wireless card with acpi=ht, but I am going to be trying that now to see if that makes any difference in how the computer responds.

---

### Post by rdunton on 2010-04-13
no difference at all when I type

iwconfig

Just like before, it hangs the system.  I have waited several minutes and no response.

---

### Post by rdunton on 2010-04-13
its starting to look like this wireless card isn't going to function in Ubuntu.  I guess I'll have to get one that works better.

---

