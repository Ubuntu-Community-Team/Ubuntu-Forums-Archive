---
title: "Help resetting default graphics / video driver"
date: 2010-01-02
forum: Mythbuntu
---

### Post by the_pod on 2010-01-02
Hello folks.  I've officially killed my display and need some help, please.

Last night I did an update on the Mythbox just to get standard updates.  Am running 9.04, 32b version.  Everything was working pretty well so in retrospect this was a bad idea.

After the updates and the requisite restart I can't see squat on my screen.  As info, the system runs an ATI 3200 graphics chip and had worked well with the restricted drivers in the repos.  The TV is 1080.

After the update the TV reaches the 720 level and then completely craps out.  Basically it's trying to load and the video isn't talking nicely to the TV so the display is unable to load correctly.  Dropping to Recovery mode is usable so I can only assume it is driver-related.

This actually happened once before (probably why I turned off the updates) but I cannot recall how I fixed it.  I've been searching for an hour and have tried various combinations of:

```

sudo apt-get remove fglrx

sudo dpkg-reconfigure -p high xserver-xorg

sudp dpkg--reconfigure xserver-xorg

sudp apt-get remove --purge xorg-driver-fglrx

rm ~/.config/monitors.xml

```

If someone could help I would truly appreciate it.

If memory serves, when I solved this in the past I (1) restored to "factory settings" so I could use my TV as video, then (2) went through the standard channels to enable ATI restricted driver.

Thanks!

---

### Post by the_pod on 2010-01-02
As info, am getting a message that says:  "Cannot open display: " when working from the Shell in recovery mode.

---

### Post by vandorjw on 2010-01-02
I assume you have already tried to re-run the installation package for the restricted ATI driver?

you said you have the ATI 3200, I assume that is the ATI Radeon HD3200?

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

So I am going to assume this is the driver you are using.

I also don't think it matters to much if you have 1000's of drivers on your system. If you still use xorg.conf you can specify which driver you wish to use.

Hope this helps, if it doesn't let me know what I am not understanding.

Cheers CC7gir

---

### Post by the_pod on 2010-01-02
> **cc7gir said:**
> I assume you have already tried to re-run the installation package for the restricted ATI driver?

you said you have the ATI 3200, I assume that is the ATI Radeon HD3200?

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

So I am going to assume this is the driver you are using.

I also don't think it matters to much if you have 1000's of drivers on your system. If you still use xorg.conf you can specify which driver you wish to use.

Hope this helps, if it doesn't let me know what I am not understanding.

Cheers CC7gir

Thanks for the help. How do I run / re-install the restricted drivers from the command line?  I get lost when not in a GUI environment (shame).

---

