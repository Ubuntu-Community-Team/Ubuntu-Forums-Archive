---
title: "Installing AMD Proprietary Driver | Need Advice"
date: 2012-06-30
forum: Multimedia Software
---

### Post by neu5eeCh on 2012-06-30
Xubuntu 12.04 - 64bit

Hi folks, I've got a Vaio running a** Mobility Radeon HD 3650**. I'm not sure what drivers I'm using at the moment (**not** the hardware driver installed by the "Additional Drivers" applet). I tried installing the FGLRX drivers, but the results are terrible: tear out, miserable performance, ghosting, etc...

I found an AMD driver here:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

I'm downloading it. Questions:

1.)  How do I identify the current driver I'm using?
2.) Is there anything I should do prior to installing the proprietary driver?
2.) How should I remove it if the results are less than stellar?

---

### Post by QIII on 2012-06-30
Did you install amdcccle, the Catalyst Control Center?

The driver included in Ubuntu 12.04 is the AMD/ATI 12.4 driver, development branch 8.960.  It's the same driver as the 12.4 driver at AMD, except that that one is development branch 8.961 -- which is just the driver released to the public after the driver was first included in the Ubuntu repos, like AMD always does on the 4th and 10th month.

---

### Post by neu5eeCh on 2012-06-30
> **QIII said:**
> Did you install amdcccle, the Catalyst Control Center?

No, I haven't. At one point, I installed the FGLRX drivers offered by the "Additional Driver" applet (**edit:** at which point I think they might have been installed). When the video performance considerably suffered, I "switched off" the FGLRX driver and also followed the [following instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx") to completely remove the drivers.

I assume I'm using some open source driver at present?

---

### Post by QIII on 2012-06-30
Right now you are using the open source driver.

I've extensively rewritten the ATI driver wiki (see my signature).

If you are having trouble with the Additional Drivers method,  check the wiki out and look at the section "Using the Ubuntu repositories (alternate command line method, including hardware acceleration)"

There is a lot you can do with the Catalyst Control Center to clean up the performance.  Are you using Compiz?  You might try switching that off and see if your performance improves.

By the way, the open source driver really is good now.  You miss some of the adjustment features in the CCC, though.

---

### Post by neu5eeCh on 2012-06-30
Thanks for responding QIII. Here's an update:

I tried installing the driver linked in my first post. The result was that rebooting landed me in a tty session. xorg apparently failed to start.  I issued the startx command and proceeded.

It seems that either the driver wasn't the correct version for mine, or that the install was somehow messed up. Trying to start aticonfig from the command line resulted in the error message that the AMD driver was not properly installed or incompatible.

I uninstalled and once again cleaned out all traces of FGLRX.

I've rebooted and am presumably using the open source drivers. This is very frustrating. I don't understand why I can't get the same performance in the Linux side as on the Windows side. There is *way* too much tear out while watching videos (which is primarily why I'd like to get things up and working on the Linux side). This is a dual boot Windows 7/Xubuntu 12.04 system.

---

### Post by neu5eeCh on 2012-06-30
> **QIII said:**
> I've extensively rewritten the ATI driver wiki (see my signature).

I'm reading it right now.

> **QIII said:**
> If you are having trouble with the Additional Drivers method,  check the wiki out and look at the section "Using the Ubuntu repositories (alternate command line method, including hardware acceleration)"

Hmm... I'm not seeing the "Using the Ubuntu repositories" section?

> **QIII said:**
> There is a lot you can do with the Catalyst Control Center to clean up the performance.  

OK, I'll try re-installing the ATI/AMD Proprietary FGLRX drivers from the repositories. I've never been able to successfully install the post-release updates however. Attempting to do so always deactivates the FGLRX driver. I'm assuming this is a bug of some kind. If you have advice, that would be great.

> **QIII said:**
> Are you using Compiz?  

No, just XFWM4.

> **QIII said:**
> By the way, the open source driver really is good now. 

I wouldn't know. I get an insane amount of tear out when watching videos. On the Windows partition, the same video is smooth as butter.

---

### Post by QIII on 2012-06-30
Are you looking at the "Community ATI Driver Wiki" link?

In the table of contents in the upper right, under "Installation", click item 2

Edit:  Taking a closer look at the instructions you used, the following was included as a file to uninstall -- which was NOT necessary for your purposes.  Its absence now may, however,  be causing you problems now.

Reinstall xorg-driver-fglrx if it is not being installed as a dependency when you attempt to install fglrx and fglrx-amdcccle.

---

### Post by neu5eeCh on 2012-06-30
> **QIII said:**
> Are you looking at the "Community ATI Driver Wiki" link?

Thanks. Found it. My bad. :rolleyes:

> **QIII said:**
> Edit:  Taking a closer look at the instructions you used, the following was included as a file to uninstall -- which was NOT necessary for your purposes.  Its absence now may, however,  be causing you problems now.

OK. I reinstalled via Additional Drivers. I opened catalyst and enabled the option to stop tear out. 

That improved tear out but (as before) video quality still pales in comparison to the Windows side. For lack of a better (or official) term, there's an extreme amount of "striping" when the video gets busy - an effect like looking through window blinds. Right now, I'm on the windows side, looking at the same video, and there is neither tear out, nor striping; so it's not a question of hardware capability.

> **QIII said:**
> Reinstall xorg-driver-fglrx if it is not being installed as a dependency when you attempt to install fglrx and fglrx-amdcccle.

Soon as I'm back on the Linux side, will do.

---

### Post by neu5eeCh on 2012-06-30
Oh... here's something interesting: SMPlayer and VLC both produce "striping". Totem doesn't, though Totem can be a little herky-jerky when the video is busy. So... seems I might be bumping into media player limitations as well.

---

### Post by QIII on 2012-06-30
If you added the video acceleration as described in the wiki, use av as you output in smplayer.

See the settings I am using (I'm not thumbnailing this so it is clear.)

---

### Post by QIII on 2012-06-30
Sorry...

---

### Post by neu5eeCh on 2012-06-30
> **QIII said:**
> If you added the video acceleration as described in the wiki, use av as you output in smplayer.

See the settings I am using (I'm not thumbnailing this so it is clear.)

OK. I haven't gotten that far yet. But I've vastly improved matters! Your encouragement has been a help.

Here's what I've done so far:

1.) Enable Tear Free Desktop.

Wait for vertical refresh: Always On. The slider option is Performance  on one side, Quality on the other. I pushed it all the way over to  Quality, then back, but didn't notice any difference.

Enable Catalyst A.I. is set to Advanced.

3D (Which probably doesn't affect video performance.)

1.) (Anti-aliasing)  Override Application Setting Checked
2.) (Adaptive Anti-Aliasing) Override Application Setting Checked
3.) (Anisostropic Filtering) Override Application Setting Checked

I was able to stop the "striping" in VLC by:

1.) Setting Deinterlace to **On**. This made a _**huge**_ difference.
2.) I set Deinterlace mode to **Blend** - also a vast improvement - though I'm still experimenting with the best setting. **Blend** is the best so far.
3.) Post Processing is set to 1.

The video playback, at this point, appears to be on par with Windows, or at least it's subtle enough that only a direct comparison could discern a difference.

---

### Post by neu5eeCh on 2012-06-30
//If you added the video acceleration as described in the wiki//

Do you mean this?

> To get hardware acceleration (tested on 12.04 Precise Pangolin), you need to add four more packages.  

sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfoOne interesting side-effect. After all this fiddling and faddling, I had to turn off "smooth scrolling" in Firefox! The flickering and stuttering as the scrolling is "smoothed" seems more pronounced now. Weird, but no great loss.

**Edit:** Installed... And Hey! We nailed it! The Linux side is just as kick-*** as the Windows side! That's the first time I've been able to write this in the three or four years (I think) that I've owned this laptop.

---

### Post by staffann on 2012-07-01
One thing that would be added to the wiki:
More people than me have had problems that the ATI driver uses underscan by default, and that the TV is detected as a projector for which the overscan slider isn't available in catalyst. Using this command corrects the situation:
> sudo aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0

---

### Post by neu5eeCh on 2012-07-01
> **staffann said:**
> One thing that would be added to the wiki:
More people than me have had problems that the ATI driver uses underscan by default, and that the TV is detected as a projector for which the overscan slider isn't available in catalyst. Using this command corrects the situation:

Thanks. I'm assuming this is strictly to hook up a TV? - which I don't do (but may at some point). The switch is 0 or 1?

---

### Post by QIII on 2012-07-02
Thanks, steffann.

I jotted a note in my black book and I'll try to remember to add that to the wiki soon.

---

