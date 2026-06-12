---
title: "Cannot connect to the net"
date: 2005-01-26
forum: Networking &amp; Wireless
---

### Post by taken on 2005-01-26
My modem is detected and the information provided by the ISP is correct too. (I have doubled checked and used two different ISPs)

Yet once my modem connects to the ISP, it is automatically disconnected. I didn't have this issue with Red Hat or Windows.

Any clues, people?

---

### Post by az on 2005-01-26
Do:

sudo pppconfig
and enter the neccessary info.
sudo pon
sudo tail -f /var/log/messages

and share the output here:

---

### Post by aleXL on 2005-01-27
'nuther newbie... I've got the same problem on a pal's machine... using wantodo... I'll post the output when I get to his machine again tomorrow morning...

3Com/USR 56 Voice Faxmodem (External Grey)... ttsy1... as the ttsy0 port doesn't seem to work/detect...

I really, really admire this distro...

---

### Post by taken on 2005-01-27
[QUOTE=azz]Do:

sudo pppconfig
and enter the neccessary info.
sudo pon
sudo tail -f /var/log/messages

and share the output here:[/QUOTE]

I'm online!

I don't know exactly how I did, and the connection is really slow, and Gaim doesn't but I'll work on making it faster now.

Ok,
Here is what I did.
In sudo pppconfig, I entered the information and changed the "CHAP" which was the default to "PAP". After that I typed:

sudo pon

And I got an error which said "*/usb/sbin/ppd: In file /etc/ppp/peers/provider unrecognized option '/dev/modem'*"

Continuing with the instructions I typed:
sudo tail -f /var/log/messages
and the output was:
[I]Jan 28 12:37:51 localhost pppd[4026]: Serial line is looped back.
Jan 28 12:37:51 localhost pppd[4026]: Connection terminated.
Jan 28 12:37:52 localhost pppd[4026]: Exit.
Jan 28 12:37:54 localhost pppd[4096]: pppd 2.4.2 started by root, uid 0
Jan 28 12:37:56 localhost pppd[4096]: Serial connection established.
Jan 28 12:37:56 localhost pppd[4096]: Using interface ppp0
Jan 28 12:37:56 localhost pppd[4096]: Connect: ppp0 <--> /dev/ttyS0
Jan 28 12:37:57 localhost pppd[4096]: Serial line is looped back.
Jan 28 12:37:57 localhost pppd[4096]: Connection terminated.
[/I]
After this, I tried using the GUI connection and it didn't disconnect me!
Any ideas of what is going on? And

---

### Post by taken on 2005-01-30
Ok, I'm still not online.

Turns out that I get disconnect within 1-10 minutes everytime. On top of that, my connection is           S            L                0                         W.

Also, I have turned off the "reconnect on failed connection or disconnection" (can't remember the exact words) in the GUI of Computer>System Settings>Networking and yet, everytime I get disconnect, my modem tries to reconnect.

Help!

---

### Post by mikeandy on 2005-01-30
Hi..Just installed Ubuntu...can't get on the net..My router is a SMC8204WBR..Do I need a driver ? Tried Prism54..but Ubuntu not able to use the tar file..says that obselete code used Please help ! :? (Very new to Linux ) Save me from giving up and reverting back to Windows !

---

