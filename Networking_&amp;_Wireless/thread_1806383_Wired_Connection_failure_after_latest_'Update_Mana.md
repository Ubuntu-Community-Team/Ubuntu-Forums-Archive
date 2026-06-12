---
title: "Wired Connection failure after latest 'Update Manager'"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by Nepenthes73 on 2011-07-17
Greetings All,

I just downloaded the most recent upgrades through 'Update Manager' (looked like there was a kernel update in there) and now my network connection is non-functional. I can connect using the installation CD, which I'm doing right now. I'm running 10.04 64bit

Incidentally, I had the same problem when I had installed 10.10 and 11.04 (i.e. I was not able to get a network connection unless I booted from the installation CD) which is what prompted me to go back to 10.04, being that it worked fine...until now.

---

### Post by Bucky Ball on 2011-07-17
Did you need to install any drivers to get your wireless going? The new kernel probably obliterated them if that is the case. Do you have anything in System>Administration>Additional Hardware for the card?

Have you done an update in the new kernel? Can you get online with a cable? If so, try these commands in a terminal one at a time:

```
sudo apt-get update
sudo apt-get upgrade
```That will update then upgrade the packages, *NOT* the release, so don't panic there. While in the terminal, could you paste this and post the output back here:

```
sudo lshw -C network
```

---

### Post by Nepenthes73 on 2011-07-17
Thanks for the reply.

OK, well I didn't have to install any drivers; when I installed lucid, it worked right off the bat (oh, and by the way, I'm using a wired connection, good ol' ethernet-modem connection, not wireless).

I've done kernel updates before. I've had lucid since it was first released and have regularly downloaded whatever updates have become available since then.

Here's the output for "sudo lshw -C network" while running the installation CD:

                                 *-network                
        description: Ethernet interface  
        product: 82578DC Gigabit Network Connection  
        vendor: Intel Corporation  
        physical id: 19  
        bus info: pci@0000:00:19.0  
        logical name: eth0  
        version: 05  
        serial: 00:27:0e:02:b2:63  
        size: 100MB/s  
        capacity: 1GB/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.10-5 ip=192.168.1.47 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s  
        resources: irq:34 memory:de300000-de31ffff memory:de324000-de324fff ioport:3020(size=32)
 
And when booted up without the CD:

                                 *-network UNCLAIMED      
        description: Ethernet controller 
        product: 82578DC Gigabit Network Connection  
        vendor: Intel Corporation  
        physical id: 19  
        bus info: pci@0000:00:19.0  
        version: 05  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm msi cap_list  
        configuration: latency=0  
        resources: memory:de300000-de31ffff memory:de324000-de324fff ioport:3020(size=32)

---

### Post by Bucky Ball on 2011-07-18
You are attempting to get wireless up or cable?

I did see an issue in a thread yesterday which matches your issue so this could be a bug in the latest 10.04 kernel, which would be highly unusual for an LTS release this old. But does happen and hopefully fixed soon.

Perhaps post output of:

```
uname -r
```Can you choose the previous, working kernel, from the menu at boot?

---

### Post by Nepenthes73 on 2011-07-18
Here are the results of uname, some options in addition to -r

2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:13:52 UTC 2011 x86_64 GNU/Linux
  
  I am connecting by cable, not wifi.
 
 As far as choosing a previous kernel, how would I do that? I don't see any options when I boot up.

I did notice a similar topic in some other threads, but since I hadn't  had any success from what I tried from the forum when the same network  snafu happened before (when I installed the newer distributions - 10.10  and 11.04) and the official Ubuntu documentation hasn't been helpful, I  figured I'd post something here.

Thanks again Bucky

---

### Post by Bucky Ball on 2011-07-18
You boot straight to Ubuntu you mean? You can't choose an OS? Try hitting escape when you're booting (or it might be shift) and see if that gets you to a menu. Then you can choose the previous kernel from the list.

If that's a problem, you can change it permanently by opening:
```

sudo nano /etc/default/grub
```

... and change this line:

```
GRUB_TIMEOUT="0"
```

... to this:

```
GRUB_TIMEOUT="5"
```

That makes the menu list show for five seconds at boot (unless you hit a key in which case it will remain).

---

### Post by Nepenthes73 on 2011-07-19
Yes, I was booting straight to Ubuntu. I eventually figure out how to get the kernel menu. When I entered the first code I got this:

```
# If you change this file, run 'update-grub' afterwards to update 
# /boot/grub/grub.cfg. 

GRUB_DEFAULT=0 
GRUB_HIDDEN_TIMEOUT=0 
GRUB_HIDDEN_TIMEOUT_QUIET=true 
GRUB_TIMEOUT=10 
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
GRUB_CMDLINE_LINUX="" 

# Uncomment to disable graphical terminal (grub-pc only) 
#GRUB_TERMINAL=console 

# The resolution used on graphical terminal 
# note that you can use only modes which your graphic card supports via VBE 
# you can see them in real GRUB with the command `vbeinfo' 
#GRUB_GFXMODE=640x480 

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux 
#GRUB_DISABLE_LINUX_UUID=true 

# Uncomment to disable generation of recovery mode menu entries 
#GRUB_DISABLE_LINUX_RECOVERY="true" 

# Uncomment to get a beep at grub start 
#GRUB_INIT_TUNE="480 440 1"
```

Eventually figured out to put "#" at start of the two lines containing "HIDDEN_TIMEOUT".

[Tangentially-related item - When I got to the menu, I remembered that my keyboard doesn't work until the OS loads; apparently a problem others have also had using this keyboard (Logitech Illuminated Keyboard) and processor (Intel Core i7) combo. I found this out when I was trying to change booting sequence in BIOS so I could boot off a thumb drive).]

Now I'm internet-functional. Results of ```
uname -r -v -m -p -o
``` give```
2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 unknown GNU/Linux
```So should I just remove the 2.6.32.33-70 kernel and header files using Synaptic? I'd rather be able to boot without having to access the kernel menu (I like my back-lit keyboard). I'd also like to have some idea why this network problem is happening.

---

