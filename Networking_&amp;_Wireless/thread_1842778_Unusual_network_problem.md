---
title: "Unusual network problem"
date: 2011-09-12
forum: Networking &amp; Wireless
---

### Post by AndyGJ on 2011-09-12
[FONT=Arial][SIZE=2]Hi there, I have whats either an infuriating or an interesting riddle, depending on where you stand on these things!

I have a ubuntu 10.04 server machine that has been around for a long time now. I can't remember the exact install date, but I reckon 3 or 4 years. Its been running with the same static network config for this entire time.[/SIZE][/FONT][FONT=Arial][SIZE=2]

Its been upgraded from ubuntus past and is now used as for XBMC, with ubuntu being a deliciously stable backend.[/SIZE][/FONT][FONT=Arial][SIZE=2]

Until Saturday night that is![/SIZE][/FONT][FONT=Arial][SIZE=2]

I was trying a new XBMC remote control app for android. I mention this despite myself because it was the only thing that changed between a completely 100% functional install and where I am now. I was testing the remote and it lost connection while loading thumbnails. Noticed that the machine had lost its network connection, and that networking restart and/or a reboot didn't fix it.[/SIZE][/FONT][FONT=Arial][SIZE=2]

I tried a bit of troubleshooting yesterday, and this was the results.[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[LIST=1]
[*][FONT=Arial][SIZE=2]Swapped cable, no joy.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Link light active on both      network card and router.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]2 other machines work wired      and wireless.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Network card still shows up      in lspci[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]ifconfig shows static      address assigned and connected. Few RX packets (like 4 or 5) but nothing      else to speak of.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Tried DHCP (was getting      desperate) - no DHCP offers.[/SIZE][/FONT]
[/LIST]
[FONT=Arial][SIZE=2]  At that point I was fresh out of ideas. My next option is something that I really don't want to have to try, and suspect its unnecessary - I figure if i re-install the OS it will probably resolve the issue. That’s not how i want to do it though!

So can anyone give me any idea where to look next? I'm not next to the machine right now, and naturally my ability to SSH to it has been fatally removed, but im quite happy to run some diagnostics and post the results later tonight.[/SIZE][/FONT][FONT=Arial][SIZE=2]

Im baffled as to what could have happened here. The only thing i can think left to try is to make sure I've completely halted XBMC to ensure something hasn't hung and taken out the network card somehow, but that seems outrageously unlikely. [/SIZE][/FONT]  [FONT=Arial][SIZE=2]

Any help gratefully received.[/SIZE][/FONT]

---

### Post by racoffey63 on 2011-09-12
[SIZE=2][FONT=Arial]I tried a bit of troubleshooting yesterday, and this was the results.[/FONT][/SIZE]

[LIST=1]
[*][FONT=Arial][SIZE=2]Swapped cable, no joy.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Link light active on both network card and router.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]2 other machines work wired and wireless.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Network card still shows up in lspci[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]ifconfig shows static address assigned and connected. Few RX packets (like 4 or 5) but nothing else to speak of.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Tried DHCP (was getting desperate) - no DHCP offers.[/SIZE][/FONT]
[/LIST][FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Have you verifies the ifconfig ip and the router ip are in the same net?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Can you ping your machine?[/SIZE][/FONT]

---

### Post by AndyGJ on 2011-09-12
Hi, indeed they are. There were no configuration changes between the connection working and not.

ifconfig displays the correct static values, correct gateway etc. Pinging the router or my machine results in "destination host unreachable" with the ubuntu machines ip address given. Strangely, not for every packet though - the seq numbers are not consequtive. 

Can't ping any machines from the ubuntu machine. If it wasn't for the link light id be assuming my ethernet card had imploded to be honest.

---

### Post by racoffey63 on 2011-09-12
I'm new to ubuntu and on my work computer, so can't work out that side to well.  But your #3, You physically plugged 2 other boxes into the line you use for your server?
 
Also, is your server just hardwired or hardwire and wireless?

---

### Post by AndyGJ on 2011-09-12
Yes, my first reaction is that a port on the router had gone bad. So I tried the server in another 2 ports, with no change. Then I turned wifi off on my laptop, then tried it with the same cable and port as the server was failing with. That worked fine, so i think ive eliminated cables / ports as being potential issues.

The server has a single ethernet card (its a realtek integrated one) set up as eth0, with no other network interfaces present.

---

### Post by racoffey63 on 2011-09-12
[SIZE=2][FONT=Arial]The only thing i can think left to try is to make sure I've completely halted XBMC to ensure something hasn't hung and taken out the network card somehow, but that seems outrageously unlikely. [/FONT][SIZE=2]

[/SIZE]I'm thinking  it didn't take out your network card, just take it over.  liking it into something like a VPN to your remote.
[/SIZE]

---

### Post by AndyGJ on 2011-09-12
I think ill try killing all of the XBMC procs when I get in - it only listens as a web server though, so I can't see how it could have caused this.

Still, ive seen stranger things happen ;)

---

### Post by racoffey63 on 2011-09-12
Everything works right in theory, nothing works right in reality.  LOL  If everything worked before XBMC and doesn't work after, then it's probly the cause.  Good luck

---

### Post by AndyGJ on 2011-09-12
Just to clarify in case anyone else has any ideas - everything worked fine with XBMC installed as well, I only mention it because I was using the XBMC web interface at the time it bombed out.

Thanks for your help :)

---

### Post by AndyGJ on 2011-09-12
Ok, I tried to kill all the xbmc stuff, but didn't get any joy. sudo killall -9 xbmc kills off the running processes but restarting networking or bringing eth0 up and down after that still doesn't do anything.

However, some log reading did bring up some interesting results.

I have a rtl8139, and checking syslog after a boot shows a message from netdev watchdog telling me that I have a "transmit queue timed out" error from eth0. 

This results in an error and a stacktrace from xbmc.bin,  so I then completely disabled xbmc and rebooted - this time the same error, but from swapper. So it looks like an error thats being triggered by anything using the network, rather than xbmc specifically.

Right, so ive narrowed it down. Googling that led me [to this ]("http://ubuntuforums.org/showthread.php?t=1139789")

However, no fix there. Also, its not quite the same error I think - those guys seem to be able to work around the issue at least - no amount of bringing the interface up and down resolves this one.

Im pretty much at the limit of my knowledge here now, I'm not sure what to try next really - does anyone have any suggestions?

---

