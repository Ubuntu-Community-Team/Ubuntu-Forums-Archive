---
title: "Accessing mythtv is unresponsive"
date: 2013-01-05
forum: Mythbuntu
---

### Post by rivode on 2013-01-05
Hi,

I'm having issues with anything accessing mythbackend, and I hope someone here might know what's going on.  Everything seems to work fine until it attempt to record something.  I can set up a recording, and the computer wakes up and the USB tuner shows a blue light, which means it's tuned in.  Nothing gets recorded and any attempt to access the backend fails.  Nothing seems to be using significant amounts of CPU time.

Using the frontend from a remote computer shows a lot of messages like this, once I select the "recorded programs" function:

```
2013-01-06 13:21:49.354303 I  MythCoreContext: Connecting to backend server: 192.168.181.3:6543 (try 1 of 1)
2013-01-06 13:21:56.358295 E  MythSocket(3100d60:40): readStringList: Error, timed out after 7000 ms.
2013-01-06 13:21:56.358403 C  Protocol version check failure.
			The response to MYTH_PROTO_VERSION was empty.
			This happens when the backend is too busy to respond,
			or has deadlocked in due to bugs or hardware failure.
```

In Mythweb, if I try to access the list of recorded programs or the TV guide, I see messages in the browser like this:

```
User Notice at /usr/share/mythtv/bindings/php/MythBackend.php, line 105:
!!NoTrans: Unexpected response to MYTH_PROTO_VERSION '72': !!

```

I've tried reinstalling a few times, and I don't think I've done anything stupid but I wouldn't be surprised.  I've attached various logs, debug traces and package information.  I don't see anything obvious in syslog.  I notice that there's various error messages about accessing the database, yet I can access it from the mysql client fine.  I didn't have this problem with Mythbuntu versions older than 12.04.  Does anyone know what's going on?

---

### Post by Lester_Burnham on 2013-01-06
Hi,

Can you check if you have two different config.xml files.
I had one good one in ~/.mythtv/ and a dud in /etc/mythtv/, which seems to be the one mythbackend checks.

I just symlinked to good one to /etc/mythtv/

Not sure if its your problem, but it was mine :)

Lester

---

### Post by topcat5 on 2013-01-06
I looked through your logs, and it seems that your backend is unable to open a tcpip socket to your SQL DB.   It's attempting to connect to it via the hostname of "spud".   

This could be caused by a number of things, but you might first want to verify the networking and name resolution to make sure that 'spud' resolves to an actual working address.

---

### Post by rivode on 2013-01-07
Typical... it's working perfectly tonight.  I shut down the computer though - it didn't wake itself up from suspend.  Maybe there's problems connecting to the database after it does, which I'll check next time it wakes itself up.

> **topcat5 said:**
> make sure that 'spud' resolves to an actual working address.

'hostname' and 'ping' works, but I'll check again next time I have problems.  Maybe I'll try to set an IP address instead.

> **Lester_Burnham said:**
> I just symlinked to good one to /etc/mythtv/


I already have that link there, it must have been put there upon installation.

Thank you for the ideas, I'll check them next time I have issues.

---

### Post by Lester_Burnham on 2013-01-07
Sounds very much like network and resuming from suspend.

I've always used ACPI wake for recording. Not had the interest to chase the grief with tuners and network when resuming. (Only once actually :))
If you want something closer to an appliance, it's worth chasing if you've got the time.

---

### Post by topcat5 on 2013-01-07
I'd also make sure your hosts file has been updated to include the hostname pointing to the loopback address and to the real IP.

---

### Post by rivode on 2013-01-08
> **Lester_Burnham said:**
> 
I've always used ACPI wake for recording.


My computer doesn't wake up if it's shut down - only if it's suspended!  And to top it off, the USB tuner doesn't like being suspended - I have to rmmod it first, which means shutting down mythtv.  This wasn't a problem in previous versions.

I looked at my suspend script and noticed that I stopped and restarted networking, which probably wasn't needed.  My script now looks like this:

```
/usr/bin/mythshutdown --shutdown
service mythtv-backend stop
/bin/sleep 1
/sbin/rmmod dvb_usb_af9015
sleep 1
/usr/sbin/pm-suspend

/bin/sleep 1
modprobe dvb_usb_af9015
sleep 1
service mythtv-backend start

```

And for some reason, suddenly I have to run  [[FONT="Courier New"]sysctl -e -w i8042.reset=1[/FONT]]("https://wiki.archlinux.org/index.php/Pm-utils#Resume_from_suspend_shuts_down_instead_of_wake_up"), otherwise the computer shuts down as soon as it wakes up!  I've never had to do that before.

> **topcat5 said:**
> I'd also make sure your hosts file has been updated to include the hostname pointing to the loopback address and to the real IP.

I'll give that a shot too.  My hosts file contained:

```
127.0.0.1	localhost
127.0.1.1	spud

```

---

### Post by rivode on 2013-01-08
The computer woke up, recorded something and shut down again... hopefully not restarting networking did the trick.  Thanks for your ideas!

---

### Post by rivode on 2013-01-09
Things are working well now.  I notice that in 12.04 they started using dnsmasq to do the name resolution, so maybe this has something to do with that.

---

