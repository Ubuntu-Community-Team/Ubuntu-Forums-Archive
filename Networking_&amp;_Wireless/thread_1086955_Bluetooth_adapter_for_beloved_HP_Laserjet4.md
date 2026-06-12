---
title: "Bluetooth adapter for beloved HP Laserjet4"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by Saunter on 2009-03-04
I have a beloved old HP Laserjet4 which has worked flawlessly for the past 15 years and has a very low cost-per-page.  I can't connect it to my year-old Dell laptop with Ubuntu.  The laptop has only USB ports, and my Laserjet has only RS232 and Parallel ports.  I tried a USB-parallel cable which didn't work.  Then I tried a WiFi parallel print server.  The documentation was so bad that it took me over a month to get it working.  It was very slow and after two months stopped working.  I haven't been able to revive it since.

My laptop has a built-in Bluetooth adapter that I use with a Bluetooth mouse without problems.  I've seen Bluetooth parallel printer adapters marketed.  Does anyone have any experience with these?  They appear to come with a disk for using them with Windoze.  I think the Ubuntu Bluetooth Manager would discover and connect to the printer adapter OK, but I don't know if CUPS would know how to communicate with an old Laserjet through a Bluetooth adapter.

I bought a new color printer just to use with my Ubuntu laptop, but I'd rather use the Laserjet for most jobs.  The print quality is better, and it's much cheaper to operate.

---

### Post by mark bower on 2009-03-04
i have used my laserjet 4 since '93 and agree what a great unit.  my credit union still uses one, just imagine the durability for commercial throughput since '93 or '94 (whenever they bot it)

my set up in WinXP which works great is a USB Hawking HBCT2 dongle and the Bluetake BT 200 attached to the printer parallel port.  see the following for the Bluetake devices:

[http://www.bluetake.com/Products/BT200.htm](http://www.bluetake.com/Products/BT200.htm)

under ubuntu 8.10, the Hawking dongle does not work properly, won't pair. so i am going to try a Cirago BTA-6210 which supports the linux OS, and a number of reports indicate that it works out of the box just fine.  

mark bower

---

### Post by Saunter on 2009-03-06
I've seen the Bluetake BT200 advertised.  Like many products, it only has drivers for Windoze.  From Bluetake's website:

Windows 98SE/ME/2000/XP
(Recommended version: Windows 2000/XP)

    * The Bluetooth software which supports Bluetooth SPP (Serial Port profile) is essential to print form the Bluetooth enabled computer to the BT200 installed printer. The Bluetooth software is usually bundled with the Bluetooth enabled device you purchased (such as the USB adapter, RS232 adapter, CF card, PCMCIA card or the Bluetooth chip equipped computer). Pease check with the device's manufacturer for details. 

I'd like to know if you get it running with Ubuntu.

---

### Post by mark bower on 2009-03-06
will do.  unless i am mistaken, in WinXP i have no drivers loaded for the BT 200.  bluesoleil was loaded for and came with the Hawking dongles.  there is a com port tweaking issue in WinXP, but easily overcome.

i am hoping will not be an issue in Ubuntu since i am a novice with Ubuntu.  and come to think of it, that might even be the problem i am having with the Hawking dongle in Ubuntu.  it sees the BT 200, but will not pair.  

i should be trying out the Cirago dongle on 9 Mar, its expected delivery date.

mark bower

---

### Post by mark bower on 2009-03-09
@Saunter

The Cirago BTA 6210 easily connects with the Bluetake BT-200 on my printer.  I can see the MAC address and BT-200 description via hcitool on the cmd line.  But the problem is setting up to print from a Virtual Serial Port.  Blue Soleil software handled this for the Hawking on WinXP.  It appears to be a rather complicated process in Ubuntu - see link below.  The process is probably over my head.  Perhaps someone will see this post and give a detailed, simpler process to make the connectivity. 

I definitely would like to connect to my HP via the BT200.

[http://eduardoflores.blogspot.com/2007/03/printing-on-windows-or-ubuntu-with.html](http://eduardoflores.blogspot.com/2007/03/printing-on-windows-or-ubuntu-with.html)

---

### Post by Saunter on 2009-03-11
Yes, I thought the problem would be with software protocols.  I'm sure if I bought a BT-200, my built-in Bluetooth would discover and connect to it fine.  But I have no idea how to tell CUPS to print through a Bluetooth connection!

Let me know if you get it working.

---

### Post by mark bower on 2010-01-08
@Saunter, hope you return and see this

please see my post full title:  "Bluetooth printing - HP Laserjet 4 & BT-200".  In Ubuntu 9.10, things seem to set up somewhat automatically.  However, the steps that definitely work are,  
1) Determine MAC addr of the BT-200 with "spdtool browse" in a terminal(retain for ref)
2) Sys/Pref/Bluetooth/<select the BT-200 when detected>/click fwd/close
3) Sys/Admin/Printing/New/<select your BT device shown/click "fwd"/select HP/select driver "hpijs pcl3,3.9.8[en] 
[in the event that your BT device and printer are not automatically selected as in 3) then try:]
4) Sys/Admin/Printing/New/<select"Other"/<enter in the URI block "bluetooth://<Mac Addr of BT-200> _without colons_/continue the set-up by selecting HP LJ4 or LJ4P and driver "hpijs pcl3,3.9.8[en] 

example of my URI entry:  Bluetooth://0008F4232871

mark

---

