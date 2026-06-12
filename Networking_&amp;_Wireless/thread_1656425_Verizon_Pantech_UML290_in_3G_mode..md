---
title: "Verizon Pantech UML290 in 3G mode."
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by dogpile1000 on 2010-12-30
I wish Verizon had 4G in my area but not yet.  I do get very good 3g speed considering I am coming off of satellite internet access(sucks 2sec latency).  I did have the usb modem working from laptop running windows xp in 3g mode with no issues.  I have Ubuntu 10.10 have read all the other posts and anything I found in Google search.  

Below is my wvdial.conf[INDENT]root@htpc:/etc# cat /etc/wvdial.conf
[/INDENT][INDENT][Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=3,"IPV4V6","vzwinternet","0.0.0.0",0,0
Modem Type = USB Modem
Stupid Mode = 3
New PPPD = yes
Dial Command = atdt
Carrier Check = no
ISDN = 0

[ Dialer Verizon3G ]
Modem = /dev/ttyACM0
Baud = 3100000
Phone = #777
Username = 518#######@vzw3g.com
Password = vzw

[ Dialer Verizon4G ]
Modem = /dev/ttyACM0
Baud = 100000000
Phone = *99***3#
Username = 518#######@vzw4g.com
Password = vzw
[/INDENT]I run "wvdial Verizon3G" and constantly get the below output except once when I did get connected :confused:.[INDENT][INDENT]root@htpc:/etc# wvdial Verizon3G
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=3,"IPV4V6","vzwinternet","0.0.0.0",0,0
AT+CGDCONT=3,"IPV4V6","vzwinternet","0.0.0.0",0,0
OK
--> Modem initialized.
--> Sending: atdt#777
--> Waiting for carrier.
atdt#777
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: atdt#777
--> Waiting for carrier.
atdt#777
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: atdt#777
--> Waiting for carrier.
atdt#777
NO CARRIER
--> No Carrier!  Trying again.
^CCaught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Thu Dec 30 21:04:32 2010

[/INDENT][/INDENT]I have trided to reproduce how I got it to work once but have had no luck.  Does anyone see something I am missing?[INDENT]root@htpc:/# wvdial Verizon3G
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=3,"IPV4V6","vzwinternet","0.0.0.0",0,0
AT+CGDCONT=3,"IPV4V6","vzwinternet","0.0.0.0",0,0
OK
--> Modem initialized.
--> Sending: atdt#777
--> Waiting for carrier.
atdt#777
CONNECT 3100000
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Thu Dec 30 19:30:36 2010
--> Pid of pppd: 2885
--> Using interface ppp0
--> pppd: [08][7f]
--> pppd: [08][7f]
--> pppd: [08][7f]
--> pppd: [08][7f]
--> local  IP address 10.160.213.15
--> pppd: [08][7f]
--> remote IP address 69.83.13.52
--> pppd: [08][7f]
--> primary   DNS address 69.78.134.231
--> pppd: [08][7f]
--> secondary DNS address 69.78.80.231
--> pppd: [08][7f]
^CCaught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: [08][7f]
--> Connect time 4.2 minutes.
--> pppd: [08][7f]
--> pppd: [08][7f]
--> pppd: [08][7f]
--> Disconnecting at Thu Dec 30 19:34:48 2010
[/INDENT]

---

### Post by alexfish on 2010-12-31
Hi

can try changing the lcp echo requests and failures

Code:
[COLOR=Blue]
sudo gedit /etc/ppp/options[/COLOR]

find the following lines and set values

[COLOR=Blue]lcp-echo-failure 0[/COLOR]
[COLOR=Blue]lcp-echo-interval 0[/COLOR]

you can look up the meaning of the error codes in pppd man pages

Code:

man pppd

alexfish

---

### Post by dogpile1000 on 2010-12-31
alexfish I tried that with no luck.  From what I can tell from the first success I had that wvdial starts pppd after carrier is detected.

[INDENT]--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Thu Dec 30 19:30:36 2010wvdial 

[/INDENT]

---

### Post by dogpile1000 on 2010-12-31
I did figure out that vzaccess manager must be issuing/setting specific  AT commands to the usb modem/connection.  What I found is from vzaccess manager in windows xp I  connect.  Then while connected unplug the modem and connect it to ubuntu and issue the wvdial command I get connected and carrier.  Any one know of a way to trace the AT commands in windows.

---

### Post by PatchesTheCaveman on 2010-12-31
> Any one know of a way to trace the AT commands in windows.

Go to Network Connections in the Control Panel, and right click on the Verizon connection and hit Properties.  Switch to the Security tab and check the *Show terminal window* box.  Then try connecting to the Verizon connection.  A black box will appear while connecting that should show you the modem commands you need.

---

### Post by alexfish on 2011-01-01
> **dogpile1000 said:**
> alexfish I tried that with no luck.  From what I can tell from the first success I had that wvdial starts pppd after carrier is detected.[INDENT]--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Thu Dec 30 19:30:36 2010wvdial 

[/INDENT]

Hi

must have been tired when looking at your post


according to the info from wvdial you are setting to dial CID

AT+CGDCONT=3,"IPV4V6",[COLOR=Blue]"vzwinternet[/COLOR]","0.0.0.0",0,0

you are dialing #777

Try changing to *99***3#

the #777 is connecting as highlighted in blue

--> pppd: [08][7f]
--> local IP address 10.160.213.15
--> pppd: [08][7f]
--> remote IP address 69.83.13.52
--> pppd: [08][7f]
-[COLOR=Blue]-> primary DNS address 69.78.134.231
**--> pppd: [08][7f]**
--> secondary DNS address 69.78.80.231[/COLOR]

 Best try to find if the Primary and Secondary DNS servers are correct, Ask Verizon what these should be , as with most 3g + connections they know how the device be connected by the payplan

ASK inf :APN  DNS1 DNS2

IE correct APN relative to your Plan ,connects to the correct server , these servers then know it is the correct connection , relative to your sim card..highlighted the APN above in blue

also check the browser the next time / note when using wvdial , for firefox , the work off line box needs to be unchecked

ADDED ; once correct info is found Network Manager can be set to use the CID dialing (IMPORTANT do not set the APN ,IE :[COLOR=Blue]LEAVE APN BOX BLANK[/COLOR] as this may send it to CGDCONT 1 ) may render it useless when back in windows 

 also to ensure correct severs are connecting set the IPv4 to use address only

enter the addresses in the DNS servers box

then from reading other info the correct user name and pass word need to be used relative to 3g or 4g( as to if these actually work remains to be seen). check your system log files

Can also see what happens when dialing  *99***1# or *99#

also you may find this how to useful 

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

TO FIND ALL the SETTINGS of  AT compatible  DEVICES , USING A SERIAL TERMINAL OR "HOW TO USE Linux TWO Terminals" it's at the begging of the how to (tryAT command AT&V)
it may save you sitting at the terminal for hours on end trying to find out which at commands to use or trying to find ( may also show Specific AT commands for the device)

---

### Post by dogpile1000 on 2011-01-02
I checked and don't see a security tab on my windows xp laptop.

---

### Post by SignTalk on 2011-01-03
> **dogpile1000 said:**
> [INDENT][Dialer Defaults]
Stupid Mode = 3

[/INDENT]

I have also been trying to get the UML290 working in a 3g only area.  I believe that "Stupid Mode = 3" is a typo in the original instructions.   Looking at the source, "Stupid mode" is a boolean and if  it is other than "1" (or string equivalent), it is taken as false. Setting it to "1" gets rid of the "Waiting for prompt" and starts pppd immediately.

The only method I have found to reconnect in Linux is to physically  remove the modem and plug it back in.  If a connection attempt is not  made soon after a signal is acquired (blue light), "NO CARRIER" is  returned.  I have not found a way to reset the modem while it is  connected.  I have tried unloading the kernel module and several AT  commands, but nothing else has worked for me.

---

### Post by SignTalk on 2011-01-04
How to configure your Pantech UML290 for 3G use: 

[http://www.evdoinfo.com/content/view/3492/64](http://www.evdoinfo.com/content/view/3492/64)

---

### Post by davisford on 2012-11-13
Did anyone on this thread find a resolution.  I am having the same issue with UML290 -- it isn't specific to 3G mode.  I am using 4G mode, and the same issue arises.

I'm using wvdial to connect.  I have init scripts that start it on a clean boot and usually it works fine.
The problem is that sometimes I wander somewhere where the network is lost, and there seems to be no way to get it back besides unplug/replug the hardware, and re-run wvdial.

I have tried the suggestions here [http://askubuntu.com/questions/645/how-do-you-reset-a-usb-device-from-the-command-line](http://askubuntu.com/questions/645/how-do-you-reset-a-usb-device-from-the-command-line) 

Including toggling the authorized bit, and running the C code that does an IOCTL reset.  Neither seem to work for this modem.  If I physically unplug it and plug it back in...wait a minute, then re-start wvdial, it works.

Once I lose network, if I kill wvdial/pppd, and restart it, all I get is NO CARRIER ad infinitum.

Has anyone found a resolution to this?

```

--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: atdt*99***3#
--> Waiting for carrier.
atdt*99***3#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: atdt*99***3#
--> Waiting for carrier.

```

---

### Post by wildmanne39 on 2012-11-13
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

