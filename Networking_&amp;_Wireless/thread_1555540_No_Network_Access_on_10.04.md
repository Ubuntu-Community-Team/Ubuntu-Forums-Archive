---
title: "No Network Access on 10.04"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by 1awesomeguy on 2010-08-18
Hey guys,

I purchased an Acer Aspire 7745G yesterday and installed Ubuntu as soon as I opened up the computer.

There appears to be a big problem however. Neither the wireless nor the LAN / ethernet are working.

'ifconfig -a' gives two items: lo and pan0. I believe pan0 is the bluetooth.

The wireless icon at the top right says "No network devices available". Network Tools shows the same results.

If I plug in an ethernet cord, nothing happens.

This is a fresh Ubuntu 10.04.1 downloaded this morning from ubuntu.com. I tried installing three times (USB, CD, DVD) including data checks on the disks. Same problem all three times.

I am guessing this is some kind of driver issue, but since I have no Internet access, I cannot do a Ubuntu Update and have Ubuntu find the drivers for me.

Any ideas?

EDIT: The wireless and ethernet are working in Windows 7.

---

### Post by dineshs on 2010-08-18
```
sudo lshw -C network
```

---

### Post by 1awesomeguy on 2010-08-18
> **dineshs said:**
> ```
sudo lshw -C network
```

Thanks dineshs. Not sure what to make of the result:

```
chris@acer:~$ sudo lshw -C network
[sudo] password for chris: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f8000000-f803ffff ioport:3000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f8200000-f8203fff
```

---

### Post by Iowan on 2010-08-18
Perhaps I'm just mis-interpreting things this afternoon (long day...), but I don't notice a driver associated with either interface.

---

### Post by 1awesomeguy on 2010-08-18
> **Iowan said:**
> Perhaps I'm just mis-interpreting things this afternoon (long day...), but I don't notice a driver associated with either interface.

Thanks Iowan. Yep, I think you are right. That seems to be the problem: For some reason Ubuntu did not install either the wireless or the ethernet drivers during the install. I am not sure how to get them and install them now. I have no Internet access on the computer. :(

---

### Post by dineshs on 2010-08-18
Try this link
[http://ubuntuforums.org/showthread.php?t=1476231](http://ubuntuforums.org/showthread.php?t=1476231)
Since you dont have internet it will be difficult to install build-essential
Can you check whether build-essential is listed in synaptic package manager?
If yes try this(see post #5)
[http://ubuntuforums.org/showthread.php?t=1553834](http://ubuntuforums.org/showthread.php?t=1553834)

---

### Post by 1awesomeguy on 2010-08-19
> **dineshs said:**
> Try this link
[http://ubuntuforums.org/showthread.php?t=1476231](http://ubuntuforums.org/showthread.php?t=1476231)
Since you dont have internet it will be difficult to install build-essential
Can you check whether build-essential is listed in synaptic package manager?
If yes try this(see post #5)
[http://ubuntuforums.org/showthread.php?t=1553834](http://ubuntuforums.org/showthread.php?t=1553834)

Thanks dineshs! I managed to get my ethernet connection working. No wireless yet...

This is what I did:

1. Installed build-essential from Live CD using:
> ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential

```
- [source]("http://ubuntuforums.org/showpost.php?p=5380712&postcount=7")

1b. Had some problems with the apt-cdrom command so used this as a fix:
> ```
sudo umount /dev/sr0
sudo mount /dev/sr0 /media/apt/
sudo apt-cdrom add
```
- [source]("http://www.linuxforums.org/forum/debian-linux-help/52770-apt-cdrom-error.html#post780882")

2. Downloaded the Ethernet driver from [here]("http://partner.atheros.com/Download.aspx?id=125")

3. Used slightly modified steps from chili555's post [here]("http://ubuntuforums.org/showpost.php?p=9257690&postcount=6"):
```
tar zxvf AR81Family-Linux-v1.0.1.9.tar.gz
cd src
sudo su
make install
modprobe atl1e
exit
```

EDIT: Once I had Internet access, I was prompted to download and install restricted drivers. Now the wireless is working fine. Thanks everyone!

---

### Post by dineshs on 2010-08-19
Happy to hear your problem is solved.Thank you for detailing this step by step procedure.Hope this will help others like V13 noob(The other thread I referred which is yet to be solved)
Thanks to chili555 and lowan

---

### Post by JohnMcReynolds on 2010-09-07
Yeah - - Worked like a charm.  Many thanks for the clear, concise notes.  For others please note that "atl1e" includes the letter "L" (lowercase) followed by the number "1".  In my browser at least this was not obvious.  Silly English alphabet.

---

### Post by jaspertb on 2011-09-10
Hi, 

Im having the same problem with this AR8151 driver from atheros.
Though I can't seem to find the patch.

I do have the AR81Family-linux-v1-1.0.1.14.patch  but when i type "make install" i get this error:
```

make: *** No rule to make target ínstall'. Stop

```

Anyone knows how to fix this?
edit: linux 2.6.32-33-generic

---

