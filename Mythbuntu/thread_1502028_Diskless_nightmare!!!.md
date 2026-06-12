---
title: "Diskless nightmare!!!"
date: 2010-06-05
forum: Mythbuntu
---

### Post by waxhead on 2010-06-05
Hi Everyone,

I'm trying - TRYING - to get a diskless frontend working over pxe.  :confused:

I've followed [https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless](https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless) and [http://ubuntuforums.org/showthread.php?t=1305845](http://ubuntuforums.org/showthread.php?t=1305845) which I used for the commandline to get the client image initially built.

In the first instance, most of problems revolved -and still does - around blacklisting the nouveau driver and getting the nvidia driver working - I need VDPAU.

So the first time around I eventually got it working, ie NVIDIA was finally installed and mythfrontend started up, however no sound.

I couldn't work out any which way to get it working.  In the end I removed /opt/lstp/* and started again.

It was during my searches that I stumbled on getting sound to working such that I could unmute the digital channels.

Now though I can't for the life of me blacklist the nouveau driver such that the nvidia driver works.

So my call for help is, how do I start completely form scratch, and how the heck do you get a kernel image that has no nouveau driver????

Is it just enough to mount proc, then chroot, edit a blacklist.conf file add in the nouveau drivers and then exit out and run ltsp-update-kernels????

Clearly, not as it's not worked for me, but I did try update-initrdfs -u while chrooted and then ltsp-update-kernels, but still the nouveau driver gets installed.

I have also appended blacklist=nouveau to the kernel line in default under  /boot/pxe.....cfg/ to no avail.

It's driving me nuts... I've been at this weeks... yes.. sad to say.. weeks and still no netbooted diskless front end with a working display and sound.  The OS boots fine I must add. :(

Any help suggestions etc.. 

I've got a USB thumb drive now, ready to just go with booting from that, but I really wanted to just use the network boot if I could.

Thanks.

---

### Post by lmclaren on 2010-06-08
Yep, Nvidia drivers on diskless is a POS.

I have tried all of the nice ways and in the end had to swap to a server kernel to get rid of noveau.

I can go looking and try to find some more detail for you if you need.

regards

LM

---

### Post by MikeUK on 2010-06-08
One option might be to build your own Kernel ?
I'll admit I've never done it on Ubuntu.
But it was a technique I used to use on Thin Clients in Slackware, both to get the size down and make sure it only had what I needed.

---

### Post by LowSky on 2010-06-08
Have you tried LinHES? It might work better in this case and still be able to connect to a master backend that is running on Ubuntu

---

### Post by jmatienzo on 2010-06-08
You have to blacklist module nouveau but for some reason adding it to /etc/module.d/blacklist.conf won't work. the only way I could blacklist it was to add "blacklist=nouveau" to the APPEND option in pxelinux.cfg/default

---

### Post by nickrout on 2010-06-08
> **jmatienzo said:**
> You have to blacklist module nouveau but for some reason adding it to /etc/module.d/blacklist.conf won't work. the only way I could blacklist it was to add "blacklist=nouveau" to the APPEND option in pxelinux.cfg/default

you don't add it to /etc/module.d/blacklist.conf, surely you add it to /opt/ltsp/i386/etc/module.d/blacklist.conf ?

---

### Post by waxhead on 2010-06-13
> **nickrout said:**
> you don't add it to /etc/module.d/blacklist.conf, surely you add it to /opt/ltsp/i386/etc/module.d/blacklist.conf ?


When you chroot your environment it works fine, since you have changed your root to point to the ltsp directory.

---

### Post by waxhead on 2010-06-13
> **jmatienzo said:**
> You have to blacklist module nouveau but for some reason adding it to /etc/module.d/blacklist.conf won't work. the only way I could blacklist it was to add "blacklist=nouveau" to the APPEND option in pxelinux.cfg/default


thanks, I read that in another thread too, and have done this.

It was this I think that worked for me the first time around.  Seems this time around nouveau still gets loaded.

I haven't fiddled with things for a while now, so might give it go again this afternoon if I get time.

---

### Post by nickrout on 2010-06-13
> **waxhead said:**
> When you chroot your environment it works fine, since you have changed your root to point to the ltsp directory.

Sorry didn't realise you were chrooted at the time.

---

### Post by waxhead on 2010-06-14
OK, it's working!!!

I have sound and I have video.

I'm not sure what it finally took, however the process I went through this time around was to get the mixer working and allowing me to unmute the digital outputs.

That solution came from here:

[http://gagravarr.livejournal.com/137571.html](http://gagravarr.livejournal.com/137571.html)

I needed the asound.conf settings.

Then I mounted the image on the server as per the process here:

[http://ubuntuforums.org/showthread.php?t=1305845](http://ubuntuforums.org/showthread.php?t=1305845)

So mount, chroot and then apt-get install nvidia-common and then apt-get install nvidia-current

Also add the blacklist=nouveau to the append section of the default file as above.

exit out of the chroot 

and then ltsp-update-kernels and ltsp-update-image

This gave me a working mythbuntu frontend with sound via the HDMI output.

Now all I have to do is setup the remote!

---

### Post by goofnrox on 2010-06-17
> **waxhead said:**
> http://ubuntuforums.org/showthread.php?t=1305845[/URL]

So mount, chroot and then apt-get install nvidia-common and then apt-get install nvidia-current

Also add the blacklist=nouveau to the append section of the default file as above.

exit out of the chroot 

and then ltsp-update-kernels and ltsp-update-image

This gave me a working mythbuntu frontend with sound via the HDMI output.

Now all I have to do is setup the remote!


This worked perfectly! Thanks\\:D/


Does the MCC or Nvidia control panel work on your setup? Neither do on mine, which is not a huge deal, just makes more manual work.

---

### Post by waxhead on 2010-06-19
No it doesn't, but I found that I didn't have to do anything to get 1920*1080.. 

I think the simplest solution is to get an xorg.conf that works on another machine and us it.

---

### Post by Gibby13 on 2010-09-17
On your frontend download the binary from Nvidia. Then stop GDM and install the new driver. You will then have the nvidia-settings installed for the GUI configuration.

---

### Post by nickrout on 2010-09-17
> **Gibby13 said:**
> On your frontend download the binary from Nvidia. Then stop GDM and install the new driver. You will then have the nvidia-settings installed for the GUI configuration.

No no no no

Do not step outside the distros packaging!!

---

### Post by Gibby13 on 2010-09-18
> **nickrout said:**
> No no no no

Do not step outside the distros packaging!!
Why not? The binaries from Nvidia fix many issues. I have used the binaries from Nvidia for years in Ubuntu.

---

