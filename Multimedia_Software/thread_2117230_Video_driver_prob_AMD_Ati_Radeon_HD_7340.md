---
title: "Video driver prob: AMD Ati Radeon HD 7340"
date: 2013-02-17
forum: Multimedia Software
---

### Post by wisecat on 2013-02-17
Hi all--

I've been reading forum posts, wikis, how-to's, help files, and everything I can find on this subject, but I cannot seem to get a good video driver working on my system!  AAAAAAAAAHHH!  I'm about ready to pull my hair out.  Been working on this for days and days.

I have an AMD Radeon HD 7340 video 'card' (part of the cpu, an AMD E2-1800 APU with Radeon(tm) HD Graphics × 2 ).  16GB system RAM, so no problem using some of it for the video.

Problem: Ubuntu (12.10 amd64) always falls back to the VESA: HONDO setting, no matter what I install, and (almost) no matter what I set the xorg.conf file to use.

I've tried these:

setting in Xorg.conf :::::::::  Result in 'System Settings-->Details'
---------------------------------------------------------------------------------------------------
  (no xorg.conf)-------------->graphics listed as 'unknown', experience: fallback  (though it will say 'standard' the first time I boot up)
        ati                                   ------------------------------->VESA: HONDO, fallback mode
        ati  (2nd try)------------------->Gallium 0.4 on AMD Palm, fallback mode
        fglrx                              ---------------------------->VESA: HONDO, fallback mode
        radeon                          ------------------------->VESA: HONDO, fallback mode
        fbdev                            -------------------------->Gallium 0.4 on llvmpipe (LLVM 0x301)

I have tried installing drivers from the AMD site, from Ubuntu repository, from Ubuntu-X Team (**ppa:ubuntu-x-swat/x-updates) **but nothing seems to work, and SOMEtimes it even hangs the system on reboot (one time I had to use the LiveCD to edit my xorg.conf file back to its original setting).

I'm not a linux expert, but have gained some competency over the past year.  but SHEESH this is a tough problem to solve!  HELP!!

---

### Post by wisecat on 2013-02-18
trying to delete this message. Where is the delete button?

---

### Post by coffeecat on 2013-02-19
@wisecat, I have moved the post you made to someone else's thread into your own thread. Please don't cross post.

By the way, that is not the output of "sudo lshw -s video" but just the initial message echoed to the terminal. Repeat the command and wait a few seconds for the actual output.

---

### Post by wisecat on 2013-02-19
> **coffeecat said:**
> @wisecat, I have moved the post you made to someone else's thread into your own thread. Please don't cross post.

By the way, that is not the output of "sudo lshw -s video" but just the initial message echoed to the terminal. Repeat the command and wait a few seconds for the actual output.
Wait, why did you move it?  That 'reply' to his post was intended to help him, by illustrating that its quite difficult to get the Radeon drivers working.  And to show him what I've tried already, so that he can replicate it on his own system (possibly, hopefully, with different results) or chase down a different solution.  It doesn't make sense to move this message here?!?!

---

### Post by wisecat on 2013-02-19
okay, now output of: sudo lshw -c video

is:
  *-display               
       description: VGA compatible controller
       product: Advanced Micro Devices [AMD] nee ATI
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:47 memory:e0000000-efffffff ioport:4000(size=256) memory:f0300000-f033ffff

---

### Post by kholburn on 2013-02-22
You might need to install the proprietary drivers unfortunately.  How to do it is here:
[http://askubuntu.com/questions/25321/how-do-i-install-drivers-for-an-amd-radeon-hd-6450](http://askubuntu.com/questions/25321/how-do-i-install-drivers-for-an-amd-radeon-hd-6450)

If you go down this path you have to reinstall each time you have a kernel upgrade.  I have had to do this before and it is a right pain.

---

### Post by wisecat on 2013-03-02
OK I tried the stable release of AMD Catalyst proprietary drivers, but they did not work.

I just tried the BRAND NEW beta driver, released on Feb 27, 2013 (3 days ago), and after following the instructions on the 'Unofficial AMD Wiki'  ( [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide) ) it seems like it installed correctly.....sort of.

The graphics driver is listed as "AMD Radeon HD 7340 Graphics" (for the first time!  yay!) but experience is still listed as "Fallback".

Results of "gtkperf" list a new faster total time, 11.19 seconds (previously was 15 seconds, using the gallium 0.4 drivers in fallback mode)

One crappy problem: in the lower right-hand corner, there is a large "AMD TESTING USE ONLY" placard overlayed on top of everything.  Sheesh.  Guess that's what I get for using a beta.

I can't help but wonder, though, if its really working, since it still says "fallback"

Ideas? Thoughts?

Specs:
OS: Ubuntu 12.10 Quantal Quetzal
RAM: 15.3 GiB
Processor: AMD E2-1800 APU with Radeon(tm) HD Graphics × 2
Grahpics: AMD Radeon HD 7340 graphics (integrated with processor)

---

### Post by wisecat on 2013-03-26
OK I just upgraded to the 'new' beta driver, that AMD released on 3/22/2013, and I don't notice much difference.  

-results of ''gtkperf" are 11.58 seconds (slighly worse than 11.19 seconds with previous beta driver version; could be due to other factors)
-driver still listed as AMD Radeon HD 7340 Graphics, experience "fallback"
-still have the 'AMD Testing use only' square in the lower-right corner (but this is to be expected, when using the beta driver)

---

### Post by wisecat on 2013-04-29
upgraded to new released driver (April 25, 2013). The "AMD Testing Only" square is gone from the lower-right hand corner (thank the gods!), but other than that I notice no difference. No performance increase noticeable. Still listed as in 'fallback' mode.  (yes, I un-installed the previous drivers first before installing the new one).

I was about to run sudo lshw -c video   to get a solid answers, and grkperf to get a solid performance number, but then the auto-upgrade was running, and during the computer restart, it NEVER came back.  That's right, the damn upgrade BROKE my install of Ubuntu 12.10 !!!  It was upgrading core pieces, so I think that it may have tripped up during that, or perhaps these new core pieces were incompatible with the new video driver!?!?!?  I don't know. But I have not been able to recover  that install on that partition.  Ran Ubuntu from a different partition, then upgraded to the new Ubuntu 13.04

---

### Post by wisecat on 2013-04-29
OK so now, with Ubuntu 13.04, it installs the default video driver as:
Driver: Gallium 0.4 on AMD PALM
Experience: Standard



results of:  sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: Wrestler [Radeon HD 7340]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:45 memory:e0000000-efffffff ioport:4000(size=256) memory:f0300000-f033ffff


and gtkperf gives a total time of 14.77 seconds.  Worse than before.  But I will try with the new catalyst driver, next.

--- 
UPDATE:
and a few days later, it changes to Experience: fallback.

argh. well, now to try the AMD Catalyst driver 13.4 (released on April 24, 2013)

---

### Post by wisecat on 2013-05-01
Now I am trying AMD Catalyst driver 13.4 (released on April 24, 2013) with Ubuntu 13.04

the system settings/details states:
Driver: AMD Radeon HD 7340 Graphics
Experience: fallback

gtkperf  ... RESULTS
total time: 10.12 seconds (a new record! i guess there is SOME improvement then!)

sudo lshw -c video  ... RESULTS
 *-display               
       description: VGA compatible controller
       product: Wrestler [Radeon HD 7340]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:47 memory:e0000000-efffffff ioport:4000(size=256) memory:f0300000-f033ffff



so looks like AMD still hasn't gotten it QUITE right.  <le sigh> :(

---

### Post by wisecat on 2013-05-06
tried a DIFFERENT install procedure this time, with Ubuntu 13.04, and it WORKED
(note: Ubuntu 13.04 is not actually supported by this latest version of the AMD Catlyst driver 13.4, only Ubuntu 12.10 is, but it seem to be working.
 note: my video card, AMD RadeonHD 7340 mobility, is ALSO not actually supported by this AMD Catalyst Driver 13.4. But I'm having a tough time telling whether my card is the 7340 mobiility or the regular. It claims to be the regular HD7340, but its in a laptop, so I can assume that its the moblity version, and that the laptop manufacturer didn't quite et all the details right in their documentation)

So, following the instuctions here: [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide)
yields a succesful install!  The main difference being (I think) that the headers were installed FIRST before anything else.

However, performance is not quite what I would expect. At least, though, I can get Google Sketchup under WINE to work properly (and no other video driver choice was able to make THAT work)

results of: lshw -c video
 *-display               
       description: VGA compatible controller
       product: Wrestler [Radeon HD 7340]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:47 memory:e0000000-efffffff ioport:4000(size=256) memory:f0300000-f033ffff


results of gtkperf  17.59 seconds...the worst yet!  argh!

system settings->details->graphics lists it as:
      Driver   AMD Radeon HD 7340 Graphics
Experience   Standard

---

