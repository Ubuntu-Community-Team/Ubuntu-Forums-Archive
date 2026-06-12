---
title: "USB Wireless USB Modem from the Command Line Termianl only?"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by CaptBry on 2010-05-14
Greetings All,

Without Gdm (The GUI Desktop running), or an Internet connection, how does One get pppd or wvdial to connect to a wireless broadband modem?
I'm SURE this can be done with any modern Distro without additional downloads...but seem to be missing some crucial step...? 

I've been trying things like: (scrips for pppd and chat and ln {links}  ttyACM0 to /dev/modem?) the modem is definitely on ttyACM0.

ln -sf /dev/ttyACM0 /dev/modem

/etc/ppp/chat-script
    #!/bin/sh
    # chat script for the modem
    exec -v \
    '' ATZ \ # Initialize modem \
    OK ATDT#777 \ # get an OK from modem, send the phone number
    CONNECT '' \
    oglin: me \ # i guess it misses the first letter
    assword: password \ # really it does!
    
then chmod 775 so it is executable
next file script:
/etc/ppp/ppp-on
     #! /bin/sh
     # the script to turn it ON
     exec /usr/sbin/pppd /dev/modem (or ttyACM0) 115000 connect /etc/ppp/chat-script

and chmod 775 to make this executable too.

but chat won't recognize the modem although dmseg, lsusb and mount do. I even copied what worked with the GUI setting into these. (gpppd)
 
I know how get into the command line as root.

I can use ln, ls, cmp, chmod, chown, vi, rm rn, mount, dmesg, lsusb.
But make, mkdev, give trouble and minicom/seyon are not on my system.
I can't use apt-get UNTIL I get this modem working (this is a duel-boot XP-pc) :(

If I simply pppd /dev/modem or /dev/ttyACM0 pppd says it doesn't see the device, linked (ls) or not...?

How can I 'ping' the modem for a sanity check? (ATZ<-->OK in a terminal)

I've written the chat , peer , and provider scripts and made them executable (which worked fine when the GUI was working) but for some reason I can't get Linux to connect from the command line using any variations. 

Puppy-Linux boots from a CDrom, finds them modem on a scan and launches Firefox in seconds....and the whole Desktop Suite is under 100K, yes Kilobytes... smart Puppy, I feel DUMB.

If I can truly LEARN how to link the modem into the Kernel properly, talk to it and write a repeatable script from the command line, I can tackle ANY Distro of Linux, maybe even Slackware some day...

help?

---

### Post by CaptBry on 2010-05-24
For the benefit of other Readers, here is what I have found to be the most direct way:

First KNOW where your modem IS; mine is ttyACM0. Then use the
command line in Terminal as root:

type:

pppconfig

this program will ask you about your phone number #777, [email]username@verizon.com[/email] and password qnc etc. and write the chat & peer scripts for you. Nice!

then ACTIVATE the connection with 

pon

I assume this is short for ppp ON (?)
 then do a 

dig google.com

and you should get a bunch of text back relating to your connection speed with google.com

from there you're connected and can use apt-get etc as all the Help files assume you can ;-)

This should work in Ubuntu and hence Debian Distros which all should have pppconfig, Experts-is this assumption true??

I realy would prefer to solve this to a Kernel Level All-Linux level so PLEASE add to it. Cheers!

---

