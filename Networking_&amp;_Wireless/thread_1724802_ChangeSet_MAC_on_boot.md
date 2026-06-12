---
title: "Change/Set MAC on boot"
date: 2011-04-08
forum: Networking &amp; Wireless
---

### Post by atomicben on 2011-04-08
UBUNTU: 10.10
Kernel: 2.6.35-27-generic-pae

I wanted to be able to change my MAC address to a (virtually) random MAC when I booted (or whenever-the-hell-else I felt like it).  After finding many suggestions that didn't seem to work, I found a solution that works for me so I decided to write this tut.

The first thing you are going to have to deal with is getting rid of Network Manager (I'll call it nm from here on out).  

Why????  Even if you bring down nm, bring down your card, change the MAC address, and bring it up again...once you restart nm it fetches the *real* MAC and all your work is erased.  Here's how I got around it:

Install WICD (it is an nm equivalent and regarded by some as superior).  To do this go to APPLICATIONS > UBUNTU SOFTWARE CENTRE search for WICD and install it.  You will find it under APPLICATION > INTERNET until you reboot, after that, it shows up where nm used to - in the panel (task bar).

Once installed ditch nm:

```

sudo apt-get remove network-manager

```then install macchanger (I know you can change a MAC using ifconfig but this is the method that worked for me)

```

sudo apt-get install macchanger

```Reboot your PC.

then we need to make a file that will change your MAC on boot:

```

sudo gedit /etc/init.d/changemac

```copy and paste the following into that file and save it:

```

#!/bin/bash
sudo ifconfig wlan0 down
sudo macchanger -e wlan0
sudo ifconfig wlan0 up
exit 0

```> 
Explanation of above:

[LIST]
[*]**sudo ifconfig wlan0 down** - this takes your wireless card down (turns it off) so we can change the MAC.
[/LIST]

[LIST]
[*]**sudo macchanger -e wlan0** - this says, 'give your wireless card a MAC that begins with a real manufacturers MAC (the first 3 segments) and randomize the next 3 segments.  See notes at the bottom about the -e switch.
[/LIST]

[LIST]
[*]**sudo ifconfig wlan0 up**  - this brings your wireless card back up (turns it on) with the new MAC address.
[/LIST]

NOTE:  My card is wlan0 yours may be different.  You may have to change the script to call your card.  If you want to know the name of your wifi card run:

```

iwconfig

```Now we need to make sure the file is executable and included in the start-up process:
```

sudo chmod +x /etc/init.d/changemac

sudo update-rc.d changemac defaults

```> 
Explanation of above:


[LIST]
[*]**sudo chmod +x /etc/init.d/changemac** - says that this script is allowed to be executed.
[/LIST]

[LIST]
[*]**sudo update-rc.d changemac defaults** - I'm no expert but seems to me it says 'run this at start up with it's default settings'
[/LIST]
Now to test your work.

Run:  

```

ifconfig

```You will see the MAC address (HWaddr) in the info beside the network card (wlan0).  This is the real address because we haven't rebooted (run our script) yet.  Make note of it!

Reboot your PC.

Start a terminal and run:

```

ifconfig

```Has the HWaddr changed?  Perfect, you have spoofed your MAC address.  Connect in privacy my friends!


NOTES:

Why/What is sudo macchanger **-e** wlan0?

A MAC address is unique for every damn network device in the world, it is like DNA.  The first 3 segments of a MAC tell you who made that device, the last the segments are like a serial number.  

SOME (not a lot, but some) access points/routers only allow MAC's to connect if they have a real manufacturers ID (the first 3 segments).  Using the -e with macchanger says "I want a random serial number but I want a REAL manufacturer".

If you used -a (totally random MAC address) you could be denied access by a router that uses this type of filtering. Using **-a** you could get a MAC like:  
> FF:FF:FF:FF:FF:FFand even if the router let you in, that's suspicious as HELL to anyone watching.

Using **-e** says "Keep my manufacturer (which is REAL) but make up the serial number (FAKE).  

This is my first TUT and is a work in progress. Written by a n00b for a n00b!

---

### Post by Kasual52e on 2013-03-29
Thank you for the awesome job you did on this.  It should be updated according to [http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts) to something along the lines of

```
#!/bin/bash

### BEGIN INIT INFO
# Provides:          macchanger
# Required-Start:    $network $syslog
# Required-Stop:     $network $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Changes the MAC address at boot time.
# Description:       Changes the ethernet and wireless cards MAC addresses
#                    that begins with a real manufacturers MAC (the first 3
#                    segments) and randomize the next 3 segments. 
### END INIT INFO


# Disable the network devices
ifconfig eth0 down
ifconfig wlan0 down


# Spoof the mac addresses
/usr/bin/macchanger -r eth0
/usr/bin/macchanger -e wlan0


# Re-enable the devices
ifconfig eth0 up
ifconfig wlan0 up


exit 0
```

---

### Post by wildmanne39 on 2013-03-29
Thread closed. Please do not post in old threads.

---

