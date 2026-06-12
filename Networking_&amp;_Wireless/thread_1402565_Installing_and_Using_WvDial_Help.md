---
title: "Installing and Using WvDial Help?"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by Nightstrike2009 on 2010-02-09
I have installed WvDial (apparently) but it has no icon or launcher to start it by default, how do i get it to run? I also need basic set up how to. 

I am running Ubuntu 9.10 (Karmic) and network manager doesn't seem to be able to use my modem to connect to the internet (set up wizard works, appears connected, but then I get page not found error). Hence I wish to use WvDial to try to connect instead.

Can anybody help?

---

### Post by Bartender on 2010-02-09
IS this for plain old phone-line dialup, or are you trying to access a cellphone system?

If you've installed wvdial, it's invoked with terminal 

```
sudo wvdial
```

If you haven't configured wvdial yet, try 

```
sudo wvdialconf /etc/wvdial.conf
```

to see if wvdial can find your modem, and 

```
sudo gedit /etc/wvdial.conf
```

to get into the file where you need to set up username/password/phone number, etc.

Setting it up for a cellphone based connection seems a little trickier because there are so many different phones and carriers etc.  I don't have any experience with that, just slow phone-line dialup.

[This]("http://ubuntuforums.org/showthread.php?t=480717") thread is old, but not much has changed.  More in-depth discussion of wvdial

---

### Post by Nightstrike2009 on 2010-02-09
Thanks for trying to help me Bartender,

Sorry I forgot to mention my cellphone modem its a Huawei K3565 v2 modem (3G Modem- Vodafone UK), will try to use your advice when i get back to my linux box.

Anyone know how to set WvDial up for Vodafone UK PAYG Network?

**PS:** I did have it working with network manager for a while but its borked again now and can't connect it worked for a short while :-( My other network manager thread is here: [http://ubuntuforums.org/showthread.php?t=1398434]("http://ubuntuforums.org/showthread.php?t=1398434") this current one is **ONLY FOR Wvdial** please use the thread mentioned just now for network manager

---

### Post by Nightstrike2009 on 2010-02-09
Thanks bartender on net now with wv dial, got commands 2 and 3 the wrong way arround but apart from that ace man cheers :-)

> Number: *99#
Username: web
Passord: web

Works great wvdial generates the below details:

> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = *99#
Modem = /dev/ttyUSB0
Username = web
Password = web
Baud = 9600

And thats how you get a Vodafone (UK) Huawei K3565 v2 modem working with wvdial.

PS: It works fine now does anyone know where i can get a GUI for Wvdial though?

---

### Post by Nightstrike2009 on 2010-02-09
PS: If you want to get it to run with network manager check this thread: [http://ubuntuforums.org/showthread.php?t=1398434]("http://ubuntuforums.org/showthread.php?t=1398434")

---

### Post by GB_Joe on 2010-02-24
Okay then...

I've read both the wvdial and Network Manager threads, and I'm not getting connected with either.

This is pretty embarrassing, it's a friend's laptop and I suggested he use Ubuntu...:redface:

Keeping to the wvdial option here, I've got a whole bunch of stuff that's being churned out in the terminal:
> --> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Wed Feb 24 21:17:15 2010
--> Pid of pppd: 2585
--> Using interface ppp0
--> pppd: (&#65533;&#65533;[08]@&#65533;&#65533;[08]
--> pppd: (&#65533;&#65533;[08]@&#65533;&#65533;[08]
--> pppd: (&#65533;&#65533;[08]@&#65533;&#65533;[08]
--> pppd: (&#65533;&#65533;[08]@&#65533;&#65533;[08]
--> pppd: (&#65533;&#65533;[08]@&#65533;&#65533;[08]
--> pppd: (&#65533;&#65533;[08]@&#65533;&#65533;[08]
--> Disconnecting at Wed Feb 24 21:17:17 2010
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds

So, other than the fact that I love having a computer tell me it doesn't know what to do (but is hoping for the best), I seem to be stuck. It just loops around this until I tell it to stop.

I have tried this on my own laptop (IBM T42, fully updated 9.10), was getting the same thing with Network Manager on friend's laptop (T60), not tried wvdial on his, but I'm guessing it'll be the same.

In case it helps, here's the stuff out of /var/log/messages (yes, it's Larry2 the Laptop - the original Larry had a fall and was jumped on by a toddler...):

> Feb 24 21:20:38 Larry2 pppd[2655]: pppd 2.4.5 started by root, uid 0
Feb 24 21:20:38 Larry2 pppd[2655]: Using interface ppp0
Feb 24 21:20:38 Larry2 pppd[2655]: Connect: ppp0 <--> /dev/ttyUSB0
Feb 24 21:20:38 Larry2 pppd[2655]: CHAP authentication succeeded
Feb 24 21:20:38 Larry2 pppd[2655]: CHAP authentication succeeded
Feb 24 21:20:40 Larry2 pppd[2655]: Modem hangup
Feb 24 21:20:40 Larry2 pppd[2655]: Connection terminated.
Feb 24 21:20:40 Larry2 pppd[2655]: Exit.

---

### Post by Nightstrike2009 on 2010-03-02
| don't know mate i get to the pppd entries but then it connects to a DNS server then i click firefox and it lets me on the net. Have to unplug dongle to disconnect though.

---

### Post by GB_Joe on 2010-03-03
Okay, well now I'm posting this using the dongle...

I am so confused...

Will it work after a reboot? I'm not putting money on it, and I'm not sure I want my mate to have to go through the terminal to get online...

---

### Post by GB_Joe on 2010-03-03
Rebooted and still working.

:confused:

Guess I'll take one more go at NetworkManager...

---

### Post by GB_Joe on 2010-03-03
No go on NetworkManager, guess I'll be sticking to wvdial.

Incidentally, Nightstrike2009 - I can get it to disconnect by hitting [Ctrl] & C in Terminal, seems a little better than just yanking the dongle!

---

