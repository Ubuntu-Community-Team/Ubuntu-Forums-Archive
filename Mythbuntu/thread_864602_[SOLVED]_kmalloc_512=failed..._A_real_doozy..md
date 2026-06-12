---
title: "[SOLVED] kmalloc_512=failed... A real doozy."
date: 2008-07-19
forum: Mythbuntu
---

### Post by Blonddeeni on 2008-07-19
Uh oh! I posted this on the General forum and now realise that being a Mythbuntu setup should have posted here. oops. Very sorry.#-o
 
Occasionally my system fails to load; showing these four lines on the display. (I've removed the splash screen option from the grub menu).

Starting Up...
Loading please wait...
[  6.142000] Kobject_add failed for :d-0000512 with -EEXIST,  don't try to register things with the same name in the same directory.
[  6.142000] Kernel panic - not syncing: Creation of kmalloc slab kmalloc_dma-512 size=512 failed.

Interestingly, the 6.1420000 number does not appear anywhere in the kern.log or the syslog for any of the boot sequences in the past.
Also, this can occur twice in a week, or not at all for a month.
The only way to get in is to do a manual reboot using the reset button, as the keyboard is locked out. Not even the 'caps-lock' key works.
This error message occurs regardless of whether it is a manual boot-up, or an automatic boot-up from the onboard ACPI timer.

here are the spec's of my system.
Motherboard:	 Asus M2NPV-VM
CPU:		AMD64 Athlon X2 5200+
Memory:		 DDR800 1G
Hard Drives x 2:  Seagate Sata 500G  with two 400G partitions  that have been LVM'd together.
Mouse:		 Microsoft PS2
Keyboard:		 Genius PS2 (Have just tried another Make of PS2, same problem)

Display : I switch between Philips lcd and my TV which uses AV. (Currently unable to use both at the same time, so have to reboot and change plugs to  change display, which is very awkward).

USB Dongle for the Mythtv remote receiver: (input: USB HID v1.10 Keyboard [Formosa21 USB IR Receiver] on usb-0000:00:0b.0-2)
Two Skystar-2 DVB-S cards for receiving Freeview signals for Mythtv. 

OS: Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Fri Feb 1 04:59:50 UTC 2008 (Ubuntu 2.6.22-14.51-generic)
ACPI

/usr/bin/mythbackend --version
Source code version     : Unknown
SVN branch              : trunk
Library API version     : 0.21.20080114-1
Network Protocol Version: 38
Options compiled in:
 linux debug using_oss using_alsa using_arts using_jack using_backend using_dbox2 using_dvb using_firewire using_frontend using_hdhomerun using_iptv using_ivtv using_joystick_menu using_lirc using_opengl_vsync using_opengl_video using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmcw using_bindings_perl using_opengl using_libavc_5_3 using_live

Internet via a dial-up modem, which max's out at 4KB/sec, but usually sits at around 2.5KB/s. So a 1meg transfer can take up to an hour sometimes.
To build the system I had to uplift the entire assembly and move couple of hundred km's to a friend's house with faster interweb, and camp there for a few days.

I have looked at the kernal log and the syslog and have been unable to see any difference between a failed boot sequence and a successful boot.
But as I am a noobie at all this, well..... what am I looking for? (I just go to the end of the failed log sequence and compare the results).

Have looked around the forums (+ google) and can only discover three other instances of this fault:
1) Having a USB card plugged in at boot via a dongle for an external hard drive.
2) Having two sata drives plugged in with a LVM partition. No reference was made as to whether internal or external.
3) Having a Genius keyboard plugged in, but no reference was made as to PS2 or USB. ([http://ubuntuforums.org/archive/index.php/t-710451.html](http://ubuntuforums.org/archive/index.php/t-710451.html))

I've changed the keyboards, (but both were PS2), removed the USB IR receiver, but no luck.

My other idea is the hostname causing problems, (Grunta+). I'm not sure how the "+" got in there, but all attempts to remove it have prevented Mythtv from working correctly, or at all sometimes.

Any ideas for a Noobie anyone?
 
I can provide the kern.log and syslog if required, but as they are incredibly long, not sure if they would fit within the restraints of a message post.

Cheers
Blonddeeni.

---

### Post by Blonddeeni on 2008-07-31
Alllrighty.
Seems this is quite the puzzler for us all.
Tried booting using the other operating system on the machine, (Knoppix), which I use for doing partimages of the system every month, only to have it fail on boot suddenly.
Yippeee. Now we're getting somewhere.
So it's most likely not a software fault.
With an independent os failing, and kmalloc standing for KernelMemoryALLOCation error, then the problem should be hardware orientated.
First suspect - The Ram.
So have replaced the ram (DDR2-800 DIMM) with DDR2-667 DIMM 1G, and will see how that goes for the next month.

Here's hoping. [-o<

---

### Post by hansdown on 2008-07-31
Hoping for the best Blonddeeni.

---

### Post by superm1 on 2008-08-01
> **Blonddeeni said:**
> Alllrighty.
Seems this is quite the puzzler for us all.
Tried booting using the other operating system on the machine, (Knoppix), which I use for doing partimages of the system every month, only to have it fail on boot suddenly.
Yippeee. Now we're getting somewhere.
So it's most likely not a software fault.
With an independent os failing, and kmalloc standing for KernelMemoryALLOCation error, then the problem should be hardware orientated.
First suspect - The Ram.
So have replaced the ram (DDR2-800 DIMM) with DDR2-667 DIMM 1G, and will see how that goes for the next month.

Here's hoping. [-o<
Giving the box a good run through memtest86 with the old ram (it's on the mythbuntu and ubuntu disks) wouldn't hurt on a day with light recordings.

---

### Post by Blonddeeni on 2008-08-22
Yep. Tried a memtest for around 9 hours, all checked out ok. I guess it happened when things were ok.
Oh great! 
Have just had the error today three times in a row. (Was wondering if it would even start).
Ick.
So back to square one.
Not the memory.
Not the ps2 keyboard.
Not the screen.

Now what we wonders?
I wonder if running a system update would help. Better do a partimage of the boot partition first.

hey ho, here we go. :|

---

### Post by ian dobson on 2008-08-22
Hi,

Sounds alot like a hardware conflict. Try removing all the hardware that you don't need to boot and try booting with a minimal on Hardware.

When the system boots try adding you hardware back one after the other until the system doesn't work again.

Regards
Ian Dobson

---

### Post by Blonddeeni on 2008-08-23
Cheers.
I'll have a go at that. Your suggestion made me go back and have a look at my system and I remember someone having trouble with a LVM partition, 

> Have looked around the forums (+ google) and can only discover three other instances of this fault:
1) Having a USB card plugged in at boot via a dongle for an external hard drive.
2) Having two sata drives plugged in with a LVM partition. No reference was made as to whether internal or external.
3) Having a Genius keyboard plugged in, but no reference was made as to PS2 or USB. ([http://ubuntuforums.org/archive/index.php/t-710451.html](http://ubuntuforums.org/archive/index.php/t-710451.html))


sooo Ill remove the LVM partition between the two sata hard drives.
If that doesn't work, remove one of the drives. (and the usb dongle for the remote).
Apart from that, not sure what else I can remove.

The curse of it all is the time delay between failures. twice in a day, or once in a month. I'll get stuck in this week, (Tue Hopefully).
I'm in for the long haul.

Will post results as I find them.
:)

---

### Post by Blonddeeni on 2008-09-01
Well here's a thing.
Sat down to do the "Remove LVM" episode, and noticed that gparted shows my swap (sda5) hanging off sda2. (Which is "extended"), whereas cfdisk just showed sda5. As swap.
I thought that looked untidy, so using both those programs removed sda2 and sda5, remade sda2 as swap, and as a "primary" partition.
Rebooted and noticed that my error on boot-up that I have always received about being "unable to load resume so loading normally" or some-such; had gone.
"Cool" I thought.
Then had a go at doing the same to my laptop (Dell Latitude D800) running Ubuntu 8.40.
Well that was a learning curve and no mistake. Turns out that my idea of what swap does, and what swap actually does are two different things. lol
Long story short, have remade the Mythbuntu 7.10 box's swap to be primary, and to remove the "resume" option, both from the kernel line in the /boot/grub/menu.lst using "noresume", and to comment out the uuid=xxxxxxxxx line in /etc/initramfs/config.d/resume file.
That was one week ago, so have another three to go before I would consider this to be a success.
Same on the laptop.
See you in three weeks: or sooner if it fails again.
Cheerio.

PS: The swap is working I think, here's my "swapon -s" result:
$ swapon -s
Filename	  			Type	    	Size    	Used	Priority
/dev/sda2                               partition	2650716	34836	-1
$

---

### Post by Blonddeeni on 2008-09-17
Ahh smeg! It did it again.:(
But since cleaning up the swap, it did not come up with the "Kobject_add failed for :d-0000512 with -EEXIST, don't try to register things with the same name in the same directory" error, only the kmalloc error.
However, now I have removed the "quiet" option from the kernel boot line in the grub "menu.1st", it shows that just before the "kmalloc " error, the previous line is simply a row of ============================== 
So what does a row of "equals" mean?
Anyone?

Today (13:15 18-sep-08 ) replaced one of the dvb cards with another one of a different type. As my mate said, "Rather than work your way through every component, if you're the only one have this problem, then what is unique to your system? Answer, you are the only one to have TWO DVB cards. So try moving them/one to different PCI slot(s)". 
Trouble is, this Motherboard only has two slots.
(I have two DVB cards because in this country we have two different frequencies, which can make for real problem when trying
to record two programs on different frequencies at the same time. Currently my machine can do 6 simultaneously, 3 on each. Means there is no hassle at the stop/start recording overlap of programs. Mythtv is so cool).
So am trying two DVB cards made by two different manufactures. Will see how that goes.

NB: Am gearing up to install Mythbuntu amd64 onto a partition on the second hard drive, and have a dual boot going. Will eventually separate the two hard drives completely, and for a month run on just one running 7.10, and then the other running 8.04. Will see how that goes.

But first, the DVB card "Conflict" theory.

"Why can't it ever go to the Goram Plan?"  Capt' M Reynolds.

PS: Ever get the feeling that I'm using this thread as my log. ;)


4 hours later: kmalloc error again. Will change the other DVB card, if still a problem, reduce down to one card.

---

### Post by Blonddeeni on 2008-09-29
Well it did it again on 28/09/08 .

So have tried just about every combination possible involving 3 dvb cards (2 x Skystar 1 x TechnoTrend), in two slots. One more test to go on that front.
Have started installation of Mythbuntu amd64 Hardy from cd onto a spare partition. Currently dual booting, default being Feisty. The Hardy version is being stubborn in that I can watch TV, but get no Program guide data.  Weird.

Bit of a bother that Hardy doesn't come with wvdial.

Once (if) I can Get Mythbuntu amd64 8.04 running, will transfer it to being the default and see how things go. But first wait for the current card test to fail.

Cheerio.

---

### Post by Blonddeeni on 2008-10-06
Well so far the only progress has been the fact that it failed while I was using my lcd monitor, so can now up load a picture of the screen.
Mythbuntu amd64 8.04 failed, but on trying the i386 version, had a success, mostly. Getting the lirc to work is not going too well. 

Hey ho, so it goes.

---

### Post by Blonddeeni on 2008-11-11
Horaaaayyyy.
Got it fixed!
Turns out it was the sda sata cable connector.
Found this out after reading the very top line of the screen on my TV when it failed, and from reading about kernel panics and how it dumps everything to the screen. But as it all scrolls off the top, not too much use. 
However, by looking at the top of the TV screen, saw three letters I recognised, (IE: sda), so went fiddling with my first sata drive. 
Removed the cable, removed the drive and put it into a different slot for different airflow, plugged the cable back in, blah blah blah.

So for the last month all ok, so now I call it solved.

I do not know how to mark this thread as SOLVED, so have just bunged that word in the title. :)

Whoo hooo, what a relief to actually nail it down to a specific item.

Have fun all.
Blonddeeni.

---

### Post by ian dobson on 2008-11-12
Hi,

To mark a thread as solved, just go to the top of the page, and there's an option "thread tools".

Regards
Ian Dobson

---

### Post by Blonddeeni on 2008-11-18
Cheers Ian.
Thank's for that.
Still not used to this big world of the interweb.:)

---

