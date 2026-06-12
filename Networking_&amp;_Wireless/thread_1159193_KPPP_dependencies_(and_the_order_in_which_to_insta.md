---
title: "KPPP dependencies? (and the order in which to install them?)"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by fredbird67 on 2009-05-14
I recently installed Ubuntu 9.04 on an old computer of mine (I bought a newer one last fall) that I gave to my father-in-law.  However, where he lives out in the sticks in southeast Missouri, he can only get dialup access where he lives.  I installed GNOME-PPP on it, assuming that it would connect to the Internet -- but it won't.  It recognizes the modem and everything, but as soon as it connects, it instantly disconnects, and the ISP (SEMO.net) is absolutely no help at all with Linux (bums!).

Therefore, I'm thinking about downloading the debs needed for KPPP and saving them to my flash drive (remember, he has no way to connect other than dialup, which isn't working right now).  However, since that's a KDE program and we're using a GNOME desktop, this is naturally going to have a mess of dependencies involved.

What I would like to know is, since I'll have to save all the DEBs to my flash drive in order to fix this, 1) what are those dependencies, and 2) since I'm sure some of those dependencies will likely have other dependencies in return, in what order should I install all those .DEB files to avoid dependency hell?

Also, does anyone know if Chestnut has dependencies in GNOME, and if so, what are they, and in what order would I need to install them to avoid dependency hell?

I know this is probably a tall order to answer, but if someone knows just what the proper order is, I'd really appreciate it.

Thanx in advance,
Fred

---

### Post by chili555 on 2009-05-14
[http://packages.ubuntu.com/jaunty/kppp](http://packages.ubuntu.com/jaunty/kppp)

Perhaps this will help. However, I believe Gnome-PPP and KPPP are both just front-ends for the same thing. I wonder if a KDE front-end makes any difference to SEMO.net in authenticating and connecting or not. I am no expert on PPP, however, I'd try to unsnarl Gnome-PPP first.

---

### Post by fredbird67 on 2009-05-18
But HOW?!!

I tried running it with the "Log" enabled and tried things from clues I found in that, all to no avail.

For the record, I even tried it with our Internet provider, which has an access number in Poplar Bluff.  No luck there, either.

Thanx for making me feel like I'm gonna be in trouble no matter what I do!

---

### Post by mikecanada on 2009-05-18
I was having a similar problem,first I had to change the dialer from root to mike to use it without typing sudo gnome-ppp at the terminal,then the system seemed to except the internet to come from the home network rather than the dial up connection.Really hard to find modem help now a days.This is what I was given to change the ownership rights,hope this helps as I still need modem help too!    sudo chown root:dip /usr/sbin/pppd

sudo chmod 4754 /usr/sbin/pppd

sudo chmod 777 /etc/ppp/pap-secrets

sudo chmod 777 /etc/ppp/peers

---

### Post by chili555 on 2009-05-18
> But HOW?!!You might post suspicious lines from the log and ask if anyone sees anything that's wrong to try to fix. You might do:```
dmesg | grep ppp
dmesg | grep wvdial
```See if there are any clues there and post them. You might also post /etc/wvdial.conf after you obscure your username and password. The easy way to do this is to copy and paste the terminal output to gedit and drag the resultant document onto a USB key to take back to St. L.

---

### Post by s03r on 2009-05-23
Hi, 
I can't help you with gnomeppp trouble, since I never use it, but if you just want to know the dependencies of kppp, theres an online tool that can help you:

[http://labs.fajran.web.id/p/apt-web/](http://labs.fajran.web.id/p/apt-web/)

just choose your ubuntu version, name of package(s) you need, and just choose random repository mirror (its default are mainly indonesian repo mirrors, you can change them with your nearest mirror manually), click submit, and voila! list of the files you need to download just show up.

hope this helps :)

c ya

---

### Post by fredbird67 on 2009-05-24
Thanks for the suggestions, y'all.

However, I tried this and other suggestions and tutorials, and nothing at all worked.  Trust me, I gave Ubuntu every chance in the world to shine here, and it was nothing but an exercise in futility.  In spite of my personal hatred for KDE (I used to be a KDE fan until version 4 came out early last year), I gave up and installed PCLinuxOS 2009 (he previously had PCLinuxOS 2007) on his computer instead, which, BTW, has KPPP right there on the live CD. Naturally, I tested that before installing, and in the dialup connection department, I hate to say it, but PCLinuxOS ate Ubuntu's lunch.

I know, there is a GNOME version of PCLinuxOS, and in fact, I tried that first, but for some funny reason, the XOrg server on the live CD kept crashing and I never could get the desktop to show up, so next in line was the main version with (ahem!) KDE, and it worked.  Oh well, at least PCLinuxOS 2009 has KDE 3.5.10 instead of that no-good piece-of-crap KDE 4.

---

### Post by chili555 on 2009-05-25
My sister likes PClinuxOS, too. She lives in Kansas. Must be a midwestern thing! I am glad it's all working for you.

---

### Post by Cahan on 2009-05-25
Howdy and here is a thot for you you can just get the Kppp to use in gnome I use using 08.04 for a long time and to get my cell to link up I had to use the bluetooth part of it and set your filles up like this as root edit the /etc/bluetooth rfcomm.conf or make a new one

#
# RFCOMM configuration file.
#

#rfcomm0 {
#	# Automatically bind the device at startup
#	bind no;
#
#	# Bluetooth address of the device
#	device 11:22:33:44:55:66;
#
#	# RFCOMM channel for the connection
#	channel	1;
#
#	# Description of the connection
#	comment "Example Bluetooth device";
#}
rfcomm4 {
        bind yes;
        device 00:12:6F:04:B0:95;
        channel 1;
        comment "Serial Port";
        }
rfcomm0 {
        bind yes;
        device 00:15:B9:84:FF:44;
        channel 4;
        comment "Cell Phone";
        }
then edit the /etc/bluetooth/hcid.conf to
#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	pin_helper /usr/bin/bluepin;

	# D-Bus PIN helper
	#dbus_pin_helper;
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "Moble-1";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;

	# Authentication and Encryption (Security Mode 3)
	#auth enable;
	#encrypt enable;

add your computers name to this part
# Local device name
	#   %d - device id
	#   %h - host name
	name "Moble-1";

in the Kppp set things up to 
Accounts: name of who you are with and edit it adding the number (for me it is #777)
Authentication: PAP/CHAP
call back type: NOTE
clik on ok then go to modems
clik on new and give it a name (your call on what)
on the Devive tab 
modem name (what you called it in the RF file)
modem device (why you set it to) for me that was (/dev/rfcomm0)
flow control Softwear [XON/XOFF]
line termm CR/LF
Conn speed max for me 460800
clik on ok and close the config of the kpp and if things are right after reboot open the kppp and set 
conect to (to the name you set)
Login ID (not need at lest for sprint but check with who your cell is with)
Password (not need for sprint but check with who your cell is with)
and then clik on connect I hope this works for you

---

