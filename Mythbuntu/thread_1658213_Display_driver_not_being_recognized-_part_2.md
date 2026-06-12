---
title: "Display driver not being recognized?- part 2"
date: 2011-01-02
forum: Mythbuntu
---

### Post by torpare on 2011-01-02
Further to my post 1 hour ago, the problem is worse than reported, and can't be traceable (as I supposed) to the antiquated graphics on my Shuttle computer.

Having now experimented further, I've found that the Mythbuntu CD won't display on my main desktop PC either - using the same monitor (via a KVM switch).  This has a far more sophisticated spec, including Asus EN210 PCI-E graphics card with 1024 MB of DDR2 memory.

Unlike the Shuttle, the Mythbuntu progress screen displays without a flicker whilst the files are loaded from the CD but when the Mythbuntu splash-screen should appear all I get is a pattern covering the entire screen which looks like a linen table-cloth!

Any help would be much appreciated.

---

### Post by BicyclerBoy on 2011-01-02
The KVM switch can interfere with EDID probing & basic connectivity detection...

The video card boot initialisation code performs some of this stuff so the BIOS POST screen is possible.

I would remove the KVM switch to begin with.

Note the GT210 is not recommended for optimal hardware accelerated video HD playback.
 
What is the monitor ?

---

### Post by torpare on 2011-01-03
@BicyclerBoy
Thanks for the reply.> What is the monitor ?LG Flatron L194WT
> The KVM switch can interfere with EDID probing & basic connectivity detection...

The video card boot initialisation code performs some of this stuff so the BIOS POST screen is possible.

I would remove the KVM switch to begin with.
I did as you suggested but its removal made no difference whatsoever from the behaviour I previously reported (did you see my first post BTW?).  
> Note the GT210 is not recommended for optimal hardware accelerated video HD playback.OK, but is this relevant?  We're only talking here about basic video playback, of text to boot.  (Currently I have no plans to play back HD video on my setup).

I would've expected the Live CD to function flawlessly "out of the box" with any NVidia card and a current driver.  (The md5sum matched, BTW).  But not only does it fail to do so with my antiquated MX Integrated GPU on the Shuttle motherboard but also with my bang-up-to-date GeForce 210 GPU.

Since this is paired with an AsRock motherboard with Via chipset I tried typing "pci-noacpi" into the command-line as suggested in 'Help'.  That didn't make any difference either.

So I'm making no progress at all so far, which is intensely frustrating since I can't see any obvious reason for this.

---

### Post by BicyclerBoy on 2011-01-03
So the monitor is a ordinary PC DFP LCD.
I read the OP to this thread, I was unsure if KVM switch was involved in both setups.

MythTV means HD playback to me sorry.

You may need later nvidia driver (outside of default packages).
Maybe its desktop effects ?
 
I would recommend nvidia 260.19.29 for the GT210 box.
You will need kernel headers as appropriate.
You can find this in 3rd ppa using dkms (so really easy to install).

Have you used mythbuntu before ?
Have you configured the frontend playback options ? vdpau profiles filters deinterlacers etc ?

Note: The MX440 ? is not supported in the later drivers.
Note the GT210 is not bang up to date & it's an orphan/lemon/runt..sorry.

---

### Post by torpare on 2011-01-04
> **BicyclerBoy said:**
> I would recommend nvidia 260.19.29 for the GT210 box.
You will need kernel headers as appropriate.
You can find this in 3rd ppa using dkms (so really easy to install).Noted, thanks.  But my problem ATM still is that I don't get any Mythbuntu GUI to display, and therefore can't progress to the stage of installing Mythbuntu.  Without installing it I can't install any other driver.  For the same reason, I can't configure anything.

I seem to be caught in an endless loop :(  Or have I missed something?

> Have you used mythbuntu before ?No.  I made an (abortive) attempt to install MythTV, running Mepis, and gave up in despair.  I intended to make a fresh start this time around, running Mythbuntu.  The rest you know...

---

### Post by torpare on 2011-01-04
One piece of additional information, in case it sheds any light.

I installed my pensioned-off Asus V9520 graphics card into the Shuttle.  This card has the GeForce FX 5200 GPU.  With this the Mythbuntu LiveCD produced an immaculate display on the frontend.

Can't do anything with it of course with no working backend.  Still...

Evidently the ver. 10.10 CD comes with the right driver for this (now pretty obsolescent) GPU, but not for the much more recent 210.  Odd.

---

### Post by BicyclerBoy on 2011-01-04
If the GUI does not come up then the X server has not loaded.

Ubuntu has usually been able to load a usable/limited GUI on my computers when there is no nvidia driver.

You can still login & check the xorg log files:  /var/log/Xorg.0.log for errors/clues.

Could be nouveaux driver blocking the nvidia driver from loading.
Could be nvidia driver is to old (you have discovered this).

With any computer...
Download the nvidia driver (260) from their website & stick in a storage location you can find from terminal login & follow the install instructions..
The install instructions indicate any build requirements..
You will need the kernel headers that match your machine, to reveal kernel: 
uname -r      
Install from cmd-line or synaptic on target PC...
linux-headers-2.6.32.something

You have to to install the nvidia supplied driver with the X server not running.
There are alternatives if you can find a 3rd party ppa pre-compiled binary with dkms.

You could do all of this with any working video card. The install script is all text mode output. 
Replace the video card after install is completed & reboot or restart X server..

---

### Post by torpare on 2011-01-06
@BicyclerBoy

Hi.

I'm very appreciative of the help you've already given.  The problem we're (both!) up against is the abysmal level of my skills when it comes to running any application using Linux - especially when it involves using a CLI.  I'm sorry about this and it isn't for want of trying, but somehow Linux and I just don't get on well together.  As a consequence, after each attempt I make to use Linux I tend to get discouraged and give up, as a result of which if/when I try again I find I've forgotten even the rudiments in the meantime.

I mention this only so you'll understand why I'm making such heavy weather of what must seem to you incredibly simple.

I recall going through this same X-window problem once before, after I installed Mepis, and on that occasion I managed to solve it - so it ought not to be beyond me, but I think it's going to take me a bit more time.  

Please bear with me.  I fully expect to be getting back to you :p

---

### Post by BicyclerBoy on 2011-01-06
Step by step..

An easier nvidia driver source is
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

You still need the kernel headers package..

Troubleshooting
[http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/README/commonproblems.html](http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/README/commonproblems.html)

The entire nvidia driver doc is very good reading...it has a linux beginner section too.

---

### Post by torpare on 2011-01-08
@BicyclerBoy

The first thing to say is that (having put my retired graphics card back into my desktop PC - just so as to be able to run Mythbuntu on it, no other reason - has enabled me to run Mythbuntu on it.  So, in principle, I now have a working backend machine, albeit with an obsolescent graphics card.

As frontend I've been forced to abandon the Shuttle completely because I was getting nowhere trying to use it.  So the whole basis on which I had planned to run a trial setup has now gone by the board.  Ah well...

Instead as frontend I'm now trying to use the LiveCD running on my HTPC (in another room - highly inconvenient).  Its integrated GPU is recognised by Mythbuntu.

So the subject of this thread has been taken as far as it can be, I think.  The outcome is anything but satisfactory so far as I'm concerned (given the original aim), and why Mythbuntu has been unable to handle either my GeForce 210 or my GeForce2 MX Integrated GPU still remains completely unclear to me, I'm afraid.  But there it is.  I'm most grateful for your patience.

I shall now have to start a new thread, because I can find no way to get the backend set up, or the frontend to talk to it.  (This Mythbuntu experience has been anything but a happy one for me so far!).

---

### Post by newlinux on 2011-01-08
seems strange as I have a g210 which had no problems (on Lucid using nvidia 260.19.29 driver). and I had a Geforce 440MX that had no problem (using legacy driver). I don't use the liveCD, these are installs, however. Is it your intention to always use a liveCD or to eventually install? I can't see any reason you wouldn't be able to get this to work but it may require you to use the commandline.

I also don't use mythbuntu proper, but rather ubuntu and then install mythtv, but for an install that shouldn't make much difference. Not sure about the LiveCD.


you may also try asking this question in the main forum, since I think this is more of a driver install issue generic than it is a specific mythbuntu issue. You might get more help there.

---

### Post by torpare on 2011-01-10
> **newlinux said:**
> seems strange as I have a g210 which had no problems (on Lucid using nvidia 260.19.29 driver). and I had a Geforce 440MX that had no problem (using legacy driver)... I can't see any reason you wouldn't be able to get this to work but it may require you to use the commandline.

...

you may also try asking this question in the main forum, since I think this is more of a driver install issue generic than it is a specific mythbuntu issue. You might get more help there.Hi newlinux

Thanks for the helpful comments.

Like you I can see no reason for why I had problems with my 210 graphics card installed.  If I can once get Mythbuntu up and running (having reverted to my earlier graphics card meanwhile) I'll probably pursue this issue further, because I'm not happy being forced by Mythbuntu to use an obsolescent card I already retired, in my workstation PC.  It's a very unsatisfactory "solution".

As to the MX440 you mention, I also have one of these as it happens (on a Chaintech card) and I did try it out in my Shuttle SN41G2 (frontend) machine, hoping the LiveCD would recognise it.  I got very inconsistent results: once, the X-server did kick in but I was never able to repeat that success.  After that, I gave up trying to use the Shuttle.  I'm not satisfied with that outcome either, and may pursue it further at some stage.> I don't use the liveCD, these are installs, however. Is it your intention to always use a liveCD or to eventually install?To install, IF I can once establish that I'm able to run Mythbuntu in a way satisfactory to me.

So far, the experiment hasn't exactly boded well :(

---

