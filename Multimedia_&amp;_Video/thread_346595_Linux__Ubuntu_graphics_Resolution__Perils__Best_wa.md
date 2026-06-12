---
title: "Linux / Ubuntu graphics: Resolution?  Perils?  Best way to proceed?"
date: 2007-01-25
forum: Multimedia &amp; Video
---

### Post by Phrawm48 on 2007-01-25
I'm a nervous newbie with 2.6.15-27-386, Ubuntu 6.06 / Kubunto 3.5 up and running.

Device Manager correctly identifies that my system hardware includes an Nvidia FX 5500 (NV34) graphics adaptor; Device Manager also states "OEM Product: Unknown (0x911a)".

Under Windows, I can run at 1280x1024; under Linux / Ubuntu / Kubunto the maximum resolution is 1024x768.  Like many users, I'd like to locate and install the proper driver for the graphics adaptor so I can enjoy higher screen resolution.

But I don't want to undertake this if all I end up doing is breaking my working installation.  So, is there a "best" online resource that explains -- in more or less step-by-step fashion --  how to (a) get the correct driver, (b) install the driver, and (c) configure my system to use the driver?

I don't mind reading the manual, but in trying to research this issue I've found multiple, sometimes contradictory discussions of how best to proceed.  Indeed, some of the "answers" I've found raise as many if not more questions than they answer...

If the new config doesn't work can the changes be readily undone?  Or would using Norton Ghost (or better yet, is there an open source alternative to Ghost?) to completely back up my current Linux partitions before beginning be necessary?

Sorry if this I've asked TOO BIG a Q=question, but I can't seem to clearly identify exactly how to install and configure my Linux system with the proper driver for my graphics hardware...

Cheers & thanks,
Ric
SFO

---

### Post by Patrick K on 2007-01-25
Have you read this.
[http://www.ubuntuforums.org/showthread.php?t=301499](http://www.ubuntuforums.org/showthread.php?t=301499)
I used his script for a painless install.

---

### Post by Phrawm48 on 2007-01-26
On Thursday 25 January, 2007 I downloaded the script "envy_0.8.1-0ubuntu3_all.deb", followed the instructions for running it outside of the Desktop Environment, and received the following error:

------ Begin error message ------

ric@ric-desktop:~/Program_Files/Envy$ ./envy_0.8.1-0ubuntu3_all.deb
./envy_0.8.1-0ubuntu3_all.deb: line 1: syntax error near unexpected token `newline'
./envy_0.8.1-0ubuntu3_all.deb: line 1: `!<arch>'

------ End error message ------

I'll pass this info on to the author.  In the meantime, I'm I'm going to explore the other methods.  If I decide I can get through these without breaking something the script problem may become irrelevant, at least temporarily...

Cheers & thanks,
Ric
SFO

---

### Post by Patrick K on 2007-01-26
I think the script is for Edgy. You might need to manually install msince you have Dapper. The manual directions in the link should work.

Actually, the first time I ran the script I had an error and had to edit the xorg.conf file back to "nv". The second time it work fine. I elected to edit the xorg file manually to "nvidia". I don't know that that had any effect but it ran fine after a reboot.

---

### Post by Phrawm48 on 2007-01-26
Unfortunately I can't make sense of the procedure for manual installation.  I want to configure my graphics card but the discussion begins with "installing restricted modules for your kernel".

I also can't even identify which four-digit driver number is the correct one for my GeForce FX 5500.

Finally, all the "if things go wrong" caveats in both the instructions and all the other related threads on this forum are overwhelming.  It's just too darn much for me to try and do at this point.

Lamentably, this is a classic illustration of why many would-be users give up on Linux.  It's just so hard to get a system properly configured, particulary when configuration requires the editing of multiple, disparate -- and essentially cryptic -- text files, each with a slightly different syntax...

Sincere thanks for your attempts to help but I'm abandoning this challenge for the time being.  Perhaps after I've acquired a few more months (years?) of Linux experience I'll be ready to undertake getting my graphics adaptor properly configured.  Sigh...

Ric
SFO

---

### Post by crumbum on 2007-01-27
I just added 1280x1024 to my xconfig and restarted works fine [IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=23966&stc=1&d=1169879220[/IMG]

---

### Post by Phrawm48 on 2007-01-27
Thanks, but the higher resolution isn't available via the GUI.

My assumption (uh oh, there's that word again) is that I need to get the correct driver to support higher resolution.

I've actually found a Linux program from the NVIDIA site which claims to provide a means of upgrading my driver without all the pain.  My first step before trying it was to Ghost my complete multi-partition drive, which then broke grub, so now I have to fix that before I can proceeed.

To be continued, one way or another...

Cheers & thanks,
Ric
SFO

---

### Post by Phrawm48 on 2007-01-29
Okay!  I now have *beautiful* 1280x1024 graphics resolution for Gnome / KDE!  The following is for other newbies confronted with the same challenge.

_What I did_:

I first downloaded and installed the Envy utility: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Note that, per that page, a single version of Envy now evidently supports both the Dapper (6.01) and newer Edgy versions of Ubuntu.  I _strongly_ recommend using this tool if at all possible.

I had a brief bit of confusion when I tried to run the Envy installation package directly.  Nah, ya' gotta' install it first: **sudo dpkg -i envy_0.8.1-0ubuntu3_all.deb**

After I got Envy installed (I used "whereis envy" to verify that I had done so), I used CTRL+ALT+F1 to go from Gnome into TTY (a.k.a. "console") mode, and had my first try at running Envy. 

Envy attempts to download and install a driver for one's graphics adaptor that's also compatible with one's Linux kernel version.  Because a  binary driver for my GeForce FX 5500 didn't exist for my current Dapper kernel, Envy needed a C compiler to continue.  So I used CTRL+ALT+F7 to get back to Gnome and took a quick side trip to System > Administration > Synaptic Package Manager to install both *gcc* and *make*.

With gcc and make installed, and back in console mode, Envy this time examined my system and began downloading a bunch of updated modules as well as a significant amount of source code.  Envy then used the source code to compile a graphics driver that was compatible with my kernel!  (My, how un-Windows like...)

After Envy had completed examining, downloading, compiling, and installing everything, I re-booted my system.  The first thing I noticed was that even at my existing, lower-than-I-wanted screen resolution the GUI, especially characters (fonts), looked dramatically better.  I also took advantage of Gnome's System > Font tool to tweak some settings that further sharpened my on-screen characters.

I still didn't have increased screen resolution, though.  Despite having successfully updated my driver, System > Preferences > Screen Resolution at this point included no new, enhanced screen resolution settings.  Moreover, because I thought this meant I'd have to descend into experimentally editing my X configuration file, I grudgingly avoided going any further with this for the time being.  This turned out to be the right decision.

A day later, while poking around, I had a wonderful surprise!  I hadn't realized that updating my particular driver had also added a GUI tool under Applications > System Tools > **NVIDIA X Server Settings**.  I started it and was amazed to find that it allows me to choose and preview a long list of alternative screen resolutions.  But wait, don't answer yet -- the tool also allows  me to simply click **Save to X configuration file**  so that my lovely new settings would be used for any subsequent, new sessions.

Long story short, it took me almost three days to sort through all the different steps necessary to acquire the knowledge and tools I ultimately needed to install the right driver for my particular NVIDIA graphics adaptor.  Now that I have, though, all aspects of my Linux display compare favorably with my "other" (a.k.a. Windows 2000 Pro) partition.  (But of course, Ubuntu / Kubuntu have much nicer themes than W2K...)

Cheers, thanks to all who helped, (and hope this lengthy narrative will help other newbies understand what's involved),
Ric
SFO

---

