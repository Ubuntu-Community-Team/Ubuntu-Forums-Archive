---
title: "Losing NIC randomly"
date: 2011-11-06
forum: Mythbuntu
---

### Post by rmjohnson144 on 2011-11-06
I have been having trouble lately keeping connected in linux.  I keep losing the nic randomly at startup, and it randomly locks up during use when it does find the nic.  Other times it works without a hitch.

Is there a way to get the latest drivers?  or compile latest drivers?  

I'm using Mythbuntu 11.10, Ubuntu 11.10, and Pinguy OS 11.04.01 and all 64-bit versions.

My motherboard is a GigaByte GA-Z68MA-D2H-B3 (rev 1.0) and it says it has a Realtek 8111E on-board NIC.

This nic works fine on multi-boot to both Win 7 and my hackintyosh OS X 10.6.8.  I find if I reboot to windows and go back then it seems to work almost everytime.  well, for a while anyway.

If anyone has any clues, please let me know.
-=Mark=-

---

### Post by rmjohnson144 on 2011-11-08
I did a little more testing and I get about 5mbs downloads (on 25mbs connection) and less than 300KBs to zero on upload speeds.  I tested on speedtest.net and never got over 5mps download, and upload usually zero.  in windows, I get my normal 30+mps downloads, and 5+mps uploads.

I have reinstalled 11.10, plus installed 10.04.3 LTS, 11.04, and pinguy OS 11.04.  I get the same results on all of them.  

How can I check my drivers to see which versions I have installed?
-=Mark=-

---

### Post by ian dobson on 2011-11-08
Hi,

Just go to the terminal prompt and type

dmesg | grep eth

This will list all kernel messages for your network card, maybe there you'll see an error. 

modinfo modulename will display the module information for a module (you should be able to find the module name for your network card from the dmesg command).

Regards
Ian Dobson

---

### Post by rmjohnson144 on 2011-11-08
Here is my dmesg output:
> mark@mark-Z68MA-D2H-B3:~$ dmesg | grep eth
[    1.149902] i2c-core: driver [adp5520] using legacy suspend method
[    1.149904] i2c-core: driver [adp5520] using legacy resume method
[    1.250858] r8169 0000:04:00.0: eth0: RTL8168b/8111b at 0xffffc90000c6e000, 50:e5:49:34:e9:64, XID 0c900800 IRQ 42
[   10.553946] r8169 0000:04:00.0: eth0: link down
[   10.553952] r8169 0000:04:00.0: eth0: link down
[   10.554647] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.765844] r8169 0000:04:00.0: eth0: link up
[   13.766338] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.015757] eth0: no IPv6 routers present


I'm in Mythbuntu right now, as I downloaded drivers from realtek for my 10.04.3 LTS and it uninstalled my original driver and the automatic make file failed and now I have no internet at all and no way to reinstall as I can't redownload anything.

I think I need to install some modules to compile the realtek driver.  Not sure what I need and the realtek help file didn't say.

I downloaded the r8168-8.026.00 driver from Realtek.   not sure of the version of this or where it came from.

I gotta bail.  lag is so bad now I'm timing out again.  I hope this goes through.

Thanks for your help
-=Mark=-

---

### Post by ian dobson on 2011-11-08
Hi,

Got another network card you can use/plugin atleast until the problems are solved.

What errors did the rtl make display?

Regards
Ian Dobson

---

### Post by rmjohnson144 on 2011-11-08
I don't remember the error, I just remember it uninstalling my current driver.  I'm not sure about the make command at at all as it has an autorun.sh batch file it executes to do ot all automatically for me.  I ran it with sudo to make sure it had all permissions.

I just reran the autorun.sh and it seems to havbe finished without errors, but it started off with a:

FATAL: Module r6186 not found.

the whole thing showed:
```

Check old driver and unload it
Build the module and install
load module r8168
FATAL: Module r6186 not found
updating initramfs. Please wait.
Update-initramfs: Generating /boot/initrd.img-2.6.32-34-generic
Completed.

```

I ran the batch with:
```
sudo sh ./autorun.sh
```

well, now that I typed in everything my wireless usb nic has installed and now I have internet again.

If you have any clues on how to compile this Realtek driver, I'd be forever greatful.
-=Mark=-

---

### Post by ian dobson on 2011-11-08
Hi,

Looks like a typing error in the make script. I though the driver is r8186 rather than r6186 

What happens you you try
sudo insmod r8186

Regards
Ian Dobson

---

### Post by rmjohnson144 on 2011-11-08
sorry, typo.  I entered the numbers in backwards.  all numbers should read r8168.

as for insmod, it reports error:
insmod: can't read 'r8168': no such file or directory.

also, I seem to have lost my wireless after running the batch script.  so I'm back to wireless.  I do however have an Intel PICe nic.  hopefully it installs without having to go online.

-=Mark=-

---

### Post by rmjohnson144 on 2011-11-08
I thought I'd link you to the Realtek driver in case you can make sense of it all.

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D%28L%29%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8168E/RTL8111F](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D%28L%29%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8168E/RTL8111F)

Thanks for all your help
-=Mark=-
ps. I put in the Intel nic and everything is 100%.  no lag, no drops, full speeds.  too bad I have to put it back in my server when done.  :P

---

### Post by ian dobson on 2011-11-08
Hi,

OK looks as if the make file creates a backup of the original module under r8169.bak so you just need to copy the original back.

just do:-
sudo updatedb
locate r8169.bak

then copy the bak file to r8169.ko in the same directory.

EDIT: ok, The make script creates a kernel module r8168.ko but tries to copy/backup r8169.ko so you need to copy this file to your kernel libs dir (/lib/modules/<kernel_version>/kernel/drivers/net/r8168.ko) then update your inital ram disk "sudo update-initramfs -u -k $(uname -r)"

Regards
Ian Dobson

---

### Post by rmjohnson144 on 2011-11-08
OK, r8169 is restored and seems to work fast now?  Maybe the Intel card cleared up some conflict.  a lot of posts said thier problem was a driver conflict.  Usually laptops as they have both wireless and ethernet on same machine.

I at first thought you wanted me to manually copy the r6168.ko driver, but that didn't make it work either.  but copying the bak file to ko and it recognized it right away.

Is there any hope for the newer Realtek driver?  it says version 8.026 while the ubuntu version says 4.00 if I read it correctly.

now, to test my mythbuntu partition (this is Ubuntu 10.04.3 LTS).  Hopefully this Intel card fixes it as well.

Thanks for your time
-=Mark=-

---

### Post by ian dobson on 2011-11-09
Hi,

If you go to the src directory where you compiled the driver, you should find a .ko file. Just try copying that to the kernel drivers directory. It might work, who knows...

Regards
Ian Dobson

---

### Post by rmjohnson144 on 2011-11-09
I did that already.  That's what I meant in the second paragraph when I said:

> I at first thought you wanted me to manually copy the r6168.ko driver, but that didn't make it work either.


I think I mistyped it and it should have read r8168,ko

I was hoping to find a way to make the new driver work, but the original one seems fine, so far.  not sure what else I can try.

Thanks again
-=Mark=-

---

### Post by ian dobson on 2011-11-09
Hi,

OK, just copy the .ko file (what ever it's called) from the src directory into your kernel network drivers directory, and see if that works.

Maybe you need to manually unload the ubuntu kernel module and manually load the new module (insmod/rmmod).

Regards
Ian Dobson

---

### Post by rmjohnson144 on 2011-11-09
It's working.

I had to delete the r8169.ko file or it would reload itself on reboot.  even after deleting it would reload itself until I ran the:

```
sudo update-initramfs -u -k $(uname -r)
```

but the Realtek drivers works wonderfully.  

also, when I removed the Intel NIC from my machine, the original r8169 driver would bog back down.  but with the new realtek r8168 driver, it works fine without the Intel NIC plugged in.

not sure what the hang up is, but the Realtek drivers did the trick.

Thanks a ton for all of your help
-=Mark=-

---

### Post by ian dobson on 2011-11-09
Hi,

Don't forget, if you install a kernel upgrade (apt-get update/upgrade) you'll need to go through the compile/install/update-initramfs process again.

Regards
Ian Dobson

---

### Post by rmjohnson144 on 2011-11-10
lol - That's what I figured.

I checked for updates when done to try and get mythbuntu working and it says I have kernel updates.  I aborted immediately.  lol

I'll try later if I need to update anything.  otherwise I'm not going to fix it if it isn't broke :P

Thanks again for your patience.
-=Mark=-

---

### Post by texaco on 2011-11-13
I had the same issue. But the NIC work pretty nice at ubuntu 11.10 32bits. You can test it with last ubuntu live cd.

I have opened an bug at launchpad.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/889646](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/889646)

I don't know how difficult be get 32bits NIC driver and put it at 64bits version.

---

### Post by ian dobson on 2011-11-13
> **texaco said:**
> I had the same issue. But the NIC work pretty nice at ubuntu 11.10 32bits. You can test it with last ubuntu live cd.

I have opened an bug at launchpad.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/889646](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/889646)

I don't know how difficult be get 32bits NIC driver and put it at 64bits version.

The 32bit and 64bit version of ubuntu/linux use the same source code, they're just compiled differently/use a different architecture files. It could well be that the 64bit version exposes a bug in the driver/hardware that doesn't show up on 32bit version.

Regards
Ian Dobson

---

