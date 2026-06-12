---
title: "Problem setting up wifi in 9.04"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by Handssolow on 2009-05-06
I'm running 9.04 Ubuntu live persistent from a USB stick on an Acer Aspire One and need help setting up wifi. In the Network Connection gui I entered my network's essid, bssid and wep key, I've left the "MAC address" blank because I'm not sure what to put. I'm not connecting.

iwconfig however shows the essid "", no wep key, the wrong channel and reports I'm not associated with the AP.

using instead iwconfig I can successfully enter my essid, channel and wep key but still no association. Running dhclient and it doesn't get a connection. After a reboot iwconfig shows none of my previous inputs have been remembered. Incidentally my essid has some none alpha-numerical characters so with iwconfig wlan0 essid I have to enter it as 'myessid~' not myessid~ or "myessid~". I assume the gui can cope with this.

sudo iwlist scanning shows it can see my router (signal quality 32/100) but doesn't know my essid because I've chosen to have it cloaked by the router I assume.



/etc/network/interfaces has just two lines
auto lo
iface lo inet loopback

---

### Post by Handssolow on 2009-05-06
Wifi now working.

I removed Network Manager and installed wicd. Wicd was able to see my wifi router but not my essid as it was cloaked. I had to manually edit /etc/wicd/wireless-settings.conf as it was still showing my essid as <hidden>, only after I re-entered my essid again in the wicd gui did things start to look more promising.

I still wasn't connected until I rebooted. However there was a halt during the re-boot, showing up at the loading of network manager stage. I overcame this with ctrl+alt_del and instead of a restart JJ appeared with a working wifi connection.

I'm not going to say this is solved just yet. I'm a bit disappointed with JJ as I've had to remove Network Manager and my Microsoft 5000 bluetooth mouse didn't connect on this fresh install until I found the bug and solution in Launchpad.

---

### Post by AnthraxMouthwash on 2009-05-06
Thanks, dude.  You just totally solved my wifi problem.  I installed wicd and...  tada.  Internet working and all.

I didn't have any boot issues.  Although, I think I crashed my stick after the first reboot.  I got to Google and nothing else worked.  So I restarted again and everything is now working 100%.

Thanks again.

---

### Post by Handssolow on 2009-05-06
I've now got wifi working with Network Manager.

After removing Network Manager and using wicd I'd got wifi but my Ubuntu 9.04 wouldn't boot properly from my USB stick, it was halting and waiting at setting up networking. So I reversed the process removing wicd and going back to Network Manager whereupon I lost wifi. I played around with adding the package plasma-widget-network-manager but couldn't then find it. I removed it to discover I'd then lost wlan0 but found it again after reinstalling Network Manager.

Now the important bit. On top tool bar a left mouse click on wifi signal strength icon (with an x over the top) gives a window showing a "hidden" network-mine and a horizontal signal strength bar. I select my hidden cloaked essid and wifi returns.

Was it there all the time if only I'd left clicked?

---

### Post by coffeecat on 2009-05-06
> **Handssolow said:**
> Was it there all the time if only I'd left clicked?

Sort of. If you haven't connected to a network before, a left-click on the NM applet icon will show you the signal strengths of the unhidden networks, but underneath will be a 'connect to hidden network' option. If you select that you only have to put in your ESSID and passkey. Certainly not the MAC address.

Thereafter, NM will 'remember' your hidden ESSID and show it with its signal strength togteher with any unhidden ones in range.

---

