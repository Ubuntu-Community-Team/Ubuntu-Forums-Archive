---
title: "Xubuntu 11.04 Bug: Wired network interface not bind address after resume from suspend"
date: 2011-05-24
forum: Networking &amp; Wireless
---

### Post by oclv on 2011-05-24
Hi, I think I may have found a bug in the default settings in the "Network Connections" App in Ubuntu / Xubuntu 11.04...

I just finished setting up Xubuntu 11.04 (natty) on a Zotac IonITX-F-E motherboard. The machine was set to suspend after 15 minutes, and that seemed to work fine, until I resumed the machine by pressing the power button on the front. Everything resumed fine _except_ the wired ethernet adapter. It never regains connection to the internet. (I waited an hour, nothing. I restarted the eth0 interface, still nothing).

"ifconfig -a" shows the eth0 interface as UP, but with no address!

I found a line in dmesg during the resume process:
"eth0: no IPv6 routers present"

So, I went into "Network Connections" App, and edited "Auto eth0" profile. Under IPv6 settings tab, I changed the method from "Ignore" to "Manual". That allowed me to un-check the box "Require IPv6 address for this connection to complete", which is checked by default, but grayed-out when method is set to "Ignore". I then Save-ed the settings. Next, I changed the method back to "Ignore", then Save-ed the settings again. Now, resume works perfectly, and the eth0 interface auto-renews the address every time!

So... I suspect that the "Ignore" method in "Network Connections" App does not directly apply to resume from suspend function in PM. PM appears to use the check-box setting "Require IPv6 address for this connection to complete", which is initially checked and gray-ed out with the default "Ignore" setting in IPv6 Settings Tab...

I've seen other posts on the forums (e.g. [http://ubuntuforums.org/showthread.php?t=1401142](http://ubuntuforums.org/showthread.php?t=1401142) ) which recommend
creating a file 90reload_network in /etc/pm/config.d with this code:
  
    Code:
     SUSPEND_MODULES="$SUSPEND_MODULES via-rhine"

for example (where "via-rhine" is the name of the network driver module) to reload the network module after resume. I did not try that solution because the simpler steps I used with Network Connections worked.

I would like to report my findings as a bug report (but I don't know how / where to do this) so it can benefit other 11.04 users and help prevent resume from suspend networking issues from the get-go.

Thanks!
Ed

---

