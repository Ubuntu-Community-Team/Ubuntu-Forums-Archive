---
title: "Unable to use WIFI on lenovo 3000 n100"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by anand6184 on 2009-01-18
HI
i just installed ubuntu on my lenovo but i am not able to use wifi on it
The results of iwconfig showed the  wireless network with essid as ""
Not sure what should go in there
Also, there is nothing in system->admin->network tools under the wireless tab.
Please assist

---

### Post by diablo75 on 2009-01-19
Have you checked System>Administration>Hardware Drivers to see if there are restricted drivers available that need to be installed to get your adapter running?

Alternatively, you could visit the Lenovo website (with an Ethernet connection) and download Windows drivers for the wireless adapter from their support pages and install them using ndiswrapper.

---

### Post by anand6184 on 2009-01-19
all drivers are present,i guess it has something to do with ESSID "".

---

### Post by diablo75 on 2009-01-19
Is your network manager icon present in the upper right corner on the task bar?  Does left-clicking on it produce any wireless networks that you can connect to?  Does the word "wireless" appear anywhere at all after clicking on it?  Does the laptop have any sort of wifi enable/disable button/switch on it that might require pressing to enable the card?  Does the BIOS contain any options in it pertaining to your wireless adapter?  I once had a Dell laptop that required you to press a Fn-Key combination to get the adapter to turn on.  I changed a setting in the BIOS to make the adapter always on and that fixed the problem.  Just a few thoughts and things you might look into.

---

### Post by anand6184 on 2009-01-19
the soft key for network is on, no i do not see any network manager on task bar (i did see it when i ran ubuntu live, but when i downloaded 8.1 from its site and installed on hdd i dont see it) is there a command to get it up there?
i guess if the hard key or some key required to turn wireless on is not pressed then the command lshw -C network will show the status of wireless as disabled. as of now its being shown as enabled

---

### Post by anand6184 on 2009-01-20
this is done
:p

---

### Post by mr_muddle on 2009-09-03
anand: I'm having the same issue I think, any chance you could tell me how you solved it? Thanks.

---

