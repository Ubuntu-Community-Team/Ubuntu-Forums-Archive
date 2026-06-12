---
title: "Wireless Power Management off in 12.04?"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by whoppr on 2013-01-20
Hi...

I am trying to disable power management for my wireless in 12.04.  On restart I have been able to shut this off by adding the commands to rc.local.

This works great until the device is restarted or disconnect/reconnects.

I have tried adding the following line to /etc/pm/power.d/wireless

/sbin/iwconfig wlan0 power off

It does not work.  Has anyone encountered this as well and has somebody gotten this to work?  

Thanks

---

### Post by tgalati4 on 2013-01-20
Why do you need to disable power management on the wireless card?

Do any of these commands work:

 Examples :
                   iwconfig eth0 power period 2
                   iwconfig eth0 power 500m unicast
                   iwconfig eth0 power timeout 300u all
                   iwconfig eth0 power saving 3
                   iwconfig eth0 power off
                   iwconfig eth0 power min period 2 power max period 4

Subsitute eth0 for your wireless device (perhaps wlan0).

Do you have the correct setting in BIOS to allow applications or hot keys (FN+F2) or both to control wireless power?

---

### Post by whoppr on 2013-01-21
> **tgalati4 said:**
> Why do you need to disable power management on the wireless card?

Do any of these commands work:

 Examples :
                   iwconfig eth0 power period 2
                   iwconfig eth0 power 500m unicast
                   iwconfig eth0 power timeout 300u all
                   iwconfig eth0 power saving 3
                   iwconfig eth0 power off
                   iwconfig eth0 power min period 2 power max period 4

Subsitute eth0 for your wireless device (perhaps wlan0).

Do you have the correct setting in BIOS to allow applications or hot keys (FN+F2) or both to control wireless power?

"iwconfig wlan0 power off"  works.  It has and have done so manually  several times.  The reason for my question is not because I cannot shut  it off manually but rather how to shut it off if the interface re-inits.   For example, if I unplug the USB and plug it back in, it will come  back up, but power management will come on even if I have shut it off  manually.

To answer your question, why I want to shut it off, it is because I am  having issues with the rt2800 driver with it on.  I have read this is  common as others have reported here:

[http://ubuntuforums.org/showthread.php?t=1974933](http://ubuntuforums.org/showthread.php?t=1974933)

If I leave power management on the connection is slow and constantly goes up/down.

The larger issue is I have an AE1000, it has the Ralink rt3572, and it  does not work well.  I have tried compiling the older driver as others  have done, but it did not work well for me.  Eventually it hangs the  machine or hoses the wireless unless I reboot.  Sometimes I cannot even  issue any root command.  I used the pre-edited files from ConfigNewton  as mentioned in the same thread above.  This worked well in 11.04 but  for some reason 12.04, it does not.

I have tried adding the iwconfig wlan0 power off to /etc/pm/power.d/wireless file but I guess when the AE1000 tries to re-establish a connection after going down, this file is not executed.

Thanks

---

### Post by tgalati4 on 2013-01-21
Now you know why I asked the question.  You followup post contained a lot of detail that was missing in the original post.  When you unplug a USB dongle, a lot of stuff happens behind the scenes (hotplug now udev).  That coupled with a crappy wireless driver will make the situation difficult.  Perhaps you can put in some "magic" commands (such as:   iwconfig wlan0 power off) in the udev rules to help set the USB dongle into the proper mode when inserted.  There are wiki's on how to add to udev rules.

Also remember whenever you update the kernel, you will have to recompile the driver since the driver is specific to the version of the kernel that you complile it under.
Hint:  don't update the kernel unless you absolutely have to.

If you can't get your dongle to work correctly, then I would look for another dongle that is more compatible and has a better driver for it.  It's also possible that your dongle has some damage.  USB dongles suffer from bending and cold solder junctions which can cause erratic behavior.

Does this machine dual-boot into Windows?  If so, then does the wireless work OK, at full speed?  And does it keep it's connection for several hours?

If you have problems in windows as well, then I would suspect a hardware problem and get a different dongle.

---

### Post by whoppr on 2013-01-23
> **tgalati4 said:**
> Now you know why I asked the question.  You followup post contained a lot of detail that was missing in the original post.  When you unplug a USB dongle, a lot of stuff happens behind the scenes (hotplug now udev).  That coupled with a crappy wireless driver will make the situation difficult.  Perhaps you can put in some "magic" commands (such as:   iwconfig wlan0 power off) in the udev rules to help set the USB dongle into the proper mode when inserted.  There are wiki's on how to add to udev rules.

Also remember whenever you update the kernel, you will have to recompile the driver since the driver is specific to the version of the kernel that you complile it under.
Hint:  don't update the kernel unless you absolutely have to.

If you can't get your dongle to work correctly, then I would look for another dongle that is more compatible and has a better driver for it.  It's also possible that your dongle has some damage.  USB dongles suffer from bending and cold solder junctions which can cause erratic behavior.

Does this machine dual-boot into Windows?  If so, then does the wireless work OK, at full speed?  And does it keep it's connection for several hours?

If you have problems in windows as well, then I would suspect a hardware problem and get a different dongle.

Thanks for the response.  It is dual boot but not to windows.  HTPC with different versions of Ubuntu.  I cannot say for sure that it is not a hardware problem, but it seems to work OK in 11.04.  If it is a hardware problem it is new.  Maybe I need to either run it longer in 11.04 or run it with a Live Distro like UBCD, backtrack or Knoppix for quite a while.

By unplugging and replugging I was simply trying to mimic if the adapter lost connection because this would run for 1-2 days and after manually turning off the power management, it turn back on.  Im probably not approaching it in the best way.

I tried several things starting with what worked in 11.04 which was compile the rt3572 driver.   I havent had the success as others have had for some reason.  Machine becomes unstable and have to reboot and even prevents root commands from executing.  When using the rt3572, I blacklist the rt2800 drivers at this point so there isnt a conflict.  The rt2870 even straight out of the Ubuntu repository seems to work well except when power management is on which is the reason for my question.

Apologies for the lack of detail, I didnt want to confuse things too much since I tried a lot already and got to the point where things were working except keeping the power management off.  Last thing to try would be to try a re-image and use rt3572 drivers in case I fouled something up and because others have had good luck.

I will try your suggestions and thanks again for all the help

---

### Post by aliqasemi on 2013-08-19
I ran these two commands,  which solved my problem, hopefully it will not comeback again:
sudo iwpriv ra0 set ATE=TXCONT
sudo iwpriv ra0 set ATETXPOW0=20
sudo iwpriv ra0 set ATETXPOW1=20

 It is a while since I am having issues with my wireless speed. Recently I compiled and installed the rt2860 driver for my rt3090 card, which  solved the speed problem, but the problem kept coming back after wake-up  from suspend. It seems that the commands above, taken from a file named sta_ate_iwpriv_usage.txt, solved my suspend problem. They turn power management off.  From the commands you can see that I have ATE enabled, which I did after reading thousands of forums :mad:, and I don't (and don't want to!) know what it is.

---

