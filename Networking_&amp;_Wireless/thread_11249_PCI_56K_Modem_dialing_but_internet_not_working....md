---
title: "PCI 56K Modem dialing but internet not working..."
date: 2005-01-15
forum: Networking &amp; Wireless
---

### Post by DjTeriyake on 2005-01-15
Hi Everybody,

I like Ubuntu a lot, and I can love it, and I want to love it. However, I'm having problems connecting to the internet via my dial up modem. My hardware is a US Robotics 3CP5610A v.92 internal PCI modem. It is listed in Linmodems.org as a NOT being a Winmodem, but a regular hardware modem.

I seem to be able to connect to the internet, but in a weird sort of way. Going to Computer>Networking, blah blah will not work. I tell Ubuntu that my modem is listed as /dev/ttyS3 (and all of the other choices, too) and then when I hit the "Autodetect" button it cannot find my modem. When I check the box to activate the ppp connection associated with the modem the lights checkbox goes away within one second. If in the taskbar I choose to try to connect via the "Modem Lights" applet it doesn't connect. I am able to connect, however, via root under a command line using wvdial. Here is my terminal output:

--------------------------------------------------------

root@ubuntu:/home/djteriyake # wvdial
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0L3
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0L3
OK
--> Modem initializing.
--> Sending ATDT3821922
--> Waiting for carrier.
ATDT3821922
CONNECT 50666/ARQ/V92/LAPM/V42BIS
--> Carrier detected - Waiting for prompt.
** 01 Communications TermServ **
Login:
--> Looks like a login prompt.
--> Sending: (username)
username
Password:
--> Looks like a password prompt.
--> Sending: (password)
      Entering PPP Session.
      IP address is 69.19.143.194
      MTU is 1524.
--> Looks like a welcome message.
--> Started pppd at Sun Jan 15 00:15:42 2005
--> pid of ppd: 5596
--> Using interface ppp0
--> pppd: +FCLASS=0L3
--> pppd: +FCLASS=0L3
--> pppd: +FCLASS=0L3
--> pppd: +FCLASS=0L3
--> local IP address 169.19.143.194
--> pppd: +FCLASS=0L3
--> remote IP address 69.19.143.194
--> pppd: +FCLASS=0L3
--> primary DNS address 69.19.190.116
--> pppd: +FCLASS=0L3
--> secondary DNS address 66.81.0.252

-------------------------------------------------------------

And from here the terminal just sits. I pick up my telephone and I hear static and modem noises, so the connection appears to be alive. So I start up Firefox. Any URL that I try to visit, it says "Resolving host XXXXX" in the status bar and just hangs, no timeouts. So I start GAIM. It doesn't connect. I start another terminal and try to ping any external URL, nothing. No messages even. When I hit CNTRL+C on the terminal which has wvdial running here is how it disconnects:

--------------------------------------------------------------

Caught signal #2! Attempting to exit gracefully...
--> Terminating on signal 15.
--> pppd: +FCLASS=0L3
--> Disconnecting at Sat Jan 15 00:35:17 2005
root@ubuntu:/home:djteriyake

---------------------------------------------------------------

This is the only way that I can "connect" to the internet. I hear the modem making it's noises when wvdial is connecting, and the phone is busy when it's connected, but I still can't use the internet. Is this due to the "Autodetect" not working in the network setup dialog? What can I do to start to resolve this?

Thanks

---

### Post by DjTeriyake on 2005-01-20
I got it to work! Apparantly my apps were looking for the connection associated with eth0, so I disabled that connection. Now to play with Ubuntu!

---

### Post by dbutcher on 2005-03-05
[QUOTE=DjTeriyake]I got it to work! Apparantly my apps were looking for the connection associated with eth0, so I disabled that connection. Now to play with Ubuntu![/QUOTE]


How did you get it to work?  I can dial in via modem and receive an IP address from Internet provider.  I have Deactivated eht0 in Network Settings.  I know I'm close, but I can't get Firefox to work, even though I can ping internet ip addresses.
All help appreciated.

---

### Post by alastair on 2005-03-05
If you can ping internet IP addresses but not ping by NAME, then this is a DNS problem.

Do you know your DNS servers? OR are they DHCP configured from your ISP?

Check the file : /etc/resolv.conf

---

### Post by dbutcher on 2005-03-05
Thanks Alastair,
I believe my dns servers *should* be set by DHCP from IP provider.
However, /etc/resolv.conf shows only settings picked up from eth0 (ie: the settings I would use if connecting through LAN)
There is also a file /etc/ppp/resolv.conf with contains nameservers obtained through dial-up.  So is this file just in the wrong directory?  I could manually copy the information, but would prefer to figure out the proper way to have it configured.
I'm trying to configure a laptop for mobile use.  That's why I need both LAN and modem access.  It's possible/likely that dial-up DNS info would change if I dial from a different location while travelling.

---

### Post by alastair on 2005-03-05
I'm not an expert on PPP configs - the first thing I would do is make sure your PPP dialup works (DNS resolution) if you use the /etc/ppp/resolv.conf settings - ping something by name.

The PPP resolv.conf is setup by pppd if "usepeerdns" is set - see "man pppd".

A script is run "/etc/ppp/ip-up" - which also runs scripts under "/etc/ppp/ip-up.d". There is a "0dns-up" script in there which /appears/ to make a backup of /etc/resolv.conf and then copy the ppp one over it.

You might want to do some research on how this all works in Ubuntu/Debian.

---

### Post by dbutcher on 2005-03-05
As a complete newbie (to both Ubuntu and linux), my main issue is how to find the documentation that already exists.  Your pointing out the "man pppd" was exactly what I needed.
I had used command line pppconfig to set up modem originally.  pppconfig defaults to "provider" as isp name.  But I could only get modem lights applet to recognise "ppp0".  I tried to copy provider settings to ppp0 manually, and somewhere in there got things confused.  
So, all good now.  I'm in.  It works!  Many thanks.

---

### Post by dbutcher on 2005-03-05
Hmm.
Well... almost.
If I type "pon ppp0" from terminal, everything works.
If I Activate Modem connection from applet panel, modem dials and retrieves IP address, but Firefox doesn't work (can't resolve address names.)
I have repeated this several times.  So I'm sure there's nothing wrong with modem, as "pon ppp0" is reliable and repeatable.  
Any insights on the applet configuration?  It *looks* correct, but ...?

---

### Post by alastair on 2005-03-05
I'm not sure - I am not in front of a modem based computer. Which applet?

Can the applet not be configured to use "pon ppp0" as its PPP command?

---

### Post by dbutcher on 2005-03-05
Applet is called "Modem Monitor".  Subtitled: "Activate and monitor a dial0up network connection".  Sounds perfect...
I've seen other references to somthing called "Modem Lights".  At first I thought these were the same thing, but now I don't think so.  I don't know where to find Modem Lights.  The other references I've seen make it seem like Modem Lights allows more configuration options.
Modem Monitor doesn't seem to allow changing the device name (defaults to ppp0), nor does it allow easy configuring for a mobile user, who might have to have more than one dial-up setting, depending on location.  
But I'm so new to all this that I can't tell the difference between weaknesses of Ubuntu or ignorance on my part (or both).  
For now, I'm using the System|Administration|Networking menu to swap between Network card and Modem.  Seems to work, but I had to add DNS servers manually.
But, hey, I'm learning a lot :)

---

### Post by raw_knee on 2005-03-12
[QUOTE=DjTeriyake]I got it to work! Apparantly my apps were looking for the connection associated with eth0, so I disabled that connection. Now to play with Ubuntu![/QUOTE]

So did I. Now I was wondering why disabling eth0 solved the problem. I am not on an eth network right now, so I really don't need it and disabled it even during startup. What happens to those connected to an ethernet network and would want their machine to connect through ppp to another machine?

---

### Post by alastair on 2005-03-12
Then that's a "default route" issue probably. Look at :

man route

and output of :

route -n

The default route is destination "0.0.0.0" and an associated device.

---

### Post by raw_knee on 2005-03-12
The output on my terminal when I called 'route -n' looks like this when eth0 is enabled:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
203.x.x.x       0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
127.0.0.0       0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         127.0.0.1       0.0.0.0         UG    0      0        0 eth0
0.0.0.0         203.x.x.x       0.0.0.0         UG    0      0        0 ppp0

```

Does this mean I have to remove the entries for eth0?
Sorry for the newbie question, but this the first time I've encountered this sort of problem.

---

### Post by brousch on 2005-03-14
I ran into this problem when setting up a computer for my Grandma, so I don't actually have it in front of me. I knew I should have written this down, but it was a nightmare I would rather forget!

The situation is having both an Ethernet and a modem connection on the same computer. The magic key for me was adding "replacedefaultroute" in the correct ppp's peers file config.

[B]sudo gedit /etc/ppp/peers/<name of your dialup connection>
Add "replacedefaultroute" (without the quotes) in the middle somewhere.
Save the file and give it your connection a try.[/B]

I spent several hours late at night trying to figure this out, so it is all a red-tinted haze now. Some things may be slightly off.

As near as I can tell, the default route tells the system how to find the Internet and is stored in resolv.conf (I think). This works fine for ethernet, but when you try to use the modem, it sticks with the default route in resolv.conf. Telling the modem to replace the deault route with it's own is the key.

I am not sure what happens when you try to go to back to your Ethernet connection, so you may have to fix something else when that happens!

---

