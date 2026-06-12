---
title: "Network not working at all!"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by mthunwardsen on 2010-10-30
I have been searching through this forum off and on for a week and I have not found anything that helps my problem.  If this is posted somewhere else, please direct me to it.

My desktop is running 10.04 and connected to the network (wired through my router)via the onboard wired ethernet port.  About 2 or 3 weeks ago I updated it and upon reboot my connection was gone.  I went to the network connection on the panel bar and clicked on the network tab and it says the my wired network is disconnected.  So click on the avaible Auto Eth0 (or one I created, Wired Eth1, it doesn't matter), and it attempt to connect for approximately 30 seconds, and then it flashes on the screen "Wired Connection Disconnected, You are now Offline".

I tried using the GUI Network Connections and deleted the Auto Eth0 from the list and tried recreating it and/or letting it auto-regenerate.  Nothing.  No matter what I do, it will not ever connect!  I check my router, it is fully functional.  I check my ethernet cable, it is fine. 

My next instinct was that the onboard ethernet went bad, so I install a PCI NIC card.  Here's is where it gets weird.  I installed it and booted up, and nothing.  I deleted the Auto Eth0 and anything else I had, and rebooted.  Upon reboot, it connected fine and I had internet.  I wish that was the end of it.  I decided to run an update and rebooted, and it has not worked since.  

I have tried everything that I can think of.  I have now tried two seperate wireless cards (my router is wireless).  The first card I tried was a D-Link AirPlus G DWL-G510, and it was almost an identical story as the wired connect is now, nothing.  I went and bought a Linksys Wireless G (WMP54G) and installed it tonight.  Now it has a little bit more life, it sees the wireless routers in my neighborhood, including mine 15 feet away.  It has good signal, but the connection from the Ubuntu side still says Wireless (and Wired) Connections Disconnected.  I try clicking on my Router, it attempts to connect for 3 seconds and then tells me that the Wireless Network is Disconnected.

I have checked the router, it works fine with my Windows 7 laptop.  This is very discouraging.  I cannot get it to connect to anything!  I believe that this is a Network Manager problem or something of that nature.  I am kind of a newbie here.  I have been running Ubuntu on this machine since 8.04 and I have not seen this kind of problem in the past.  I can't really post anything off the terminal commands because I cannot connect the computer to anything, and I cannot see the computer from within my network.  Please, someone, can you please give me a hand.  I am at my wits end with this.

I have tried looking at both ifconfig and lshw -C Network.  Both commands see both the wired adapter and the wireless adapter.  Everything looks in order, and that makes me think the harware is working okay.  Being that I cannot connect to anything, even when it sees the network I want to connect to, makes me believe this is something to do the OS.

If I do sudo ifdown wlan0, it says that "interface wlan0 is not configured".  It says the same thing for eth0.  I hope this helps.

Also, it says the nm-applet is already running and NetworkManager is already running.

Thank you all for your help, I appreciate any wisdom you can supply me.

---

### Post by mthunwardsen on 2010-10-30
Anyone have any idea's where I should start?

---

### Post by srhart on 2010-10-30
If you ask me network manager is a law unto itself but this may be causing your problem:

Take a look at the networking udev config file, from the command line:
sudo nano /etc/udev/rules.d/70-persistent-net.rules

You could delete any lines after the first five because these lines are recreated by udev but best practice would dictate that you backup this information anyway so instead of deleting these, simply comment them out by putting a hash in front.

Reboot

If you get your network back, if you feel the need you could return to the file and delete the lines you commented out.

Good luck
Simon
------------------
[www.L3n.co.uk]("http://www.L3n.co.uk") L3n Network Support - Contact L3n for voice and data network design, supply, installation and support - based in Cambridge UK

---

