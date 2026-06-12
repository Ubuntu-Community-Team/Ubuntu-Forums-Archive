---
title: "Resolution 17-Generic Kernel"
date: 2008-05-30
forum: Multimedia Software
---

### Post by reagentz on 2008-05-30
I don't know exactly what is going on, but I messed up and installed a virus called Vista on my computer! I finally got rid of it by formatting and installing Ubuntu 8.04 x64 then i386 back on my machine.

Since this new installation I'm having the worlds worst time getting my video to work properly, when it use to be nothing to sweat setting up. When I freshly install the best resolution I get is 1024x768, I get the alert for activating the nVidia proprietary drivers reboot and all goes to hell. Best resolution at that point is 640x480 or 800x600, then I get the proprietary notice again, click the alert and nVidia is "in use." I have never, ever had this issue with Ubuntu, I'm running the exact same hardware I've ran since last summer, no changes what-so-ever.

I then decide to use the displayconfig-gtk utility, Ctrl+Alt+Backspace log back in all is great can set 1600x1200 resolution, but guess what? nVidia is not activated, check it for "in use" reboot and now I get the displayconfig-gtk coming up every time before GDM logon. Set that up yet again, get a really large logon resolution, once I login I have to set the resolution back to 1600x1200 but nVidia is not active yet again. It's like I'm caught in a perpetual loop.

Editing my xorg.conf file just hoses things worse so I've left it alone. I even downloaded nVidia's 173.x.x release for Linux, shut down to console Ctrl+Alt+F1 then sudo /etc/init.d/gdm stop, after which I install the drivers sh ./NVIDIA-Linux-173.x.x.5-pkg1.run etc. Yet I'm getting no where! After that GDE doesn't even load without going through displayconfig-gtk all over again.

I'm at a loss I can't figure it out, it doesn't seem like I had this problem with 16-generic kernel?

Can someone please help me figure this out, I will be in debt to you forever!

I won't be here for a few hours I have an appointment to attend, but when I get back in I could post my xorg.conf file and we can go from there.

Thanks in advance!


I would like to add I've tried Gentoo 2008 beta, Fedora 9, openSUSE 10.3, Kubuntu 8.04 x64, Ubuntu x64 i386 versions of 8.04, right now I'm thinking of going back to 7.10 i386. All do me the same way, I don't know if it's some new issue, I know Fedora 9 had an issue with nVidia and creating an xorg.conf but was supposed to be resolved with 173.x.x nVidia module/driver release. I would also like to add I have install Ubuntu 8.04 x64 before with no issues but it was an upgrade from 7.10 x64.

thanks again guys, this community is the best! System spec's below, but running 1x xFx 7800 GT card, I have since my first run with 8.04 amd64.

---

### Post by reagentz on 2008-05-30
Wow, been gone almost 8 hours and not one response, geez thanks guys.

I guess I'll read back through the countless posts on setting up displays in xorg.conf yet again, like I hadn't been doing that for 3 days.

---

### Post by reagentz on 2008-05-30
welp something interesting, I switched to Ubuntu 7.10 i386 and everything worked fine on my xFx 7800 GT with nVidia hardware update. I have all my resolutions and proper refresh rate freq.

Weird, huh? Now I'm thinking what is different with 8.04 and all the newer Linux Distro's that is causing me to have conflicts with nVidia and my xorg.conf file that wouldn't allow my desktop to display anything other than 640x480 and 800x600?

Still love'n Ubuntu, trying to figure stuff out and making it run smooth as silk is the fun part. Friends of mine that try Linux primarily Ubuntu always go back to Winblows because they can't get things to work right, I tell them there's a lot of reading involved when you run into an issue. They're just to lazy to read, I then tell them OS X or WinBlows is the best thing for them then. Makes me feel fine though, a majority of the people I work with come to me when we have customers running Linux. Sort of like when you call support Press 1 for English, Press 2 for Spanish, ISP's need a new option Press 3 for Linux!

---

### Post by erik.lonroth on 2008-06-04
I'm running Hardy Heron 8.04

During my upgrade from nvidia driver version 169.12 -> 173.14.05

I lost my graphics similar as to what you describe.

Assuming you did a correct install of the nvidia driver.

Check your /var/log/Xorg.0.log for something like:

[I]NVRM: API mismatch: the client has the version 173.14.05, but
NVRM: this kernel module has the version 169.12.  Please
NVRM: make sure that this kernel module and all NVIDIA driver
NVRM: components have the same version.[/I]

To resolv this I did:

sudo modprobe -r nvidia
sudo modprobe -r intel_agp
sudo insmod /lib/modules/2.6.24-18-generic/kernel/drivers/video/nvidia.ko 
sudo /etc/init.d/gdm restart

I'm sure there is a way to make this permanent and probably in a better way, but as it is now I have to do this manually every time I reboot my computer.

This fixes my problem, which smells a bit like yours.

---

