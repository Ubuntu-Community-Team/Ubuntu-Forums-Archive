---
title: "pppd question"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by around_the_block on 2011-10-16
Hi all, I've been working off and on for a long time on trying to get Ubuntu connected to the 'net with a dial up. I installed a driver for my external USB modem, got wvdial installed, and set the phone number, user and password in wvdial.conf. I think I am -THIS CLOSE- to surfing. What I got in the terminal last night was a message over and over about specifying a PPPD path. Tonight I get something similar:
( phone number changed)

james@james-KM400-8235:~$ sudo wvdial  
 [sudo] password for james:  
 --> WvDial: Internet dialer version 1.60  
 --> Cannot get information for serial port.  
 --> Initializing modem.  
 --> Sending: ATZ  
 ATZ  
 OK  
 --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0  
 ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0  
 OK  
 --> Modem initialized.  
 --> Sending: ATDT*00,000-0000
 --> Waiting for carrier.  
 ATDT*00,000-0000
 CONNECT 57600  
 --> Carrier detected.  Waiting for prompt.  
 ** Welcome to ISDN.net **  
 System Password:  
 --> Looks like a password prompt.  
 --> Sending: (password)  
 System Password:  
 --> Looks like a password prompt.  
 --> Sending: (password)  
 System Password:  
 --> Looks like a password prompt.  
 --> Sending: (password)  
 --> Don't know what to do!  Starting pppd and hoping for the best.  
 --> Starting pppd at Sat Oct 15 23:21:30 2011  
 --> Pid of pppd: 1469  
 --> Using interface ppp0  
 --> pppd: &#65533;[07]&#65533;[08][10][06]&#65533;[08] 
 --> pppd: &#65533;[07]&#65533;[08][10][06]&#65533;[08] 
 --> pppd: &#65533;[07]&#65533;[08][10][06]&#65533;[08] 
 --> pppd: &#65533;[07]&#65533;[08][10][06]&#65533;[08] 
 --> Disconnecting at Sat Oct 15 23:21:40 2011  
 --> The PPP daemon has died: A modem hung up the phone (exit code = 16)  
 --> man pppd explains pppd error codes in more detail.  
 --> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.  
 --> Auto Reconnect will be attempted in 5 seconds  
 

 

 What can I do to get connected? Please bear in mind that I'm a beginner of beginners. Thanks in advance.

---

