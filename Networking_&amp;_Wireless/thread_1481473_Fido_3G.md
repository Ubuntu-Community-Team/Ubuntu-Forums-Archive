---
title: "Fido 3G"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by hauger on 2010-05-12
Hi.

I'm somewhat of a user, not really a newbie but not a power user by any means.  I have an old EeePC 2GB surf that I've set up with EeeXubuntu 7.10, and as a goodwill gesture I was going to give it to my non-tech-savy inlaws as an internet appliance to allow them to check their email and read the newspaper when they're away from home (they're retired RV types).

In any event, we got them a Fido 3G USB Stick (link: [http://www.fido.ca/web/content/internet/3g_mobile_internet_stick?cm_mmc=Redirects-_-External-_-Marketing-_-USBupdate]("http://www.fido.ca/web/content/internet/3g_mobile_internet_stick?cm_mmc=Redirects-_-External-_-Marketing-_-USBupdate")).  Of course, as with all great companies, there's no linux support.

Further, I can't really upgrade away from 7.10 do to very limited storage space on the little machine.

I've read a number of [SOLVED] threads that make mention of using wvdial to get these sticks flying, but they all require manually editing the wvdial.conf file.  I'm rather comfortable editing conf files if I know roughly what to put in them, but one of the first lines I run across is [Modem = /dev/ttyUSB2].  Thing is, I don't have a "ttyUSB2" listed, or anything similar.

I'm quite sure it exists.  7.10 recognizes the file structure and brings up the files when plugged in.  Typing sudo lsusb lets me see the device is actually there although it doesn't identify itself really nor does it point me towards what /dev/ name it's running under.

So, anyone want to take pity on me and help me out?  I have about a week before I have to send it back defeated if I can't get it to work.  Any help would be great.

Thanks.

---

### Post by hauger on 2010-05-12
looked up the modem, it's a ZTE MF 636 USB Modem, if that helps.  Funny thing, it keeps being identified as a CD-ROM....why is that, and how do I maybe stop that so it identifies as a modem?

Thanks

---

### Post by hauger on 2010-05-12
***UPDATE***

Okay, since the last post, I found [this thread.]("http://ubuntuforums.org/showthread.php?t=1005910")  In it, user GeorgeVita wrote a nice guide.

So, steps so far:

1. Insert 3G USB Stick.

2. Right click desktop icon and "eject" disk.  This I guess forces the modem to switch from CD-ROM mode to modem mode.

3. In a terminal, type: **lsusb**, make note of vendor and product numbers.

4.  Next, in a terminal, type **sudo modprobe usbserial vendor=0x19d2 product=0x0031**.  I don't know what modprobe is or what exactly it does, but it works in forcing the modem to be recognized at /dev/ttyUSB2.

5.  In the same terminal: **sudo mousepad /etc/wvdial.conf**.  There, I edited the config file like so:

[Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 7372800
Dial Attempts = 1
Username = user
Password = pass
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = ATS7=60 S30=0 S0=0
Init4 = AT+CGDCONT=1,"IP","fido"
Phone=*99#
Stupid Mode = 1

Now, things I don't know.  I don't know what the Username/Password really are, nor do I know what the APN ("fido" in the above example) is.  Worse, I don't know what to ask a tech support guy on the other end of a 1-800 to find out what these are, since I really don't know what an APN is.

6.  Typing **sudo wvdial**, I get the following:

WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: AT&F &D2 &C1
WvDial Modem<*1>: AT&F &D2 &C1
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATS7=60 S30=0 S0=0
WvDial Modem<*1>: ATS7=60 S30=0 S0=0
WvDial Modem<*1>: OK
WvDial<*1>: Sending: AT+CGDCONT=1,"IP","fido"
WvDial Modem<*1>: AT+CGDCONT=1,"IP","fido"
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99#
WvDial Modem<*1>: CONNECT 7200000
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Wed May 12 19:22:44 2010
WvDial<Notice>: Pid of pppd: 5464
WvDial<*1>: pppd: H&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: H&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: H&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: H&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: H&#65533;[06][08]&#65533;&#65533;[06][08]

All this looks good for a minute or so, when I then get the following error:

WvDial<*1>: Disconnecting at Wed May 12 19:25:01 2010
WvDial<*1>: The PPP daemon has died: A modem hung up the phone (exit code = 16)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
WvDial<Notice>: Auto Reconnect will be attempted in 5 seconds
WvModem<*1>: Cannot get information for serial port.

So at this point, like I said, I'm 90% of the way there.  

Here's what I'd like to know...

1. Any help (please) to make it the last 10%?
2. What's an APN?  What do I ask tech support for to get this APN (given the stock answer will be "we don't support linux")?  Any chance this is the problem?
3. Once things are successful, will wvdial do everything automatically, ie...do I just open a web browser and surf, or is there another step?

and lastly...

4. Is there any way to automate the process...ie: write a script so my tech-challenged inlaws can double click an icon and a terminal will just go ahead and do all the steps (modprobe, wvdial, all in sudo) for them?

Really, thanks for anything you can offer up.

---

### Post by hauger on 2010-05-12
***Update***

Okay, I know I'm single handedly carrying this thread, but if I don't no one else will.

I managed to get the thing working, the issue was the APN.  Turns out the trick was to put the key into a windows machine and let it connect, then pick out the information from the options/setup (in my case, the APN was "internet.fido.ca").  It's still flaky though, it seems it's important for the modem to have service before starting wvdial or it can't resolve it once service comes up.  This seems to me like it might be a pain in the butt in areas of weak coverage.

So, thanks for acting as a sounding board.  Last but not least, can *anyone* point me to a resource that would explain how to create a script that would open up a terminal (preferably hidden, say maybe on a different virtual desktop), and work though the steps of ejecting the key, allowing it to reset, then doing that modprobe on it, finally running wvdial, all under super user mode?

Thanks.

---

