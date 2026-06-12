---
title: "pppd &quot;Terminating on signal 15&quot; (SIGTERM) - Where is the signal coming from?"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by ziesemer on 2009-06-02
I'm using a 3G wireless (cellular) card for Internet access, connected using pppd, as fully documented [on my blog]("http://blogger.ziesemer.com/2008/10/alltel-um175al-usb-evdo-ubuntu.html").  I originally had this setup under 8.04 (Hardy), followed by 8.10 (Intrepid) and now 9.04 (Jaunty).

Unfortunately, I'm having an issue where pppd is terminating rather than redialing when the connection is dropped.  I had this happen intermittently on the previous OS releases, but now it is happening consistently and I cannot figure out why.

The high-level issue is that when the "Modem hangup" is detected, "persist" is enabled and pppd should redial.  Instead, the "Modem hangup" is being followed by a "Terminating on signal 15" message, which causes pppd to exit and no redial is attempted.

System details:

```
$ uname -a
Linux z-util 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

pppd version 2.4.5
```

Looking at the source code in /ppp-2.4.5git/pppd/main.c, the logic seems pretty simple.  From handle_events:

```

...
    waiting = 0;
    calltimeout();
    if (got_sighup) {
        info("Hangup (SIGHUP)");
        kill_link = 1;
        got_sighup = 0;
        if (status != EXIT_HANGUP)
            status = EXIT_USER_REQUEST;
    }
    if (got_sigterm) {
        info("Terminating on signal %d", got_sigterm);
        kill_link = 1;
        asked_to_quit = 1;
        persist = 0;
        status = EXIT_USER_REQUEST;
        got_sigterm = 0;
    }

```

Since asked_to_quit is never set, the main loop in the main method should pause for the holdoff (if set), then redial.  However, it certainly seems that a separate SIGTERM / signal 15 is being received following the "hangup", which then causes the loop to break and pppd to exit.

Here is a section of the PPP log from an actual modem session:

```

Script /etc/ppp/ip-up started (pid 6737)
Script /etc/ppp/ip-up finished (pid 6737), status = 0x0
Hangup (SIGHUP)
Modem hangup
Connect time 16.4 minutes.
Sent 71444 bytes, received 183221 bytes.
Script /etc/ppp/ip-down started (pid 7049)
Connection terminated.
Script /etc/ppp/ip-down finished (pid 7049), status = 0x0
Terminating on signal 15

```

Where is this signal 15 (SIGTERM) coming from?  Is there any method or tool to trace it?  I don't see anywhere in the pppd source where it sends the signal to itself.

I normally have this connection configured as an "inet ppp" entry in /etc/network/interfaces.  For the purposes of ruling some of that out, I ran pppd directly, using "pppd call Alltel debug nodetach persist" - and had the same issue where the "signal 15" is received and logged, and causes pppd to exit.

This is really getting to me, and I really wanted to try to find out what was causing this.  To rule out my ISP, data card, and even USB (and a lot of udev), I setup pppd on another box running as a mock server, and connected the two through the RS232 serial ports and a null-modem adapter.  I was able to reproduce the issue.  By sending a SIGHUP to the "server" pppd, the "client" logs the hangup, as well as a "Terminating on signal 15" - just like the actual issue I'm having with the 3G data card.  The only difference seems to be that the mock "server" using pppd seems a bit more courteous, and sends a reason of "User request" before disconnecting:

```

rcvd [LCP TermReq id=0x2 "User request"]
LCP terminated by peer (User request)
Connect time 1.6 minutes.
Sent 19734 bytes, received 0 bytes.
Script /etc/ppp/ip-down started (pid 24060)
sent [LCP TermAck id=0x2]
Script /etc/ppp/ip-down finished (pid 24060), status = 0x0
Connection terminated.
Modem hangup
Terminating on signal 15

```

Going back to the actual modem, I can't think of a way to "force" it to hangup / disconnect to test the redial short of disconnecting it from the USB cable.  This works, and does result in the same "Connection terminated.", "Modem hangup", and "Terminating on signal 15" messages.  However, I don't want to do this too often at risk of damaging the device.

I really need to find out where these 15 / SIGTERM signals are coming from.  This is a clean install of Jaunty.  I started removing / disabling all scripts in /etc/network/if-down.d, /etc/network/if-post-down.d, and /etc/ppp/ip-down.d, and wasn't able to resolve the issue.

My /etc/ppp/peers and /etc/chatscripts files are already documented [on my blog]("http://blogger.ziesemer.com/2008/10/persistent-ppp-ubuntu.html") (next post from previous), but included below for your convenience:

```

/dev/ttyACM0
lock

persist
#debug
hide-password

noauth
user ##########@alltel.net

defaultroute
#usepeerdns #Using bind9 instead.

init "/usr/bin/logger -i /etc/ppp/peers/Alltel Calling..."
connect "/usr/sbin/chat -Vf /etc/chatscripts/Alltel 2>/var/log/Alltel.log"

```

```

ABORT 'BUSY'
ABORT 'NO CARRIER'
ABORT 'ERROR'
'' 'AT'
'OK' 'ATQ0V1E0'
'OK' 'ATZ'
'OK' 'AT&F'
'OK' 'AT+CSQ'
'OK' 'ATDT#777'
CONNECT CLIENT

```

Any help would be greatly appreciated.  Please let me know if there are any additional logs I can provide or tests I can perform.  Thanks!

---

### Post by ziesemer on 2009-06-04
I finally have this somewhat narrowed down:  After removing the "auto ppp0" line from /etc/network/interfaces, I no longer observe the SIGTERM from happening.

It doesn't matter if I don't use "ifup ppp0" or "sudo call <peername>".  If the "auto ppp0" line is in /etc/network/interfaces, the SIGTERM happens.  Additionally, it doesn't seem to matter if the rest of the "inet ppp0" entry is in /etc/network/interfaces.  This means I can still use the ifup / ifdown commands.

My connection is still coming up automatically after system restart, but only because of a udev entry I added so that it would automatically reconnect after I would disconnect and reconnect the USB modem.  If I do something like "/etc/init.d/networking restart", I'll still need to manually restart ppp0 as well.

I think there were some scripts related to networking that, when run, read through the /etc/network/interfaces file, and operate based on the presence of an "auto <name>" line.  Unless anyone else can clue me in, I guess I'll have to keep searching and hopefully find the issue.

---

### Post by woltion on 2009-07-07
If you have not yet solved the issue, see [bug 396804]("https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/396804") which is the problem in Jaunty.

I personally fixed it by changing /lib/udev/rules.d/85-ifupdown.rules by replacing "--allow auto" with "--allow hotplug".

---

### Post by ziesemer on 2009-11-06
> **woltion said:**
> If you have not yet solved the issue, see [bug 396804]("https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/396804") which is the problem in Jaunty.

I personally fixed it by changing /lib/udev/rules.d/85-ifupdown.rules by replacing "--allow auto" with "--allow hotplug".

Thanks woltion, that was it exactly.

---

### Post by ziesemer on 2009-11-18
See also: [http://rants.atmurray.net/2007/01/pppd-persist-not-so-persist-with-udev.html](http://rants.atmurray.net/2007/01/pppd-persist-not-so-persist-with-udev.html)

---

### Post by Muzafsh on 2011-03-15
Hi folks,

I have been experiencing this error on my 3G connection since yesterday. Earlier to yesterday i had no issue as my 3G connection would connect each and every time i have attempted.

But since yesterday, its highly unstable. and is demonstrating strange behavior. One such behavior i have been able to duplicate is as follows.

Backdrop :
I am using a Gobi 2000 device for my 3G connection.
over an Ubuntu 10.10 OS.

I have configured my 3G connection to connect automatically on log on. when i start my laptop on a Ubuntu boot before yesterday the 3G connection would connect automatically. but since yesterday its not been connecting. It tries to connect for a few minutes and drops unsuccessfully. However the strange behaviour that i have been able to duplicate is that from this state when i restart my Ubuntu OS it connects to my 3G on this restart.

I am enclosing the syslog file with which has recorded one such instance of this behavior the first file attached is the log of the instance where the machine was powered on from a shutdown state which results in an unsuccessful 3g connection. and the second file attached is the log of the instance where the restarted session results in a stable and successful 3G connection.

Please help me in identifying the issue.

Do let me know if you require any more details.

UPDATE !!!

now the restart workaround has stopped working too...

pls find the syslog readings when i try connecting my 3G connection.


```

Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]: <info> Activation (ttyUSB0) starting connection 'Airtel 3G quality (GPRS)'
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]: <info> (ttyUSB0): device state change: 3 -> 4 (reason 0)
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Mar 16 00:49:52 ***LLAH-1 modem-manager[1038]: <info> Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
Mar 16 00:49:52 ***LLAH-1 modem-manager[1038]: <info> Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> connected)
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled...
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting...
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]: <info> (ttyUSB0): device state change: 4 -> 5 (reason 0)
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) successful.
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]: <info> Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete.
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]: <info> Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) started...
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]: <info> (ttyUSB0): device state change: 5 -> 7 (reason 0)
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]: <info> starting PPP connection
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]: <info> pppd started with pid 15438
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]: <info> Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) complete.
Mar 16 00:49:52 ***LLAH-1 pppd[15438]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
Mar 16 00:49:52 ***LLAH-1 pppd[15438]: pppd 2.4.5 started by root, uid 0
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar 16 00:49:52 ***LLAH-1 NetworkManager[1025]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Mar 16 00:49:52 ***LLAH-1 pppd[15438]: Using interface ppp0
Mar 16 00:49:52 ***LLAH-1 pppd[15438]: Connect: ppp0 <--> /dev/ttyUSB0
Mar 16 00:49:52 ***LLAH-1 pppd[15438]: CHAP authentication succeeded
Mar 16 00:49:52 ***LLAH-1 pppd[15438]: CHAP authentication succeeded
Mar 16 00:49:57 ***LLAH-1 vnstatd[1238]: Interface "ppp0" enabled.
Mar 16 00:50:13 ***LLAH-1 NetworkManager[1025]: <warn> pppd timed out or didn't initialize our dbus module
Mar 16 00:50:13 ***LLAH-1 NetworkManager[1025]: <info> (ttyUSB0): device state change: 7 -> 9 (reason 5)
Mar 16 00:50:13 ***LLAH-1 pppd[15438]: Terminating on signal 15
Mar 16 00:50:13 ***LLAH-1 modem-manager[1038]: <info> Modem /org/freedesktop/ModemManager/Modems/0: state changed (connected -> disconnecting)
Mar 16 00:50:13 ***LLAH-1 pppd[15438]: Connection terminated.
Mar 16 00:50:13 ***LLAH-1 NetworkManager[1025]: <info> Marking connection 'Airtel 3G quality (GPRS)' invalid.
Mar 16 00:50:13 ***LLAH-1 NetworkManager[1025]: <warn> Activation (ttyUSB0) failed.
Mar 16 00:50:13 ***LLAH-1 NetworkManager[1025]: <info> (ttyUSB0): device state change: 9 -> 3 (reason 0)
Mar 16 00:50:13 ***LLAH-1 NetworkManager[1025]: <info> (ttyUSB0): deactivating device (reason: 0).
Mar 16 00:50:13 ***LLAH-1 avahi-daemon[1019]: Withdrawing workstation service for ppp0.
Mar 16 00:50:13 ***LLAH-1 NetworkManager[1025]: <info> Policy set 'AMyCon' (wlan0) as default for IPv4 routing and DNS.
Mar 16 00:50:13 ***LLAH-1 NetworkManager[1025]: <info> Policy set 'AMyCon' (wlan0) as default for IPv4 routing and DNS.
Mar 16 00:50:13 ***LLAH-1 NetworkManager[1025]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar 16 00:50:14 ***LLAH-1 pppd[15438]: Exit.
Mar 16 00:50:17 ***LLAH-1 modem-manager[1038]: <info> Modem /org/freedesktop/ModemManager/Modems/0: state changed (disconnecting -> registered)
Mar 16 00:50:17 ***LLAH-1 vnstatd[1238]: Interface "ppp0" disabled.

```

Pls Help, so that i can have a stable 3G connection as before yesterday.

thanks,

---

