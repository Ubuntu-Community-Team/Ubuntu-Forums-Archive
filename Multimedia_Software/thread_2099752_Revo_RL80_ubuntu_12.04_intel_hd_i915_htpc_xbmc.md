---
title: "Revo RL80 ubuntu 12.04 intel hd i915 htpc xbmc"
date: 2012-12-30
forum: Multimedia Software
---

### Post by fieus on 2012-12-30
Hi

I'm trying to install Ubuntu 12.04 LTS on a Acer nettop Revo RL80 without success. I tried xorg x-swat, xorg edgers, linux kernel 3.2, 3.5 and 3.6 (3.6.5 specifically) but I cannot get the Intel HD videocard to work. If I set nomodeset in a file in the /etc/modprobe.d directory or in the /etc/default/grub file I can boot. This is without any video card hardware acceleration. No need to say this s*xx for a PC meant to use as XBMC player. So a 10 FPS with CPU at 200% :(

The problem is see is or a black screen, but most of the time I see a colorful screen showing all rainbow colors. 
Any help would be greatly appreciated.

Mark

---

### Post by SR_ELPIRATA on 2012-12-30
Not sure how much I can help, but my 2 cents would be to use other distros to see if its only ubuntu (you could try lubuntu for example), or if the harddrive you plan to use is empty I would suggest also xbmcbuntu.

I would also ask you why you chose that model with the Intel card, they arent the ones most known for good HD performance (not even video gaming performance). In general, xbmc/gaming requires a good 3D card (you can also look at the xbmc wiki, they show the minimun requisites).

But, even if you werent to use the system for HD media, any distro should work, and if none do I would think is because the system was originally designed to only run window$ (I've seen some) and as such makes it harder to get linux working on them (not that is impossible, just way harder).

Also, try the xbmc forums, you might not be the first who has encountered this problem. My best suggestions is try other distros, lubuntu or macbuntu would be my choices, but intel video suxxx (usually).

I have run xbmc many times, (and I love it), but never tried to do it on intel video cause they dont have the same power that nvidia/ati do have.

ELP

PS: If the sole use of that system is going to be XBMC... you could even go with Openelec.
PS2: Another suggestion, install ubuntu using another computer, then bring the hard drive to this one. This one Im using right now has been exchanged between 5 different computer systems (and has nvidia/ati drivers), used in both AMD and Intel cpus, and ATI and Nvidia gpus as well. Its one of my preffered things about Ubuntu, I can simply move the hard drive between computers with utmost confidence that it will work. I would simply install (in your case) ubuntu plain, and if it works, then install xbmc on it and enjoy.

---

### Post by fieus on 2012-12-31
Well, thanks for the reply. I also noticed the support for Intel GFX is just plain bad. In the mean while I found Mythbuntu 11.10 is able to install. I'm now upgrading it to 12.04, for which I know it will break the install, but I also found a solution for that.

The Revo RL80 is by many users perceived as a good solution for a htpc - XBMC pc. It is the successor of the RL3600 which is very good. A pity that they put an Intel HD GFX inside.
More info [http://www.amazon.de/Acer-Aspire-Desktop-PC-Dual-Core-Blu-ray/dp/B009YQ1XWA/](http://www.amazon.de/Acer-Aspire-Desktop-PC-Dual-Core-Blu-ray/dp/B009YQ1XWA/)

---

### Post by luwii on 2013-01-09
Same problem here with Revo RL80 and Ubuntu 12.04 LTS - It stops at some point with a flashing screen during install (with no text.)

Thanks for the tip on Mythbuntu 11.10. At least that installs and saved me trying lots of distro's!  I also tried the automated upgrade to 12.04 from within Mythbuntu, but the screen problems return after reboot. 

i'm not using it as a HTPC, just a low power server. 

Any other experiences or ideas to get a stock Ubuntu 12 on the Revo?

---

### Post by rodhull on 2013-01-09
I had the exact same problem but after much digging I found this:
[https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/217767](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/217767)

...and I finally got the installer for 12.10 booting by using the suggestion in that post and editing the boot line using the F6 option and adding:

 i915.blacklist=1


before the "--"

This appears to stop Ubuntu from trying to use the i915 module (which seems to be causing problems with this hardware), and it will fall back to VESA instead.

It installed fine but then gave similar issues on first boot - simply hit shift as Grub starts, and you should be able to use "e" to edit the boot line and add the blacklist option again.

To make it permanent, once booted, again follow **actionparsnip's** instructions...

---

### Post by luwii on 2013-01-09
Thanks!! - I've not had time to test all of it, but the install is working. So I'm sure the rest will as well.

---

### Post by bloodearnest on 2013-01-09
I had the same problem with an RL80

I got 12.04.1 installed using the alternate installer in expert mode. But to get it to boot post-install, I had to use the rescume mode, and add nomodeset to the grub kernel paramers.

Works ok now, except for no hw acceleration, which sucks, as the whole point of it was xbmc :(

I also tried the xorg-edgers ppa, but that didn't give me any benefit

---

### Post by jmate24 on 2013-01-09
intel and nvidia's code is broken in ubuntu and many other distros that are based on ubuntu like xbmcbuntu...

---

### Post by rodhull on 2013-01-15
Has there been any movement on this? I'm also using xorg-edgers and there's still no improvement - there doesn't seem to be a way of using the correct Intel drivers presently, only the VESA one (which doesn't accelerate video decoding)...

---

### Post by purct on 2013-01-18
I am considering buying one of these revo RL80's, I already have the RL70 version and i think its great...but I am somewhat put off buying now!!  

Can somebody try this and let us know the results:

Modify the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub to:

GRUB_CMDLINE_LINUX_DEFAULT="video=i915:modeset=1 i915.i915_enable_rc6=1 i915.lvds_downclock=1 i915.i915_enable_fbc=1 pcie_aspm=force"


Then run:

sudo update-grub

After running update-grub restart ubuntu!

NOTE: You may wish to also try with i915.modeset=0

Also it maybe worth trying the following:

edit the file /etc/mkinicpio.conf and add:

MODULES="intel_agp drm i915"

I hope it helps!

---

### Post by fieus on 2013-01-22
Last update: I have a full working setup, based on MythBuntu 11.10 without nomodeset for all clarity so I have the hardware acceleration. I presume stock Ubuntu 11.10 also works. After installation I installed XBMC.
I did NOT install any updates as it breaks my system and I've seen enough of the screen flashing :/
For the sound to work I had to do some extra config in 2 files. I can post them here if anyone would need them. The sound does not work through the digital connector, only through HDMI.

I tried the xorg-edges and all that crack with the only result a flashing screen. If anyone could get it to work soon I'll pay him/her a pizza ;) In the other case, I wait for Ubuntu 13.04 or I try some other distro.

---

### Post by gnasher666 on 2013-01-23
Would love to know if this will ever be resolved, the only reason I purchased the Revo was for xbmc duties.

Using the older 11.10 Mythbuntu, does anyone know if XBMC Frodo is support with Hi-Def audio bitstreaming?

I'd also throw in a Pizza for the resolver of this!

---

### Post by gnasher666 on 2013-01-25
Will test tonight and report back.

Thanks for your assistance.

> **purct said:**
> I am considering buying one of these revo RL80's, I already have the RL70 version and i think its great...but I am somewhat put off buying now!!  

Can somebody try this and let us know the results:

Modify the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub to:

GRUB_CMDLINE_LINUX_DEFAULT="video=i915:modeset=1 i915.i915_enable_rc6=1 i915.lvds_downclock=1 i915.i915_enable_fbc=1 pcie_aspm=force"


Then run:

sudo update-grub

After running update-grub restart ubuntu!

NOTE: You may wish to also try with i915.modeset=0

Also it maybe worth trying the following:

edit the file /etc/mkinicpio.conf and add:

MODULES="intel_agp drm i915"

I hope it helps!

---

### Post by gnasher666 on 2013-01-25
Hi,

tried the GRUB_CMDLINE.... settings and still no go.

I wasn't able to locate the mkinicpio file to edit so I've not been able to try that.

Any other suggestions please?

Cheers.

> **purct said:**
> I am considering buying one of these revo RL80's, I already have the RL70 version and i think its great...but I am somewhat put off buying now!!  

Can somebody try this and let us know the results:

Modify the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub to:

GRUB_CMDLINE_LINUX_DEFAULT="video=i915:modeset=1 i915.i915_enable_rc6=1 i915.lvds_downclock=1 i915.i915_enable_fbc=1 pcie_aspm=force"


Then run:

sudo update-grub

After running update-grub restart ubuntu!

NOTE: You may wish to also try with i915.modeset=0

Also it maybe worth trying the following:

edit the file /etc/mkinicpio.conf and add:

MODULES="intel_agp drm i915"

I hope it helps!

---

### Post by monkley on 2013-03-12
> **fieus said:**
> Last update: I have a full working setup, based on MythBuntu 11.10 without nomodeset for all clarity so I have the hardware acceleration. I presume stock Ubuntu 11.10 also works. After installation I installed XBMC.
I did NOT install any updates as it breaks my system and I've seen enough of the screen flashing :/
For the sound to work I had to do some extra config in 2 files. I can post them here if anyone would need them. The sound does not work through the digital connector, only through HDMI.

I tried the xorg-edges and all that crack with the only result a flashing screen. If anyone could get it to work soon I'll pay him/her a pizza ;) In the other case, I wait for Ubuntu 13.04 or I try some other distro.

Could I get those config files please? Just about to try MythBuntu 11.10 for my Revo (L80).

---

### Post by rodhull on 2013-03-12
I appreciate that 11.10 appears to work but for me it isn't acceptable for me to install a release that will not be supported shortly.

Is there any further news on this hardware working correctly with the Intel driver (without nomodeset etc.) in 12.04 or 12.10, or even if support is planned for 13.04?

---

### Post by mrdemeanour on 2013-03-30
> **rodhull said:**
> I appreciate that 11.10 appears to work but for me it isn't acceptable for me to install a release that will not be supported shortly.

Is there any further news on this hardware working correctly with the Intel driver (without nomodeset etc.) in 12.04 or 12.10, or even if support is planned for 13.04?

I have the RL80 working with kernel mode setting.

This involved patching a 3.9 kernel. 
I used this kernel:
[http://cgit.freedesktop.org/~danvet/drm-intel/snapshot/drm-intel-next-2013-03-23.tar.gz](http://cgit.freedesktop.org/~danvet/drm-intel/snapshot/drm-intel-next-2013-03-23.tar.gz)

I applied this patch:
[https://bugs.freedesktop.org/attachment.cgi?id=77018](https://bugs.freedesktop.org/attachment.cgi?id=77018)

The result: I have a native i915 driver (not VESA) with kernel mode setting, I can use xrandr to set custom modes, *and* as a bonus, Intel HD Audio seems to work quite a bit better than it did with any other kernel I've tried. 

Dan Vetter and the Intel Graphics team turned this problem around for me in about 36 hours; I was really impressed. I have no idea how long it will take for this patch to get into mainstream Debibuntu distros.

---

### Post by mrburns2013 on 2013-03-30
interesting...

I have the same problem with my RL 80. Can I hope that the problem will be solved in older Kernel (3.2.39 in Ubuntu 12.04) ?
Also i have seen a new Bios P11.A2L "Bios for Linux" for Revo 80. If i start the bios update, the screen shows &#8220;Error: File ROM ID incorrect" 
Acer in germany will not hepl with linux-os, if the device was shipped with windows 8.

---

### Post by lasttoknow0 on 2013-03-31
I compiled the kernel using the patch that mrdemeanor listed, starting from ubuntu 12.10, and it appears to have worked.  I can boot without the i915.blacklist option, and I don't get the flashing rainbow colors.  

Video playback still isn't as fast as I had hoped; I played a youtube video in firefox and it was pretty sluggish.  The mouse is also sluggish to react.  I don't know if this is related, but I suspect it may also be related to the graphics because the compz process spikes up in cpu utilization when I move the mouse around.

Edit:  mouse lag seems to happen if I change my TV to a different video source and back.  If I restart the RL80 the mouse lag goes away (until I change the TV again).

---

### Post by rodhull on 2013-04-01
I presume that this is the bug?
[https://bugs.freedesktop.org/show_bug.cgi?id=60029](https://bugs.freedesktop.org/show_bug.cgi?id=60029)

Is there any way someone can provide a pre-compiled .deb of a working patched kernel? I can't remember the last time I had to compile a kernel from source and my skills are a little rusty!

---

### Post by mrburns2013 on 2013-04-04
how can I install this patch in the Ubuntu 3.2.0.xx kernel ? When will be  included this patch  in Ubuntu original kernel or in mainline kernel?

---

### Post by rodhull on 2013-04-18
The patch has now been merged into the drm-intel-nightly tree!

There are pre-built Ubuntu .debs of the kernel here that work for me in 12.10:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/2013-04-18-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/2013-04-18-raring/)

Download the linux-headers...all.deb plus the other two .debs appropriate for your arch into a new dir. Go into the dir you downloaded them and install using "*sudo dpkg -i *.deb*"

Remember to remove any workarounds you had previously set in /etc/default/grub (such as i915.modeset=0 or similar) and run "*sudo update-grub*".

Reboot, then you'll have a working i915 driver with full HW acceleration!

Get hold of the package** libva-intel-vaapi-driver** and use something like SMPlayer to get full-screen 1080p video playing without a hiccup (only ~50% CPU usage!).

---

### Post by haqman on 2013-04-18
> **rodhull said:**
> The patch has now been merged into the drm-intel-nightly tree!

There are pre-built Ubuntu .debs of the kernel here that work for me in 12.10:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/2013-04-18-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/2013-04-18-raring/)

Download the linux-headers...all.deb plus the other two .debs appropriate for your arch into a new dir. Go into the dir you downloaded them and install using "*sudo dpkg -i *.deb*"

Remember to remove any workarounds you had previously set in /etc/default/grub (such as i915.modeset=0 or similar) and run "*sudo update-grub*".

Reboot, then you'll have a working i915 driver with full HW acceleration!

Get hold of the package** libva-intel-vaapi-driver** and use something like SMPlayer to get full-screen 1080p video playing without a hiccup (only ~50% CPU usage!).

Hi,

I just registered to say thank you, it worked for me flawlessly.
Now using Ubuntu 12.10 with Acer Revo RL80 with no problems.

I was going to build the kernel from source, didn't know about that ppa :)

The sad news is, this patch won't make it for 13.04 :|

---

### Post by jimwild100 on 2013-05-16
okay, so i've entered this world of pain and bought one of these. it had feedos on it. I didn't even look at that.  

So 12.04 server doesn't work, except by blacklisting, i finally worked how to do that one.  

So please help me:
a) do I need to install 12.10 a fresh and then apply the .deb packages described?  I can't seem to get my 12.04 to upgrade ](*,)
b) Those nightly builds linked in previous posts are not available, if I do a fresh install will the new latest 12.10 nightly builds work? 
c) or is it patched and working in 13.04 by now?  (I'll set that to download and perhaps see shall I?)

Many thanks,
Jim.

---

### Post by fieus on 2013-06-30
> **jimwild100 said:**
> 
c) or is it patched and working in 13.04 by now?  (I'll set that to download and perhaps see shall I?)

Hey Jim, did you try this already? :)

---

### Post by rag2 on 2013-08-14
> **fieus said:**
> Hey Jim, did you try this already? :)

If anyone's still following this thread the **very** good news is that the Saucy Salamander 64 bit desktop alpha 2 release seems to work straight out of the box. The 12.10 release gives video problems, but the patch seems to have made it in to 13.10&#9082;2.

---

### Post by fieus on 2013-09-02
@rag2: still following yeah ;) Thanks for the update. I'll try it later this week. Do you know by any chance weather the (digital) audio also does work?

---

### Post by rag2 on 2013-09-03
> **fieus said:**
> @rag2: still following yeah ;) Thanks for the update. I'll try it later this week. Do you know by any chance weather the (digital) audio also does work? Sadly the machine is currently decommissioned following a move, but, as far as I can recall, *Sound Settings* offered HDMI audio. Can't remember if there was an option for SPDIF output. Should be up & running again in a few days. **Iff** I remember, I'll post the results here—there's a lot of other stuff going on at present!

---

### Post by rag2 on 2013-09-30
> **fieus said:**
> @rag2: still following yeah ;) Thanks for the update. I'll try it later this week. Do you know by any chance weather the (digital) audio also does work?

The pulse audio chooser offers **SPDIF**, but I've not had the opportunity actually to use this, **HDMI (digital audio)** does work, plugging in a cable reveals a **headphone output** option, which works fine (and is always labelled headphones)—**this is absent without a cable plugged in**. An external USB DAC is correctly found and behaves correctly. No complaints on the audio output front. YMMV

---

