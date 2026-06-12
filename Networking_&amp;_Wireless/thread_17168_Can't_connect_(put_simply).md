---
title: "Can't connect (put simply)"
date: 2005-02-26
forum: Networking &amp; Wireless
---

### Post by refused777 on 2005-02-26
Hey guys,
I'm having another problem (after only just solving the last one). I cant seem to connect to the internet in Ubuntu. It starts dialling OK, but the 'noises' the modem makes last only half as long as normal, and then disconnects after a short period of silence from the modem with no errors displayed. It's almost like it's missing a step in the connction process and the ISP is not letting it through.

My ISP is Wanadoo UK and my modem is a 3Com 56k Message Modem connected through the serial port.

Thanks in advance for any help!

---

### Post by alastair on 2005-02-26
Check the logs. I'm not sure where they go, but somewhere in /var/log.

If you can, you can have a terminal open and "tail" the logs as you dial. So you see the dialling messages/errors as they happen i.e.

sudo tail -f /var/log/syslog

(or best log file - check the newest after dialling attempt)

---

### Post by refused777 on 2005-02-26
Since my last post, Ubuntu now refuses to dial at all! There is no modem activity at all now.

As requested, here is the logfile.

Heres the part before it started refusing to dial: 

```
Feb 26 18:45:47 localhost wvdial[5533]: WvDial: Internet dialer version 1.54.0 
Feb 26 18:45:47 localhost wvdial[5533]: Initializing modem. 
Feb 26 18:45:47 localhost wvdial[5533]: Sending: ATZ 
Feb 26 18:45:47 localhost wvdial[5533]: ATZ 
Feb 26 18:45:47 localhost wvdial[5533]: OK 
Feb 26 18:45:47 localhost wvdial[5533]: Sending: ATL1 
Feb 26 18:45:47 localhost wvdial[5533]: ATL1 
Feb 26 18:45:48 localhost wvdial[5533]: OK 
Feb 26 18:45:48 localhost wvdial[5533]: Modem initialized. 
Feb 26 18:45:48 localhost wvdial[5533]: Sending: ATDT147008089916080 
Feb 26 18:45:48 localhost wvdial[5533]: Waiting for carrier. 
Feb 26 18:45:48 localhost wvdial[5533]: ATDT147008089916080 
Feb 26 18:46:04 localhost wvdial[5533]: CONNECT 9600/ARQ/V34/LAPM/V42BIS 
Feb 26 18:46:04 localhost wvdial[5533]: Carrier detected.  Waiting for prompt. 
Feb 26 18:46:04 localhost wvdial[5533]: ~[7f]}#@!}!}!} !}!}$}%\}"}&} }*} } }#}%B#}%}%}&z?}#q}'}"}(}"}1}$}%b[14]d~ 
Feb 26 18:46:04 localhost wvdial[5533]: PPP negotiation detected. 
Feb 26 18:46:04 localhost pppd[5529]: Serial connection established.
Feb 26 18:46:04 localhost pppd[5529]: Using interface ppp0
Feb 26 18:46:04 localhost pppd[5529]: Connect: ppp0 <--> /dev/ttyS0
Feb 26 18:46:08 localhost pppd[5529]: Remote message: Password: 
Feb 26 18:46:08 localhost pppd[5529]: PAP authentication failed
Feb 26 18:46:14 localhost pppd[5529]: Connection terminated.
Feb 26 18:46:14 localhost pppd[5529]: Hangup (SIGHUP)
Feb 26 18:46:14 localhost pppd[5529]: Terminating on signal 15.
Feb 26 18:46:14 localhost wvdial[5643]: WvDial: Internet dialer version 1.54.0 
Feb 26 18:46:14 localhost wvdial[5643]: Initializing modem. 
Feb 26 18:46:14 localhost wvdial[5643]: Sending: ATZ 
Feb 26 18:46:14 localhost wvdial[5643]: ATZ 
Feb 26 18:46:15 localhost wvdial[5643]: OK 
Feb 26 18:46:15 localhost wvdial[5643]: Sending: ATL1 
Feb 26 18:46:15 localhost wvdial[5643]: ATL1 
Feb 26 18:46:15 localhost wvdial[5643]: OK 
Feb 26 18:46:15 localhost wvdial[5643]: Modem initialized. 
Feb 26 18:46:15 localhost wvdial[5643]: Sending: ATDT147008089916080 
Feb 26 18:46:15 localhost wvdial[5643]: Waiting for carrier. 
Feb 26 18:46:15 localhost wvdial[5643]: ATDT147008089916080 
Feb 26 18:46:33 localhost wvdial[5643]: CONNECT 9600/ARQ/V34/LAPM/V42BIS 
Feb 26 18:46:33 localhost wvdial[5643]: Carrier detected.  Waiting for prompt. 
Feb 26 18:46:33 localhost wvdial[5643]: ~[7f]}#@!}!}!} !}!}$}%\}"}&} }*} } }#}%B#}%}%}&v=[02]>}'}"}(}"}1}$}%baz~ 
Feb 26 18:46:33 localhost wvdial[5643]: PPP negotiation detected. 
Feb 26 18:46:33 localhost pppd[5529]: Serial connection established.
Feb 26 18:46:33 localhost pppd[5529]: Using interface ppp0
Feb 26 18:46:33 localhost pppd[5529]: Connect: ppp0 <--> /dev/ttyS0
Feb 26 18:47:20 localhost pppd[5529]: Hangup (SIGHUP)
Feb 26 18:47:20 localhost pppd[5529]: Modem hangup 
``` 

And here's the bit where it starts refusing:

```
Feb 26 18:47:32 localhost pppd[5896]: unrecognized option '/dev/modem'
Feb 26 18:47:32 localhost pppd[5898]: pppd 2.4.2 started by root, uid 0
Feb 26 18:47:33 localhost pppd[5898]: Serial connection established.
Feb 26 18:47:33 localhost pppd[5898]: Using interface ppp0
Feb 26 18:47:33 localhost pppd[5898]: Connect: ppp0 <--> /dev/ttyS0
Feb 26 18:47:35 localhost pppd[5898]: Serial line is looped back.
Feb 26 18:47:35 localhost pppd[5898]: Connection terminated.
Feb 26 18:47:36 localhost pppd[5898]: Exit.
Feb 26 18:47:38 localhost pppd[5965]: The remote system is required to authenticate itself
Feb 26 18:47:38 localhost pppd[5965]: but I couldn't find any suitable secret (password) for it to use to do so.
``` 


Please help!

Thanks again in advance.

---

### Post by alastair on 2005-02-26
I've never used wvdial, and haven't used dialup for a long time.

But it looks like there is a problem with the communication between you and your ISP i.e. the link is up, but the chat is wrong.

Check the username, password and any other config for how the communication happens. You should know what the ISP server prompts you for and what you need to reply i.e. prompts - login, password, protocol etc. - or whatever.

---

### Post by refused777 on 2005-02-26
It's funny though, because I'm not aware I'm using a program called wvdial. I'm connectiong to the internet by going to the Computer menu, then into the Network settings area, then pressing 'Activate'. And in there, there are not a lot of options to change the chatter between me and my ISP - it seems to be fairly LAN/broadband centered. Is there a better program for editing my dial up settings?

---

### Post by refused777 on 2005-02-26
Here's something interesting.

When I try wvdial at the command line, it says:

/dev/modem: No such file or directory

Strange. Does this mean Ubuntu has not detected my modem?

---

### Post by alastair on 2005-02-26
I'll have to get back to you about this. I just went through the pain of getting my modem working on my laptop again - and finally managed it. But using fairly basic pppd and a chat script. This will not neccessarily be of use to you. The wvdial program notes (/usr/share/doc/wvdial) says that it is "intelligent" - but if it doesn't work then ... you are perhaps stuck *except to use normal methods like chat scripts and pppd).

The "required to authenticate itself" message might just be needing "noauth" in /etc/ppp/options, rather than "auth".

Your modem is /dev/ttyS0, but you could just make a link to /dev/modem i.e.

sudo ln -s /dev/ttyS0 /dev/modem

Not elegant though - and udev might rewrite (if you use udev).

Your logs show a connection happens - but the logging in (use/pass etc.) is not happening correctly.

---

### Post by m4ng0 on 2005-02-26
You can also take a look at:
[http://www.ubuntulinux.org/wiki/DialupModemHowto](http://www.ubuntulinux.org/wiki/DialupModemHowto)

---

### Post by taken on 2005-02-27
I had a somewhat similar problem that still hasn't been solved completely. :(

Here's what I did:
1. Deleted all the connections in the Computer>>System Configuration>>Networking.
2, Run the pppconfig command. (See previous post.)
3. Using pon still doesn't work after this but adding a new connection in the Networking worked.

By the way, make sure that when using pppconfig, you switch from CHAP (default) to PAP (default for Microsoft Windows connections.) That might be the problem.

And oh yeah, anyone has an idea on how to make pon work for me?

---

### Post by scooby on 2005-03-12
Hi, total newbie to linux here. Been browsing the threads and this is the closest to my issue. I've installed Ubuntu 4.10 on an older pc and can't get my external modem to work (typing from a w2k machine). I have 2 external modems, a US robotics sportster 56k and a motorola modemSURFR 56k (motorola is currently plugged in). I have tried both the 'networking- setup a PPP connection' and the 'terminal- sudo pppconfig' methods as detailed on the web; the modem is autodetected at /dev/ttyS0 by networking option but has to be manually found by the sudo method. The modem doesn't seem to connect- never actually dials. At least with 'sudo pon' it appears the pc is trying to, I set up the modem light and it counts in the left box awhile but never activates the modem. By that I mean if I pick up the phone I still hear a dialtone even when it should be dialing; I also get a message of connected but 0m transferred (once again, at any point in the procedure when I pick up the receiver I get a dialtone as though nothing is attempting to access the line). If I type sudo poff I get something like no active connection (after about 30 sec; if I type that before it apparently 'thinks' it's disconnecting). Help/suggestions?

---

### Post by scooby on 2005-03-12
OK, I had to enter a string to init the modem; it now connects (I hear the dial and handshake stuff) but I still can't go online: firefox can't find anything; synaptic doesn't either

---

### Post by jllitvay on 2005-04-06
I have the same problem with my USR2976 hardmodem. I got a script that make ubuntu detect it, dial via pppconfig/pon , make the modem noises but do not connect. pppnegociation failed.
Any help?

---

