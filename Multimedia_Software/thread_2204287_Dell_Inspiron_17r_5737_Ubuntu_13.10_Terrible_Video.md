---
title: "Dell Inspiron 17r 5737 Ubuntu 13.10 Terrible Video"
date: 2014-02-07
forum: Multimedia Software
---

### Post by GandalfTheNerd on 2014-02-07
The machine basically works, but the display looks to be very low resolution and with strange green and purple colours. Text is readable, but only just. However, the display settings show 1600 x 900. The display is OK in Windows 8.1, which I am not a fan of.

The effect sounds a bit like this: [http://ubuntuforums.org/showthread.php?t=2203700](http://ubuntuforums.org/showthread.php?t=2203700)

I tried the Intel drivers suggested (but version 1.0.3 for Ubuntu 13.10) and it made no difference at all. The display is the same when booting from an unmodified 13.10 on a USB memory stick. I have attached the output of lspci -k and most of Xorg.0.log. The latter is somewhat edited to meet the forum's file size limit.

The line "[    23.152] (II) intel(0): Setting screen physical size to 423 x 238" is interesting. The resulting display is consistent with this.

I'd be really grateful for any useful suggestions. At present, my brand new laptop is essentially useless!

---

### Post by GandalfTheNerd on 2014-02-08
Strangely, I get a reasonable picture with correct colours using an external monitor connected via HDMI. The resolution is incorrect but I hope to be able to fix that.

---

### Post by oldfred on 2014-02-08
This mentions you have to leave BIOS/Legacy on, even when booting with UEFI as Intel has some issue with Haswell chips.

       Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[URL="https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z"]
https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z[/URL]

 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)

You many need to add boot options.

 Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

       
 Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)
New Intel driver installer (only with 13.04)
[http://www.phoronix.com/scan.php?page=news_item&px=MTQyNTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTQyNTQ)
[https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

---

### Post by Stew_Benedict on 2014-02-17
Same issue with a new 12.04 install on the same machine.
Also installed Kali Linux and Mageia 4 - all have the same display problems :/
Tried all the referenced solutions, no joy.

---

### Post by GandalfTheNerd on 2014-02-23
Thanks Stew_Benedict, at least I am not alone! To illustrate the problem, I have attached two photographs. 20140223_152339.jpg is the internal monitor display resulting from an unmodified 13.10 ubuntu installed on a USB memory stick. For comparison, 20140223_153139.jpg is the same, but using an external HDMI monitor. In this latter case, the system is perfectly usable - though not really ideal for a laptop!

The Intel drivers appeared to make no difference at all, though perhaps they had an effect on graphics performance. I suspect a monitor configuration problem.

---

### Post by Chris_Shumeyko on 2014-03-16
I'm having the exact same issue. Have tried numerous solutions to no avail. Have you made any headway on this?

---

### Post by GandalfTheNerd on 2014-03-16
No progress at all, I'm afraid. I'd love to be able to report otherwise.

---

### Post by oldfred on 2014-03-16
Although not yet final, some are reporting that 14.04 works right out of the box, or only with minor fixes.

But 14.04 should not be your primary system until released.

---

### Post by GandalfTheNerd on 2014-03-16
If it does there will not only be delight on my part, but also a contribution to Ubuntu! Roll on April 17th so I can try it!

---

### Post by Chris_Shumeyko on 2014-03-17
Thanks for the update, all. I have another laptop that I was running 12.04 on until the HDD quit. I have a new HD coming in this week so I hope to get that up and running, at which point I'll use that as primary until 14.04 becomes official and I can switch back to the new Dell.

---

### Post by GandalfTheNerd on 2014-03-17
I've just tried Ubuntu GNOME 14.04 (Trusty Tahr) Beta 1 from a USB stick and it behaves as 13.10 in this respect :-(

I'll try 14.04 again when it is released.

---

### Post by GandalfTheNerd on 2014-03-18
Ubuntu 14.04 (Trusty Tahr) Daily Build for 18/3/2014 doesn't solve this either.

---

### Post by mrichards on 2014-03-20
I am also experiencing this problem.
Does installing the "official" Intel Graphics Stack drivers help resolve this at all? (On 13.10 of course, as they do not appear to support the daily 14.04 builds)
I also have tried the Ubuntu [COLOR=#000000]14.04 (Trusty Tahr) daily [/COLOR]build (19/03/2014), and still does not resolve this issue.

---

### Post by GandalfTheNerd on 2014-03-20
I tried the Intel drivers (version 1.0.3 for Ubuntu 13.10) and it made no difference to this issue at all. I have yet to find anything that does!

---

### Post by Jezdec on 2014-03-26
The comment about 12.04.1 in the thread

[http://ubuntuforums.org/showthread.php?t=2204599](http://ubuntuforums.org/showthread.php?t=2204599)

made me try 12.04.2. And, I found that

[http://old-releases.ubuntu.com/releases/12.04.2/ubuntu-12.04-desktop-amd64.iso](http://old-releases.ubuntu.com/releases/12.04.2/ubuntu-12.04-desktop-amd64.iso)

makes for a happy video experience. The video continues working even after installing all updates. However, starting with 12.04.3 or 12.04.4 does not make the word a happy place. I think that this is enough to call this a regression introduced in 12.04.3.

---

### Post by digimotifgmail.co on 2014-04-02
I also have the Dell Inspiron 5737.  I finally found something that doesn't give me the green (incorrect) colored screen with the horrible looking (fuzzy) text just as you all have been having issues with.

I used the "nomodeset" boot option and it gave me the correct looking display.

Apparently, this option forces the kernel to use basic BIOS display settings and to not attempt to use video drivers.

Once I booted the Live USB of 13.10 and the daily of 14.04 using this boot option, everything looked great.

---

### Post by digimotifgmail.co on 2014-04-02
I just finished the install and rebooted -- just using "nomodeset" as a boot option isn't working.  I get no desktop at all, as X crashes.  /var/log/Xorg.0.log shows "open /dev/dri/card0: No such file or directory" and ends with "no screens found(EE)"

So I've got more digging to do.

---

### Post by digimotifgmail.co on 2014-04-02
> **digimotifgmail.co said:**
> So I've got more digging to do.

OK, I found that some were saying to replace the "quiet splash" options with "nomodeset", so I did that in the boot options, but I still wasn't getting a working X environment.

I looked through /var/log/syslog and found this error come up during my last boot:

> error vesafb: module verification failed: signature and/or required  key missing - tainted kernel

Some others that had this error mentioned issues with their BIOS not allowing the VESA mode to be used.  I had already shut off Safe Boot in UEFI, but I didn't enable the legacy mode.  So I went back into my 5737 BIOS and enabled legacy mode (safe boot still off, boot mode was still set to UEFI).

Now if I specify "nomodeset" I get a working X server with proper colors and resolution.  However, the system says that Xorg crashed and wants to file a crash report.

---

### Post by oldfred on 2014-04-02
The article on the XPS15 says you do have to have legacy on even with UEFI as it is some issue with Intel:

 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)

---

### Post by digimotifgmail.co on 2014-04-02
OK, so I tested all of my function keys and found the brightness controls weren't working, and the settings for backlight weren't available, but everything else (volume controls, keyboard backlight, wireless, touchpad) all worked.  Found some suggestions in other threads for adding "acpi_backlight=vendor" to the boot options as well and that worked.  Now all of the function keys work.

So, to recap:

First, in BIOS, I disabled Secure Boot and needed to enable Legacy Support. 

When booting from Live USB, adding "nomodeset" to the boot command line (Hit "e" to edit boot options before making a selection, then hit F10 to boot your edited command) prevents the kernel from loading video drivers and the X server loads video correctly.

Once installed, I had to boot and edit /etc/default/grub so the following line read:
> CODEGRUB_CMDLINE_LINUX_DEFAULT="nomodeset acpi_backlight=vendor"

then ran:

> update-grub

the rebooted one final time.

Now I believe I have a fully functioning Ubuntu 13.10 install on my Dell Inspiron 17r (5737) laptop. :guitar:

---

### Post by victor_sk on 2014-04-03
> **GandalfTheNerd said:**
> The machine basically works, but the display looks to be very low resolution and with strange green and purple colours. Text is readable, but only just. However, the display settings show 1600 x 900. The display is OK in Windows 8.1, which I am not a fan of.

The effect sounds a bit like this: [http://ubuntuforums.org/showthread.php?t=2203700](http://ubuntuforums.org/showthread.php?t=2203700)

I tried the Intel drivers suggested (but version 1.0.3 for Ubuntu 13.10) and it made no difference at all. The display is the same when booting from an unmodified 13.10 on a USB memory stick. I have attached the output of lspci -k and most of Xorg.0.log. The latter is somewhat edited to meet the forum's file size limit.

The line "[    23.152] (II) intel(0): Setting screen physical size to 423 x 238" is interesting. The resulting display is consistent with this.

I'd be really grateful for any useful suggestions. At present, my brand new laptop is essentially useless!

Hi,

I was having very same problem on my Dell Inspiron 17R.  The solution I use is on Ubuntu's certified hardware for Dell.  There is no exact model for my new Inspiron 17R, however using Ubuntu's 12.04 worked for me.  I do get correct colors and resolutions (not purple-green as before).  But, please note that even though all colors are displayed correctly and resolution is sharp, sometimes mouse pointer flickers a bit when you click on links  (has to do with HTML5? not sure).  And also you may not be able to adjust your display's settings (change refresh rate, brightness) it's just everything seems to default to correct specs without having any additional control over your graphics.

In short, I've found that any distribution with kernel <= 3.2 works on my Dell Inspiron 17R.  I decided to stay with Ubuntu because it also worked with my wireless (another issue you might experience as we seem to have the same model).  But that's for another thread ;)

All the best,
Victor.

---

### Post by GandalfTheNerd on 2014-04-12
This has been filed as a bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1300349]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1300349") by the fellow who wrote [http://askubuntu.com/questions/440597/dell-inspiron-17r-5737-ubuntu-13-10-terrible-video]("http://askubuntu.com/questions/440597/dell-inspiron-17r-5737-ubuntu-13-10-terrible-video"). I might give the "nomodeset" solution a go, but I gather from [http://askubuntu.com/questions/207175/what-does-nomodeset-do]("http://askubuntu.com/questions/207175/what-does-nomodeset-do") it might hurt the graphics performance a lot.

It might lend some weight to this issue if those affected all hit the "this bug affects" on the bug report. Doubtless anyone with information on how to fix this would no doubt help too!

---

### Post by mrichards on 2014-04-17
Well, I upgraded to 14.04 today..
 Now Ubuntu only detects one screen resolution 1024x768.

Any ideas?

---

### Post by mrichards on 2014-04-20
fyi, I was able to boot a clean installation of 14.04 with nomodeset using secureboot (not legacy boot). 
This seems to have resolved the issue for now.

---

### Post by GandalfTheNerd on 2014-05-05
I did try nomodeset on my current build with no luck. However, according to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1300349](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1300349), kernal "v3.15-rc2-trusty" works. So it seems there is a permanent fix "upstream", and all we have to do is wait.

---

### Post by oldfred on 2014-05-05
I have never installed a newer kernel, but you can. Using ppa is easiest.

[http://ubuntuforums.org/showthread.php?t=2222066](http://ubuntuforums.org/showthread.php?t=2222066)

But you may also need other drivers and parts of userspace drivers.
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY](http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY)

---

### Post by GandalfTheNerd on 2014-05-05
Thanks, OldFred. I did consider that, but I'm just not brave enough at the moment. The machine is in daily use as my computing platform and I don't want to try anything that might break something else. At the moment it runs perfectly on an external monitor. If I had a bit more time just now I'd probably try it anyway!

---

### Post by mrichards on 2014-05-05
I took the plunge and installed v3.15-rc2-trusty ppa kernel
This has resolved the issue for me, I no longer need the nomodeset option in grub..
Though I'm not able to alter the backlight level it seems (even when using acpi_backlight=vendor).

---

### Post by victor_sk on 2014-05-06
> **mrichards said:**
> I took the plunge and installed v3.15-rc2-trusty ppa kernel
This has resolved the issue for me, I no longer need the nomodeset option in grub..
Though I'm not able to alter the backlight level it seems (even when using acpi_backlight=vendor).

I would also confirm that kernel 3.15-rc2 with my Ubuntu 12.04 installation works well with my Dell 17R 5737 model.  I then used Debian's intel-linux-graphics-installer to optimize the driver.  I originally had "Distribution not supported" error since mine was 12.04 (Dell certified), so I edited /etc/lsb-release and indicated:

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.10
DISTRIB_CODENAME=saucy
DISTRIB_DESCRIPTION="Ubuntu 13.10 LTS"

```

After that it was a matter of adjusting screen resolution and everything worked beautifully :)  For me, this is most optimal solution in Ubuntu :)

Cheers,
Victor.

---

### Post by GandalfTheNerd on 2014-05-10
I took the plunge too and installed linux-image-3.15.0-031500rc2-generic_3.15.0-031500rc2.201404201435_amd64.deb from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc2-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc2-trusty/). You can do this simply by double-clicking on the downloaded file. After a reboot, you can check the version running with "uname -r", which in my case now gives "3.15.0-031500rc2-generic".

The built-in display now works perfectly, and I have marked the thread solved. Thanks for your help everyone!

---

### Post by GandalfTheNerd on 2015-04-24
I can confirm that this works "out of the box" with 15.04!

---

