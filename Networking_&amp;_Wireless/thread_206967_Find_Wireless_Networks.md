---
title: "Find Wireless Networks"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by Thund3rstruck on 2006-06-30
If I want to list all the wireless networks in range to my laptop, what is the command? The network manager tool isn't very good since once you connect to one network it forgets all the available networks. So now when I'm on travel, it becomes a whole ordeal trying to connect to hotel wifi

T3

---

### Post by mariodiaz on 2006-06-30
You should take a look to ifplugd and wpasupplicant. I haven't tested, but a friend told me this combination works for him.

---

### Post by Dr. Nick on 2006-06-30
wifi-radar looks like a good app, it showed me the ap's but didnt want to connect to them.

If you just want to use the terminal to get the name of the ap. try this command

** iwlist scan**

---

### Post by hda on 2006-07-01
IMHO, kismet is the best tool for sniffing wireless networks. It puts your WLAN adapter in monitor mode and passively listens to packages within reach and even can try 'hidden' networks (with SSID broadcast turned off). By far the best tool I've ever seen, if you want to check networks within reach or test your on WLAN.

_hda_

---

### Post by Thund3rstruck on 2006-07-01
Thanks guys

I ran iwlist scan but that only reveals details regarding the network I'm connected to. 

I installed kismet as well but thats going to take quite some time to configure, it appears. I was hoping there was some simple tool out there like the windows xp 'Find Availablle wireless networks' feature. I'm not trying to do anything clandestine, I just want to connect to some unsecured networks near me to do some VPN testing (outside my network) and I was to be sure that when I travel I'll be able to see networks in range. 

I'm curious how the network manager tool in ubuntu lists networks. I've found that as long as you have never connected to any wifi network it will list the available ones but once you connect, thats it... it will no longer even attempt to search for networks and will only see the network to which you are connected. 

Thanks again
T3

---

### Post by N6546R on 2006-07-01
wlassistant works quite well.

Perry

---

### Post by Dr. Nick on 2006-07-01
wifi-radar is similar to the windows "find avaible networks" 

I think I sort of goofed on the iwlist scan bit

from the iwlist manual

> scan[ning]
              Give the list of Access Points and Ad-Hoc cells  in  range,  and
              optionally a whole bunch of information about them (ESSID, Qual&#8208;
              ity, Frequency,  Mode...).  The  type  of  information  returned
              depends on what the card supports.
              Triggering  scanning  is  a privileged operation (root only) and
              normal users can only read left-over scan results.  By  default,
              the  way  scanning  is  done  (the  scope  of  the scan) will be
              impacted by the current setting of the driver. Also,  this  com&#8208;
              mand is supposed to take extra arguments to control the scanning
              behaviour, but this is currently not implemented.

So you may have better luck running **sudo iwlist scan** to make it find the new ones, without the sudo it is just showing the ones it already knows about, not any new ones.

kismet is pretty neat application aswell, just be aware that it will not run if you are using ndiswrapper for your wireless drivers, you must have a driver built into the kernel

---

### Post by Thund3rstruck on 2006-07-01
Thanks again guys. I should have looked over the man pages for iwlist, sorry on that. I looked over the options and ran several under sudo but I ended up with the same results. It only listed details on the network I was already connected to. 

I checked out wlassistant, it detected a 2nd network in my range and wifi radar detected 3 networks in range. Windows detects 6 networks but I wonder if wifi-radar and wlassistant only detect non-security enabled networks. But ultimately thats not important since I'll need to look at kismet for that (I'm not using ndis wrapper, my onboard wifi was detected and installed during the Dapper installation).

Thanks again guys for the insight. Looks like wifi-radar will suite my immediate needs. 

T3

---

### Post by Dr. Nick on 2006-07-02
Yeah, hopefully wifi-radar works better for you then it did for me. Windows seems to detect more than linux, but alot of the ones windows detects are never accessible, and when I try to connect they dissappear.

I think it has something to do with the way the driver accesses the cards between the 2 os's that account for the ap's detected, maybe linux filters out the ones that are out of range for reliable usage or something, who knows

---

### Post by Thund3rstruck on 2006-07-02
I spent some time today compiling and configuring kismet and that's really slick. Nothing else can touch that guy. It detected everything... and even a few networks I have never seen before (hidden SSID, I guess).

I'll have to recommend kismet to everyone who asks this question in the future

---

### Post by hda on 2006-07-03
... and the best thing is that kismet does the scanning passively. So you just silently can scan for available network without being recognised. It gives a lot of information about what's going on in the airwaves around you. ;-)

_hda_

---

