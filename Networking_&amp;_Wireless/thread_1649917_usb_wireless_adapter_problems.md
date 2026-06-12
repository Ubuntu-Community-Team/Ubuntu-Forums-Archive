---
title: "usb wireless adapter problems"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by cwgosling on 2010-12-20
Greetings. I've read through about a dozen different threads trying to figure out how to get my new USB wireless adapter to run. I tried following the installation instructions supplied by the manufacturer. I've followed threads about installing ndiswrapper and countless different drivers and tried most everything. The funny thing is that something worked two nights ago- the stars aligned and the card functioned perfectly. Then I rebooted the machine (without changing any of the settings) and have been banging my head against the wall ever since. I've tried many ways to replicate that moment and nothing has worked- hence this plea.

I apologize in advance for posting this when there are already so many threads devoted to the same topic, but since I've gone down so many different paths it's hard to figure out where I'm at and what needs to happen next to get this to work. 

Background: I'm not professional by any means, but am proficient. Fairly new to linux, but I really like it. Most of the stuff I type will be from a separate machine since I can't get mine to connect. If I've omitted key information just ask and I can always copy the files and post the output directly.

Hardware: dell desktop running Ubuntu Lucid 10.04 2.6.32-26-generic-pae
Set up as a dual-boot with Windows Vista (for itunes)
Wireless card is a Medialink wireless-n USB 2.0 adapter. This uses the Ralink 3070 chip.

Current settings:
I added the following lines to the bottom of the /etc/modprobe.d/blacklist.conf/ file:
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
# blacklist rt2870sta

# blacklist b43
# blacklist b43 legacy
# blacklist ssb

(some are currently commented out so I could try different settings)

Here is a list of the outputs from a couple of different commands so you can get an idea of what I'm working with:

code: iwconfig

lo no wireless extensions
eht0 no wireless extensions

code: lsusb
lots of stuff- I think the most relevant one is:
Bus 002 Device 003: ID 148f:3070 Ralink Technology, Corp.

code: lsmod | grep rt2 
(no output)

code: ndiswrapper -l
WARNING: All config files need .conf /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netr28u: driver installed
     device (148f:3070) present (alternate driver: rt2800usb)

code: sudo depmod -a
(no output)

Does it make a difference if the adapter card is plugged in when the machine is turned on? I feel like I'm really close since this actually worked for a little while. I just need to stumble my way out of the darkness- any help you could offer would be very much appreciated.

Thanks!

---

### Post by PhantmKllr on 2010-12-20
Try adding ndiswrapper to modprobe:

```
sudo ndiswrapper -m
```
then
```
sudo ndiswrapper -ma
```
then
```
sudo ndiswrapper -mi
```

Now, install the driver that worked with the card.

BTW I had the same problem with my wireless, but I found out that the ndiswrapper kernel mod doesn't load properly. The above commands should fix that.

Hope that helps! :D

---

### Post by cwgosling on 2011-01-02
Thanks for the speedy reply. I apologize for the delay on my end- I was out of town for the holiday.

I ran the commands you suggested.  Here are the results:

sudo ndiswrapper -m
module configuration already contains alias directive
(this line was repeated for 2-3 pages)

sudo ndiswrapper -ma
module configuration is stored in /etc/modprobe.d/ndiswrapper

sudo ndiswrapper -mi
module configuration is stored in /etc/modprobe.d/ndiswrapper


Does this sound like it worked? Should I install the version of the driver from the Ralink website or the Windows .inf version that came on the installation cd?

Thanks!

---

### Post by cwgosling on 2011-01-03
Today I used the dmesg command and found a series of lines in the boot log  that address ndiswrapper. Here are the lines that  seem particularly noteworthy:

14.317690] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netr28u'
14.318197] ndiswrapper (load_wrap_driver:108): couldn't load driver netr28u; check system log for messages from 'loadndisdriver'

Then I go to the syslog.1 file. There is a line that reads:

chris-desktop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver netr28u

This is followed by a series of lines that all reference ndiswrapper and a load of unknown symbols.

So it seems like everything falls apart when the netr28u driver doesn't get properly loaded. Does anyone have suggestions for how can I get this to load correctly when the system boots up? 

Or might I be better off returning this USB card and getting one that plays better with Linux? Seems like a cop out, but this game is getting a bit old. If you have a moment to lend a hand I'd really appreciate it.

Thanks!
Chris

---

### Post by Bucky Ball on 2011-01-03
Have you plugged in an ethernet cable, gotten online, then plugged in the USB dongle?

---

### Post by cwgosling on 2011-01-03
No, I haven't. I can give it a shot- would this have to be done every time the machine is rebooted?

---

### Post by Bucky Ball on 2011-01-03
Nope. It might offer to install the appropriate drivers and firmware for your card. As you have gone down the ndiswrapper path (can be a nightmare and to be avoided) you may find unusual problems though.

Could you run:

lspci

... in a terminal and identify your card model. It will be in the line starting with 'Network Controller', generally somewhere toward the end of the output. :)

---

### Post by cwgosling on 2011-01-03
It's a USB adapter, so I ran lsusb as well. Here is the output:

chris@chris-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV620 LE [Radeon HD 3450]
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]

chris@chris-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:2010 Dell Computer Corp. 
Bus 004 Device 002: ID 413c:1003 Dell Computer Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0644:0200 TEAC Corp. 
Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0424:2514 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Thanks for the suggestion about making a wired connection. I'd like to try it, but it's slightly complicated because after I got the wireless card working (for the one day it worked), I moved the router clear across the house. So I either move the computer (it's a desktop, so the monitor goes as well) or move the router back. Or I wait until tomorrow and go get a long cable so I can avoid the hassle.

-Chris

---

### Post by cwgosling on 2011-01-03
Frick on a stick. I was trying to add username to the sudoers file in /etc/ so I wouldn't have to enter a password every time. I tried uncommenting the indicated line and adding my username. Now it doesn't work, and when I enter sudo gedit sudoers I get the response of:

no valid sudoers sources found, quitting

I remember that in the sudoers file there was a command to reset it- can anyone bail a bumbling fool out of yet another mistake?

---

### Post by Bucky Ball on 2011-01-03
Bugger. Might pay you to post another thread for your new problem with a descriptive title. There is an easier way of logging in automatically without the need for username or password: 

System->Admin->Login Screen->Login Automatically. 

For a graphical description go to this page:

[http://www.liberiangeek.net/2010/07/automatically-login-ubuntu-10-04-lucid-lynx-login-screen/](http://www.liberiangeek.net/2010/07/automatically-login-ubuntu-10-04-lucid-lynx-login-screen/)

---

### Post by cwgosling on 2011-01-03
Will do, thanks for the advice on that front. Was the output from the lspci or lsusb commands particularly helpful?

---

### Post by Bucky Ball on 2011-01-03
My mistake, forgot you had usb adapter. lsusb doesn't tell much. :)

---

### Post by Bucky Ball on 2011-01-03
Here you go. Try post #1.

[http://ubuntuforums.org/showthread.php?t=1547195&highlight=3070](http://ubuntuforums.org/showthread.php?t=1547195&highlight=3070)

As mentioned, you may need to completely remove all ndiswrapper components for this to work, but give it a go. You will need to reboot after the fix to see any results.

---

### Post by cwgosling on 2011-01-03
Thanks for pointing me in the right direction. I'll try that as soon as I get my new issue worked out. I really appreciate the help.
-Chris

---

### Post by cwgosling on 2011-01-04
Bucky Ball-
Thanks a million for the link- it worked like a charm and even works after rebooting. It took a while because I dug myself into a deeper hole messing around with the sudoers file. Thank you so much for the advice!
Cheers!
Chris

---

### Post by Bucky Ball on 2011-01-04
Excellent news and my pleasure! Enjoy, and don't forget to post back in a new thread with any other probs. ;)

---

