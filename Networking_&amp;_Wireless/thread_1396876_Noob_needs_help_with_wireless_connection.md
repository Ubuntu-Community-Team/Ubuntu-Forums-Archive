---
title: "Noob needs help with wireless connection"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by squeak12 on 2010-02-02
I really hate to post this, but I see no other way for me to figure out how to connect to wifi.  I just installed Ubuntu onto my Gateway.  I've done some searching both here and google, but I'm so uneducated on Linux that I can hardly decipher what is going on.  As soon as something doesn't go perfectly with the guide, I get lost and don't know what to do.

I can left click the networking icon and see the options for wireless and wired, but there isn't anything under wireless to click on.

---

### Post by marin123 on 2010-02-02
first check if your wireless switch (on your laptop is turned on :) ), then check your proprietary drivers (System-> Administration -> Hardware Drivers) are they installed...

---

### Post by squeak12 on 2010-02-02
I don't have a switch on my laptop for wireless, or at least not a button.  Is there a command for it perhaps?

Screenshot of hardware driver

[IMG]http://i18.photobucket.com/albums/b132/squeak12/Screenshot.png[/IMG]

---

### Post by marin123 on 2010-02-02
yeah, and at the bottom of that window says :  Driver is installed but DISABLED...

just click on Activate button and voila :)

---

### Post by squeak12 on 2010-02-02
After attempting to activate...

[IMG]http://i18.photobucket.com/albums/b132/squeak12/Screenshot2.png[/IMG]

---

### Post by bkratz on 2010-02-02
did you have the wired connection plugged in when doing this? I believe you have to, or what does that log actually say?


Oh, and you also should reboot after doing so.

---

### Post by squeak12 on 2010-02-02
Yes, it was connected to the internet via wired connection.  How do I get to the log?  EDIT:  I found the log viewer, do I just need to paste the whole log of "jockey.log" to here?

---

### Post by marin123 on 2010-02-02
```
gedit /var/log/jockey.log
```

thats strange... it says that driver is just disabled, but still in use... can you uninstall the driver and then try again?

---

### Post by squeak12 on 2010-02-02
Typing the above into terminal gave a lot, but I just truncated the data back about 20 minutes

2010-02-02 16:16:07,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5b3acc> about HardwareID('modalias', 'pci:v000010B9d00007101sv0000161Fsd00002036bc06sc80i00')
2010-02-02 16:16:07,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5b3acc> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-02 16:16:07,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5b3acc> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-02 16:16:17,445 DEBUG: _check_polkit_privilege: sender :1.84 on connection <dbus._dbus.SystemBus (system) at 0xa1ba17c> pid 2875 is not authorized for com.ubuntu.devicedriver.install: dbus.Dictionary({}, signature=dbus.Signature('ss'))
2010-02-02 16:16:30,048 DEBUG: unbind/rebind on driver /sys/module/b43/drivers/ssb:b43: device ssb0:0
2010-02-02 16:17:10,911 DEBUG: unbind/rebind on driver /sys/module/b43/drivers/ssb:b43: device ssb0:0
2010-02-02 16:27:29,186 DEBUG: unbind/rebind on driver /sys/module/b43/drivers/ssb:b43: device ssb0:0

---

### Post by marin123 on 2010-02-02
i have no idea what is wrong... i'm just not that much a geek :(
hope someone with more experience will read this and give you answer... good luck!

---

### Post by squeak12 on 2010-02-02
And it works.  I have no idea what I did, but it works now.  I tried activating it, restarted it, tried activating it again with the same result as before.  I went outside to talk on the phone, came back in and wireless networks were available.  I'll be sure to come back for more help if it messes up again.

The only issue is that I have to goto hardware drivers and activate it everytime that I log on.  I saw somewhere earlier where someone else had the same problem and solved it.  I will see if I can find it again, but if someone else knows how to fix it, that would be great as well.

---

