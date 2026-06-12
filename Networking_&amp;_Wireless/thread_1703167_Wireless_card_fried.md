---
title: "Wireless card fried?"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by lonewolf88 on 2011-03-08
p, li { white-space: pre-wrap; } [FONT=Monospace]Toshiba T110 laptop/netbook, Ubuntu 10.04 Gnome, Dual boot with Win7 Pro.[/FONT]
[FONT=Monospace]
[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]2.8Gb memory; 3.7GB swap.[/FONT]
[FONT=Monospace]
[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]Wireless adaptor is Realtek 8191SE 802.11n; booting into kernel 2.6.32-29[/FONT]
[FONT=Monospace]
[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]Until kernel 2.6.32-28, this wireless card was not even recognised.[/FONT]
[FONT=Monospace]
[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]I can pick up wireless networks & connect to the network ok in hotels, [/FONT]
 [FONT=Monospace]airport lounges etc., but the browser fails to connect (Firefox "can't find the server blah blah..") and KMail, KNode do not recognise the connection.[/FONT]
[FONT=Monospace]
[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]Using Gufw, firewall configured to "Allow" all outgoing connections, [/FONT]
 [FONT=Monospace]"Reject" all incoming, no other rules.[/FONT]
 [FONT=Monospace] [/FONT]
 [FONT=Monospace]ifconfig shows[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]wlan0     Link encap:Ethernet  HWaddr 70:1a:04:39:f4:2a  [/FONT]
 [FONT=Monospace]          inet addr:10.167.33.201  Bcast:10.167.35.255 Mask:255.255.252.0[/FONT]
 [FONT=Monospace]          inet6 addr: fe80::721a:4ff:fe39:f42a/64 Scope:Link[/FONT]
 [FONT=Monospace]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
 [FONT=Monospace]          RX packets:4098 errors:0 dropped:0 overruns:0 frame:0[/FONT]
 [FONT=Monospace]          TX packets:521 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
 [FONT=Monospace]          collisions:0 txqueuelen:1000 [/FONT]
 [FONT=Monospace]          RX bytes:660059 (660.0 KB)  TX bytes:39968 (39.9 KB)[/FONT]
 [FONT=Monospace]          Interrupt:17 Memory:f8310000-f8310100 
[/FONT]
[FONT=Monospace]
[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]I have tried iptables -F but makes no difference.[/FONT]
[FONT=Monospace]
[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]System monitor also shows receiving & sending bytes.  Ping google.com times out.[/FONT]
[FONT=Monospace] [/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]These messages in sys log:[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]Mar  9 02:31:30 jp-laptop kernel: [ 2138.055788] rtl8192_SetWirelessMode(), [/FONT]
 [FONT=Monospace]wireless_mode:10, bEnableHT = 1[/FONT]
 [FONT=Monospace]Mar  9 02:31:30 jp-laptop connmand[1877]: wlan0 SCANNING[/FONT]
 [FONT=Monospace]Mar  9 02:31:36 jp-laptop connmand[1877]: wlan0 INACTIVE[/FONT]
 [FONT=Monospace]Mar  9 02:31:39 jp-laptop kernel: [ 2147.056924] rtl8192_SetWirelessMode(), [/FONT]
 [FONT=Monospace]wireless_mode:10, bEnableHT = 1[/FONT]
 [FONT=Monospace]Mar  9 02:31:39 jp-laptop connmand[1877]: wlan0 SCANNING[/FONT]
 [FONT=Monospace]Mar  9 02:31:45 jp-laptop connmand[1877]: wlan0 INACTIVE[/FONT]
[FONT=Monospace]
[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]Does this mean card is turning itself on and off?[/FONT]
[FONT=Monospace]
[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]Same issue running Win7 Pro; exactly same as described above, except with Firefox, Agent and Thunderbird.[/FONT]
[FONT=Monospace]
[/FONT]
[FONT=Monospace]Help desk from one hotel service provider could see the connection being dropped by the card from time to time, thought it may have been a router issue.  Rebooting the wireless router failed to help.[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]Hotel could connect ok with their laptop running XP. No issues for them.[/FONT]
[FONT=Monospace]
[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]I could understand maybe a Linux issue, but with Windoze doing the same;  is the card on the blink?  Or maybe something I am missing here?[/FONT]
[FONT=Monospace]
[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]Strangely enough, happened after I upgraded to kernel 2.6.32-020632 (I [/FONT]
 [FONT=Monospace]presume this was the upgrade,top kernel in the Grub list, but this kernel completely fails to read the wireless card) a couple of days ago, however I doubt if this is the issue, being same problem in Windoze? 
[/FONT]
[FONT=Monospace]
[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]Or is it the problem? Or just a coincidence?[/FONT]
[FONT=Monospace]
[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]Wired Ethernet connections no issue at all[/FONT]
[FONT=Monospace].[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]Any clues? Any diagnostics I can run?[/FONT]
[FONT=Monospace]
[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]Or is the card ready for a warranty claim through a difficult Toshiba drone? [/FONT]
 [FONT=Monospace]<shudder>[/FONT]

---

### Post by lonewolf88 on 2011-03-09
Err .... anyone?

---

### Post by Kirboosy on 2011-03-09
Hmmm since its doing it in Windows as well, you might have a bad chip...

Try updating the drivers manually in Windows and see if that helps. (I bet it won't since Ubuntu and Windows are having the same problem an they are independent of each other) If it doesn't I would go ahead and fire up the phone and call Toshiba.



~Caboose

---

### Post by lonewolf88 on 2011-03-10
> **Caboose885 said:**
> Hmmm since its doing it in Windows as well, you might have a bad chip...

Try updating the drivers manually in Windows and see if that helps. (I bet it won't since Ubuntu and Windows are having the same problem an they are independent of each other) If it doesn't I would go ahead and fire up the phone and call Toshiba.



~Caboose

Thanks, fearing that result, talking to a drone from Toshiba!

---

### Post by zenwalker on 2011-03-10
Does ping works?? 

Also you can use wget command to download data off server to check if its the browser problem. But i bet i wont be, since its same in winnie too. 

As you said its on and off status. May be that the chip might have lost a contact with the mobo properly. Get it repaired by a techy.

---

### Post by tgalati4 on 2011-03-10
Pull the battery out for an hour.  It might reset the wireless chip.

---

### Post by lonewolf88 on 2011-03-10
> **tgalati4 said:**
> Pull the battery out for an hour.  It might reset the wireless chip.

Thanks, have tried that.

Will be in airport lounge later, and will try to connect.

As another poster suggested;  maybe chip has come lose?  The laptop is in my briefcase and gets carried around a lot in luggage bins on planes.

---

