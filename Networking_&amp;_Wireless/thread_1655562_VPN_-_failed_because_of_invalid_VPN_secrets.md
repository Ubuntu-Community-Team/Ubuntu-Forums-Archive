---
title: "VPN - failed because of invalid VPN secrets"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by chuckNbanna on 2010-12-29
Okay - I have tried lots of different options on this.  I am running Ubuntu 10.04 and have vpnc running through the nice Network Manager GUI.

The problem is that my university is fairly backwards in terms of offering LINUX support.  The very basic info they provide for the Cisco settings does not match the information requested in the GUI, in terms of the field names.

I've put in the credentials in various permutations and have restarted network manager numerous times.  

I've tried to run it from the command line at vpnc-connect, with and without some kind of config file.

The main problem seems to be that there is a 'group password' and there is a 'IPSec secret' and they are not the same.  I've tried each as the group password in the GUI but nothing works.

Anybody got any hints for me?

Thanks in advance!
Chuck

---

