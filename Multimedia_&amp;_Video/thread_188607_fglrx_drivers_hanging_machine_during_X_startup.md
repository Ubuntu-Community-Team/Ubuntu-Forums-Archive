---
title: "fglrx drivers hanging machine during X startup"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by pascal_belron on 2006-06-04
I installed kubuntu 6.06 from the Kubuntu liveCD. By referring to  [this page]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide"), followed method 2 and installed fglrx drivers from ati (was carefull to select 64 bits drivers, as my machine is built upon an Athlon 64 x2 CPU).
Ran the aticonfig program, and xorg.conf was correctly updated to reflect the use of fglrx. Rebooted the machine. 

When X started, got a blank screen, and machine was dead : no CTRL ALT BCKSP to kill the X server, had to hard-reboot. The Xorg.log.0 I obtained is included here. Problem seems to come from the ati drivers, but I see lots of people using them so I guess it s my configuration... Any ideas ?

---

### Post by KiLLeR_WoMBaT on 2006-06-04
I followed those directions too (tried both methods) and neither one worked.  I had to revert to failsafe terminal mode and use dpkg-reconfigure xserver-xorg and set the display to VESA to get back in.

I did notice that whenever I select either fglrx or ATI with the above or when I followed the directions in either of the methods mentioned above that at the log on screen I get TWO Drum sounds.  When this happens and I log in the system just hangs at a blank screen with the mouse cursor.

Upon reverting back to VESA...everything works except still no DRI.

Anyone have similar or solutions?

---

### Post by pascal_belron on 2006-06-04
Killer do you happen to have the same segfault then me (please see included log file) ? I think it may come from an hardware incompatibility issue, as my hardware is pretty recent (Abit AT8 - Ath64X2 4400+ - Radeon 1900XT). ATI says 1900 is supported since previous version, anyone has a 1900 working with fglrx driver ?

---

### Post by disturbed1 on 2006-06-04
The x1X00 series support was added with 8.24.

The ati-config --initial setup doesn't work all that well. Rather than changing your existing xorg.conf, it makes new entries.

Also, your log file stated an error locating the device, usually an improper PCI device location in the xorg.conf file.

Here's a copy of my xorg.conf for a x1600.

---

### Post by barney_1 on 2006-06-04
I have the same problem and started a thread about it.  See that one here:
[http://www.ubuntuforums.org/showthread.php?t=187074&highlight=blank+screen]("http://www.ubuntuforums.org/showthread.php?t=187074&highlight=blank+screen")

This seems to be a problem for a lot of people, I found a bug report here:
[https://launchpad.net/distros/ubuntu/+source/xorg-driver-fglrx/+bug/30447]("https://launchpad.net/distros/ubuntu/+source/xorg-driver-fglrx/+bug/30447")

Let's hope this gets fixed soon.  You can get 2d rendering to run if you add:
```
Option     "nodri"
```
to the device section of your xorg.conf

---

### Post by disturbed1 on 2006-06-04
[quote=barney_1]I have the same problem and started a thread about it.  See that one here:
[http://www.ubuntuforums.org/showthread.php?t=187074&highlight=blank+screen]("http://www.ubuntuforums.org/showthread.php?t=187074&highlight=blank+screen")

This seems to be a problem for a lot of people, I found a bug report here:
[https://launchpad.net/distros/ubuntu/+source/xorg-driver-fglrx/+bug/30447]("https://launchpad.net/distros/ubuntu/+source/xorg-driver-fglrx/+bug/30447")

Let's hope this gets fixed soon.  You can get 2d rendering to run if you add:
```
Option     "nodri"
``` to the device section of your xorg.conf[/quote]

Makes it even worse.
Doing the browser test [http://librarian.launchpad.net/1585880/test.html](http://librarian.launchpad.net/1585880/test.html)

no dri
nothing .947
divs    13.871
text    141.443

with dri
nothing 3.195
divs    6.037
text    10.528

Think I'll keep dri enabled.

---

### Post by Syirrus on 2006-06-04
[QUOTE=pascal_belron]Killer do you happen to have the same segfault then me (please see included log file) ? I think it may come from an hardware incompatibility issue, as my hardware is pretty recent (Abit AT8 - Ath64X2 4400+ - Radeon 1900XT). ATI says 1900 is supported since previous version, anyone has a 1900 working with fglrx driver ?[/QUOTE]


I'm having the same problem.  I load the ATI drivers and I get a blank screen.  I'm trying to run x1900xtx, 64bit 6.06 Pentium D EMT64

---

### Post by KiLLeR_WoMBaT on 2006-06-04
[QUOTE=pascal_belron]Killer do you happen to have the same segfault then me (please see included log file) ? I think it may come from an hardware incompatibility issue, as my hardware is pretty recent (Abit AT8 - Ath64X2 4400+ - Radeon 1900XT). ATI says 1900 is supported since previous version, anyone has a 1900 working with fglrx driver ?[/QUOTE]

Pascal...I have a 9600 and it worked great under Breezy with ATI Drivers.  I get NO errors at all.  Just the two drum sounds (which let's me know it won't work) at the login screen.  Username and password go great and as it logs in it just sits there with the cursor.

What should I post to help diagnose this?  I'm a "seasoned" noob! :KS

Here is the Xorg.log file from the last failed attempt:

---

### Post by YR600 on 2006-06-04
I had the same problem it would boot and show a blank screen after a minute or so the desktop background would show through and the mouse pointer would be there but nothing else. 

The problem was with the drivers that are pre-installed with 6.06. reconfigure xserver to use the vesa or mesa driver so that you can get x up. sudo dpkg-reconfigure xserver-xorg

once you get in load up the synaptic package manager and search for fglrx remove the drivers that come with 6.06. then reinstall the ati drivers and then run aticonfig --initial to setup xorg-conf if aticonfig isn't able to run (mine refuses to run for some reason) reconfigure x as above but select the fglrx driver instead.

Hope that helps.

---

### Post by pahbi on 2006-06-04
On my Dell Inspiron 8200 with ATI MOBILITY 9000, I had to follow the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.25.18_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.25.18_drivers_in_Ubuntu_Dapper_Manually) and then replace the libGL.so.1.2 file in the /usr/lib/ directory with one I found in this thread: [http://www.ubuntuforums.org/showthread.php?t=185033&highlight=libGL.so.1.2](http://www.ubuntuforums.org/showthread.php?t=185033&highlight=libGL.so.1.2)

Once I did those two things, fglrxinfo worked and 3D acceleration seems to be working.

I'm only posting in case this helps another Inspiron 8200 user who might be searching the threads.

- Pahbi

---

### Post by pascal_belron on 2006-06-04
I added the Option "nodri" in the xorg.conf config file (in the fglrx definition section), and indeed it is working properly. The only thing is then that we got 2D acceleration, but no 3D yet... Any word from ATI ? I submitted a bug report one week ago, and they said they received it, but that I should not wait for any further news from them... strange support policy :;)

---

### Post by Eversmann on 2006-06-27
I'm having the same problem, wanted to get back this thread because problem still with 8.26.8

Everytime i use fglrx, after introduce my password, gnome hangs on load, nad have to ctrl+alt+backspace to enter on terminal safe mode and revert-back the changes on xorg.conf

One weird thing is: i tried to boot with "irppoll" on the kernel line and worked, but  just tried one time only, and don't know why it worked.

BTW, my sound loop with the ubuntu drums when it hangs.

---

