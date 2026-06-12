---
title: "ndiswrapper: SIOCGIFFLAGS error: No such device"
date: 2005-01-20
forum: Networking &amp; Wireless
---

### Post by Alexander Kirillov on 2005-01-20
I am having some problems with my wireless card (Dell Truemobile 1300 mini-PCI, based on Broadcom chip). I have installed ndiswrapper. Yet, when I try to use Network Monitor applet, I get this strange error message (wlan0 is not yet up at this point):

```
SIOCGIFFLAGS error: No such device
```

Yet I can manually start wlan0 fine: 
```


root@dhcp110:/home/shurik # ifup wlan0
Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:4b:6f:2c:dc
Sending on   LPF/wlan0/00:90:4b:6f:2c:dc
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.102 -- renewal in 270320 seconds.

```

after which Network Monitor works just fine.

Anyone has seen this before?

---

### Post by DW5 on 2005-07-05
I am having this same problem with a compaq nx9010 and broadcom chipset.  I got wireless running, but the monitor has a warning symbol through it and gives the message: 

SIOCGIFFLAGS error: No such device

The wireless does work, but the monitor does not.  I tried ifup and it does not change anything.  This isn't an emergency, but I would like to fix it at some point.

```
dwilliam@DUUbuntu:~$ sudo ifup wlan0
Password:
ifup: interface wlan0 already configured

dwilliam@DUUbuntu:~$ iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:"snu_wlan"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:01:F4:EC:A0:14
          Bit Rate:11 Mb/s   Tx-Power:14 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-43 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:24  Invalid misc:24   Missed beacon:0

dwilliam@DUUbuntu:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:4b:59:da:a8
Sending on   LPF/wlan0/00:90:4b:59:da:a8
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 172.16.200.3
bound to 172.16.53.69 -- renewal in 18576 seconds.
```

DW

---

### Post by DW5 on 2005-07-18
I deleted that troublesome applet and added the network monitor applet to my panel.  Internet activity shows as well as signal strength (though I think I read that this was buggy.)

Maybe this is the solution....

---

### Post by nozavroni on 2007-01-08
I realize this is an old thread, but I figured why make a new one when there's this perfectly good old one available? Anyway, hi! I'm new to Ubuntu and Linux in general. I'm having this same issue. When I click on the network monitor, it gives me this error:

[QUOTE=error]SIOCGIFFLAGS error: No such device[/QUOTE]

I apologize, but I kind of need my hand held. I really want to stay with Linux and kiss Windows good-bye, but I need help :)

---

### Post by nozavroni on 2007-01-09
Is it too soon to bump this? :confused:

---

### Post by darkmediator on 2007-01-10
1 .Open "/etc/network/interfaces"
2. Comment the wireless network interfaces that correspond to ur system! On mine its "eth1"!
3. Reboot! It shud work now!

---

### Post by fb581 on 2007-01-11
This quick fix worked for me: 

1) Right click the symbol for the Network Monitor and choose "remove from panel"
2) Right click the panel again and choose "add to panel"
3) Pick the "Network monitor"

---

### Post by devillion on 2007-04-26
None of this worked for me. I read support ticket/tag/whatever #329 ([here]("https://answers.launchpad.net/ubuntu/+question/329")) and nothing there helped either. Though, honestly, i don't know how to comment a line as "darkmediator" suggests...is it <!-- --> or #? maybe //?

Anything else to try? I can't bring the network up manually, as the OP said to try, and even when i run off of a LiveCD, i get the same freaking error. How can this be?

---

### Post by H.E. Pennypacker on 2007-05-01
> **fb581 said:**
> This quick fix worked for me: 

1) Right click the symbol for the Network Monitor and choose "remove from panel"
2) Right click the panel again and choose "add to panel"
3) Pick the "Network monitor"

I was just about to say the same.  This should definitely work.

---

### Post by ugasoft on 2007-05-31
Hi all, I've the same problem and I don't understand your proposed solution...

I've upgraded from 6.10 to 7.04 on my laptop. Edgy recognized my wireless card while Feisty doesn't.

It is a little unbelievable...

How can I make my wireless connection working? 

I say once again that yesterday, with ubuntu 6.10, it worked!!!

---

### Post by ninewives on 2008-03-09
I ran into the same problem, in a way that I suspect will affect a number of people, and the solution is not mentioned here, so I think this will be useful.  My situation is that I have a Dell laptop and I need to run Ubuntu 6.06.1.  So, in order to get my wireless network to work, I had to follow the instructions at [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)  (a VERY EXCELLENT guide).

When I recently applied updates automatically, the wireless card stopped working.  To make a long story short, the problem is that the kernel gets upgraded to 2.6.15-51, and then the command "sudo modprobe nidswrapper" returns the error "Error inserting ndiswrapper ... invalid argument".

To make another long story short, the solution is to update ndiswrapper.  HOWEVER, the latest version 1.52 doesn't work, because it won't compile.  I was running 1.47, and I found that it fixed it to upgrade to 1.48.  There may be other versions between 1.48 and 1.52 that compile and work, but I stopped when I got one that worked.

To do the update, just follow the instructions of the excellent guide at [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092) again.  You can omit the "wget ... R151517.EXE" and the "sudo echo blacklist ...", and when you do the "sudo make uninstall" you should do it in the "old" directory.

Note that a temporary workaround you can use, for example, to download the new version of ndiswrapper, is to boot under the kernel that you had before the update, because grub saves a startup link for you to boot with the old kernel.

Good luck, hope this is helpful!

---

### Post by ninewives on 2008-03-09
Oops, I forgot to mention one thing ... when you do the update, you can stop after the "sudo make install".  In other words, don't do "Step 4" Install Drivers" because all that stuff is still set up.

---

### Post by cvbruce on 2008-03-19
I was fighting this one for while, too.

I found the following via Google, but in the end, I checked the system on my Dell Latitude and the wireless device (Centrino chip) was OFF!!!!  Now it's ON and everything works.

quote:
Hi,

I'm pretty new too and setup my new Centrino laptop on Ubuntu 6.10 a few days ago (and I didn't even know what my ESSID was, just my key (only that parts written on the outside of my router).

Here's how I did it, I understand your computer froze when you tried to type in your password but maybe (hopefully that won't keep happening...).

1. I opened Applications | Accessories | Terminal
2. Tapped in apropos wireless (apropos tells you about commands related to a keyword  )
3. Played around with the various wireless tools, eventually discovered that
4. Tapping in 'iwlist eth1 scanning' discovered all available WiFi networks in the vicinity (there's a few) and gave me my ESSID too .
5. Went into System | Administration | Networking and
6. unticked Wired Connection, since I didn't want to use it, and ticked Wireless Connection.
7. Then I clicked on Wireless Connection and then properties just to the right of it.
8. Made sure the tick box in the corner ("enable this connection") was on and then copied and pasted the ESSID from Terminal, changed "Password Type" to "Plain (ASCII)" because my password contains letters other than just 0-9 and a-f (e.g. x and s) and so was clearly not a Hexidecimal password.
9. Checked "Automatic Configuration (DHCP)" was selected from the drop-down and hit OK.
10. Clicked the Save icon up the top (the floppy disc) and saved the details as Ed's Flat (I'm living at my friend's flat whilst he's in OZ for a few months, that's why I didn't know the ESSID).
11. Pressed Close, opened up Firefox and it was working.

This should be all there is to it.
If it's still not working, make sure you PC does not have an external killswitch for turning the WiFi on/off - most laptops do, switch it to the On position. If one of these was present and turned off, you'll likely need to reboot and then follow the above instructions (the relevant ones anyway) from the start.'
(end quote)

---

