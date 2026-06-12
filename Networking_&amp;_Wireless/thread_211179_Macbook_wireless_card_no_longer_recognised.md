---
title: "Macbook wireless card no longer recognised"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by forbes on 2006-07-07
Hi,

I have a Macbook (not pro), which up to last night was working great with WPA and network manager.  Unfortunately this morning when I powered it up, there was no wireless shown in my network settings.  The hardware is Ok as I have booted into OS X and its still working OK there.  The only thing I did last night before shutting it off was install the citrix client and did an update.

Anyone else having this problem now? How should I troubleshoot this from here, I'm a bit of a noobie.

---

### Post by forbes on 2006-07-08
OK, I've done a bit more digging.  Here's what I come up with so far.  Just hope someone can offer some advice [-o< 

Remember the card was recognised and working a couple of days ago.  I believe it is a Atheros AR5006EX (aka AR5424).> 

However its not being recognised any more:
```
$ lcspci
0000:02:00.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001c (rev 01)
```

This is my kernel version:
```
$ uname -r
2.6.15-25-386

```

but:
```
$ sudo modprobe ath_pci
WARNING: Error inserting ath_rate_sample (/lib/modules/2.6.15-25-386/madwifi/ath_rate_sample.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath_pci (/lib/modules/2.6.15-25-386/madwifi/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

I've checked synaptic for which madwifi modules are installed and I've got the following:
```
linux-restricted-modules-2.6.15-23-386 (installed 2.6.15.11-1)
linux-restricted-modules-2.6.15-23-686 (installed 2.6.15.11-1)
linux-restricted-modules-2.6.15-25-386 (installed 2.6.15.11-2)
linux-restricted-modules-2.6.15-23-686 (installed 2.6.15.11-2)
```

please help, I've idea where to go except a fresh install :oops:

---

### Post by forbes on 2006-07-08
OK, I should have confidence in myself :oops: 

To fix I re-installed the madwifi module in synaptic.  One of the config files must have been corrupted.  Thanks for reading this far.

---

### Post by hajk on 2006-08-04
Going through some older posts, I notice that you are running a -386 kernel, that is a kernel that is not SMP-enabled. Seems like a waste to let one of your Core Duo processors go unused... The 686 kernels are all SMP-enabled.

---

### Post by martinbures on 2006-08-04
When you update the kernel on the macbook, update manager sets it back to 386, single core.  If you check out the post here, at the bottom, I wrote how to make the thing run 686 SMP again.

[http://bin-false.org/?p=17](http://bin-false.org/?p=17)

My question, is my macbook seems to run really hot when it is running Dapper, even when it is idle.  When I am running OS X and not doing much, it is pretty cool.  My thought is that somehow, the kernel never scales down the CPU, even when it is not doing anything.  Does anybody have any ideas on how to fix this?  Or, does anyone know where to start looking to point me in the right direction?

Thanks.
martin.

---

### Post by hajk on 2006-08-05
> **martinbures said:**
> When you update the kernel on the macbook, update manager sets it back to 386, single core.


Not quite! The symlinks /vmlinuz and /initrd.img are set to point to the last updated kernel, in your case the non-SMP 386 kernel. But why don't you just remove that kernel with Synaptic (search for "386" in Name, there should be 4 items to remove)? With only the SMP-enabled 686 kernel, restricted modules and their "latest dependency" packages installed, any update will still have the symlinks pointed to the right kernel, no?

---

### Post by martinbures on 2006-08-05
Well, I am not necessairly new to linux, but my experience delving under the hood is somewhat limited.  In getting this macbook, I have been forced to look more and more under the hood, so, I guess the reasons that I have not done that are that (1) I did not think of that and (2) I am trying to slowly change things and make sure that I don't hose my system.  I will look at doing this.  Thanks!

---

### Post by Raznog on 2007-02-03
I am using a Macbook pro 17" and the same thing happend to me when i did an update ( on 6.10) reinstalling the modules worked for me too thanks alot =D

---

