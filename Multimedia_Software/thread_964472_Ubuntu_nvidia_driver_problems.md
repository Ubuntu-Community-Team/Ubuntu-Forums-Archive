---
title: "Ubuntu nvidia driver problems"
date: 2008-10-30
forum: Multimedia Software
---

### Post by jcapinc on 2008-10-30
At first install X does not even load.  it gives the the option of "reconfigureing" or running in low graphics mode, to which I choose reconfigureing.  From here I "reset to generic video mode" and then it starts to work!  so great!

But problem :: I want to run dual screen and i've got an nvidia card.

Ok, no worries so how do I get the nvidia driver to work?  Right!  the driver manager!  ok, this should be no sweat, it worked great in 8.04, so this should be no problem.

and I load up the driver manager, I see two possible drivers, 176(3?) and 177, and 177 is recomended.  so I say great! and click 177 and click activate and...

this loading screen flashes, glitches, then dies, and my driver manager is staring back at me like a limp noodle shrugging and saying IDK?

So I get frustrated and click it twenty times to the same flash, glitch, and IDK, then I hit google.

I find a bug report on Launchpad that speaks to this exact same problem and I say great!  Im saved!  this will tell me how to fix it.  wrong.  It was geared toward those more technical and excluded a spacific solution.

But it mentioned missing linux headers, and that the driver manager did not resolve dependancies it should have, to which i had an idea of uninstalling the driver from synaptic and re-installing it, to which APT would be intelligent enough to plug in the right drivers.

So I say great!  This might fix it!  I go to synaptic, and uninstall the 177 package and it says I gotta get ridda this one too and I say fine!  and it uninstalls... only the other one?  the other one is now uninstalled, its nvidia-common, and it decided it was not worth living anymore and kicked teh bucket (lolrus says "bucket!!!??? where!").

I try to install nvidia-common back and I say noes!  I needses that!  and synaptic says noes! you donts!  Synaptic tells me its not available right now its seeing someone else.

I tried to go back and re-install to tell you great guys the error message, and it gives me no error, instead I re-install nvidia graphics and all the modules that are giving me a headache right now.

But this puts me back at square one, because I have the same two cross-eyed retarded looking nvidia drivers staring at me like idiots saying IDK?  in other words, the drivers will not activate?

Methinks it has something to do with linux-headers-common (whatever that is?) like the guy at launchpad says, but I havent a clue what I am doing in that arena?

halp me!  why dids the precious (ubuntu) regress in its driver-coolness... why! smeagle asks yous!

eh-hem... any help hear would be much appreciated :lolflag::)

---

### Post by Laibcoms on 2008-10-31
I am not sure if this will work, but I had a problem like yours that 177 won't activate.

So I did:
1) Open Synaptic Package Manager
2) Search nvidia
3) Installed all the 177 that are not yet installed (except those with the -dev suffix)
4) Made sure nvidia-settins is installed as well
5) Restarted
6) Went to "Hardware Drivers"
7) Activated 177
8) Voila

Hope that helps.

---

### Post by tuxxy on 2008-10-31
177 and also 173 drivers both work fine on Intrepid

---

### Post by WelterPelter on 2008-10-31
> **tuxxy said:**
> 177 and also 173 drivers both work fine on Intrepid

Not for me. Neither 177 nore 173. So far when I enable either of them, it boots to a black screen.

---

### Post by Cobbs on 2008-10-31
would there be a way to do all of this through the command line?

---

### Post by bj0 on 2008-10-31
> **Cobbs said:**
> would there be a way to do all of this through the command line?

You can do it using aptitude (or apt-get) through the command line.
```

aptitude search nvidia
aptitude install nvidia-settings nvidia-... etc etc

```

---

### Post by bj0 on 2008-10-31
> **Laibcoms said:**
> I am not sure if this will work, but I had a problem like yours that 177 won't activate.

So I did:
1) Open Synaptic Package Manager
2) Search nvidia
3) Installed all the 177 that are not yet installed (except those with the -dev suffix)
4) Made sure nvidia-settins is installed as well
5) Restarted
6) Went to "Hardware Drivers"
7) Activated 177
8) Voila

Hope that helps.

Ok I spoke too soon, it seemed to work until I restarted and the problem persist.

I'm also getting the error about not having kernel headers.  I have 2.6.24-19-generic, but I don't see headers for it...

---

### Post by bj0 on 2008-10-31
Ok I fixed this by upgrading to the 2.6.27 kernel, which is what Ibex uses.  My upgrade failed to upgrade the kernel for some reason, and the nvidia drivers didn't like the old one.

---

### Post by chsub on 2008-10-31
> **bj0 said:**
> Ok I fixed this by upgrading to the 2.6.27 kernel, which is what Ibex uses.  My upgrade failed to upgrade the kernel for some reason, and the nvidia drivers didn't like the old one.

How do you update the kernel?

---

### Post by skankster on 2008-10-31
I'm getting the same issue (it seems quite common based on the number of threads), but I'm using the Intrepid kernel and I've tried all the above suggestions.

It seems this issue may be common but there are a number of potential fixes (not found mine yet). I looked for the Launchpad bug but couldn't find it, can someone post the number so I can have a look at it, please?

---

### Post by skankster on 2008-10-31
> **skankster said:**
> I'm getting the same issue (it seems quite common based on the number of threads), but I'm using the Intrepid kernel and I've tried all the above suggestions.

It seems this issue may be common but there are a number of potential fixes (not found mine yet). I looked for the Launchpad bug but couldn't find it, can someone post the number so I can have a look at it, please?

Found it: [https://bugs.launchpad.net/ferchohacker/+bug/283329](https://bugs.launchpad.net/ferchohacker/+bug/283329)
Will take a look at it soon, when I get the chance.

---

### Post by skankster on 2008-10-31
Okay, that bug report helped me to fix my issue. Here's what I did, using Synaptic, so no command line needed.

Firstly, I checked what kernel I was using - this can be done through the command line, but I just made a note from the boot menu. My kernel is 2.6.27-7-generic.

After booting I opened Synaptic and searched on "headers" (searching on 2.6.27-7 may also work). This showed me that the 2.6.27-7-generic headers were not installed (the 2.6.27-7 headers were, but not the "generic" ones). I installed the generic headers, and nvidia-kernel-common which also wasn't installed. This latter may not be needed, but I went with it as it looked important ;)

After that, I found that going to Hardware Drivers and enabling 177 now worked (reboot required), and hey presto, I now have a working system again.

Hope this helps.

---

### Post by jcapinc on 2008-10-31
IDK what happened but thank you all for your responses and concern.  For some reason it just started working!  maybe the re-install did it? :\  in any case it works now... but now I have a new issue!  nvidia-settings crashes before it is able to save settings!  should i start a new thread on this?

---

### Post by soho2014 on 2008-11-09
My Nvidia driver 177 works OK with Ubuntu 8.10, except that it breaks the fast-user-switch-applet, and you can't quickly change to another user.

---

### Post by SavageFreedom on 2008-11-23
[EDIT (solved my own problem): After a clean-install, running a full software update (89 files worth) and rebooting enabled the nvidia 177 driver activation. Not sure why, but it worked. When I booted up it went straight to the command line, startx revealed "no screens." I simply ran

dmesg | grep nvidia

found the PCI settings for my two cards, edited xorg.conf and added the BusID to the device section, and up it came. Hooray!]

I just did a clean (non-upgrade) install of Ubuntu 8.10, my Kernel is the Ibex kernel, all headers and all nvidia items in Synaptic are installed. When I go activate the nvidia 177 drivers, it asks for my password, I click okay, it flashes "0%" on the progress bar and then it disappears. No reboot, nothing. When I check again, it still shows both nvidia drivers as deactivated.

Any ideas?

---

### Post by tfmorris on 2009-04-18
> **skankster said:**
> Okay, that bug report helped me to fix my issue.
...
After booting I opened Synaptic and searched on "headers" (searching on 2.6.27-7 may also work). This showed me that the 2.6.27-7-generic headers were not installed (the 2.6.27-7 headers were, but not the "generic" ones). I installed the generic headers, and nvidia-kernel-common which also wasn't installed. This latter may not be needed, but I went with it as it looked important ;)

After that, I found that going to Hardware Drivers and enabling 177 now worked (reboot required), and hey presto, I now have a working system again.

A recent upgrade broke my installation and this tip helped me fix it.  Apparently the kernel headers are required, but not included correctly in the dependencies and attempts to activate the NVIDIA Accelerated Graphics Driver (version 180) will silently fail without any error message if they're missing.

In my case I had linux-headers-2.6.24-16 installed, but not linux-headers-generic, so when the kernel got upgraded I didn't automatically get the required linux-headers-2.6.27-11-generic.  Installing linux-headers-generic pulled in the necessary dependencies and fixed the problem.

I wasted over an hour on a problem that a simple error message could have identified in a few minutes.  Why don't failed attempts to activate a restricted drive provide an error message ?!?!

Tom

---

### Post by jearod on 2009-06-19
> **skankster said:**
> Okay, that bug report helped me to fix my issue. Here's what I did, using Synaptic, so no command line needed.

Firstly, I checked what kernel I was using - this can be done through the command line, but I just made a note from the boot menu. My kernel is 2.6.27-7-generic.

After booting I opened Synaptic and searched on "headers" (searching on 2.6.27-7 may also work). This showed me that the 2.6.27-7-generic headers were not installed (the 2.6.27-7 headers were, but not the "generic" ones). I installed the generic headers, and nvidia-kernel-common which also wasn't installed. This latter may not be needed, but I went with it as it looked important ;)

After that, I found that going to Hardware Drivers and enabling 177 now worked (reboot required), and hey presto, I now have a working system again.

Hope this helps.

Skankster, you're a genius. I had the same problems (although I'm running the server kernel) but I had the generic installed but not the actual server headers. Installing the server headers worked like a charm.

Being fairly new to linux, what exactly do the kernel headers do (for future reference)?

---

