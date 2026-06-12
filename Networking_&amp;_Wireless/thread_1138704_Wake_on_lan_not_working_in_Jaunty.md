---
title: "Wake on lan not working in Jaunty"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by nelbert on 2009-04-26
I use my Ubuntu machine as a music server for my Squeezebox.  The Squeezebox uses Wake on LAN to start the server - if required.  I have previously had Gutsy and Hardy both working with wake on lan - using ethtool -s eth0 g in a start script.  The machine would wake on lan from a complete shutdown without any problems.

I upgraded to Jaunty this week and the wake on lan no longer works.  I haven't made any other changes (BIOS etc remains untouched).  This is a big problem to me, as my machine is situated nowhere near my Squeezebox and it's a bit tiresome to have to turn it on manually.

Using ethtool it seems as though the wake-on setting is reverting to d at some point (I've checked it at numerous points and sometimes it reports 'g' othertimes 'd' - and wake on lan does not work regardless of the setting when I shut it down).

I can't easily get to the back of my machine but it does seem as though the network cards lights are still functioning after a shutdown.

I have tried putting the ethtool script in the post-down networking directory, with no luck.

I did seem to get wake on lan working when I hibernated, rather than doing a shutdown.  But this only seemed to work when I hibernated from a logged in session (I have an automatic shutdown script that will hibernate when the network is inactive from a not logged in session and I could not wake the machine from this setting).

Can any of you help?  I really need this feature and will actually uninstall Ubuntu Jaunty if I can't get it working.

---

### Post by nelbert on 2009-04-28
Just thought I'd say that I've solved this (though it's hardly ideal).

I found a previous post about nVidia chipsets needing the MAC address to be sent in reverse order.  The post was from several years ago - and this clearly wasn't an issue with Gutsy and Hardy versions of Ubuntu.

This solved the problem - although only partially, as I have no control over the MAC address sent by the Squeezebox in its magic packet.

So I'm hoping that Jaunty will get an update - presumably to the nVidia driver - soon that fixes this problem.

---

### Post by HuckleSmothered on 2009-05-10
Just fixed my WoL problem in my new Jaunty install.

The BIOS was untouched.
Worked in Intrepid.

Had to use ethtool to find out it was disabled:
> sudo ethtool eth0
My settings: 
> Supports Wake-on: pg
Wake-on: d

Enabled it via this command:
> sudo ethtool -s eth0 wol g

Went into /etc/init.d/halt
Change NETDOWN=yes to NETDOWN=no

sudo halt command now shuts down the system.
wakeonlan <mac address> now brings it up.

Checked ethtool eth0 again. The Wake-on showed "d" again (disabled). So I made a script.
> #! /bin/sh
sudo ethtool -s eth0 wol g
Made it executable and put it in /etc/init.d/
Ran: sudo update-rc.d <my_script_name> defaults
Halted, did a successful WoL, ran ethtool eth0 and showed "d" again.
Still works fine though. The script apparently runs at shutdown and allows for the detection of Magic Packets.

Hope this helps.

---

### Post by MaximCarnage on 2009-05-24
HuckleSmothered i tried your method to get WOL working.
Sadly I can't get it to work. Upon halting...the NIC light turns off -_-
Well back to smashing my head against the wall

---

### Post by HuckleSmothered on 2009-05-24
My NIC card light never stayed on.
But it still worked when I sent a MagicPacket to it.
Did you still try to send the MagicPacket still?
How are you sending the command?

---

### Post by MaximCarnage on 2009-05-24
Yea I still tried sending the WOL magic packet.

Im directly connected to the internet. I used [http://www.depicus.com/wake-on-lan/woli.aspx](http://www.depicus.com/wake-on-lan/woli.aspx)
and an application on my Android phone to send the magic packet. Interesting thing is if I try using the two methods while my Laptop is still on, I can see the Magic Packets arrive in iftop (13Bytes). So the WOL packets are being sent properly. It just seems that Ubuntu still turns off the NIC

---

