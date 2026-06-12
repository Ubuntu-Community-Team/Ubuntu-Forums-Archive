---
title: "Jaunty's not working with my video"
date: 2009-05-08
forum: Multimedia Software
---

### Post by b@sh_n3rd on 2009-05-08
Hey dudes, I installed Jaunty on my second PC and apparently I don't have proper video drivers. I *think* I'm (I was) using the vesa driver. I love Ubuntu and I love Jaunty so I really wanna check it out on my most powerful PC. The thing is video. It's got an Intel 82845G/xxxx card and I don't have 3D acceleration. VESA seems to be giving trouble too, like when GDM loads the display shows some corruption and then it comes back to normal again. All I wanna do is try out compiz...at least THEN I could even show the "coolest" face of Ubuntu to my friends and family :D. I tried what's in this post: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) and broke my system :D. Reinstalling now, please help if you can. Thanks in advance.

---

### Post by Kareeser on 2009-05-08
Is the package "xserver-xorg-video-intel" installed?

```
apt-cache policy xserver-xorg-video-intel

```

---

### Post by coffeecat on 2009-05-08
You've got two problems. Firstly, the 82845G chipset is very old now, and you'll likely never get very good 3D acceleration from it even if it were not for the second problem, which is...

There are a lot of issues with some Intel chipsets and the Intel graphics driver + version of xorg that comes with Jaunty. [This]("https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance?") gives the background. Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1134984"). The OP mentions the i845 series, which is yours I believe, so some of the fixes posted there might help.

---

### Post by b@sh_n3rd on 2009-05-09
Hi guys, I entered that command and got the following output: ```
xserver-xorg-video-intel:
  Installed: 2:2.6.3-0ubuntu9
  Candidate: 2:2.6.3-0ubuntu9
  Version table:
 *** 2:2.6.3-0ubuntu9 0
        500 http://lk.archive.ubuntu.com jaunty/main Packages
        100 /var/lib/dpkg/status

```
I suppose I DO have the driver.
Coffeecat, yeah I know my card is very old...It's integrated to my Intel D845GVSR mobo.
Thanks for replying :)

---

### Post by coffeecat on 2009-05-09
**b@sh_n3rd**, another thought. Have you got an AGP slot on the motherboard? You might be able to pick up an AGP Nvidia card cheaply and even a fairly modest nvidia chipset will give you good compiz effects with the proprietary driver. Go for a Geforce 6200 at least. Anything earlier might be a disappointment.

If you've only got PCI slots (possible on a machine with that Intel chipset) then I wouldn't bother. I doubt whether you can get anything later than a Geforce 5200 on a PCI interface, and to buy new they're very expensive - and hard to find.

I'm assuming that you don't have a PCIe slot. With the 845G chipset, that would be very unlikely.

---

### Post by b@sh_n3rd on 2009-05-09
yeah...no AGP slot...just 3 PCI...but then again even if i HAD an AGP slot I wouldn't spend any money for another card coz I'm gonna build another machine later this year...was wondering whether to use an ATI card or an Nvidia one...That's on another thread, "AMD vs. nForce"...

I checked your first link and tried the first section: ```

 # Save your work first!
 $ sudo rmmod i915
 $ sudo modprobe i915
 $ lsmod | grep i915
 i915 65412 1
 drm 96424 2 i915
 $ sudo pkill X
```
When I try the first command, (sudo rmmod i845) I get ERROR: Module i845 does not exist in /proc/modules.
Same goes for i915.[FONT=Verdana] How do I install these? The xserver-xorg-video-intel packages are installed. And when I tried another command
I found on that site, Jaunty responded saying software acceleration is enabled. It's not supposed to be that way right?
[/FONT]

---

### Post by b@sh_n3rd on 2009-05-09
Hey I checked out the Intel driver downloads in the Support section. It's got heaps of Intel drivers but it's either SUSE, RedHat or something called RedFlag. Which do I choose? or isn't there a proprietary driver for other Linux distro's? Now why is it that I can boot my PC with an Intel 82845G without VESA or any other problem on Gentoo, OpenSUSE and Fedora?? It's puzzling...and I really like Ubuntu too :(...The strangest thing is Ubuntu is older than Fedora which I suppose should say that they've got more experience. But maybe it's Ubuntu's architecture too. Gentoo I can say coz it's an advanced OS and I suppose it's got plenty of geeks to run it :D. Hey, maybe we could reverse engineer one of 'em OS'es and find out what their "secret recipe" is???? :D

---

### Post by b@sh_n3rd on 2009-05-11
OK, I tried a round-about way to get my hardware detected and the correct driver to load...I just added, [[COLOR=Green]Driver     "intel"[/COLOR]] in place of "[COLOR=Green]vesa[/COLOR]" in my "[COLOR=Green]xorg.conf[/COLOR]" file and that got the correct driver. Now the display works without much problems and now I can see what happens when shutting down...previously it was just a blank screen and I just watched for LED signals and waited for it to Power Off.

Anyway, even though I have the correct driver, when I try "[COLOR=Green]glxinfo | grep render[/COLOR]" I get this:
```
[COLOR=Navy]get fences failed: -1
param: 6, val: 0
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 845G GEM 20090326 2009Q1 RC2 x86/MMX/SSE2[/COLOR]
```What does this error and the leading line mean? How can I set up 3D on my card to work properly?

---

### Post by b@sh_n3rd on 2009-05-11
Ok, I tried enabling UXA acceleration by editing my xorg.conf file as [this]("https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance") article mentions. Now I've got perfect video and screensavers that wouldn't work at all or wouldn't work smoothly are all working perfect now! Now, I'm gonna try compiz or something...AWN I suppose...wish me luck...Oh yeah, for reference purporses...

My card is the i845. This is my xorg.conf file after I edited it:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        BusId           "PCI:0:2"
        Option          "AccelMethod" "uxa"
EndSection

```I added "BusId" coz I've got two video adapters...just in case :D. It works same even without it.

**EDIT:** OK, Desktop effects don't work for some reason...spitty...I just tried clicking "Normal".
**EDIT2:** When running AWN, performance isn't too good...Screensavers are all jittery...
**EDIT3: **OK, I caught the bug...I tried the other [thread]("http://ubuntuforums.org/showthread.php?t=1130582") on the intel graphics card previously but couldn't install the kernel. I fixed that problem which was to do with my partitioning method. Now I'm gonna try it again from the top. I edited my xorg.conf file as mentioned and am downloading the 2.6.29 kernel release...It should work ok this time.

---

