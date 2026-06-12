---
title: "Using a HD Homerun Dual tuner card directly plugged into Backend/Frontend"
date: 2013-09-25
forum: Mythbuntu
---

### Post by agamotto on 2013-09-25
Hello, I recently purchased a Silicon Dust HD Homerun Dual tuner card to expand my current Mythbox.  I plugged the unit in via the ethernet jack, and tried the hdhomerun tool that comes with Mythbuntu (10.04/ v25).  The green light blinks non-stop, with no tuner lights.  The tool that comes with Mythbuntu doesn't 'see' the unit.  I have been looking through various fora, and am still confused.  I have tried the following:

Setting the wired connection to Static IP 169.254.1.1, mask of 255.255.0.0  Supposedly, the Mythbox should 'see' the unit, yet the tool doesn't show anything after hitting the 'rescan.'  

Any ideas?  


Once the unit is 'seen,' I think I can configure the backend stuff myself...

---

### Post by cjgump720 on 2013-10-05
I'm having the same problem.  I was able to connect the HDHomerun to my windows laptop ethernet port, and it worked fine.  But if I try the same thing on the backend ethernet port it isn't detected.  I'm running Ubuntu 12.04  with mythtv installed.

I tried setting up the wired connection as Manual using the ip address/netmask suggested here:

[http://www.silicondust.com/forum2/viewtopic.php?f=15&t=4088&p=23690&hilit=direct+connect+ethernet#p23690](http://www.silicondust.com/forum2/viewtopic.php?f=15&t=4088&p=23690&hilit=direct+connect+ethernet#p23690)

but no luck.  I tried setting the connection method to Link-Local Only, but again no luck.

In both cases, ```
hdhomerun_config discover
``` says no devices found.  The Hdhomerun is showing the blinking green LED, indicating its waiting for a DHCP lease.  The Network Connections window says that that wired connection has never been used.  I read through this thread:

[http://www.gossamer-threads.com/lists/mythtv/mythtvnz/542508](http://www.gossamer-threads.com/lists/mythtv/mythtvnz/542508)

but no luck.  

I've read that it may be necessary to install a DHCP server on the mythbox in order to make the connection work, but I couldn't get any details on if that was true or not.


You mentioned that you searched through forums for solutions, so I don't know if any of this information was new for you, but maybe it can help.  If you do figure it out, I'm looking for a solution, too.

-Chris

---

### Post by steeldriver on 2013-10-05
Try setting the connection's IPv4 method to 'Link-Local Only' instead of 'Manual'

---

### Post by cjgump720 on 2013-10-05
I had tried that, but still got the blinking light and no connection.  That was with and without specifying the HDhomerun MAC address.

---

### Post by cjgump720 on 2013-10-06
I did a little more poking around, and I think the problem lies with my ethernet port.

I have a portable wireless AP that I used before I got a internal wireless adapter.  It works to connect my XBOX wirelessly to my router via the ethernet port so I know it works, but it isn't recognized by the computer.  I used this AP when I first built the computer and installed Mythbuntu (I'm running the full Ubuntu 12.04 now), so I know it should work here.  

Could the fact that I have a separate PCI-e wireless adapter be affecting the onboard ethernet port for my motherboard?  When I run ifconfig I get entries for local loopback (lo) and the ethernet (wlan1), but nothing for eth0.

Edit:  As I do more searching on web, I'm more convinced that the problem is that the Ubuntu is not recognizing eth0 as a device.  While I'm seeing other people who had similar problems, I can't quite follow the solutions, or even if they're applicable in my case. Can someone explain the troubleshooting/solution I can use?  Thanks



Last Edit:  Turns out the ethernet port was disabled in the motherboard BIOS.  Derp.  I doubt that will help you, agamotto, but it would at least be something to check.  Make sure the LEDs by your ethernet port are lit up when you plug in the cable.

---

### Post by agamotto on 2013-10-13
> **steeldriver said:**
> Try setting the connection's IPv4 method to 'Link-Local Only' instead of 'Manual'

Ok, that seems to have done the trick.  Now I will torture-test it with some recordings this evening, and see what results!

---

### Post by agamotto on 2013-10-30
It has been awhile now, and I have to announce that I am giving up on the Homerun.  With my system at least, it can't manage to be stable for more than a week at a time.  I thank everyone who has tried to help, but I need a tuner card that 'just works,' and this isn't it.

---

### Post by dave65 on 2013-12-01
Did you hook it up with a crossover cable?

Or find a router with a DHCP server on it so that the HDHR can get an IP. 

I have my MythTV and my HDHR on my network; I set up a DHCP reservation in the router so that the HDHR always gets the same IP address. That has saved me a ton of grief. As for reliability, I have an early version of the HDHR (2 ATSC/QAM tuners, no CableCARD, 2 RF inputs) and it has been pretty solid. If there is a power failure or if I take the router down I usually have to power cycle it, but that ends up being once every few *months*.

--Dave

---

### Post by agamotto on 2013-12-05
Yes it was hooked up with a crossover.  I had to plug it in to the system, as I can't go poking holes in my house to route ethernet.  I was able to get it working, but it 'reset' too many times for it to be useful.  I don't mind some tinkering, but I no longer have the time or patience for items that aren't easy to figure out.

---

