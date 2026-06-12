---
title: "Trouble with RT patch to kernel"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by inverarity on 2006-07-11
Ok, so I've read through the whole forum and nobody's had this problem yet:  I followed the insructions to compile the vanilla kernel from [http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption](http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption).
The only difference between my procedure and the procedure on the wiki is that I used a later patch for the 2.6.16 kernel (patch rt29 instead of rt26).  Anyway, there are no errors in compiling or installing the kernel, but when I go to reboot with the new kernel, it hangs right after printing out:

```
Uncompressing Linux... Ok, booting the kernel.
```

and then it's frozen.  I've tried recompiling twice with slightly different kernel options in menuconfig that I thought might be relevent, but nothing has worked.  Given how long it takes to compile and test, trial and error is not the most effective method for troubleshooting so I figured I'd ask y'all.  Unfortunately, my messing with the config options in menuconfig was pretty haphazard so I can't recall which variations I tried.

My computer is a laptop, an IBM thinkpad T42 with a Pentium M 1.8Ghz.  I'm not sure if any other info about my computer is relevent but if so I'm happy to post it.

Anyway, I don't really know where to look to try to find feedback on the bad boot, but if y'all can tell me where to look, I'll dump some log files up here if you think it'll help.  I have a feeling that very little if anything got written to the logs since it hangs so early.

Perhaps there's some overlooked option that I should set?

Anyway, thanks for any help.

---

### Post by inverarity on 2006-07-11
Just an update, I tried using the rt26 patch instead of rt29 and it has the exact same problem.  Compiles and installs sucessfully, but hangs at boot.

---

### Post by Sheik Yerbouti on 2006-07-11
Are you sure it's frozen? With my RT kernel it goes to bring up the graphic splash which is not really defined so the screen blanks but it is still booting. Watch the HD light and see if that is the case.

---

### Post by dolson on 2006-07-11
I swear I put something in the wiki about removing the splash option from that grub menu entry... I guess not. I will add it now.

Okay I already had it there:
Next, find the line that says something similar to *kernel /vmlinuz-2.6.16-rt26 root=/dev/hda2 ro quiet splash* located nearer the bottom of the file, and remove the word *splash* from the end of the line. This will prevent your screen from being blank as your system boots the realtime kernel.

If you did this, can you confirm how long you are waiting for boot up? It is very odd that the kernel would hang there, so I suspect it was simply the oversight. Let us know!

---

### Post by inverarity on 2006-07-12
Ok, I deleted "splash" from the kernel line in menu.lst---sorry for not reading tfm---but it didn't help.  This time I let it hang for a little over 7 minutes just to be certain and sure enough nothing happened.  The hard drive activity light never flickered.  Just for comparison I timed the boot with the stock ubuntu kernel (version 2.6.15-25-686) and it took about 50 seconds.  In case it helps the menu.lst is this:

```
title           Ubuntu, kernel 2.6.16-rt26
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.16-rt26 root=/dev/hda3 ro quiet
savedefault
boot

title           Ubuntu, kernel 2.6.16-rt26 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.16-rt26 root=/dev/hda3 ro single
boot

title           Ubuntu, kernel 2.6.15-25-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-25-686 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-25-686 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-25-686 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-25-686
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

```

There's some further lines dealing with memtest and my windows partition which I didn't include.  Perhaps the lack of an initrd line has something to do with it?  /boot/initrd.img-2.6.16-rt26 doesn't exist at all.

---

### Post by dolson on 2006-07-12
That is the only possible explanation... Why on earth don't you have an initrd line?! lol

Check if the initrd file exists, it should be /boot/initrd.img-2.6.16-rt26. If it does, add the line in.

---

### Post by inverarity on 2006-07-12
Perhaps I forgot to add the --initrd option when I ran make-kpkg?  I'll try again to be certain.

---

### Post by inverarity on 2006-07-13
Ok, bad news.  After recompiling the kernel with the --initrd option this time, it still doesn't boot.  I double checked that the initrd image is in /boot/ this time and the line for it is present in menu.lst AND I disabled the splash just to be safe but after all this, it still hangs.  Just like before the hard drive activity light doesn't even flicker once.  Is it possible that there's a menuconfig option that needs to be set in order for the the initrd to be properly constructed or something?  It makes sense actually that this would happen since the first two times I tried (when I was using rt29) I followed the instructions on the wiki line for line and thus I'm pretty sure I didn't forget the --initrd option.  So, any other ideas?  As I said before, I don't even know what logs to check to start solving this problem.

---

### Post by inverarity on 2006-07-13
I tried adding support for ext2 and ext3 into the kernel itself instead of using modules, but it still freezes.  I turned off the "quiet" option in menu.lst so I could actually get a look at some useful output.  The last message from the kernel before it hangs is:
```

input: AT Translated Set 2 keyboard as /class/input/input0
```

What's really irritating about this is that any messages from my custom kernel don't appear in the system log browser (from System>System Log).  If there's a way to see the messages from these failed boots I don't know it...  Since there's nothing in /var/log/messages I'm guessing that the freeze happens too early in the process for thos messages to have been written to a file yet.  Since I don't feel like watching it crash and writing each message out by hand I'll just leave you with that one for now...  Looking at dmesg from a successful boot of the ubuntu kernel the next messages after that one are:

```
[17179573.740000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.740000] TCP established hash table entries: 262144 (order: 9, 3145728 bytes)
[17179573.744000] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[17179573.744000] TCP: Hash tables configured (established 262144 bind 65536)
[17179573.744000] TCP reno registered
[17179573.744000] TCP bic registered
[17179573.744000] NET: Registered protocol family 1
[17179573.744000] NET: Registered protocol family 8
[17179573.744000] NET: Registered protocol family 20
[17179573.744000] Using IPI No-Shortcut mode
[17179573.744000] ACPI wakeup devices: 
[17179573.744000]  LID SLPB PCI0 UART PCI1 USB0 USB1 AC9M 
[17179573.744000] ACPI: (supports S0 S3 S4 S5)
[17179573.744000] Freeing unused kernel memory: 332k freed
```

So perhaps the freeze has something to do with IP & TCP?

---

### Post by inverarity on 2006-07-15
Success!!!  After some extremely painful trial and error, I finally got the custom kernel to compile, even with the latest rt29 patch applied.  My hunch that it had to do with iptables turned out to be correct, and when I activated the following options in menuconfig (which had previously been off) I was able to compile a bootable kernel:

```

Networking--->
   Networking Options--->
      [*]Network packet filtering (replaces ipchains)

Networking--->
   Networking Options--->
      [*]Network packet filtering (replaces ipchains)--->
         Core Netfilter Configuration--->
            <M>Netfilter Xtables support (required for ip_tables)

Networking--->
   Networking Options--->
      [*]Network packet filtering (replaces ipchains)--->
         IP: Netfilter Configuration--->
            <M>IP tables support (required for filtering/masq/NAT)

```

After that I only had 2 other problems with my new kernel.  First: my wireless card wasn't working at all and according to dmesg it was failing during boot with an error -2.  A quick google search took me to this site: [http://ipw2200.sourceforge.net/INSTALL](http://ipw2200.sourceforge.net/INSTALL) where I followed the directions under section 10.  It was as easy as downloading the firmware from [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php), creating the /lib/firmware/2.6.16-rt29 directory, and then copying the 7 .fw files into that directory.  I used version 2.4 because that's what the dmesg error indicated it couldn't find... (If you have this problem you should look into the dmesg error to find out what version to download.)  After that the wireless worked automagically just like with my stock ubuntu kernel.

Second: I have an ati graphics card (Radeon 9600) and use the fglrx driver normally but even though I had the fglrx-driver-source in my /usr/src/modules directory, and evne though it compiled a .deb which installed without error, it wasn't actually working fully.  3d acceleration didn't work (output of fglrxinfo was "mesa") and there was a bizarre glitch involving the mouse pointer where sometimes a black or white line would appear under it and follow it around as if it were part of the sprite.  I tried running module-assistant to recompile and reinstall the module, but it gave me some errors regarding missing makefiles.  A search on the ubuntu forums took me to this thread: [http://www.ubuntuforums.org/showthread.php?p=1237831](http://www.ubuntuforums.org/showthread.php?p=1237831) where ehula's post contained the clue that allowed to fix the fglrx module.  I now have 3d acceleration working with the custom kernel too.

I realize that most of this has nothing to do with ubuntu audio since the problems had nothing to do with the realtime patch in the end, but I wanted this post to be as useful as possible to others experiencing these problems.

As far as audio goes, I'm happy to report that I can now run jack at 32 frames with no xruns,  (1.45 milliseconds latency) a big improvement over my old kernel which had about 50 milliseconds latency w/out xruns at best!

Can't wait to see how the ubuntu studio project develops!

---

### Post by dolson on 2006-07-17
I would have never even suspected that... But good for you, and good job getting it working!

---

### Post by hanzomon4 on 2006-07-20
I'm having problems getting my 2.6.17-rt6 to boot.
When I boot in to the kernel evrything seems fine, but after the "uncompressing the kernel" it stops and shows about a half screen output that starts with this ```
kernel BUG at kernel/rtmutex_common.h:74!
```
I am kind of lost as to what to do. I've compiled a 2.6.17 witout the rt patch and it worked. I tried the rt7 and rt6 patch but I still got the same problem.

I would appreciate any help

---

### Post by markusw on 2006-08-01
Hello all,

well after this nice descriptions I thought, that should work for my IBM A31p notebook, too. But unfortunately, it doesn't.
The boot process stops just after the AT keyboard message and before this IP chain stuff, as described before. I followed all the hints, especially the ones about the networking options.

Perhaps, meanwhile someone acquired more wisdom and tricks about the kernel configuration.
With the Ubuntu kernel-image (current Dapper 6.06 LTS) sound performance is not as good as with my old genuine debian distribution with customly compiled kernel (with RT-patch).

So every help in getting forward to low latency is really appreciated.

Best wishes,

Markus

---

### Post by markusw on 2006-08-01
Sorry, I forgot to add, that this booting hold occurs even for an RT-unpatched kernel source (just the evm-patch).

Markus

---

