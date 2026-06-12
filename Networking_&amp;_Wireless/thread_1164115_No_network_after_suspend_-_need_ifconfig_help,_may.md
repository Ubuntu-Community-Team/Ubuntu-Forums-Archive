---
title: "No network after suspend - need ifconfig help, maybe?"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by ed325i on 2009-05-19
After 9.04 wakes from Suspend, my computer can no longer see my LAN or the Internet.

ifconfig -a shows eth0 is still active
"ifconfig eth0 down" plus "ifconfig eth0 up" does not restore network access

In Windows XP, ipconfig/release + ipconfig/renew tend to resolve similar issues.  Is there a similar set of commands in Ubuntu?

Logging off from the current session didn't seem to help.  A reboot is needed to regain network access.

---

### Post by superprash2003 on 2009-05-19
try typing **sudo /etc/init.d/networking restart**

---

### Post by ed325i on 2009-05-19
Thanks!  I will try it tonight.

---

### Post by floborg on 2009-05-19
Same problem here.  I started this thread 3 days ago:

[Disconnected from Network (wired) After Suspend/Resume]("http://ubuntuforums.org/showthread.php?t=1160802")

superprash2003's suggestion did **not** work for me.

---

### Post by ed325i on 2009-05-20
I tried:
"[B]sudo /etc/init.d/networking restart"

Nothing happened.


[/B]

---

### Post by floborg on 2009-05-23
There's no way to reconnect through the GUI, and the command line suggestions thusfar have proven ineffective.  The workaround, which I haven't verified even works for wired connections, requires the root to edit a file in /etc.  I'd say this is something the Ubuntu devs should fix.

---

### Post by bradhaack on 2009-05-24
Same issue here.  I can never get the wired connection up after a suspend.  I tried the restart suggestion.  I'm using 9.04, same issue w/ 8.10.

---

### Post by floborg on 2009-05-25
Well, the workaround appears to work.  I've returned from a few suspends, and the wired network connection is automagically brought down and then reconnected, which was not happening before.

Specifically, I added

```
SUSPEND_MODULES="e1000e"
```

to the already-existing file

/etc/pm/config.d/unload_modules

e1000e is my network driver.

Still, the Ubuntu devs shouldn't be let off the hook just because a workaround exists.

---

### Post by Vunutus on 2009-05-25
I'm having this same problem as well. I haven't tried any of the workarounds, I'd really like to see an official fix. It doesn't just happen to me after suspends, it happens after ANY power event. If I even close the lid and trigger the "Blank screen" action just for a second, networking is dead and I have to restart to get it back. Obviously this isn't good on my battery life if I can't close the lid and turn off the screen.

---

### Post by Psyphre on 2009-06-09
same problem here with my p5q-e motherboard.

---

### Post by bradhaack on 2009-06-10
Hmmm,  on my system, 9.04, I don't have a /etc/pm/config.d/unload_modules file.  Should I just create one and add a line similar to yours?  How do I determine what my network driver is?

> **floborg said:**
> Well, the workaround appears to work.  I've returned from a few suspends, and the wired network connection is automagically brought down and then reconnected, which was not happening before.

Specifically, I added

```
SUSPEND_MODULES="e1000e"
```

to the already-existing file

/etc/pm/config.d/unload_modules

e1000e is my network driver.

Still, the Ubuntu devs shouldn't be let off the hook just because a workaround exists.

---

### Post by QCompson on 2009-06-11
> **bradhaack said:**
> Hmmm,  on my system, 9.04, I don't have a /etc/pm/config.d/unload_modules file.  Should I just create one and add a line similar to yours?  How do I determine what my network driver is?

I don't have an unload_modules file either.  I'm on intrepid.

I second the question about determining what the network driver is.  Thanks.

---

### Post by floborg on 2009-06-12
Try using this command:

```
lshw
```

Look for a network section.  Hopefully, you will see a line that contains "driver=something."  "something" is the name of the driver in use apparently.

I would assume your 9.04 would use an unload file whether it was created by you or automatically.  You can try just creating it by hand.

If all else fails, something that worked for me when my router spontaneously restarted at bootup was to unload and then reload the driver.  I did that with these commands:

```
sudo modprobe -r e1000e
sudo modprobe e1000e
```

---

### Post by here.david on 2009-06-18
> **floborg said:**
> Well, the workaround appears to work.  I've returned from a few suspends, and the wired network connection is automagically brought down and then reconnected, which was not happening before.

Specifically, I added

```
SUSPEND_MODULES="e1000e"
```

to the already-existing file

/etc/pm/config.d/unload_modules

e1000e is my network driver.

Still, the Ubuntu devs shouldn't be let off the hook just because a workaround exists.

While I had no "...already-existing file..." this made a new one and I changed the network driver to mine type ----

THANK YOU!!!!!!!!!!!!!!! after months of searching and trying ...THIS worked...amd64 9.04...now if I could get Firefox to stop closing...<g>...

---

### Post by elev on 2009-09-17
This worked for me too.  Thank you!

---

### Post by floborg on 2009-11-02
Hey, don't forget about this if you do a clean intsall of Karmic because _this bug has not been fixed._  Should we be surprised?

---

### Post by bristolbadger23 on 2010-07-30
Yup, worked for me too.

$ lshw | grep force

Presented me with:
          configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=172.16.0.4 latency=0 maxlatency=20 mingnt=1 multicast=yes

so I did

$cd /etc/pm/config.d/
$ nano unload_modules

dropped in this line:

SUSPEND_MODULES="forcedeth"


saved the file with changes, restarted my machine, (it may have worked by just re-starting networking, but anyway, it worked.

Thanks heaps everyone :)

Except the dev team who REALLY ought to sort this sort of **** out.

---

