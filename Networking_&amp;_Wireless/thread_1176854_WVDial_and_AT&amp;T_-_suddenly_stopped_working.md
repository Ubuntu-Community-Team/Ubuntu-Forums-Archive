---
title: "WVDial and AT&amp;T - suddenly stopped working"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by telegramsam17 on 2009-06-02
Okay here's the sob story - AT&T has DSL service everywhere in Nashville except the 2 square mile area I live in. The told me two years ago they'd have DSL service here "very soon", but they lied. I can't afford $50 a month for cable internet, so that's why I'm the last sucker on earth using a 56k connection to read my freaking Gmail (slowly).

I was using WVDial on Ubuntu 7.10 just fine for over a year and last week it just stopped working, out of the blue. Nothing about my system has changed, I haven't updated or upgraded anything, I have not changed my username or password for my internet service.

So now I'm stuck logging into the windblows partition on my computer, which makes me cry (and, by the way, connects over this flipping dial-up connection using the exact same username and password pair that WVDial is stating to be incorrect). I can only assume AT&T has changed something on their end but when I called them up they didn't seem to have any freaking clue what I was talking about and their tech people apparently don't know Linux from a hole in the ground, which is why I am here with my hat in my hand begging for a magic solution (which probably doesn't exist, but hey I figure it's worth a try)

I try to dial up and here's what happens:

WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot set information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT2548787
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT2548787
WvDial Modem<*1>: CONNECT 57600 
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: STATION ID - wasdc18rh01hp017,wasdc42ev
WvDial Modem<*1>: Welcome 
WvDial Modem<*1>: Please Sign-on: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: huntemann
WvDial Modem<*1>: huntemann
WvDial Modem<*1>: Password:
WvDial<*1>: Looks like a password prompt.
WvDial<*1>: Sending: (password)
WvDial Modem<*1>: Name, password pair incorrect
WvDial Modem<*1>: Please Sign-on: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: huntemann
WvDial Modem<*1>: huntemann
WvDial Modem<*1>: Password:
WvDial<*1>: Looks like a password prompt.
WvDial<*1>: Sending: (password)
WvDial Modem<*1>: Name, password pair incorrect
WvDial Modem<*1>: Please Sign-on: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: huntemann
WvDial<Notice>: Don't know what to do!  Starting pppd and hoping for the best.
WvDial<Notice>: Starting pppd at Tue Jun  2 18:16:27 2009
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 6432
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: H&#65533;&#65533;&#65533;&#536;[06][08]8&#65533;[06][08]
WvDial<*1>: pppd: H&#65533;&#65533;&#65533;&#536;[06][08]8&#65533;[06][08]
WvDial<*1>: pppd: H&#65533;&#65533;&#65533;&#536;[06][08]8&#65533;[06][08]
WvDial<*1>: pppd: H&#65533;&#65533;&#65533;&#536;[06][08]8&#65533;[06][08]
WvDial<*1>: pppd: H&#65533;&#65533;&#65533;&#536;[06][08]8&#65533;[06][08]
WvDial<*1>: pppd: H&#65533;&#65533;&#65533;&#536;[06][08]8&#65533;[06][08]
WvDial<*1>: pppd: H&#65533;&#65533;&#65533;&#536;[06][08]8&#65533;[06][08]
WvDial<*1>: Disconnecting at Tue Jun  2 18:16:58 2009
WvDial<*1>: The PPP daemon has died: A modem hung up the phone (exit code = 16)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
WvDial<Notice>: Auto Reconnect will be attempted in 5 seconds
WvModem<*1>: Cannot set information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.

...at which point it just keeps on endlessly re-dialing until I close it.

It looks as far as I can tell just like it used to right up to the "WvDial Modem<*1>: Name, password pair incorrect" part. I've gone into wvdial.conf and played around with stuff but nothing seems to work.

Right now it looks like this:

[Dialer Defaults]
Phone = 2548787
Username = huntemann
Password = *my password is here*
New PPPD = yes

Thoughts? Ideas? Sympathy?

---

### Post by GeorgeVita on 2009-06-03
Hi **telegramsam17**,
although you note that you did not change any file, I will give some ideas. As wvdial reports:
> ... Name, password pair incorrect...
... Warning: Could not modify /etc/ppp/pap-secrets: Permission denied...
you should try: **sudo wvdial**

Also try adding the following lines to your **/etc/wvdial.conf** file
(from a terminal window: **sudo gedit /etc/wvdial.conf**)

[B]Stupid Mode = yes
Dial Attempts = 3[/B]

The "stupid mode" will try to force ppp and do the user/password negotiation there, and "Dial Attempts = 3" will stop trying infinitively to connect.

Regards,
George

---

### Post by robert shearer on 2009-06-03
@GeorgeVita has good advice and I hope it solves your problem:)

I have never had a useful connection using wvdial but have used  pppconfig and pon poff to manage dial-up in the past.

if all else fails you could try...

```
sudo pppconfig
```

fill out the set up window and to use it open a terminal and type

```
sudo pon
```
to connect.Leave the terminal open while connected and when finished use..
```
sudo poff
```
to disconnect

---

### Post by telegramsam17 on 2009-06-03
> **GeorgeVita said:**
> Hi **telegramsam17**,
although you note that you did not change any file, I will give some ideas. As wvdial reports:

you should try: **sudo wvdial**

Also try adding the following lines to your **/etc/wvdial.conf** file
(from a terminal window: **sudo gedit /etc/wvdial.conf**)

[B]Stupid Mode = yes
Dial Attempts = 3[/B]

The "stupid mode" will try to force ppp and do the user/password negotiation there, and "Dial Attempts = 3" will stop trying infinitively to connect.

Regards,
George

Thanks. I already tried sudo wvdial and even tried logging in as root (risky I know but I was desperate) I will try those other things tonight.

---

### Post by telegramsam17 on 2009-06-03
Well, the "stupid mode" line fixed it! And no, the sheer appropriateness of having to use something called "stupid mode" for AT&T is not lost on me. :p

Thanks a ton! No more windblows! :)

---

