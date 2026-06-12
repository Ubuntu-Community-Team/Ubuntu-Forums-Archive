---
title: "I am new"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by Skramer on 2009-04-04
Hi, am brand new to both Linux and Ubuntu.
I am trying to get wireless connection on my computer.
I am useing Ubuntu 8.04
The wireless PCI adapter I am useing is from encore electronics ENLWI-G2.
I tried to put in the CD that it came with but that did not work.
So I went on to my other computer and went on to the encore website and put the driver for for Linux on to my flashdrive.
Then I put my flashdrive into the compputer that I put the Ubuntu on.
When I opened the file and  right clicked and hit open it says that there is no application installed for this file type.
Howevere below where it said open it said open with application.
I have no idea what to do.
Can anyone help me?

---

### Post by Ericyzfr1 on 2009-04-04
Did the driver came with a *.deb extension? if not browse the forum and you should be able to find the procedure to install it correctly. In the search term input " driver installation" or "wireless driver".

---

### Post by cariboo on 2009-04-04
The driver for your device may already be installed. Open an Applications-->Accessories--Terminal and type:

```
sudo lshw -C network
```

and paste the output in your next post.

Jim

---

### Post by Skramer on 2009-04-04
Ok I did that an I got:


Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [options ...] 
lshw-version

-version    print program version (B.02.12.01)

format can be
       -html          output hardware tree as HTML
       -xml           output hardware tress as XML
       -short         output hardware tree as paths
       -bussinfo      output bus information

options can be
        -class CLASS  only ahow a certain class of hardware
        - C CLASS     same as '-class CLASS'
        -disable      TEST disable a test (like, pci, isapnp, cupid, etc.)
        -enable       TEST enable a test (like, pic, isapnp, cupid, etc.)
        -quiet        don't display status
        -sanitize     sanitise output (remove sensitive information like serial numbers, etc.)





Now what do I do?!

---

### Post by Iowan on 2009-04-04
I presume your typing may have slipped - I get that page when I mistype something (netowrk is my usual trick). Try it again - notice the capital "C".

---

### Post by Skramer on 2009-04-04
So just try to put "sudo lshw -C network" in again?

---

### Post by Iowan on 2009-04-05
Yes, **sudo lshw -C network** in a terminal.

---

### Post by Skramer on 2009-04-05
Ok I did that an I got this:

Now what?

---

### Post by mogul218 on 2009-04-06
Go to System -> Preferences -> Network Configuration and click on the Wireless tab and set up your wireless network preferences.

---

### Post by Sniper.In.The.Darkness on 2009-04-06
Yeah, now you should just be able to go into the wireless config in the top corner and enter your network key and it should work.

---

