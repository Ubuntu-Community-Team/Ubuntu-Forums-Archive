---
title: "Graphics problem, Nvidia GTX 570"
date: 2011-11-19
forum: Multimedia Software
---

### Post by clruwe on 2011-11-19
Hello dear community! I'm in Ubuntu 10.04 (dual boot Win 7) and for a while now I've been having serious graphic problems in Ubuntu.

It started a few months ago after an update. When I rebooted I got the "operating in Low Graphics mode" screen. So after searching the forums for a while I decided to just reinstall the driver, which I did manually after downloading it from Nvidia website. That worked for a while till the next update, when it happened again. This has been going on for a while now (not every time it updates, but often). But the last few re-installations are not doing the job... Everything is jumpy/jerky, I use dual monitors and if I'm doing something in one, then the other one just freezes and most games are unplayable, movies are jerky too. I know is not the hardware since I experience no problems on Win 7.

Things I've noticed: When I install the driver it finds some errors, things like etc/something does not exist. Unable to something, something... As you can see I'm not very good with computers, but I do know how to use a terminal! I read the forums often so I am able to follow instructions. 

The other thing perhaps worth mentioning is I tried installing XBMC and I get: Error XBMC need hardware accelerated OpenGL rendering. I have looked through Synaptic Package Manager and it says OpneGL is installed and it works if I start it from a terminal using sudo.

The card is an Nvidia GTX 570, the computer an Intel i7 with 24GB Ram.

Thank you in advance!

---

### Post by papibe on 2011-11-19
Hi clruwe.

Could you post the content of these two files:
```
/var/log/Xorg.0.log

/etc/X11/xorg.conf
```
Paste the content of the files separately  here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and post the links so we can take a look.

Regards.

---

### Post by clruwe on 2011-11-20
Hello papibe! Thank you for your reply, I forgot I had to subscribe to the thread to get alerts, oops! I have pasted the logs, not sure how the paste thing works exactly, but here is the address:

X.Org.0.log: [http://paste.ubuntu.com/744339/](http://paste.ubuntu.com/744339/)

xorg.conf: [http://paste.ubuntu.com/744340/](http://paste.ubuntu.com/744340/)

I hope this is the way to do it... Thanks again!

---

### Post by papibe on 2011-11-20
There is some inconsistencies between the refresh frequencies.

Your xorg.conf says:
```

    HorizSync       31.5 - 80.0
    VertRefresh     56.0 - 75.0

```
But the log shows that the driver finds that the freqs from your monitor don't match (50.0 Hz). This could be the reason that you are booting into low graphics.

I notice that you have 2 monitors, but you don't have 2 "monitor sections" on your xorg.conf. I'm guessing that is confusing the driver.

I have 2 monitors too (one Dell flat panel and an HDTV). I just check my conf file, and I have 2 monitor sections:
```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1907FP"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "SONY TV"
    HorizSync       15.0 - 70.0
    VertRefresh     58.0 - 62.0
    Option         "DPMS"
EndSection

```

Since I didn't put the those freqs myself, it means that the driver can recognize them and put it in there.

This is the method I would use to recreate a better config file.

First back up your config file (just in case):
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Unplug your analog monitor (CRT), and restart into safe mode, then choose boot normally so you can get into text mode. Log in and run:
```
sudo nvidia-xconfig
```
Restart normally to the GUI.

You should now get full resolution. Connect your analog monitor, and open the 'Nvidia X Server Settings' as root:
```
gksudo nvidia-settings
```
Press 'X Server Display Configuration' on the right, then on the left look for the analog monitor. If it doesn't appear press 'Detect Displays' (it has on).

Now configure both monitors as you need them.

Finally, save that actual configuration by pressing 'Save to X Configuration File'.

Restart, to test your configuration.

I hope that helps. Tell us how it goes.
Regards.

---

### Post by mörgæs on 2011-11-20
_C_hanged the thread title.
Please watch your language, Clruwe. 

[URL="http://ubuntuforums.org/member.php?u=1119223"]
[/URL]

---

### Post by clruwe on 2011-11-20
Thank you papibe! I did everything you suggested, but nothing's changed. After I finished the whole procedure I  checked the xorg.conf file and the refresh frequencies continue to be the same. I wonder if this has anything to do with the fact that I have the two monitors configured as twin view? Since they are different types of monitors maybe the driver is trying to find a common ground? Sorry if this sounds silly...

Just to make sure I did the right process:

1.- By "restart into safe mode" I presume you meant recovery mode? Because that's what I did.
2.- By "boot normally" I clicked where it said continue normal boot.
3.-By "restart normally" I presume you meant sudo /etc/init.d/gdm start

So I logged in, connected the monitor and gksudo the settings. The analog monitor started on its own and my old configuration was already present. 

I did an experiment earlier in the afternoon and started a game from terminal, just to see what it said was the problem. I got NVIDIA: could not open the device file /dev/nvidiactl (Permission denied). Don't know if this helps...

Basically if I run games from the terminal with sudo or gksudo they run perfectly well. Same goes for XBMC, if I sudo xbmc then it runs. If I don't and I try to run them from the menu or an icon then I get jumpy/jerky graphics and in the case of XBMC I get "XBMC needs hardware accelerated OpenGL rendering. Install an appropriate driver". But obviously I have the driver otherwise it wouldn't work with sudo... Right?

This computer used to have a different graphics card about six months ago, maybe there's some stuff left behind? I went through Synaptic and uninstalled everything that had the word ATI in it.... Don't know why, I've never had an ATI card...

Any ideas? Thank you for your time!

C.

PS: I don't think "gone to hell" is bad language, it's just an expression.

---

### Post by bcschmerker on 2011-11-20
> **clruwe said:**
> ...When I install the driver it finds some errors, things like etc/something does not exist. Unable to something, something....The other thing perhaps worth mentioning is I tried installing XBMC and I get: Error XBMC need hardware accelerated OpenGL rendering. I have looked through Synaptic Package Manager and it says OpneGL is installed and it works if I start it from a terminal using sudo.

The card is an Nvidia GTX 570, the computer an Intel i7 with 24GB Ram.

Thank you in advance!Ubuntu® already has a Package **nvidia-current** in the **Restricted** repository (accessible from Synaptic, provided that Restricted is enabled in the Repositories section), configured for correct operation in your particular release.  That's what I needed for a rebuild for KUbuntu® 10.04.4-LTS of an eMachines®/Acer® EL1210-09 with a second video display adapter, viz., an Asus® EN210/DI/512MD3(LP), in addition to a 500W Shuttle® PSU and a 500GB Western Digital® SATA hard drive; the unit already had a planar nVIDIA® GeForce® 8200 supported by an MCP78S chipset, and nvidia-current is required for simultaneous operation of the 8200 and 210 GPU's.

---

### Post by clruwe on 2011-11-20
> **bcschmerker said:**
> Ubuntu® already has a Package **nvidia-current** in the **Restricted** repository (accessible from Synaptic, provided that Restricted is enabled in the Repositories section), configured for correct operation in your particular release.  That's what I needed for a rebuild for KUbuntu® 10.04.4-LTS of an eMachines®/Acer® EL1210-09 with a second video display adapter, viz., an Asus® EN210/DI/512MD3(LP), in addition to a 500W Shuttle® PSU and a 500GB Western Digital® SATA hard drive; the unit already had a planar nVIDIA® GeForce® 8200 supported by an MCP78S chipset, and nvidia-current is required for simultaneous operation of the 8200 and 210 GPU's.

Thank you bcschmerker, I have to say I only understood a tenth of your reply... Heh, heh, heh! Sorry! However, I did check Synaptic for nvidia-current and it was already installed. To play it safe I renistalled, but I still have the same issue....

Why would OpenGL work in sudo but not on normal? Something must be blocked or in the wrong directory....? No?

I'm sorry, I don't really know what I'm talking about.

I appreciate your time.

C.

---

### Post by clruwe on 2011-11-20
OK, here is an update. I found  a page where someone was asking how tell if OpenGL is really working. The suggestion was glxinfo | grep '^direct rendering:'

I tried it and I got NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

So I tried the same command with sudo and I got: NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

Am I getting close? Is this perhaps the issue?

---

### Post by clruwe on 2011-11-20
OK, no more need to worry, found the solution here: [http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal](http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal)

I post it in case anybody else comes looking for it.

The lesson here is: don't download drivers from nvidia website!

Thank you all very much!

C.

---

### Post by mörgæs on 2011-11-21
In that case, please mark the thread 'solved'.

---

