---
title: "default AnyConnect connection?"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by DouglasAWh on 2009-06-16
I'm not sure if Networking is the best place to put this, but here goes.

I manage a few Ubuntu systems (some Intrepid, some Jaunty, at this point).  We run Cisco AnyConnect 2.3.  I'd like to set the default VPN server since users do not know the name of this server typically.  Is there some sort of configuration file where I can set that? thanks!

---

### Post by DouglasAWh on 2010-02-04
We are now on 2.4 in case someone wants to help with this. 

Also, we are preparing our Lucid images and AnyConnect doesn't seem to work in Lucid.  It doesn't appear to be a Firefox 3.6 issue as I installed 3.6 on Karmic and it worked fine.  I looked at the Cisco requirements and the packages in Lucid, and I don't see a problem.  Does someone have this working?

---

### Post by casevh on 2010-02-18
There are two places where you can store server location information. For global settings, look in /opt/ciscop/vpn/profile and create an xml file based on the template located in that directory. The Cisco ASA can be configured to update that file automatically. The same profile file can be used for multiple OSes. 

For a per-user setting, look at the .anyconnect file in the user's home directory.

If you need example files, let me know and I'll the ones I use.

I haven't tested Lucid yet. I'll see if I can try in the next few days.

casevh

---

