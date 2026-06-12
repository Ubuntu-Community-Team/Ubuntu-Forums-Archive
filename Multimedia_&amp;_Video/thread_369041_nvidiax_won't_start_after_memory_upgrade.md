---
title: "nvidia/x won't start after memory upgrade"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by cbozic on 2007-02-24
I have an HTPC box running an up-to-date dapper drake ubuntu with 512MB of ram.  The other day I ordered a stick of 1GB RAM for the machine.  When I replaced the old stick with the new one, everything started out fine until the boot process tries to start X (gdm) using the nvidia driver.  It gives me the error, no usable screens found.  

It's interesting to note that the nv driver works fine with the new ram.  However, I need the mpeg decoding features that the nvidia driver gives me so using nv can't be a permanent solution for this machine. 

Also interesting is that everything works fine when I revert to only the original 512MB DIMM.  

Suspicious that I had a bad 1GB DIMM, I sent the first one back and got another.  The problem still exists with the replacement.  

I noticed that dmesg says NVRM: RmInitAdapter failed! when I try to restart X with the nvidia driver but after searching the web I still don't know what this means or how to fix it.

Does anybody have any ideas on how to get around this problem?

---

### Post by kerry_s on 2007-02-24
Have you tried running> sudo nvidia-xconfig <when it drops you to command line.

---

### Post by cbozic on 2007-02-24
Unfortunately, running nvidia-xconfig doesn't change anything.    Keep in mind that my nvidia driver worked/works fine when the 512M DIMM is the only memory in the machine.  So, in theory my xorg.conf shouldn't need to be changed.  Then again, in theory a memory upgrade shouldn't cause X to stop working.  :) 

Any other ideas?

---

### Post by kerry_s on 2007-02-24
No, if your system uses shared resources, then changing the ram could throw it off since it calculates by ram amount. You should try completely removing the nvidia driver and then reinstall it after a reboot.

---

### Post by cbozic on 2007-02-24
Well, I tried completely uninstalling everything nvidia related from synaptic.  The restricted modules, nvidia-glx nvidia-common.  I rebooted and then installed the latest nvidia driver available on Nvidia's website.  Then I ran nvidia-xconfig manually.  I still get the following lines in dmesg:

NVRM: RmInitAdapter failed! (0x21:0xffffffff:679)
NVRM: rm_init_adapter(0) failed
allocation failed: ouot of vmalloc space - use vmalloc=<size> to increase size.

I assume vmalloc=<size> is a kernel boot prarmeter.  Does anyone have a suggestion on what a possible value for <size> should be?

Or, any other ideas?

---

### Post by tseliot on 2007-02-24
Boot using the Nvidia driver, let the Xserver crash, then type:
```
cp /var/log/Xorg.0.log $HOME/
```

then set the driver to "nv" and get back to the Desktop Environment.

Then post the Xorg.0.log which you will find in your home folder

---

### Post by cbozic on 2007-02-24
Thanks for taking a look at this.

---

### Post by kerry_s on 2007-02-24
```
(--) Assigning device section with no busID to primary device
```

This is the line where i think the problem starts. Go into your bios and see if yours is set to start the pci first for video.

If all looks okay, you might try moving the video card to another slot to see if it works with a different busid. 
Is your card in the 3rd slot?
```
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:3:0:0. 
```

---

### Post by cbozic on 2007-02-25
The motherboard has 2 PCI slots, 1 PCI Express x16 slot, and 1 PCI Express x1 slot.  The video card is a PCI Express x16 card so I only have one place to put it. Also, the BIOS is already set up to look in the PCIE slot first.  It is in the proper place according to lspci.  Attached is the output of lspci -v.  

I doubt it's a bad pci slot because it works with the 512MB stick of RAM.  Still, I'm open to suggestions because I'm obviously out of any better ideas.

---

### Post by kerry_s on 2007-02-25
I running out of idea's to. :( 
Are you sure you got the right kind of memory?
Does your board support 1gb?
Can you post the output of> sudo lshw <so we can see all your specs?

---

### Post by kerry_s on 2007-02-26
Hey, you might want to check out this site and see if you see any thing there that might help-> [http://download.nvidia.com/solaris/1.0-8762/README/index.html](http://download.nvidia.com/solaris/1.0-8762/README/index.html)

I'm reading through it now and even found some nice new features i didn't know about. :)

---

### Post by cbozic on 2007-02-26
Well, the motherboard is supposed to support 1G sticks.  It's an ASUS A8N-VM CSM board.  I even updated the firware just to see if that would work.  Still no luck.  This is certainly a strange one.  

I haven't had a chance to look at that site yet, but I will ASAP.

Attached is the output of lshw.  Enjoy!  :)

---

### Post by sabotor78 on 2007-03-04
Hello! I have the same problem. But, i can start X after i reinstall nvidia drivers and everything woks just fine until poweroff/reboot. After a reboot, X server crashes and i must reinstall nVidia drivers.

---

