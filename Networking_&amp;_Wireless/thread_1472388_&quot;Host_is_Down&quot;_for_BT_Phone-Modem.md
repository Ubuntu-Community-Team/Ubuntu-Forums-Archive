---
title: "&quot;Host is Down&quot; for BT Phone-Modem"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by RMOP on 2010-05-04
10.04 on an eeePC 701 with a BT connection to a Nokia E71

This was working FINE on 9.04 and earlier versions, but I must have lost some crucial aspects of the configuration in the upgrade to 10.04, even though I used the same wvdial and rfcomm .conf files which I kept aside for just such an event.

I have paired my phone to Ubuntu via Bluetooth, and can connect to it and browse files on the phone from Ubuntu. I thought I'd gotten the new configuration right, but when running wvdial (after unmounting the phone file system), I get the following error:

**--> Cannot open /dev/refomm0: Host is down**

other information:

[B]$ sudo rfcomm bind /dev/rfcomm0 00:11:22:33:44:55 2
Can't create device: Address is already in use

$ hcitool dev
hci0 00:11:22:33:44:55[/B]

$ hcitool scan reports the correct MAC and Channel for my phone, but I'm obviously missing something crucial.

It doesn't tell us much, but if I connect the same phone to the same eeePC via USB cable, the Mobile Broadband connection works just fine.

Anyone able to assist on this, please? Sure, I can post .conf files if needed, but will await a relpy.

Many thanks.

**UPDATED:** using my original settings, I got a solid connection using wvdial from the command prompt as well as from a icon on the panel. Looked good. However, **after DISCONNECTING and trying to RECONNECT**, I get the message:

**--> Cannot open /dev/rfcomm0: Device or resource busy**

Nearly there -- if I sort this on my own, I'll post a brief howto for those who want a short guide...but I'm not there yet.

UPDATED AGAIN: This is getting interesting. After yet another reboot, wvdial WORKED like before, both from command line and from the panel icon which points to wvdial. I tried this several times, and all seemed fine, but then...

The dreaded error message:

**--> Cannot open /dev/rfcomm0: Device or resource busy**

returned and persists. I've not rebooted again, but suspect that might restart things. I need to know what's behind this nonsense and how to fix it.

Help on this, please?
[B]
UPDATED yet AGAIN...[/B]

After a reboot, I've been able to connect/disconnect multiple times w/o a problem but, sooner or later, I get the "Device or resource busy" error message. I can't say where the problem is, but there is one. A reboot only solves the problem for a time. Then it's back.

***Comments appreciated.***

---

### Post by RMOP on 2010-05-07
I decided to repy to my own post in order to update things, rather than making another edit to the original.

Current status: I've got TWO similar 10.04 systems running now. One is an eeePC 701 and the second is a Toshiba NB205. Unbuntu, on both machines, is installed to an SD card (two different SD cards).

Initially, I was using the same BT dongle, switching it between machines as needed for testing. Since, however, and thanks to the good advice in THIS forum, I've gotten the on-board BT working on the NB205. Now, I'm getting similar if not always identical results on both machines.

Both can connect to my Nokia E71 and browse files. Both can initially connect to the E71 as a modem, at least after a reboot. Sometimes, I can (manually) connect/disconnect/reconnect multiple times using wvdial from a command prompt. If I use ^C to disconnect, I'm USUALLY returned to the command prompt, though not always. Sometimes wvdial won't terminate, and I have to close the terminal.

AFAIK, my issues are configurational, not HW-specific.

I've tried using pon.wvdial and poff.wvdial, hoping that might generate different results. It DOES, but not what I wanted: after using pon.wvdial and making a connection and then exiting via ^C, I get:

**--> Cannot open /dev/rfcomm0: Device or resource busy**

when I try to reconnect.

Interesting...after getting that error, I turned BT OFF/ON (on the NB205 - haven't gotten to this on the eeePC yet) and then wvdial connected w/o complaint. Maybe this is progress? I'd previously pulled the BT dongle to no avail, but didn't actually toggle BT OFF/ON.

Since the initial toggle of BT, I've been able to connect/disconnect/reconnect using pon.wvdial and poff.wvdial repeatedly. If I issue pon.wvdial to connect, and poff.wvdial (in a 2nd terminal, of course), wvdial doesn't exit, and I still have to use ^C to return to a command prompt (in the first terminal). If is issue a straight wvdial command and use poff.wvdial in the second window, wvdial exits completely.

So, FWIW, I seem to be able to get out of the error state by toggling BT OFF/ON. Not sure WHY this works, and would appreciate any insights.

**This might mean something.** When I toggled BT OFF/ON, there was OUTPUT to the (first) terminal at the command prompt in BOLD below):

msl@IDELL:~$ --> WvDial: Internet dialer version 1.60
--> Cannot open /dev/rfcomm0: Device or resource busy
--> Cannot open /dev/rfcomm0: Device or resource busy
--> Cannot open /dev/rfcomm0: Device or resource busy
^C
msl@IDELL:~$ --> [B]pppd: `;&#65533; &#65533;6&#65533; &#65533;<&#65533; 
--> Connect time 0.3 minutes.
--> pppd: `;&#65533; &#65533;6&#65533; &#65533;<&#65533; 
--> pppd: `;&#65533; &#65533;6&#65533; &#65533;<&#65533; 
--> pppd: `;&#65533; &#65533;6&#65533; &#65533;<&#65533; 
--> Disconnecting at Fri May  7 11:32:06 2010
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot open /dev/rfcomm0: No route to host
--> Cannot open /dev/rfcomm0: No route to host
--> Cannot open /dev/rfcomm0: No route to host
--> Disconnecting at Fri May  7 11:32:06 2010
^C
msl@IDELL:~$[/B]

I'm sure this is unrelated, but I'll throw in the only other error messages that display when dialing:

--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.

Not sure what this is about, but it seems NOT to affect the ability to make a PPP connection. And I'm not sure why wvdial would need to modify those files anyway...

Comments appreciated. Thanks.

---

