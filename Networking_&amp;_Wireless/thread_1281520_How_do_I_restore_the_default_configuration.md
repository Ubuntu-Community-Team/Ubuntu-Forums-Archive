---
title: "How do I restore the default configuration?"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by kebabbaro on 2009-10-03
Hi,
I just moved to a new home and changed my ISP as well, so that now Ubuntu from LiveCD automatically connects to my LAN, while Ubuntu installed on my HD, still with the old connection parameters, cannot connect nor detect any network.


So what I need to do is to just restore the network configuration to its original state, equal to that of the LiveCD.

I need to cancel my previous connection, which was thru a PPPoE device and which I configured with the terminal to launch at startup. Running the PPPoEconf script proved to be pointless, as the script just lists 4 PPPoEconf devices, then scans them in order to find "PPPoE access concentrators" and finally tells me that
> 
Sorry, I scanned 4 interfaces, but the Access             
          &#9474; Concentrator of your provider did not respond. Please     
          &#9474; check your network and modem cables. Another reason    
          &#9474; for the scan failure may also be another running pppoe  
          &#9474; process which controls the modem.
Of course there is another running pppoe process which controls the modem, as my old PPPoE-type connection is launched at startup.

How do I do that? How do cancel my previous PPPoE connection and restore the network configuration files at their default state?
I cannot use the Network Manager as it doesnt see this previous connection.

Thanks for your help :)

---

### Post by kebabbaro on 2009-10-04
> **kebabbaro said:**
> Hi,
I just moved to a new home and changed my ISP as well, so that now Ubuntu from LiveCD automatically connects to my LAN, while Ubuntu installed on my HD, still with the old connection parameters, cannot connect nor detect any network.


So what I need to do is to just restore the network configuration to its original state, equal to that of the LiveCD.

I need to cancel my previous connection, which was thru a PPPoE device and which I configured with the terminal to launch at startup. Running the PPPoEconf script proved to be pointless, as the script just lists 4 PPPoEconf devices, then scans them in order to find "PPPoE access concentrators" and finally tells me that
Of course there is another running pppoe process which controls the modem, as my old PPPoE-type connection is launched at startup.

How do I do that? How do cancel my previous PPPoE connection and restore the network configuration files at their default state?
I cannot use the Network Manager as it doesnt see this previous connection.

Thanks for your help :)

Up

---

### Post by awam66 on 2009-10-04
Hello there,
I had a similar problem with my laptop and after much messing about, reading forums etc., the only way I cold restore everything was to do a fresh install. Backed up my home directory first of course.
Sorry not much help on the technical side.  Keep trying and if you come up with an answer it would be useful. I wonder if it could be a bug!

---

### Post by Iowan on 2009-10-04
What is in */etc/network/interfaces*? It should have only two lines defining "lo" interface. If that is the case, you might be able to use Alt-F2 to run **gconf-editor** and look under system>networking>connections. Otherwise, comment out the extra lines and restart/reboot.

---

### Post by kebabbaro on 2009-10-05
> **Iowan said:**
> What is in */etc/network/interfaces*? 
BINGO!

I arrived to the solution independently, but you hinted the right path =D>

In fact I learned from some page in the wiki that that file is just the one who manages the network configuration options so that i just copied this same file from the CDLive and pasted it to my hard disk filesystem (substituting the existing file).

After a reboot of the system, the problem has just disappeared :guitar:

Thank you mate.

---

