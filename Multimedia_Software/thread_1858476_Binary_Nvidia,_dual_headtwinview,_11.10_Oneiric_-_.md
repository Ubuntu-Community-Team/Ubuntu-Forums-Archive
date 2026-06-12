---
title: "Binary Nvidia, dual head/twinview, 11.10 Oneiric - not working"
date: 2011-10-12
forum: Multimedia Software
---

### Post by cmdln on 2011-10-12
After updating to 11.10 the binary nvidia driver no longer wants to do dual head (two external) with my laptop dock.

I have a Lenovo W520 with a Quadro 2000M (there is an intel gpu also, but I have it set to discrete in the bios so only using the nvidia).

Before upgrading to 11.10 while docked I could select two external monitors and set the Resolution to OFF on the laptop display in Nvidia X Server Settings -> X Server Display Configuration.

Now (while I can still see the external monitors) I can only select one 
successfully. When I select twinview for the second the nvidia-settings gui stops responding and I see no errors on the console. It also fails any subsequent launches if I ctrl-c it.

I don't see any errors in the X log, not sure where I should expect to see any other errors.

I've tried both the nvidia-current and the nvidia-current-updates

---

### Post by wolfen69 on 2011-10-12
Did you upgrade or clean install?

---

### Post by cmdln on 2011-10-12
I did an upgrade.

I should also note that I can still dualhead with one external monitor and the laptop screen. I am just not able to disable the laptop screen and do two external monitors as I was able to do previously.

---

### Post by jgruber on 2011-10-13
Same here.  Dell Latitude E6410.. Nvidia GT218.

---

### Post by cmdln on 2011-10-13
> **jgruber said:**
> Same here.  Dell Latitude E6410.. Nvidia GT218.

Just to clarify, you can dualhead with one external and the laptop display itself, but you cannot disable the laptop display and drive two external monitors?

You could do this before upgrading correct?

---

### Post by yoshi121212 on 2011-10-13
Probably. I know I could run my dual monitors just fine before the upgrade, and now while X thinks it has two monitors available for twinview (you can lose windows really easily this way), the card only outputs onto one of them. Serves me right for upgrading right away...

---

### Post by cmdln on 2011-10-13
> **yoshi121212 said:**
> Serves me right for upgrading right away...


Hey, someone has to find the bugs.

---

### Post by skitheo on 2011-10-14
Screens also garbled by NEW INSTALL of 11.10, nvidia-current or nvidia-current-updates trying to enable Twinview for multiple displays. GeForce GTS 450. Primary display is DFP connected via DVI, secondary is also an LCD connected via VGA/Analog cable. x86_64 version.

---

### Post by jmbarra78 on 2011-10-14
It doesn't work for me. I did a clean install and when I activated current-updated drivers, Twinview didn't work. I've two monitors (DVI and VGA conectors) and a nvidia GTX 550 TI

---

### Post by Levak on 2011-10-15
Same here. Twinview doesn't work :
> Failed to associate display device 'DELL P190S' with X screen 0.  TwinView cannot be enabled with this combination of display devices.

QuadSLI 2*GTX295

The two screens are on the same graphic card, if I change one o another, it won't detect the display anymore (before, it does).

---

### Post by psypher on 2011-10-15
This could be related to this bug as I am having similar issues.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/813343](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/813343)

---

### Post by cmdln on 2011-10-18
> **psypher said:**
> This could be related to this bug as I am having similar issues.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/813343](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/813343)

Thats different from what I am seeing. I am running gnome-shell. I can get twinview working, but only with the laptop screen and one external montior. Setting the laptop monitor to Off and trying to add two external monitors to twinview locks up nvidia-settings.

---

### Post by AzN1337c0d3r on 2011-10-18
Quadro 6000 + 2x U3011 (One on displayport, the other on DVI). Enabling Twinview results in half a screen displayed on each monitor as well as corruption.

---

### Post by wpichler on 2011-10-24
hi all,

i do have the same problem here - also a laptop with nVidia Corporation G84M [Quadro FX 570M] - when i try to attach two external displays (one using dfp - one using crt) then nvidia-settings does hang when i activate dual view in the program. I have also tested the latest fedora core 16 - with propertiary nvidia driver - same problem there. So it seems to be a problem specific to a xserver / nvidia version... Configuring it with sperate x screen does work.

---

### Post by tharsan on 2011-10-24
I'm experiencing the same issue on a clean install of 11.10. Previously on Natty, I would use nvidia-settings to setup both external displays (and disable the laptop display) manually every time I booted.

Now, when selecting TwinView for the second display, the nvidia-settings app hangs and does not launch again until the X server reboots. I can select (and use) TwinView on the first display.

I removed the proprietary driver in favour of nouveau, and using the Displays application, I can configure the second monitor. However, when I try to Apply those changes, the second monitor still does not receive any signal but Ubuntu and the Displays application seem to think everything is fine.

Tharsan

---

### Post by cmdln on 2011-10-25
I went ahead and posted on the nvidia forms as well.
[http://forums.nvidia.com/index.php?showtopic=213799](http://forums.nvidia.com/index.php?showtopic=213799)

Looks like several people have slightly different issues with 11.10 and the nvidia driver.

---

### Post by blausand on 2011-12-15
Similar problem with nvidia 280GTX in a Guru Laptop after upgrade to 11.10
Internal LCD works fine,
connecting external monitor it won't be detected,
nvidia-settings stderrs a lot like
[COLOR="Navy"] (nvidia-settings:2819): Gtk-WARNING **: Im Modulpfad »pixmap« konnte keine Themen-Engine gefunden werden,[/COLOR]
and esecially
[COLOR="Navy"]Traceback (most recent call last):
  File "/usr/share/screen-resolution-extra/nvidia-polkit.py", line 75, in <module>
    operation_status = main(options)
  File "/usr/share/screen-resolution-extra/nvidia-polkit.py", line 51, in main
    exit_code = conf.backupAndWriteXorgConf([options.backup_filename, options.filename])
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 143, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 630, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: com.ubuntu.screenresolution.Mechanism.AccessDeniedException: com.ubuntu.screenresolution.mechanism.configure[/COLOR]

Rebooting with the external monitor, however, allows for detecting it and saving into the xconfig file. But after reboot, the internal monitoris gone and the resolution of the external one can't be adjusted to the correct (high) values.

So far, i can choose to use the internal or the external with lower resolution.

<OT>[COLOR="DarkGreen"]Has anybody ever wondered why error dialogues can't be text-selected? Seems very stupid to me.[/COLOR]</OT>

---

