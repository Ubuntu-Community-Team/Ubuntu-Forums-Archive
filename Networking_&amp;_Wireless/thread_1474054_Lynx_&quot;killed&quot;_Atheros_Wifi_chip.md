---
title: "Lynx &quot;killed&quot; Atheros Wifi chip"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by ErikMil on 2010-05-05
Hi everybody,

I know it sounds absurd, but :

I installed 10.04 on may 2nd as second OS (dual boot with vista).
Wifi (atheros AR 5001) was running like charm. 

Than all in a sudden it stopped working, meaning I can't see any hotspots as well in lynx and vista...

I rebooted with the 10.04 live cd and it worked again.

Now it stopped working again on both OS and it will not restart neither under Vista nor Lynx or Lynx Live-CD. Even Koala Live didn't work...

Anyone a idea what happend and how to fix it?

What do you need pasted here?

Thanks a lot for your help,

Erik

---

### Post by tgalati4 on 2010-05-05
Boot the Live CD.  Open firefox and load a page (if your card works temporarily).

Your card could be overheating causing it to lockup.

Open a terminal

dmesg | tail -50

What kind of machine?

---

### Post by ErikMil on 2010-05-05
Hi tgalati4,

thanks for your fast reply.

Unfortunately the wifi isn't even working temporarily, so even booting with liveCD doens't help.

result of dmesg | tail -50 

```
[18443.610705] ath5k phy0: gain calibration timeout (2412MHz)
[18444.000794] ath5k phy0: gain calibration timeout (2417MHz)
[18444.394680] ath5k phy0: gain calibration timeout (2422MHz)
[18444.792705] ath5k phy0: gain calibration timeout (2427MHz)
[18445.177332] ath5k phy0: gain calibration timeout (2432MHz)
[18445.561432] ath5k phy0: gain calibration timeout (2437MHz)
[18445.959752] ath5k phy0: gain calibration timeout (2442MHz)
[18446.356389] ath5k phy0: gain calibration timeout (2447MHz)
[18446.750180] ath5k phy0: gain calibration timeout (2452MHz)
[18447.131620] ath5k phy0: gain calibration timeout (2457MHz)
[18503.612165] __ratelimit: 4 callbacks suppressed
```

:( Erik

---

### Post by tgalati4 on 2010-05-06
Sounds like your reciever went out since it can't calibrate a signal on any "g" frequency.  This could be an electronic problem or it could be an antenna wire problem.  How old is the laptop and what make and model?  Sometimes the wireless card needs to be reseated.  Any panels on the bottom side?

Sometimes you can reset the digital tuner in a card by removing the battery from the laptop.  Keep it unplugged.  Press the power button to release any energy in the capacitors.  Let it sit overnight without the battery.

Put it back together and cross your fingers.

---

### Post by ErikMil on 2010-05-06
Hi tgalati4,

you are now officially my personal hero....

I did as you suggested and wifi now works like a charme.
\\:D/ =D>

Thanks a lot,

Erik

---

### Post by tgalati4 on 2010-05-06
Many hardware problems look like software problems.  Dmesg is your friend.  Any entry that you don't understand, just google it.  It could save you some time.

Welcome back to the web. 

How do you like Vista?

---

### Post by ErikMil on 2010-05-06
Hi,

I did google about 10.04 and atheros probs, but of course not the dmesg result.... 

Vista... well, let me say it like this, at least, it does the job of operating a computer. It is ok, some annoying things, but not too bad. I liked XP more. :)

There are some advantages for the windows OS (like hardware drivers from the vendors (e.g. printers, scanner etc.) or games that don't come for Linux etc.) but ubuntu is getting closer every day.

For working ubuntu simply rocks. I don't need vista anymore, it's just as a fallback on my HD.

:) Erik

---

### Post by tgalati4 on 2010-05-06
I haven't used Windows since 6.06 (June 2006) so I have to check in every now and then to see what's new.  I guess Windows 7 was my idea.

---

### Post by ErikMil on 2010-05-07
Well, I never used 7, but read a lot good things about it. Even from guys how are not the MS friendliest.

Maybe I should give it a try someday, just for fun.

But my heart stays somehow with linux and ubuntu.

:) Erik

---

### Post by ErikMil on 2010-05-08
Well, that's weired.... 

I had the same issue again, just a couple of minutes ago.

Could solve it with the same trick as above mentioned, but I'm getting a bit irritated.
It would be a very rare coincidence, that this occurs just when I installed lynx.

Is there any possibility to make a wifi chip being out of sync just through software?

:) Erik

---

### Post by El_Perro_Perduto on 2010-05-24
Having similar problems with my wireless card.  Presumably it is an atheros card. The wireless network is detected and then around 10 minutes later it drops the connection.

[  139.918814] ath5k phy0: gain calibration timeout (2447MHz)
[  140.302027] ath5k phy0: gain calibration timeout (2452MHz)
[  140.704899] ath5k phy0: gain calibration timeout (2457MHz)
[  146.634471] __ratelimit: 2 callbacks suppressed 
....
[  177.292060] ath5k phy0: gain calibration timeout (2442MHz)
[  177.696221] ath5k phy0: gain calibration timeout (2447MHz)
[  178.084817] ath5k phy0: gain calibration timeout (2452MHz)
[  178.471861] ath5k phy0: gain calibration timeout (2457MHz)
[  184.385390] __ratelimit: 2 callbacks suppressed
[  184.385400] ath5k phy0: gain calibration timeout (2412MHz)
[  184.744294] ath5k phy0: gain calibration timeout (2412MHz)

I tried the work around by editing the /etc/NetworkManager/nm-system-settings.conf and changed all the managed values from false to true and added a few new ones.  This still doesn't help.
Also reinstalled the linux wireless kernel headers from the latest version (I don't remember which).  Today, tried to power up my wireless card and ....bupkess...using the hard wire connection which works. 
Any suggestions?

---

### Post by Cabalbl4 on 2010-06-08
I spent a lot of time with that problem after upgrade to lucid from karmic. When my Toshiba Satellite is powered on without ac charge this problem appears until reboot with battery disconnect. It renders laptop wlan unusable on battery power.

Trying to install latest atheros (ath5k) drivers from repos - failure (problem persists) (kernel 2.6.31 - 2.6.32)
Trying to build latest stable drivers from source ([http://linuxwireless.org/](http://linuxwireless.org/)) - failure (Tried all builds avaliable there at the moment in compat section) 
(problem persists)(kernel 2.6.31 - 2.6.32)
Trying to upgrade kernel (2.6.34 and 2.6.35rc) - failure (problem persists)
Trying to build driver on upgraded kernel  - failure (problem persists)
Trying to install a fresh installation of lucid (formating partition with upgraded version and installing lucid from scratch) -  failure (problem persists) (kernel 2.6.31 - 2.6.32)
Trying to force kernel downgrade to 2.6.31-rt (as a last hope) - success! Problem disappeared at generic driver with no need to build anything more.

Conclusion - 100% 2.6.32 and higher kernel issue.

Damn. Lucid is driving me nuts...

---

### Post by fransfrans on 2010-06-11
I'm having exactly the same problem. The problem was there already on lucid alpha version (at least alpha 2). 
I am having an AR5007EG wireless adapter, but lspci sais:

Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

I have tried installing the backports modules, but nothing helps. Wireless was perfect in Karmic, but not in Lucid. About 1 out of 3 times it gives this warning and a reboot doesn't even help in that case. I really have to turn off my laptop when the calibration timeout occurs.

Here's my dmesg

---

### Post by Cabalbl4 on 2010-06-11
> **fransfrans said:**
> I'm having exactly the same problem. The problem was there already on lucid alpha version (at least alpha 2). 

Like I already said, install an older kernel (for example  2.6.31-10-rt) from synaptic.
It works by me.

---

### Post by BinaryMn on 2010-07-14
I'm also experiencing this problem and downgrading to 2.6.31 right now.

Has anyone filed a bug report upstream about this regression?

---

### Post by Cabalbl4 on 2010-07-15
> **BinaryMn said:**
> 
Has anyone filed a bug report upstream about this regression?
Yep. [Here at the launchpad.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269253?comments=all")

---

### Post by ErikMil on 2010-09-03
Hi again,

I still have the same issue and now a different output from dmesg | tail -50:


```
erik@Chr0m3:~$ dmesg | tail -50
[    8.874916]  (Note that use of the override may cause unknown side effects.)
[    8.874939] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    9.178506] Console: switching to colour frame buffer device 80x30
[    9.578859] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 16
[    9.578867]   alloc irq_desc for 16 on node 0
[    9.578869]   alloc kstat_irqs on node 0
[    9.578881] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 16 (level, low) -> IRQ 16
[    9.578886] hda_intel: Disable MSI for Nvidia chipset
[    9.578926] HDA Intel 0000:00:07.0: setting latency timer to 64
[   11.350719] type=1505 audit(1283544942.270:5):  operation="profile_load" pid=766 name="/usr/share/gdm/guest-session/Xsession"
[   11.352800] type=1505 audit(1283544942.270:6):  operation="profile_replace" pid=771 name="/sbin/dhclient3"
[   11.353099] type=1505 audit(1283544942.270:7):  operation="profile_replace" pid=771 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.353269] type=1505 audit(1283544942.270:8):  operation="profile_replace" pid=771 name="/usr/lib/connman/scripts/dhclient-script"
[   11.420136] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input9
[   11.752319] type=1505 audit(1283544942.670:9):  operation="profile_load" pid=772 name="/usr/bin/evince"
[   11.756024] type=1505 audit(1283544942.670:10):  operation="profile_load" pid=772 name="/usr/bin/evince-previewer"
[   11.758351] type=1505 audit(1283544942.670:11):  operation="profile_load" pid=772 name="/usr/bin/evince-thumbnailer"
[   12.005873] type=1505 audit(1283544942.920:12):  operation="profile_load" pid=786 name="/usr/lib/cups/backend/cups-pdf"
[   12.006240] type=1505 audit(1283544942.920:13):  operation="profile_load" pid=786 name="/usr/sbin/cupsd"
[   12.162170] type=1505 audit(1283544943.080:14):  operation="profile_load" pid=791 name="/usr/sbin/tcpdump"
[   13.665163]   alloc irq_desc for 28 on node 0
[   13.665168]   alloc kstat_irqs on node 0
[   13.665178] forcedeth 0000:00:0a.0: irq 28 for MSI/MSI-X
[   13.665383] eth0: no link during initialization.
[   13.666047] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.264435] ppdev: user-space parallel port driver
[   74.790062] hub 2-0:1.0: unable to enumerate USB device on port 4
[   75.110034] hub 4-0:1.0: unable to enumerate USB device on port 4
[   75.550040] hub 2-0:1.0: unable to enumerate USB device on port 4
[   75.970040] hub 4-0:1.0: unable to enumerate USB device on port 4
[   76.410042] hub 2-0:1.0: unable to enumerate USB device on port 4
[   76.830038] hub 4-0:1.0: unable to enumerate USB device on port 4
[   80.520048] Clocksource tsc unstable (delta = -71508593 ns)
[   88.879611] hub 4-0:1.0: unable to enumerate USB device on port 3
[   95.990136] usb 4-6: new low speed USB device using ohci_hcd and address 6
[   96.222007] usb 4-6: configuration #1 chosen from 1 choice
[   96.562083] usbcore: registered new interface driver hiddev
[   96.569627] input: MLK Wireless Desktop as /devices/pci0000:00/0000:00:04.0/usb4/4-6/4-6:1.0/input/input10
[   96.569894] generic-usb 0003:046A:0101.0001: input,hidraw0: USB HID v1.00 Keyboard [MLK Wireless Desktop] on usb-0000:00:04.0-6/input0
[   96.579427] input: MLK Wireless Desktop as /devices/pci0000:00/0000:00:04.0/usb4/4-6/4-6:1.1/input/input11
[   96.582718] generic-usb 0003:046A:0101.0002: input,hiddev96,hidraw1: USB HID v1.00 Mouse [MLK Wireless Desktop] on usb-0000:00:04.0-6/input1
[   96.584246] usbcore: registered new interface driver usbhid
[   96.584256] usbhid: v2.6:USB HID core driver
[  144.004670] lo: Disabled Privacy Extensions
[  206.912532] CE: hpet increasing min_delta_ns to 15000 nsec
[  244.424454] eth0: link up.
[  244.425275] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  255.360066] eth0: no IPv6 routers present
[  290.152862] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  303.898880] lo: Disabled Privacy Extensions

```

Could anybody explain me what happened here?

Oh, and by the way, turning off the laptop and removing the battery for a couple of hours doesn't work any more. Since the last time the wifi-Chip went off, I used a cable connection. Now I wnated to give it a try since there where some kernel updates, but nope.... chip is still off. I hope it didn't die at all....

Thanks a lot,

Erik

---

### Post by ErikMil on 2010-10-06
Hi everybody,

maybe my last post just was overseen. :)

Could anybody help me? 

Thanks,

Erik

---

### Post by Cabalbl4 on 2010-10-07
2 ErikMil

Have You tried kernel 2.6.31-rt or lower version? According to launchpad all kernels above 2.6.31 have issues with atheros :(

---

