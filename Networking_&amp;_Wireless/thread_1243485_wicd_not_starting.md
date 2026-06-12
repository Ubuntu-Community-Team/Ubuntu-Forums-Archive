---
title: "wicd not starting"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by p110011 on 2009-08-18
Not sure what I messed up, but I was testing one of my routers and all that I can think of was that I unchecked automatically reconnect.

Now when I boot up the system says it needs to access my network cards, enter password and nothing happens. The wicd does not start.

Tried to start in the shell, and it says this:
   [SIZE=1]$ wicd-client[/SIZE]
  [SIZE=1]Has notifications support True[/SIZE]
  [SIZE=1]Loading...[/SIZE]
  [SIZE=1]Connecting to daemon...[/SIZE]
  [SIZE=1]Can't connect to the daemon, trying to start it automatically...[/SIZE]
  [SIZE=1]Connected.[/SIZE]
  [SIZE=1]ERROR:dbus.proxies:Introspect error on :1.28:/org/wicd/daemon: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)[/SIZE]
  [SIZE=1]warning: ignoring exception org.freedesktop.DBus.Error.ServiceUnknown: The name :1.28 was not provided by any .service files[/SIZE]
  [SIZE=1][SIZE=2][FONT=&quot]warning: ignoring exception org.freedesktop.DBus.Error.ServiceUnknown: The name :1.28 was not provided by any .service files[/FONT][/SIZE]

I tried to upgrade to 7.10 and still had the error, so I formated and installed 9.04
[/SIZE]

---

### Post by p110011 on 2009-08-19
I have not made progress and I'm not sure what is going on but, is the dbus, wicd or network dongle at fault?

What or where do these missing service files come from?

I mistype in my OP that the system asked for my password, it's actually wicd that says it needs my password. (It never did before)
 This is my lshw -c network
```
*-network DISABLED      
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:6a:33:f9:dc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2870 driverversion=1.52+Ralink Technology, Corp.,11 link=no multicast=yes wireless=IEEE 802.11g
```

I have it disabled and using Ethernet for now. 

I hope this is not hopeless because this OS has really worked well.

TIA, 

Gill

---

### Post by PatrickVogeli on 2009-08-19
last time I tried, I had to install Wicd from ubuntu's repositories, since the one I downloaded from the web wouldn't work. I don't know if it has changed since then, but if you installed from a .deb, you could trying removing that and install using apt-get install wicd.

---

### Post by p110011 on 2009-08-19
I tried completely removing and installing again from Synaptic manager and it does the same thing.:(

---

### Post by p110011 on 2009-08-20
It seams something is problematic with the dbus interface. After completely removing wicd and installing NM, I can see my network, but the connect button is grayed out. Manually setting up does no good either. 

Then I reinstalled wicd, and a message pops up that says some resources are missing.

Hopefully I'm not bumping this too soon, and someone can give me some help please.

Gill

---

### Post by maplon on 2009-08-28
I suddenly have the exact same problem with wicd 1.6.2-2 on Intrepid. 

Symptoms: On startup, I suddenly get a message telling me that wicd needs to access the network cards an have to provide my sudo password, which I do.

Still, "ps -ef | grep wicd" shows no running daemon and when I try to run wicd-client I get the same error message as the OP.

???

---

### Post by p110011 on 2009-08-28
> **maplon said:**
> I suddenly have the exact same problem with wicd 1.6.2-2 on Intrepid. 

Symptoms: On startup, I suddenly get a message telling me that wicd needs to access the network cards an have to provide my sudo password, which I do.

Still, "ps -ef | grep wicd" shows no running daemon and when I try to run wicd-client I get the same error message as the OP.

???
One thing I didn't try was booting into an older kernel, might try that.

---

### Post by maplon on 2009-08-28
> **p110011 said:**
> One thing I didn't try was booting into an older kernel, might try that.

I have this problem running the newest kernel that I have installed, 2.6.27-14, and the oldest one in the GRUB list. Happens with both.

Is this issue solved for you now? I see you marked this as solved, but cannot see how you did it.

Thx 

m.

---

### Post by p110011 on 2009-08-28
I did not really know how to mark it, but in my edit you can see that it formated and am now running 9.04

I googled dbus and wicd problems and never found any answers.

---

### Post by maplon on 2009-08-30
I have now solved this as well.

I upgraded to Jaunty. Wicd was not installed anymore, and I was not online. Using a different computer, I downloaded the .deb of wicd from the Ubuntu Jaunty repository, copied it to the laptop and installed it using dpkg -i.

It still didn't work: The daemon didn't start: "sudo /etc/init.d/wicd start" reported "OK", but "ps -ef | grep wicd" showed no running process, and trying "wicd-client" gave error messages similar to the one above.

After LOTS of googling and trying different solutions, this finally worked:

```
sudo wicd -foe
```

revealed a parsing error in /etc/wicd/wired-settings.conf   -- There was a line with an empty "[]" on it, which I simply removed (that line, not the file). (No clue how it got in there, since I never edited it manually.)

Now, /etc/init.d/wicd start  starts the daemon, and wicd-client works fine as well, and I'm back online. 

Phew.

---

### Post by DJ_Peng on 2009-09-28
Thanks, maplon, that helped me resolve my error as well. I'll post what I got when I ran your wicd command to help others resolve the issue more quickly.
```
:~$ sudo wicd -foe 
---------------------------
wicd initializing...
---------------------------
wicd is version 1.6.2.2 463
Traceback (most recent call last):
  File "/usr/share/wicd/wicd-daemon.py", line 1750, in <module>
    main(sys.argv)
  File "/usr/share/wicd/wicd-daemon.py", line 1714, in main
    daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
  File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
    self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
  File "/usr/share/wicd/wicd-daemon.py", line 1330, in __init__
    debug=debug)
  File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
    self.read(path)
  File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
    self._read(fp, filename)
  File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
    raise e
ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
    [line 22]: '[]\n'
:~$
```I suspect the error in line 22 of /etc/wicd/wired-settings.conf came at some point when I switched from the wireless connection to my wired connection. I made that switch due to some annoying issues with our local wireless router. I'm really glad I got wicd fixed because the regular network-manager flat out refused to stay connected to our wireless router for more than ten seconds or so at a time.

/me looks for maplon's THANKS button

---

### Post by lisanels47 on 2011-01-17
I had a problem where wicd was running, but I had no notification on the panel.  I fixed it by doing this:

cd /home/myhome/.wicd
touch USE_NOTIFICATIONS

That's it.  Now the status icon is there.

Lisa:p

---

