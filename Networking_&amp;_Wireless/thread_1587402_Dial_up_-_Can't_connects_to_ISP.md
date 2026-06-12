---
title: "Dial up - Can't connects to ISP"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by causeitsme on 2010-10-03
System info:
Linux carol-desktop 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux

I'm trying to help an older friend of mine get internet access back. She was on XP SP3 but it was so virus ridden that the only option was to wipe it and reinstall. She knew I used Linux and wanted it installed instead. **Note: I am not a computer tech, I've gotten where I am on this project via 6 hours of googling and trial and error.**

So here I am. I have gotten her this far:


[LIST]
[*]Ubuntu installed and updated
[*]Found Conextant modem drivers and installed
[*]Installed wvdial and can dial out
[*]Installed gpppon - It locks up when I try to use it
[/LIST]

Her provider is Turbo USA.

This is the terminal output of - sudo wvdial:

```
carol@carol-desktop:~$ sudo wvdial
[sudo] password for carol: 
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT<2297984010>
--> Waiting for carrier.
ATDT<2297984010>
CONNECT 460800 
--> Carrier detected.  Waiting for prompt.
Level 3 Comm nas26.2ga1 UQKT2
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: <REDACTED>
<REDACTED>
Password: 
--> Looks like a password prompt.
--> Sending: (password)
Request Denied
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: <REDACTED>
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sun Oct  3 12:42:14 2010
--> Pid of pppd: 1698
--> Using interface ppp0
--> pppd: (&#65533;W[08]@&#65533;W[08]
--> pppd: (&#65533;W[08]@&#65533;W[08]
--> pppd: (&#65533;W[08]@&#65533;W[08]
--> pppd: (&#65533;W[08]@&#65533;W[08]
--> Disconnecting at Sun Oct  3 12:42:29 2010
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
^CCaught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Sun Oct  3 12:42:31 2010
carol@carol-desktop:~$ 

```
I do recognize that it says request denied right after --> ```
Looks like a password prompt.
--> Sending: (password)
Request Denied.
``` I don't know why as I've rechecked the password several times and it is correct. 

This is from /var/log/message when trying to connect using the terminal command - sudo wvdial:

```
Oct  3 12:42:14 carol-desktop pppd[1698]: pppd 2.4.5 started by root, uid 0
Oct  3 12:42:14 carol-desktop pppd[1698]: Using interface ppp0
Oct  3 12:42:14 carol-desktop pppd[1698]: Connect: ppp0 <--> /dev/ttySHSF0
Oct  3 12:42:29 carol-desktop pppd[1698]: Modem hangup
Oct  3 12:42:29 carol-desktop pppd[1698]: Connection terminated.
Oct  3 12:42:29 carol-desktop pppd[1698]: Exit.
```


Here are the contents of /etc/wvdial.conf

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = <2297984010>
ISDN = 0
Password = <REDACTED>
New PPPD = yes
Username = <REDACTED>
Modem = /dev/modem
Baud = 460800
```

I've also done - sudo pppconfig **Note: I don't know where pppconfig is stored so below you'll find a list of what I entered in the wizard.**

[LIST]
[*]Main Menu - Create a connection
[*]Provider name - provider
[*]Configure Nameservers (DNS) - Dynamic, (I tried Static at first, it didn't work either)
[*]Authentication Method for provider - PAP (I tried Chat once, didn't work either)
[*]User Name - I have tried the username with and without @TurboUSA
[*]Password - I have entered the password
[*]Speed - 115200
[*]Pulse or Tone - Tone
[*]Phone Number - 2297984010
[*]Choose Modem Config Method - Yes
[*]Results in next page being 'Select Modem Port' (*) Manual Enter the port by hand.
[*]Maually Select Modem Port - my modem is at /dev/ttySHSF0. That is what I entered. I tried /dev/ttyS0 once prior and had no luck with that either.
[*]"Properties of provider" - Here I highlight 'Finished Write files and return to main menu.'
[*]Finished - OK
[*]Main Menu - Quit
[/LIST]

---

### Post by klemes on 2010-10-03
Your wvdial.conf configuration seems right you say you double checked password and it's OK and modem drivers are obviously installed correctly since you got this far.It's something minute obviously but hard to trace.Maybe you could try and have a look at /etc/ppp/pap-secrets and /etc/ppp/chat-secrets files and search for any conflicting username/password combinations.There maybe is where lies the problem.Just a guess.
And also while at it you could try to edit /etc/ppp/peers/provider and then try to connect directly with pppd command (or pon & poff commands for that matter).:guitar::popcorn:

---

### Post by dineshs on 2010-10-04
please see [this ]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9")link for errors especially> 
add [COLOR="Blue"]Carrier Check = no[/COLOR] as a new line (useful for Smartlink modems)
add [COLOR="Blue"]Stupid mode = on[/COLOR] as a new line (will start pppd immediately--required by some ISPs)  
and [this]("http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html") for other dialup methods

---

### Post by causeitsme on 2010-10-04
Got it working! :guitar: Using gnome-ppp launched as ```
sudo gnome-ppp
``` (sudo wvdial just wouldn't work for some reason. Neither would pon.)

I added 'Stupid mode = on' to /etc/wvdial.conf as dineshs suggested. 

There is a problem with Network Manager however. It seems it doesn't want to recognize that one is online when using dial up. To rectify that I edited /etc/network/interfaces. I added a line:```
iface eth1000 inet dhcp
```

This fools Network Manager somehow and tells Firefox that you are online. Without doing so Firefox starts up in Offline Mode and will not connect to any server.

---

