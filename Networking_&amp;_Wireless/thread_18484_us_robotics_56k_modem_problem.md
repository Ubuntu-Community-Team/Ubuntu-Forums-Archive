---
title: "us robotics 56k modem problem"
date: 2005-03-07
forum: Networking &amp; Wireless
---

### Post by thane on 2005-03-07
Hi,

This is the first time I have had a problem setting up Internet on Linux and desperately need some help.

I have looked up the documentation on how to do pppconfig at Ubuntu and have done it, at least I think correctly; i.e. , correct ttyS0 etc.  I try pon after having added the user, or sudo pon, or su and then pon, but the modem only lights up but does not ring out.

I have also tried to set up Internet with the Gnome tool in the menu, and it has worked sometimes, but rarely.

I have installed kde and have tried kppp. I can ring out but then it stops.  Here is what I get: 

ppplog:
Mar  6 01:50:28 localhost pppd[26869]: The remote system is required to authenticate itself
Mar  6 01:50:28 localhost pppd[26869]: but I couldn't find any suitable secret (password) for it to use to do so.
Mar  6 01:50:28 localhost pppd[26869]: (None of the available passwords would let it use an IP address.)

I have also run kppp from within a root terminal and get the following:
Opener: received OpenDevice
Opener: received RemoveSecret
Opener: received RemoveSecret
Opener: received OpenResolv
Opener: received OpenResolv
Opener: received KillPPPDaemon
Opener: received RemoveLock
Opener: received SetSecret
Opener: received SetSecret
Opener: received OpenLock

Opener: received OpenDevice
Opener: received ExecPPPDaemon
In parent: pppd pid 26300
Couldn't find interface ppp0: No such device
Kernel supports ppp alright.
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
pppd: The remote system is required to authenticate itself
pppd: but I couldn't find any suitable secret (password) for it to use to do so.pppd: (None of the available passwords would let it use an IP address.)
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
It was pppd that died
pppd exited with return value 1
Sending 26295 a SIGUSR1
Opener: received RemoveSecret
Opener: received RemoveSecret
Opener: received OpenResolv
Opener: received OpenResolv
Opener: received RemoveLock
Opener: received PPPDExitStatus
Opener: received PPPDExitStatus

I have tried to use wvdial but either get a message that it can't find /dev/modem or if I manage to edit the wvdial.conf file and put in /dev/ttyS0, it rings up, starts the process, but then opens and shuts down the connection three times in rapid succession and gives the following message:

thanes@thanes:~ $ sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT95460465619990
--> Waiting for carrier.
ATDT95460465619990
CONNECT 33600/ARQ/V34/LAPM/V42BIS
User Access Verification
Username:
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT95460465619990
--> Waiting for carrier.
NO CARRIER
ATDT95460465619990
--> No Carrier!  Trying again.
--> Sending: ATDT95460465619990
--> Waiting for carrier.
NO CARRIER
ATDT95460465619990
--> No Carrier!  Trying again.
--> Sending: ATDT95460465619990
--> Waiting for carrier.
ATDT95460465619990

I have also read before that it would be good to include the results from tail -f /var/log/messages. Here is what I get:

root@thanes:/home/thanes # tail -f /var/log/messages
Mar  6 22:38:06 localhost pppd[2787]: Connect: ppp0 <--> /dev/ttyS0
Mar  6 22:38:08 localhost pppd[2787]: Serial line is looped back.
Mar  6 22:38:08 localhost pppd[2787]: Connection terminated.
Mar  6 22:38:09 localhost pppd[2787]: Terminating on signal 15.
Mar  6 22:38:09 localhost pppd[2787]: Exit.
Mar  6 22:38:20 localhost gconfd (thanes-3879): Resolved address "xml:readwrite:/home/thanes/.gconf" to a writable configuration source at position 0
Mar  6 22:38:38 localhost gconfd (root-4036): starting (version 2.8.1), pid 4036 user 'root'
Mar  6 22:38:38 localhost gconfd (root-4036): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar  6 22:38:38 localhost gconfd (root-4036): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Mar  6 22:38:38 localhost gconfd (root-4036): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2

Could someone please help me???  [-o<

---

### Post by thane on 2005-03-10
I am going to make a reply to my thread. I copied the text you see above and googled it at work.  

What I found is that in the /etc/ppp/options file there is a line with the word auth. If that line is not commented out i.e., #auth (place a pound sign in front of it), then kppp, if you have installed and are using kde, will not work; you get the error messages shown above.

Now, I have modem lights linked to kppp instead of pon, and I can get out on the Internet fine. Pon and poff still do not work, and I haven't worried about wvdial.

I hope this helps anyone having trouble getting out on the Internet. If it does, please let me know and I'll try to get this fix more visible in Ubuntu help information.

If a Linux guru knows why pon and poff still only make my modem light up but not ring up my ISP, please let me know! 

/Thane  8)

---

### Post by landotter on 2005-03-10
[QUOTE=thane]. Pon and poff still do not work, and I haven't worried about wvdial.

I hope this helps anyone having trouble getting out on the Internet. If it does, please let me know and I'll try to get this fix more visible in Ubuntu help information.

If a Linux guru knows why pon and poff still only make my modem light up but not ring up my ISP, please let me know! 

/Thane  8)[/QUOTE]

Modem lights needs to know which accounts to pon and poff.

You can set this up w/o messing with kppp, I use both KDE and Gnome, and the configurations stay seperate, so don't feel scared trying. :P

Run "sudo pppconfig" in a terminal and answer the questions...then tell modem-lights to "pon accountname" and "poff accountname" using the accountname you created.

---

### Post by jllitvay on 2005-04-01
I have the USR2976 pci hardmodem.
well, after some work I got the pppconfig to recognize the modem.
pon (my isp configured in pppconfig) but
it recognize the modem, dials, make noise but ... do not finish the connection.
any tip?
I think is the pppconfig is not configured correctly, so it do not aswer the connection from ISP.

---

### Post by TheOtherShoe on 2005-05-29
[QUOTE=thane]
I have tried to use wvdial but either get a message that it can't find /dev/modem or if I manage to edit the wvdial.conf file and put in /dev/ttyS0, it rings up, starts the process, but then opens and shuts down the connection three times in rapid succession and gives the following message:

thanes@thanes:~ $ sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT95460465619990
--> Waiting for carrier.
ATDT95460465619990
CONNECT 33600/ARQ/V34/LAPM/V42BIS
User Access Verification
Username:
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT95460465619990
--> Waiting for carrier.
NO CARRIER
ATDT95460465619990
--> No Carrier!  Trying again.
--> Sending: ATDT95460465619990
--> Waiting for carrier.
NO CARRIER
ATDT95460465619990
--> No Carrier!  Trying again.
--> Sending: ATDT95460465619990
--> Waiting for carrier.
ATDT95460465619990
[/QUOTE]
 I believe you can fix your wvdial problem by enabling stupid mode. Just add a line to your wvdial.conf file that looks like this,

```
Stupid Mode = on
```
There is a checkbox for the same option in gnome-ppp.

Also make sure that you are in the dip group to get rid of 'cannot open modem' errors.

---

