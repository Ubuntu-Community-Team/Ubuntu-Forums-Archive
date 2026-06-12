---
title: "Nvidia 9800 GT issue &amp; sound issue"
date: 2008-10-14
forum: Multimedia Software
---

### Post by melzanis on 2008-10-14
Okay, I'm at the end of my ropes. I can't seem to get my video card working right, and after trying to get the video card to work I lost sound.

I'm use the Nvidia GeForce 9800 GT video card. I'm not running with any sound cards just what's on-board. The motherboard is an ASUS P5KPL-CM model, it's for the intel quad-core CPU's. 

All I need to know is how do I get the drivers for my video card, and how do I get my on-board sound back?

---

### Post by tuxxy on 2008-10-14
Which drivers have you tried? that card does work see this thread

[http://ubuntuforums.org/showthread.php?t=909460](http://ubuntuforums.org/showthread.php?t=909460)

---

### Post by markbuntu on 2008-10-14
Does that card have HDMI? If so it is most likely that your default sound is being set to the HDMI on the video card. It is a vey common problem with HDMI graphics cards. You can get:

asoundconf.gtk

and use it to set the default sound card.

---

### Post by melzanis on 2008-10-14
Well I did a fresh install of Ubuntu 8.04. I truthfully don't know what drivers I need for this video card. Can someone, anyone tell me what drivers or whatever else I need to get this God-forsaken video card working

---

### Post by tuxxy on 2008-10-14
> **melzanis said:**
> Well I did a fresh install of Ubuntu 8.04. I truthfully don't know what drivers I need for this video card. Can someone, anyone tell me what drivers or whatever else I need to get this God-forsaken video card working

Did you read the post I already linked?

That tells you to try the newest driver versisons available at nvidias homepage.  Im sure theres a card selector app so you you know your getting the correct one.

Also you could try envyng-gtk application available in the repos, this should install the correct one for you, although with a card that new it may require a visit to nvidia homepage.

EDIT: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by melzanis on 2008-10-14
Okay, I have read over that information in that link you sent me tuxxy. I reinstalled with the 64bit version, updated everything that was given to me in the update manager. I also downloaded the drive (Linux x64 (AMD64/EM64T) Display Driver) it seems that I now allows me to run it. However, in the i386 version I can't. It's simply a type mismatch. 

I am now faced with another issue that I'm sure will be a simple fix. I need to change my default runlevel, however I'm not sure where the file is that will allow me to change this setting. The reason for changing the default runlevel is simple. I need my system to boot into the console first, this way if something goes south. I still have access to my system. 

once I know where the file is that allows me to change this setting, I should be able to have this drive installed in no time. So if some one is able to help me locate file, that would be great

---

### Post by melzanis on 2008-10-14
Okay, I have been reading up and I've found the file it should be...
However, I can't find /etc/inittab for the life of me. has that filename 
changed and I'm not aware of it. I guess you can say I'm in the dark.

Help please!!!!

---

### Post by melzanis on 2008-10-14
Okay so I made progress with changing my run level. I started the install process of the Nvidia driver. 
However it gave me an error saying: "Error:you do not appear to have libc header files installed on your system.
                                     Please install your distribution's libc development package"
I'm not sure which ones I have to install i've looked up "libc" about the selection is a little overwhelming. I'm
hoping that someone out their can point me in the right direction here?

---

### Post by jon_herr on 2008-10-15
Be sure you have installed the 'build-essential' package

sudo apt-get install build-essential

For what it is worth, I've tried installing these drivers in my x64 bit ubuntu, and 32 bit ubuntu (both v8.04) and can't get the drivers to work.

It's not a matter of compiling, the driver install goes fine, it's a problem with X11 itself - after reboot or starting GDM my computer freezes solid or gives up a 'segmentation fault' with the driver module.

I've installed or re-installed the driver several times - all with the same result.

My only solution for now is to use the generic 'nv' driver - which it terrible - as I use this PC to play games on, and have to keep rebooting in to windows in order to do so.  (This machine is dual booted).

Is there anyone in 'ubuntu land' that can pre-compile this newer driver?  It's been officially release for both 32 and 64 bit versions of the OS - but I can't get it to work.  Someone with more experience than me might be able to fix it.

Ubuntu is the best linux distro out there, IMHO, but this has become a weak spot since my upgrade to v8.04.

Thanks,
Jon

---

### Post by melzanis on 2008-10-15
Jon I want to thank you for your reply, you seem to be the only person in 'Ubuntu land' that seems to have some advise at precent. But I want to tank all those that have helped me up to this point so far. 

I have made some progress with install this God-Forsaken driver(which by the way isn't instane, this driver should be a lot easier to install with this Linux Distro) but right now i'm not at my house so i'm only able to give part of the information I gather after installing the drive. 

As you had pointed out Jon, the problem is not installing this driver but getting it to work right with X11 after the installation. I did install a C(programming langue) library and then dropped down to runlevel 3. The install went smoothly, however when I went to bump back into X interface it scream at me saying that there is a driver mismatch. The driver needed to be the 177..-- I don't know the rest of the module type -- this is only part of the information my computer at home gave me when trying to start X.

I had to reinstall, however I am using the amd64bit version of Ubuntu. I'm not sure if this is bad thing because i am using the Intel quadcore 2.4GHz CPU. If this is another issue please let me know.

Cheers, 
Melzanis

---

### Post by melzanis on 2008-10-15
Now the error message stated this when I went to run X:

"Error:API mismatch: the nvidia kernel module has version 169.12, but this Nvidia driver component has version 177.80. Please make sure that the kernel module and all Nvidia driver components have the same version"

it then went on to say:
"(EE)NVIDIA(0): failed to initialize the NVIDIA kernel
        "       module!Please ensure that there is a supported 
        "       NVIDIA GPU in this system, and that the NVIDIA device
        "       files have been created properly
 (EE)Screen(S) found, but non have a usable configuration
  Fatal server error:
  no screens found
  xinit: Connection reset by peer (errno 104):unable to connect to X
         server
  xinit:No such prcess(errno 3):server error "

Okay frist off what the hell does this all mean? the setup went great but starting X just wasn't going to happen after words. Second what is going on with this nvidia kernel module version 177.80 and 169.12. If my card has 169.12 then why did it use 177.80? how do I get the right version number? lastly is there anything special about this Nvidia GPU (Graphical Processing Unit)?

---

### Post by l39pilot on 2008-10-24
Hello all;
For what it's worth. I used the previous writers remarks to help me do this. I'm just getting back into Linux after an absence of some 8 years. Things have changed a great deal.... 
I had tried installing the driver for the 9800 several times, but had no luck with it. Gradually, "things" started to come back to me regarding missing kernel headers etc.
Short story is that when I tried it again this evening, it failed at first. NOT because it wouldn't compile. It went through all that OK. At one point, the installer asked me if I wanted to install the 32 bit item. Without thinking, I told it "sure." It finished up nicely. I started gdm again, and everything seemed OK. But when I went to check "resolution" it was still at the default. I then booted the machine, but nothing changed. But I was just happy it didn't screw anything else up!
A little while later, the thought occurred to me that I am a !64! bit machine! So, I ran it again, and THIS time I told the installer NO to the 32 bit bit... and once again, it ran to completion. I then fired up gdm once more and THIS time I got the monster "NVIDIA" logo immediately! I didn't even have to boot. When I check the resolution again, it had automagically selected by native screen resolution 0f 1680 x 1050.
BTW, it ALSO installed the "NVIDIA X server Settings" tool under "Applications/System Tools"
So I have to say that, after a few false starts, their 177.80 worked fine for me.
My machine is a "Thermaltake" AMD64. Uname gives:
Linux LeShittleV2 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux
If anyone would care for more detail, I'll do my best to provide it.
:):

---

