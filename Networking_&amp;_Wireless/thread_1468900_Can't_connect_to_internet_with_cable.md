---
title: "Can't connect to internet with cable"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by Hunnter on 2010-05-01
Hey peeplz,

I'm completely new to linux so I appologise in advance if I haven't provided enough info :P
Anyways, I'm having trouble connecting to the internet... I'm using Ubuntu 10.04 on a PC with Windows XP installed. When I click the little network icon at the top there's an option called "auto eth1" but when I click it, it just says "Wired Connection: Disconnected - you are now offline." I've looked through the help files and forums but I can't find anything which helps. :(

If anyone can help I'ld greatly appreciate it!

Carl

---

### Post by garvinrick4 on 2010-05-01
> **Hunnter said:**
> Hey peeplz,

I'm completely new to linux so I appologise in advance if I haven't provided enough info :P
Anyways, I'm having trouble connecting to the internet... I'm using Ubuntu 10.04 on a PC with Windows XP installed. When I click the little network icon at the top there's an option called "auto eth1" but when I click it, it just says "Wired Connection: Disconnected - you are now offline." I've looked through the help files and forums but I can't find anything which helps. :(

If anyone can help I'ld greatly appreciate it!

Carl
Right click on the network icon on the upper right panel and check enable wireless.

---

### Post by Iowan on 2010-05-01
> **garvinrick4 said:**
> Right click on the network icon on the upper right panel and check enable wireless.I'll be curious to see if that helps with his wired connection.;)

If it says "Disconnected", then **ifconfig -a** (from a terminal) will probably reveal no IP address. (Also from a terminal) You might check **sudo lshw -C network** for more information about your interface. Also, if machine is supposed to get DHCP address, you could try (still from terminal) **sudo dhclient eth0**

Just noticed the "eth1"... is there an "eth0"?

---

### Post by Hunnter on 2010-05-02
hey,

When I right click the icon, "Enable Networking" and "Enable Notifications" are ticked, there were no other options. "Connection Information" is greyed out.

I just tried those two commands, but when I tried the first it asked for a password then said "sudo: Ishw: command not found". I tried the second command with both eth0 and eth1 at the end and it seemed to work but I dont understand the output :P I've attached a screenshot if that helps.

It doesn't currenlty show eth0, it did when I first installed the OS but I switched the ethernet cable from slot 1 to slot 2 to see if it made any difference

---

### Post by Iowan on 2010-05-02
That's a lowercase "L" - short for _l_i_s_t _h_ard_w_are.
**dhclient** was unsuccessful getting an IP address on eth1... :(

---

### Post by Hunnter on 2010-05-03
> **Iowan said:**
> That's a lowercase "L" - short for _l_i_s_t _h_ard_w_are.

ahhh, ok :P

I've just tried "sudo lshw -C network" but it didn't output anything :( it did look like it was doing *something* but there was no output afterwards.

I've attached a screeny of ifconfig in case there's any useful info in there but it doesn't look like it (the ethernet cable is plugged into port 1 now so it should be eth0 again)

---

### Post by outer_space on 2010-05-04
I have the same problem.  It just started this morning when I updated and it asked to restart.  When I restarted, it says ETH0 is 'disconnected' though clearly its connected and the connection works because I tried plugging it into a laptop and it worked. How can I get ethernet back on my desktop?

---

### Post by vigneshs on 2010-05-06
hi 
 I am also new to ubuntu(and linux :D) .Today morning i created a usb live and tried to boot from it.I had problems.
  My network is not working it seems to be smiler to the one discussed here.It is a cable internet.It works on xp.I have tried previous versions of ubuntu(9.4,9.10 live cd).Had no problems. I was planing to install the new ubuntu (finaly ).It is a 64 bit version(does it mater,previous versions were 32bit).

---
1.8 GHz athlon 64,2gb ram,GF 6100,(How do i find my network hardware?,It seems to be using NVIDIA nForce Networking Controller #2, does that mean something?) 

--
Thanks

---

### Post by akshaypande1989 on 2010-05-06
I installed Ubuntu Lynx netbook version yesterday. It isn't able to detect and connect to my wired network automatically, like karmic used to. My network itself is working fine (currently using on the same computer with dual boot in windows.)
 
Is the wired network in Lynx not "out of the box"? Must something extra be done?

---

