---
title: "Very creative BCM4312 issues, please help!"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by adempewolff on 2010-01-27
Unlike most people with wireless problems, my wireless appears to work fine, it starts up on a boot, still works after suspend/resume, works with WEP and WPA, etc.

My problem though is that my computer is plagued by kernel panics, ranging from once every other day or as much as once every couple minutes.  I suspect my wireless driver is the problem for three reasons:

1. To the best of my memory the panics only happen when wireless is enabled.
2. The panics happen more frequently the more the wireless connection is being utilized (the panics every couple minutes happened when I was using transmission to download large torrents, they continued, albeit every 5-10 minutes when I put a speed limit on the download)
3. The wireless driver is the only thing I can think of that would be in kernel space every time I've had a panic.

My computer is a Dell Latitude D630.  The wireless controller is the Broadcom Corporation BCM4312 802.11a/b/g (rev 01).  I had previously been using the Broadcom STA driver in the ubuntu repos (bcmwl-kernel-source).  I'm using network manager but I don't think that is anywhere near kernel space.

I finally decided to try and fix my problem by compiling the newest bcmwl driver (5.10.91.9.3) from source ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)).  However I seemed to fudge up the process, and now, not only do I still have the panics but my networking modules are all in a bungle.

The build process went smoothly until I got to these instructions:

```
3: Remove any other drivers for the Broadcom wireless.

There are several open source drivers that are used to drive Broadcom 802.11
chips such as b43 and ssb. If any of these are present they need to be removed before this 
driver can be installed.  Any previous revisions of the wl driver also need to
be removed.

# lsmod  | grep "b43\|ssb\|wl"

If any of these are installed, remove them:
# rmmod b43
# rmmod ssb
# rmmod wl

To blacklist these drivers and prevent them from loading in the future:
# echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
# echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf

4: Insmod the driver.

If you were already running a previous version of wl, you'll want to provide a
clean transition from the older driver. (The path to previous driver is usually
/lib/modules/<kernel-version>/kernel/net/wireless)

# rmmod wl 
# mv <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig
# cp wl.ko <path-to-prev-driver>/wl.ko
# depmod
# modprobe wl

Otherwise, if you have not previously installed a wl driver do this:

# modprobe lib80211
# insmod wl.ko

wl.ko is now operational.  It may take several seconds for the Network Manager
to notice a new network driver has been installed and show the surrounding
wireless networks.

```

Long story short, I was not able to tell whether the old wl modules was still around.  I was not able to find it in /lib/modules/2.6.31.17-generic/kernel/net/wireless/ and systemwide searches for it revealed nothing.

So I just copied the newly compiled wl.ko into that directory and added it which appeared to work.

Problem is, next time I restarted, the wireless wasn't working and "lsmod  | grep "b43\|ssb\|wl" revealed a whole slurry of modules it hadn't before, including both b43 and ssb, but not wl!

So I rmmoded both b43 and ssb and then loaded lib80211 and wl.ko and the wireless worked again.  For good measure I blacklisted b43 and ssb so they wouldn't load on the next restart.

I then tried to test to see if my panics were fixed and booted transmission to see how long it would work for, it paniced after 5 minutes or so.  So either the newest STA driver doesn't fix the problem, or I didn't correctly install the newest one.

Things got even worse when I rebooted from the panic.  Not only was the wireless not working but wired networking was also disabled.  I unblacklisted b43 and ssb and then restarted.

Now networking worked again but the wireless said "device not ready" in the nm-applet.  So I rmmodded b43, which made the wireless option in the nm-applet disappear.  Then I rmmodded ssb.  Then I did modprobe lib80211 and modprobe wl and voila, wireless comes online.

I cannot for the life of me figure out why b43 and ssb were not used before, but not blacklisting them completely disables wireless.  Furthermore, I can't figure out why wl.ko is not loaded on boot.

I would appreciate any insights people might have over where I've messed things up and where to go from here. I have a feeling though that this might be a good time to call things quits and do a fresh install...

Love Ubuntu, but these frequent undiagnosable crashes are starting to get old.  Not bad enough to use Windows, but maybe some other distro plays nicer with my setup!

---

### Post by northd_tech on 2010-02-20
It sounds to me like you are missing some source header files.  Have you tried re-compiling the Broadcom driver after entering this command?

```
sudo depmod -a
```

There should be a readme.txt at Broadcom's website that gives very specific instructions, and I remember it working flawlessly with my 4321AG Broadcom under Jaunty 9.04.

---

