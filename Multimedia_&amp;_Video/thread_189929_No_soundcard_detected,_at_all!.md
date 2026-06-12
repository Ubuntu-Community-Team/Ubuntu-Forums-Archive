---
title: "No soundcard detected, at all!"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by sparX CG on 2006-06-05
I just installed Xubuntu 6.06 on my old Compaq. (Woohoo!  3 day old OS on a 10 year old computer!)  Runs really great, actually quite responsive with the color depth set at 16 bit.

Everything works, except one thing.  The soundcard isn't detected at all.

```
sparx@sparxP200:~$ dmesg | grep snd
sparx@sparxP200:~$
```

```
sparx@sparxP200:~$ lspci | grep snd
sparx@sparxP200:~$
```

```
sparx@sparxP200:~$ cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
sparx@sparxP200:~$
```

I have a feeling Ubuntu doesn't even know I have a sound card in there.  It's an on-board, I don't know which one though.  I know it's supposed to work because it was blasting music when it was a Windows box.

Any ideas?

---

### Post by ktulu1115 on 2006-06-05
It seems there's a lot of sound issues in Dapper.  I'm afraid I can't give any advice, except for the fact that I'm suffering the same problem.  Supposedly some people installes latest stable ALSA from source and it worked, but in my opinion that's a pretty extreme measure....  I would expect more from Ubuntu than this.

---

### Post by sparX CG on 2006-06-05
True...  However, my problem seems far worse than that of others, as I'm getting nothing about sound from dmesg nor from lspci.  To make matters even worse, my /proc/asound doesn't even exist.

Not happy!  I'll try out some other live CD to see if sound works there.  If it does, I really hope the Ubuntu team will fix this fast!

---

### Post by sparX CG on 2006-06-06
Okay, now...  This is really weird...  No soundcard is detected on SLAX nor on DSL...

I have no clue what's going on.  Do you?

Thanks in advance, Ubuntu rocks! :D

---

### Post by ktulu1115 on 2006-06-06
That doesn't sound (ha) right....    this may be stupid but just to rule it out, could you double check your BIOS settings and ensure the onboard sound wasn't disabled?  If none of the distros detect it, I'd be willing to bet it's hardware-related.

Do you know exactly what the onboard card is?  Or maybe the model number of the Compaq could help.  It's possible it's some kind of software-based device or something - like the Winmodems (let's hope not).

---

### Post by sparX CG on 2006-06-06
Thanks for the reply!  I thought this thread was going to die...

It's a Presario 3060.  Its original 4 CD changer wasn't bootable, so I had to change the CD-ROM drive.  The BIOS doesn't support booting from CD either, so I used a Smart BootManager floppy to boot from CD.  In fact, the BIOS isn't configurable at all...

The computer is a bit like an iMac, with everything built into one box.  It's a bit like a tower with an LCD panel stuck on its side.  Speakers are integrated.

The audio chip on the motherboard says ESS, I don't remember the numbers...

The CPU is a 200MHz Pentium.  Old, yes. :)

Another thing, the speakers make a little bit of static noise when I move the mouse or when the HD is running.  It doesn't do that on other live CD's though.

I'd really like to get this fixed soon, I wanna play some CD's on it! :)

---

### Post by sparX CG on 2006-06-07
Bump!  I really need help on this...

Does anyone have any ideas?

---

### Post by ktulu1115 on 2006-06-07
About the only thing I can recommend is trying to find out specifically what kind of audio chip is in your PC.  Either open it up and get the info written on the chip, or search online for Presario 3060.  Then see if you can find what kernel module works with that card and try manually loading it with a modprobe...  Other than that I don't have any suggestions unfortunately.

---

### Post by cheuschober on 2006-06-08
Just to throw in my two cents in the matter (and maybe this can lead some of you geniuses to the answer)...

Specs: xubuntu 6.06, 386 kernel, on Toshiba A45-S130 (Intel Celeron with the Intel 855mb and Intel integrated sound card)

Trying to use the stock ALSA drivers to no sucess - but that's not *entirely* true and I'd like to know if anyone has experienced the same:

When the system boots to the login screen the drums that signal the system has essentially loaded do play through my speakers, however, after login I lose the sound. This would leave me to believe that somehow somewhere the existing alsa drivers can do that voodoo that they do.

Anyone's thoughts of course would be appreciated.

Best,
~Chad

---

### Post by lesjohnson on 2006-06-08
I guess I'll join the thread. Just upgraded to dapper and lost all sound. No sound card found. 

using: ASUS a8n premium, AMD athlon 64x2 3800, 2 gig corsair memory.

This is close to ktlu1115's setup. I wonder what steps you went through to get sound?

Listening to Sound of Silence. :(

---

### Post by sparX CG on 2006-06-08
I didn't do an upgrade, but rather a fresh install to a formatted HD.

I'm thinking it's maybe that my on-board sound is too old or too proprietary to be detected.  1996 Compaqs... :(

---

### Post by jobezone on 2006-06-08
EDIT: try installing these packages: 
alsa-base alsa-utils alsa-oss
then run **sudo alsaconf**.

---

### Post by Ekin on 2006-06-09
Good solution...except one thing:
THERE IS NO ALSACONF IN UBUNTU since warthy. It has been removed because of some bug ur something like that.

---

### Post by ktulu1115 on 2006-06-09
After a *lot* of tinkering, I finally nailed down the problem.  For those who are experiencing the problem, did you have an existing /home partition that you didn't format?  On my system, I kept my /home unformatted from my previous Dapper install.

However, after a good amount of frusteration and many reinstalls, I decided to create a new user during the install process and not use my existing account I had in /home.  The sound worked perfectly on the new account, no matter what changes I made to the system.  When I added the old account, it originally worked but quickly broke.

In the end, it all came down to /etc/groups and /etc/gshadow.  The existing user I had wasn't placed in all the same groups as the new user was - I specifically recall a group named 'sound', which I suspect was the whole problem all along.  :roll:

cheuschober & lesjohnson - from the symptoms you described, it sounds like this might work for you (with some luck)

sparX CG - unfortunately, I can't think of anything.  pretty much all the sound problems I've seen/heard of with Dapper is the sound originally working then breaking.  if it's not being detected at all from the get-go, I believe it's most likely an entirely different issue.  anyone else agree?

---

### Post by sparX CG on 2006-06-09
I think I would have to agree...

Hopefully a later update will fix it!

---

### Post by enslam on 2006-06-09
Thanks for narrowing down the problem ktulu1115.
After adding my user to all of the groups oem was in everything started working fine.

---

### Post by ktulu1115 on 2006-06-09
[QUOTE=enslam]Thanks for narrowing down the problem ktulu1115.
After adding my user to all of the groups oem was in everything started working fine.[/QUOTE]
Glad to hear it!  I drove myself nuts for awhile trying to narrow this one down, I had a feeling it had to be something really simple like this.

---

### Post by enslam on 2006-06-09
The really interesting thing is that making the change made my usb disk auto mount and cdrom's were read correctly.
This fix could solve a lot of other issues as well.

---

### Post by ktulu1115 on 2006-06-09
That's excellent to hear - I'm curious what the whole cause of this is - perhaps a udev or hotplug issue?  Regardless, I suppose this is something that should be made known more widely.

---

### Post by blueturtl on 2006-06-09
> I didn't do an upgrade, but rather a fresh install to a formatted HD.

I'm thinking it's maybe that my on-board sound is too old or too proprietary to be detected. 1996 Compaqs...

I would like to point out that systems of this age often use ISA soundcards that are not automatically detected by modern Linux distros to avoid unnecessary crashes (has something to do with SoundBlaster compatibility and the way the ol' ISA bus worked). Your souncard most likely is supported, but you will have to manually configure it.

Knowing Compaqs (and I did own a 96 Presario) it probably has a flavour of ESS AudioDrive in it. Try  [this link]("https://wiki.ubuntu.com/HowToSetupSoundCards") and see if you can find something usefull there!

---

### Post by sparX CG on 2006-06-09
Oh, great...  I just did 'sudo modprobe snd-es1688' and the static became louder... :(

EDIT: Right, I opened it up, and it's an ES1888 that I have.  I'll try probing that.

EDIT2: No good, probing snd-es1888 says no such module, probing snd-es18xx says device not found...  Maybe I misread those little characters printed on the chip?

EDIT3: SHWEET!!  I'm blasting music again, thanks to the snd-es1688 driver.  However, there's a weird crackling noise when I move my mouse, when I type stuff and when the HD is working. :/  I'd like to see that fixed...  I'll keep you updated.  Thanks to bluturtl for providing the link, thanks to whoever wrote the wiki page. :)

---

### Post by jobezone on 2006-06-10
[QUOTE=Ekin]Good solution...except one thing:
THERE IS NO ALSACONF IN UBUNTU since warthy. It has been removed because of some bug ur something like that.[/QUOTE]
What, totally removed, even from alsa-utils?
Then I'm sorry, because I was running a debian machine, and I found it in this package. But just to make sure if it exists in some package, try doing this (if you want to pursue this matter, of course):
```
sudo apt-get install apt-file
sudo apt-file update
apt-file search alsaconf
```
and does this find any package which installs **/usr/bin/alsaconf**?
If it doesn't, then I'll slowly move back, turn to the door, and run fast like hell for waisting everybody's time! :)

---

### Post by Tyche on 2006-06-11
jobezone said:
"and does this find any package which installs /usr/bin/alsaconf?
If it doesn't, then I'll slowly move back, turn to the door, and run fast like hell for waisting everybody's time! "

<humor>
You can start running now.  <apt-file search alsaconf> returned nul.
</humor>
It WAS a good try, though.
Tyan motherboard
Pentium III 750 chip
SoundBlaster Live 5.1 sound card
512MG RAM
80 G Hard drive - split 40/40

Craig
Tyche

---

### Post by sparX CG on 2006-06-11
Nobody has a soltuion to my fuzzy sound?  I think this problem is Ubuntu specific, as my other live CDs didn't emit any fuzz...

---

### Post by ktulu1115 on 2006-06-11
Mouse, keyboard, & hard drive access...  what do they all have in common - IRQ's!  If I didn't know any better, I'd say there's some sort of problem with IRQ handling, or perhaps the sound card/player not having large enough buffers to handle the interrupts (this would make sense on an older machine).  What doesn't make sense is that it works fine on other distros like you said - what application are you using...  XMMS?

---

### Post by greghill on 2006-06-11
Might as well throw in my 2 cents as well -- just upgraded to Dapper and like the rest of you, all sound disappeared. No sound card recognized. How do I run "detect" to see if Dapper can find a sound card? Live CD seemed OK, but I did the "upgrade" thing live on line (didn't use the CD). Really strange.

---

### Post by greghill on 2006-06-11
Just as a not to my post above, this is what I get when I try to sudo alsaconfg:

greg@ubuntu:~$ sudo gedit alsaconf
Password:
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver return ed error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned er ror: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned err or: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
greg@ubuntu:~$

---

### Post by sparX CG on 2006-06-11
Yup, sound is a bit fuzzy when I use XMMS.  But there's still fuzz when I'm not playing anything.  For example, I can hear the HD running (der der der) but there's also fuzz coming right out of the speakers (bz-z-zt) that's synched with the HD's noise!  The speakers also click when I'm typing and they hum when I move the mouse.  Weird though, the hum is different according to what I'm pointing at.

I can adjust the volume though, when I mute it, there's no fuzz.  But that also means no music. :(

Oh, and what are IRQ's? ^^;

---

### Post by greghill on 2006-06-11
OK Guys... I fixed it!!
This is what I found.
I did the upgrade from Breezy using the "upgrade" and not the CD. NO Sound!
No sound card detected. Nothing using sound worked. Looked in the system configuration files and no sound card was detected. Strange, because everything worked great in Breezy. After spending all day upgrading, I wasn't about to give up.
I finally traced it down to the kernel version. When I rebooted, (dual booting with SuSE 9.3), the menu was STILL SHOWING THE OLD KERNEL VERSION! From what I'd read on these forums, I remembered something about the old kernel couldn't recognize or use some of the new features in Dapper.
Using Synaptic I re-installed the new kernel for Dapper. Because the bootloader was installed using SuSE, I booted into suse and reconfigured the bootloader to rescan the OSs installed, changed the kernel boot option for Dapper to the new kernel, and rebooted into Dapper. The new kernel version found my sound card and that was it. VIOLA! EVERYTHING NOW WORKS!!! Sound for everything. I hope this works for you all. Let me know. I'm happy.
By the way, just in case it helps to know, I'm running PC with x386, AMD Duron 1.2 GHz, ATI Sound card, with GForce4400 Video card, dual hard drives (Maxtor 38 GB, and Western Digital 80GB) dual boot with SuSE 9.3 on hdb and Dapper on hda.

---

### Post by sparX CG on 2006-06-11
I thought this thread was about my problem... ;)

Just kidding, you can post yours too... :)

So nobody knows how to fix my buzzing?

---

### Post by ktulu1115 on 2006-06-12
Hmm...  that is *very* strange.  Perhaps you need to pass special module options to the module for IO parameters, IRQ settings, etc...  that's really about the only thing I can think of.  Maybe try upgrading to a newer kernel through Synatpic and see if that changes anything.

And for your other question...

IRQ's are also known as interrupt requests.  The x86 processor series are interrupt driven, which basically means the CPU keeps chugging away at a process, and when an 'event' happens that the computer needs to know about - the CPU is "interrupted" (through special hardware channels), and execution of the current process is paused, and the CPU starts running special interrupt handler code which handles the interrupt.  Once this is finished, it will return back to the original process and continue executing.  On modern CPUs, this happens so fast the user is completely unaware of the context switch (as it's called) - many many thousands of these happen a second.

Most hardware devices inside the computer have their own IRQ channel to use - devices like the keyboard, hard drive, timer, etc all have their own - ie: the letter 'a' was pressed by the user, a read request for a sector of data on the drive is finished, data is incoming on the first serial port - these are all examples of something that would trigger an interrupt.

They were created to solve the problem of "polling" - instead of the computer constantly asking a hardware device if the data is ready (which just wastes lots of computing time), the CPU will just continue running and instead the device will tell the computer when data is available though an interrupt and action nees to be taken.

Hope that answers your question - tried to keep it simple, but it's not the easiest of things to explain.

---

### Post by sparX CG on 2006-06-12
My kernel's already the newest...  And I have no idea how to "pass special module options to the module for IO parameters, IRQ settings, etc..."

Please explain? :)

---

### Post by ktulu1115 on 2006-06-14
[QUOTE=sparX CG]My kernel's already the newest...  And I have no idea how to "pass special module options to the module for IO parameters, IRQ settings, etc..."

Please explain? :)[/QUOTE]
It's not so much needed with recent hardware, but on older systems (pre-PNP), sometimes the kernel had difficulty detecting certain hardware - trying to automatically probe would crash the system, cause it to become unstable, etc... 

Sometimes it was able to be resolved by directly telling the kernel what hardware settings to use for the device (by passing specific module options to the driver)...   but this is pretty much a last resort.  Unless it's a known issue with that sound card, I doubt it'd make much difference.

I did a quick search though - and found this page: [http://www.linuxquestions.org/questions/showthread.php?t=234814](http://www.linuxquestions.org/questions/showthread.php?t=234814)
A user was having difficulty with his ESS sound card - I think the chip might be similar to the one in your system.  For him, a "modprobe sb esstype=1869 io=0x220 irq=5 dma=1" fixed the problem - trying doing the same just change the command to "esstype=1888" (if that's the model of your sound card).

If that doesn't work, I'd go out and pick up a cheap ISA (if you can find one), or PCI sound card and just throw that in the system & disable the onboard sound in the BIOS.  Low-end sound cards are relatively inexpensive and should hopefully resolve your issues.

---

### Post by sparX CG on 2006-06-16
Actually, there's no way to disable anything in the BIOS.  Can't even change boot order, nor anything else.

I'll try your suggestion though, thanks!

Not working, device 'sb' not found...

---

