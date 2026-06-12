---
title: "Much needed help before a reload."
date: 2010-11-26
forum: Multimedia Software
---

### Post by search66 on 2010-11-26
Running 10.10... I've really screwed up my video settings, etc. somehow and have made multiple posts to the forums requesting help; and no one has responded.

So... This is my last ditch effort before I have to reload the OS.

There is a problem with my nvidia driver and the kernel.  Right now, I'm 'working' but not optimally.  I have a GTX280 as well as a 8600GT (tried both)... When I upgraded the kernel yesterday, it won't boot to Gnome; it will simply boot to command line.

If I boot to the older kernel; it boots fine (but still not optimally)... I've tried reinstalling the nvidia drivers, etc... but I really think I've screwed things up more than actually helping.   Here's a screenshot of my 'additional drivers'.

So, what I'm looking for... Is how to basically wipe everything clean (video setting-wise) and have ubuntu autodetect my settings like it did on a fresh install.

Thanks so much for your help.

---

### Post by efflandt on 2010-11-26
How did you get 260.19.21?  Did you add x-swat ppa to your repositories or did you manually install something from nvidia?  In other words what shows as the version for nvidia-current in Synaptic?  I think it would normally show nvidia-current version as 260.19.12, but it would show 260.19.21 if you added x-swat.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```

I have been using x-swat.  Not sure if that updates automatically because when I noticed that they switched from 260.19.12 to 260.19.21, I just used Additional Drivers to remove nvidia, rebooted, activated nvidia, rebooted, and ended up with the new version.

So I don't know if you just need to remove, reboot, and reactivate nvidia in Hardware Drivers, or do something else to clean up whatever you did.

I have never had any trouble doing kernel updates with the x-swat ppa added.

I was using 260.19.21 for a GT 220 and am now using it for a GT 430 in maverick or natty development (which has that as default nvidia version).

---

### Post by search66 on 2010-11-26
I'll give it a shot... the 21 driver was from nvidia itself.

Thanks for the feedback; and Ill give it a shot.
> **efflandt said:**
> How did you get 260.19.21?  Did you add x-swat ppa to your repositories or did you manually install something from nvidia?  In other words what shows as the version for nvidia-current in Synaptic?  I think it would normally show nvidia-current version as 260.19.12, but it would show 260.19.21 if you added x-swat.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```

I have been using x-swat.  Not sure if that updates automatically because when I noticed that they switched from 260.19.12 to 260.19.21, I just used Additional Drivers to remove nvidia, rebooted, activated nvidia, rebooted, and ended up with the new version.

So I don't know if you just need to remove, reboot, and reactivate nvidia in Hardware Drivers, or do something else to clean up whatever you did.

I have never had any trouble doing kernel updates with the x-swat ppa added.

I was using 260.19.21 for a GT 220 and am now using it for a GT 430 in maverick or natty development (which has that as default nvidia version).

---

### Post by search66 on 2010-11-26
Well... I've tried this, and now I'm getting the following...

I've Googled my butt off for the last two-weeks, and am about to tear my hair out... wait... I'm bald.

---

