---
title: "Intermittent Connectivity using Huawei E 1550 USB Modem on Ubuntu 10.4"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by czue on 2010-08-18
Hi,

I've spent a lot of time trying to read and learn as much as possible with respect to making my modem configuration work, but it doesn't seem like anyone has the same problem I have and so I'm trying to post it here.

I have a Huawei E 1550 USB stick modem and I'm trying to consistently get it working with Ubuntu 10.4.  Using usb_modeswitch and wvdial I've got the device recognized as both a modem and disk drive and it seems to be working okay.  wvdial usually is able to find the modem and connect and I can get online no problem.  That's the good part.

However, after some amount of time (sometimes just a few minutes, sometimes hours, but it always eventually happens) the modem stops working and gets into a state where when I run wvdial it keeps looping and failing with:

```
ATDT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
```Interestingly enough, when it's in this state I am still able to access the modem, and via AT commands am able to see that it has signal, can make phone calls, and can send SMS messages!  It just can't seem to dial a data connection.

Now, unplugging and plugging the modem back in almost always seems to solve this problem, only for it to fail randomly at some undetermined point in the future.

Why can't I just keep unplugging and replugging the modem, you ask?  Because the computers (yes there are currently 9 computers and modems I need this to work on) are being deployed to clinics and offices in rural Africa where they will be locked in a box so they aren't stolen. 

I have pursued ways to shutdown power to the USB port in order to "fake" a hard pull of the cord in software, but haven't been successful so far.  I've also tried reading as much as I can on the NO CARRIER response, but so far it's not turned anything up.

The cell network I'm on is Zain Zambia (who sold us the modems) but I'm guessing that not a lot of people have much experience with them....

I'm wondering if anyone here has any ideas either in hard-resetting power to the modem or (better) solving the root cause of the NO CARRIER issue.  Unfortunately, I'm just about out of them. 

thanks much!

---

### Post by alexfish on 2010-08-18
not sure about the switching on of the device / possibly need to access the gpio
you would need to know if the facility exists on the modem , + the AT command to send

as regards your connection try using different tty ports either from gnomeppp

or if using wvdial run the configuration 

[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

hope this helps . also have a look at Sakis3g if your connection is 3g . looks as if it is from the dial command

regards

alexfish

---

### Post by Sakis3G on 2010-08-18
Hi Czue,

You may try experimenting with "-R" argument of Usb-ModeSwitch (see its man page).

Another one way that may work for you, is "soft-resetting" modem. Depending on modem/firmware:

[LIST]
[*]it may be possible or not,
[*]it may require resupplying PIN number or not.
[/LIST]

I've found it to be useful on some Alcatel modems (make sure you change ttyUSBX to whatever value is valid for your modem, type of quotes _does_ matter):
```
$ sudo bash
Password:
(Set modem on minimum functionality, that is, almost off:)
# chat -e "" '\pAT' OK AT+CFUN=0 OK '\pAT' OK >> /dev/ttyUSBX < /dev/ttyUSBX
(Set modem back to full functionality:)
# chat -e "" '\pAT' OK AT+CFUN=1 OK '\pAT' OK >> /dev/ttyUSBX < /dev/ttyUSBX

```If you find this one trick working, you may as well try disabling modem using AT+CFUN=4 (instead of AT+CFUN=0). This one sets modem on "flight mode" (i.e. no radio). It should be less "messy" and may help modem recover faster, when AT+CFUN=1 is sent (but may as well not be effective).

Some more AT commands you may find useful are:
**1.** Checks if modem needs PIN, and supplies 1234 as PIN. Does nothing if SIM is PIN-unlocked or SIM needs another number (like PUK).
```

# chat -e -t 2 ABORT READY "" '\pAT' OK 'AT+CPIN?' "SIM PIN" "" OK '\pAT' OK 'AT+CPIN="1234"' OK >> /dev/ttyUSBX < /dev/ttyUSBX

```**2.** Forces modem to detach and re-attach to GPRS packet domain:
```

(Check current status:)
# chat -e "" '\pAT' OK AT+CGATT? OK '\pAT' OK >> /dev/ttyUSBX < /dev/ttyUSBX
(Detach:)
# chat -e "" '\pAT' OK AT+CGATT=0 OK '\pAT' OK >> /dev/ttyUSBX < /dev/ttyUSBX
(Attach:)
# chat -e "" '\pAT' OK AT+CGATT=1 OK '\pAT' OK >> /dev/ttyUSBX < /dev/ttyUSBX

```We are waiting for your feedback,

Sakis

---

### Post by czue on 2010-08-19
Thanks Sakis!

Unfortunately so far nothing seems to be working.  For the commands you gave me, resetting the modem to CFUN=0 makes the light blink green twice (according to the reference this means that the modem is powered on but not on network).  Setting it back to CFUN=1 causes the light to change to a single blink (registering with a 2G network).  Running wvdial in either state still shows the NO CARRIER issue.

It doesn't seem to like CFUN=4 at all.  It goes into it ok and this triggers the double green light, but when I try to switch it out (to either 0 or 1) it responds with ERROR.  So far have't found a way to get it out of that state besides unplugging it.

Doesn't look like the PIN is the problem, and the GPRS commands also don't seem to do anything.  Any other thoughts?

Note: I tried using sakis3g as well, but couldn't figure out how to tell it that it didn't need a user/password.  Even when I tried sending APN_USER='' it complained that I didn't have one set.

---

### Post by Sakis3G on 2010-08-19
At first, when no username and password are required by APN, you need to set something anyway. If your operator indeed does not need it, it will work. Try these for example: APN_USER="foo" APN_PASS="bar" and it will work.

Since it seems not that easy to work around this problem, we should establish a plan. Possible causes:

[LIST]
[*] Wrong modem initialization:
[LIST]
[*] You can try connecting with Sakis3G and check whether initialization done by Sakis3G prevents this behavior.
[*] In case your Windows driver contains an *.inf file containing AT commands, you may have a look there for locating an AT command which looks interesting.
[/LIST]
 
[*] Buggy modem firmware (which by the way, I sense is the reason):
[LIST]
[*] Check with another modem model whether this behavior persists. If no other modem is available, you may get your hands on a 3G cellular phone. Almost all 3G capable phones (with a USB port), expose their modem as a USB interface.
[/LIST]
 
[*] Something wrong with pppd/setup (I doubt about it. Problem looks like being beyond USB port):
[LIST]
[*] Maybe try with another distribution.
[*] If possible, try with one operating system for which drivers are embedded on device.
[/LIST]
 
[*] Something wrong with operator:
[LIST]
[*] Try inserting a SIM card from another operator on modem and check if behavior persists. If modem is locked-to-network, try inserting modem's SIM card on an another modem/phone and check if problem persists.
[*] If it is indeed operator derived, since replugging modem works, you could try those AT commands below. These instruct modem to re-register on network (I doubt it will work, since CFUN commands also result into same thing, but you should try it as well).
[/LIST]
 
[/LIST]
 
Command is AT+COPS (abbreviation for "operator selection"). 
**1.** Checks whether command is supported. Any modern modem should be OK with this one and return available networks (scans for network). When using it with chat-program you need to provide argument -t (timeout) to a large value, as it may take long for modem to respond. Example: chat -e -t 120 "" AT OK 'AT+COPS=?' OK AT OK
```

AT+COPS=?

```**2.** Returns current settings:
```

AT+COPS?

```Response is of the following format: <mode>,[<format>,<operator>]
**Mode** denotes network search mode and can be:
0 = Automatic network registration. Whichever network allows access and has better signal is automatically selected.
1 = Manual network selection. This means that <format> and <operator> fields will be present, denoting currently "manual" settings, _even if modem is currently unable to reach assigned network_.
2 = Instructed to _not_ register any network.
4 = Manual network selection (same as 1), but, in the absence of appointed network, it will automatically switch to Automatic mode (same as 0). This one is more like a "preference mode".

**Format** denotes format in which <operator> field is presented and can be:
0 = Long string representation of network name (which might be different from operator name, in case operator is a VNVO or MVNO, I don't remember exactly. Anyway, if operator is a virtual operator using another operator's network).
1 = Short string representation of network name (suitable for being displayed by cellular phones).
2 = Numeric ID of network. 5 or 6 digits. First three denote country code, the rest uniquely identify network within country.

[b]Operator[b] field provides selected network detail specified by <format> field. This field is not present when modem is not registered to any operator, with the exception of modes 1 and 4.

**3.** Set command. Sets preferences of network search mode and preferred network. Additional mode "3" is supported, for setting preferred format without changing value.
```

Sets numeric presentation for further queries:
AT+COPS=3,2

``````

Manually selects network 20205:
AT+COPS=1,2,"20205"

```Idea behind these all, is to force modem to attempt and log another one network (so that it disconnects from present one) and then instruct it to re-register correct one (in case this fixes NO CARRIER issue). Also, I would suggest to use a terminal emulation software than mess with chat from command line, as it might take long (gtkterm is a good one). Scenario is like this (example lists numeric IDs of Greek networks, you adapt accordingly):
```

# Request that all information is printed with numeric IDs. Trust me, is better like this:
You type:      AT+COPS=3,2
Modem replies: OK
# Read currently registered network
You type:      AT+COPS?
Modem replies: AT+COPS=0,2,"20205"
Modem replies: OK
# Scan for available networks (it will take a while):
You type:      AT+COPS=?
# I don't remember exact format, but should look like:
Modem replies: AT+COPS=(..."20201"...), (..."20205"...), (..."20210"...)
Modem replies: OK
# You then instruct it to register a random other one:
You type:      AT+COPS=1,2,"20201"
Modem replies: OK
# And then force it to re-register home network:
You type:      AT+COPS=1,2,"20205"
Modem replies: OK

```Have terminal software closed (for the ttyUSB port to get released) and try connecting again.

Sakis

---

### Post by czue on 2010-08-19
So I'm maybe making progress by following your first line of reasoning (wrong modem initialization).

Sakis3G does seem to produce wildy different behavior than wvdial for me.  A few things of note:

After connecting via sakis3g the modem now shifts between 3G and GPRS mode (I can tell because the indicator light says what it thinks it's doing, and flip flops between blue (3G) and green (Edge/GPRS)).  There is NO 3G in this country yet, so blue mode seems odd.  

sakis3g seems able to connect, but treats it as a 3G connection.  The modem is able to get an IP, but then after about 3-5 seconds get's kicked off and loses connection.  Then it blinks green for a bit and goes back to blue.  At one point sakis3g established a green connection, and the modem seemed very happy.  Not to say that the problem was gone, but it was as reliable a connection I've been able to get from one of these guys. 

Continuing down this road I'm wondering:

Is there a way to see what AT commands/calls are being used by sakis3g?  
Is there a way to tell sakis3g to not try to use 3G but only to use GPRS (want to see if this solves the problem)?
What AT command can I use to switch the modem that now wants to use 3G back to GPRS? (it continues to try blue when being plugged into other machines now, failing)
Does sakis3g have auto-connect and auto-reconnect functionality?

We have already started looking at other available modems here.  If it is the firmware we will definitely switch models.  I'm also planning on trying with a Nokia 2700c.

Haven't tried the pppd config or another operator yet.  I will be buying a few more SIM cards tomorrow to pursue that route.

The COPS route seemed like a dead end (same behavior when switching as everything else -- still NO CARRIER).

Again, thanks for all the excellent advice so far.

Cory

---

### Post by Sakis3G on 2010-08-19
> **czue said:**
> After connecting via sakis3g the modem now shifts between 3G and GPRS mode (I can tell because the indicator light says what it thinks it's doing, and flip flops between blue (3G) and green (Edge/GPRS)).  There is NO 3G in this country yet, so blue mode seems odd.
We cannot tell for sure what modem considers Blue or Green. It may be as well be based on both effective speed and allocated slots from cell. If there is no 3G, there is no way it could get an IP while being blue. But it does. So, blue led does not really mean 3G for this one modem.


> **czue said:**
> The modem is able to get an IP, but then after about 3-5 seconds get's kicked off and loses connection.  Then it blinks green for a bit and goes back to blue.
During the time it was "kicked off" do you happen to also witness lines like these on your syslog?
```

option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0 
option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1 
option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2 
option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3 
usb 2-3: GSM modem (1-port) converter now attached to ttyUSB0 
usb 2-3: GSM modem (1-port) converter now attached to ttyUSB1 
usb 2-3: GSM modem (1-port) converter now attached to ttyUSB2 
usb 2-3: GSM modem (1-port) converter now attached to ttyUSB3 
option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0 
option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1 
option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2 
option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3 
usb 2-3: GSM modem (1-port) converter now attached to ttyUSB0 
usb 2-3: GSM modem (1-port) converter now attached to ttyUSB1 
usb 2-3: GSM modem (1-port) converter now attached to ttyUSB2 
usb 2-3: GSM modem (1-port) converter now attached to ttyUSB3 

```> **czue said:**
> Is there a way to see what AT commands/calls are being used by sakis3g?
Yes, there is. Enabling debug mode will produce a full log on what it thinks and what it does (I am including arguments I already know you use, you should add whatever else you use as well). Debug mode works better when being already root when invoking Sakis3G. Reason is that (for security reasons), sudo does not allow a user process to capture output from a process running with root privileges. So you should do it like this (which as well employs text-mode UI, so that it gets captured as well on log):
```

$ sudo bash
Password:
# sakis3g APN_USER=foo APN_PASS=bar iterm debug 2>&1 | tee sakis3g.log

```> **czue said:**
> Is there a way to tell sakis3g to not try to use 3G but only to use GPRS (want to see if this solves the problem)?
Not directly. Reason is that this sometimes relies on device dependent AT commands. What you can use is [INIT variable]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_configuration#INIT") like this:
```

sakis3g INIT="AT+COPS=1,2,\"XXXXX\",Y"

```Where XXXXX is your network ID and Y can be 0 (GPRS) or 2 (3G) or vice versa (can't remember). Sakis3G script will then add your commands just before dialing/invoking pppd. It may not work though. Reason is that double quotes surrounding XXXXX are required (according to specifications), but Sakis3G removes them from arguments, to avoid being injected by a malicious user providing specially crafted shell commands. So, we actually hope that your modem will accept command even without double quotes. What seems to made your modem act like this is those previous AT+COPS commands I suggested you (I am sorry. I don't really remember commands that well, by heart).


> **czue said:**
> What AT command can I use to switch the modem that now wants to use 3G back to GPRS? (it continues to try blue when being plugged into other machines now, failing)
**Update:** I found nothing specific for your modem. Just try using standard AT+COPS with that additional argument (see above).


> **czue said:**
> Does sakis3g have auto-connect and auto-reconnect functionality?
Not directly. It is only possible when using [**--pppd** switch]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_configuration#pppd") along with [**PPPD_OPTIONS** variable]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_configuration#PPPD_OPTIONS") like this:
```

sakis3g pppd PPPD_OPTIONS="modem crtscts -detach defaultroute dump noipdefault replacedefaultroute usepeerdns usehostname ktune logfd 2 noauth name sakis3g lock persist maxfail 3"

```This will attempt to re-establish a dropped connection three times, before failing. What you need is "maxfail 0" which means try forever, even if you get failures. But I advise you not to set maxfail to 0 at this moment (before problem is resolved).


Sakis

---

### Post by Sakis3G on 2010-08-19
Bump. Post above ^^ is now updated.

---

### Post by lemonsqueeze on 2013-01-03
Hi,
I had a somewhat similar issue with a huawei E1762, except problem was on startup: either it would just work, or i'd be getting "NO CARRIER" forever.

It seems the modem is getting confused when wvdial starts talking to it before it's registered: waiting until network registration is done solved it for me. Maybe something similar is happening here also ?

Here's the [full story.]("http://superuser.com/questions/527543/randomly-getting-no-carrier-from-huawei-3g-modem-under-linux/")

---

