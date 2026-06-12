---
title: "Still Another Crashing KPPP"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by GuyK on 2009-01-01
I have seen two previous recent threads reporting KPPP  “crashes” that describe the problem I am having, which have not elicited a response. I'm going to provide some data that may provide a stimulus for someone to give some help. I'm trying to get Ubuntu 8.10 up and working and it is difficult without internet capability by dialup. I don't yet have wired broadband and must go to the local library for wireless.
I have had relatively uncomplicated success with KPPP in a couple of other Linux  implementations and am reasonably confident that I have configured it properly. BTW, I have installed KPPP in version 8.10 (because of my previous experience) expecting to have a dual desktop (gnome and KDE). The dual desktop function isn't working (this problem described in another thread here) but I am trying to run in gnome.

To date, KPPP has been flakey, not knowing which  which way it is going to terminate. One form has it claim that it can't find the device (ttyUSB1). Most often lately it will initialize the modem, dial, CONNECT reporting modem speed and indicating it is “Starting pppd.dial, CONNECT reporting modem speed and indicating it is “Starting pppd.” At this point it will either display a KPPP error window  saying “pppd daemon died unexpectedly” “Exit status: 0,” or it will just quit without a message. There is no evident indication of any login in transactions.   

Whenever I can see a transaction log it looks like this:

*********
Dec 31 09:16:27 guy-laptop pppd[8665]: pppd 2.4.4 started by guy, uid 0
Dec 31 09:16:27 guy-laptop pppd[8665]: Using interface ppp0
Dec 31 09:16:27 guy-laptop pppd[8665]: Connect: ppp0 <--> /dev/pts/3
Dec 31 09:16:57 guy-laptop pppd[8665]: LCP: timeout sending Config-Requests 
Dec 31 09:16:57 guy-laptop pppd[8665]: Connection terminated.
Dec 31 09:16:57 guy-laptop pppd[8665]: Modem hangup
Dec 31 09:16:57 guy-laptop pppd[8665]: Exit.

KPPP's best guess
The remote system does not seem to answer to configuration request. 
Contact your provider.







The transactions displayed on the console after issuing the KPPP command (which terminated with KPPP error window; i.e., “ppp daemon died...”) follow: 

*****
Opener: received SetSecret 
Opener: received SetSecret 
kppp(14549) Modem::opentty: Opening Device:  "/dev/ttyUSB1" 
Opener: received OpenDevice 
Opener: received ExecPPPDaemon 
In parent: pppd pid 14579 
Opener: received OpenResolv 
error opening resolv.conf! 
Kernel supports ppp alright. 
Couldn't find interface ppp0: No such device 
Couldn't find interface ppp0: No such device 
Couldn't find interface ppp0: No such device 
It was pppd that died 
pppd exited with return value 0 
Sending 14549 a SIGUSR1 
Opener: received RemoveSecret 
Opener: received RemoveSecret 
Opener: received OpenResolv 
Opener: received OpenResolv 
error opening resolv.conf! 
Opener: received PPPDExitStatus 
Opener: received PPPDExitStatus 
Opener: received OpenSysLog 
QLayout: Attempting to add QLayout "" to KDialog "", which already has a layout
*****

The transactions displayed on the console after issuing the KPPP command (which quit without a message) follow: 

*****
kppp(7513) Modem::opentty: Opening Device:  "/dev/ttyUSB1" 
Opener: received OpenDevice 
Opener: received ExecPPPDaemon 
Kernel supports ppp alright. 
received unexpected SIGCHLD. 
In parent: pppd pid 7700 
Opener: received OpenResolv 
error opening resolv.conf! 
Couldn't find interface ppp0: No such device 
Couldn't find interface ppp0: No such device 
Couldn't find interface ppp0: No such device 
           .
           .           #  Several pages of line here have been deleted
           .
           .
Couldn't find interface ppp0: No such device 
Couldn't find interface ppp0: No such device 
Opener: received KillPPPDaemon 
In killpppd(): Sending SIGTERM to 7700 
Opener: received RemoveSecret 
Opener: received RemoveSecret 
Opener: received OpenResolv 
Opener: received OpenResolv 
error opening resolv.conf! 
Opener: received KillPPPDaemon 
In killpppd(): Sending SIGTERM to 7700 
Opener: received RemoveLock 
Opener: received SetSecret 
Opener: received SetSecret 
Opener: received OpenLock
************* 
So, there it is. I hope that somebody can make some sense out of this for me.

Let me know whether there is anything more that I can provide

Guy K

---

