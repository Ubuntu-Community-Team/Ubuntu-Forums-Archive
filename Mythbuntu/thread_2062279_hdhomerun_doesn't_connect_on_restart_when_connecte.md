---
title: "hdhomerun doesn't connect on restart when connected direcly to the lan port"
date: 2012-09-24
forum: Mythbuntu
---

### Post by alforddm on 2012-09-24
I know this was supposed to be fixed back in 2009 but it's not for me.  Here's the situation.  I have a new hdhomerun connected directly to the lan port on an hp laptop.  The laptops wifi is used to connect to the internet.  The only way I could get the hdhomerun config to see the tuners was to set the lan to local only.  Otherwise ubuntu keep trying to connect to the internet through the eth0 port.  My wifi connection isn't fast enough and at the time I can't set up a wired connect so the direct connect is my only choice.  So I have two lan connections the hdhomerun at eth0 and the wifi at eth1.  

At first I tried to install mythbuntu over an existing Ubuntu install and noticed this.  Then, I started having diskspace problems so just wiped everything and started over.  I re-installed using mythbuntu 12.04 64bit.  I was hoping the re-install would fix this but is still there.  It's probably because it takes longer for everything to load because I'm using two separate connections?  I tried following some of the older posts before this bug was originally fixed but it seems those fixes no longer apply.  

Any help would be greatly appreciated.  It's not a huge problem but if hubby has to restart the computer he doesn't want to have to run hdhomerun_config and then restart mythtv-backend.

---

### Post by bertsdirt on 2012-09-25
This sounds like a networking issue.  Assuming your default gateway is set for your wifi connection, you probably need a static route to the HDHomerun device.  They are on different networks, right?

---

### Post by nickrout on 2012-09-25
The HDHR will work on a link local address, make sure you have mythbackend set up to access it by ID not IP address. 

Set the wired link to link local. 

That should be all you need to do.

---

### Post by alforddm on 2012-09-27
I have eth0 set to local which is where the hdhomerun is connected and mythtv is set to access by id not ip.  It still doesn't connect on startup.   I have to run hdhomerun config and then restart mythtv-backend.

Yes, since the hdhomerun is local, it is on a different network from wifi.  How would I set up a static route?  

Thank you for the replies

---

### Post by nickrout on 2012-09-27
What do you mean "does not connect". What are the symptoms?

---

### Post by alforddm on 2012-09-27
Nothing records and when you go to watch tv it tries to work then boots you back to the main menu.  Also, the light on the hdhomerun that turns solid when it is connected, instead of being solid, continues to blink.  After running hdhomerun_config and restarting mythtv-backend recording works as does watching live tv and the light on the hdhomerun stays turns solid green and stays that way until the next time the computer is rebooted.

---

### Post by nickrout on 2012-09-27
Try putting something like```
hdhomerun_config discover
```in /etc/rc.local

---

