---
title: "Modem Driver Appears Installed But It Won't Connect"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by Kiddalee on 2006-07-07
Driver:

I used the [Dapper special instructions]("https://help.ubuntu.com/community/DialupModemHowto#head-1369d555560449b7b395cf9cd08446b38f6bbb11") at DialUpModemHowTo.

They appeared to work, as the graphical modem connection interface can finally Autodetect my Modem port.  WvDial also seems to acknowledge that Linux can now see my modem.

Connecting:

First, I tried System>Administration>Networking>Modem connection.  I filled in all the fields.  My Modem port was found to be in /dev/modem.  Activate is what is supposed to connect you, right?  It just doesn't work for me.  It says it works, but I don't hear my modem making any noises even when it's turned all the way up, and my Firefox isn't browsing.

When I run wvdial, it tells me that "Configuration does not specify a valid phone number... login name... password." I do have these specified in wvdial.conf .  I have tried it with and without Stupid Mode, x3, and Carrier Check.

... Now what?

---

### Post by zxee on 2006-07-07
I didn't go through all the info in the link, but what modem are you using? Have you tried the command 'sudo pppconfig' from a shell? Regarding wvdial-do you have a wvdial entry in /etc/ppp/peers? Using the command pppconfig executes a script that may, if it works, create the files needed to get dial up working.

---

### Post by Kiddalee on 2006-07-07
Answer:  Yes and Yes.  However, you have inspired me to mess around a bit and try a different port than the one automatically detected.  I'll see...
At least I'll only be stuck until the end of August if I don't get it working.

---

### Post by Kiddalee on 2006-07-08
New Answer: That doesn't appear to be my problem.  Either that or it's just not working.

---

