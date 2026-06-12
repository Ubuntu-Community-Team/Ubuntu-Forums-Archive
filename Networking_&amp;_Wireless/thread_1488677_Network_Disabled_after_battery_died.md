---
title: "Network Disabled after battery died"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by Alan McNea on 2010-05-20
Hello all,

  Today I fell asleep with my laptop on and not connected to the A/C power.  Well, my battery power eventually ran out and the computer did whatever it does in such a situation.  I don't know if it realized it was running low and turned off or just turned off due to running out of power.  Anyways when I plugged it in and turned the laptop back on the Network Manager icon in the panel bar said Network Disabled.  So, I tried to establish a connection manually using iwconfig to set the essid of my wireless network.  After issuing the command "iwconfig wlan0 essid dlink" iwconfig would show the essid as a string of backslashes with hex codes or something really weird like that.  I tried "ifconfig wlan0 down/up" and a few other things to no avail.  I couldn't find any errors in dmesg or anything.  I then booted into windows and tried searching the forums to no avail (my wireless card was working in windows).  I then had the idea of switching off the wireless card while booting up (using the physical switch on the computer).  After booting into ubuntu I then switched the wireless card back on.  The Network Manager then recognized my card and everything returned to normal.  I don't really know what the problem was but it is fixed now.  I just thought I would report my experience since I couldn't find any info on it and someone else might have a similar problem.

Info:
Computer: Lenovo Thinkpad T61
Wireless Card: Intel 4965AGN
OS: Ubuntu 10.04 LTS (Lucid Lynx)

I also have dhcpd running on my ethernet port (eth0).  I don't know if that would contribute.

---

### Post by puppywhacker on 2010-05-20
I had the same experience in ubuntu 9.10 with a DELL laptop once where "rfkill" reported that the wifi killswitch was set to "wifi disabled" no matter which position it physically was in, for me it turned out that the module dell_laptop should be blacklisted.

In your case it sounds more that your wifi was put to sleepmode, just like it's master =)

---

### Post by SaintDanBert on 2010-05-20
There is a configuration setting *that I can never find when I want it but I know it is there* that will turn off your wifi (and other) radio when battery power is critical.  This is distinct from whatever suspend-to-ram or suspend-to-disk that might happen under low battery conditions.

I suspect that things activate **radio off** followed by **suspend**.  Suspend saves the current state ... including the
radio off details.  When you wake from suspend, you recover the saved
state ... including radio off details.  Now you must turn on your
radio so that wifi (and other) radio will work again.

My laptop has a mechanical button that controls the radio. If I cycle
that button off then on, whatever dance happens to turn everything on again regardless of how they were turned off. YMMV.

Cheers,
~~~ 0;-Dan

~~~ 0;-Dan

---

