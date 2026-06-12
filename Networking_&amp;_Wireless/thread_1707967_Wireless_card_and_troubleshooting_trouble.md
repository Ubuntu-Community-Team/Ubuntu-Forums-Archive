---
title: "Wireless card and troubleshooting trouble"
date: 2011-03-16
forum: Networking &amp; Wireless
---

### Post by Fizz44 on 2011-03-16
Symptoms:
Wireless connection to Linksys WRT54G router was working fine.
Then I installed ~47 software updates (that I been putting off due to a deadline).
After I rebooted, no wireless.  Network Manager showed no networks.

System Details:
Lenovo Thinkpad T61 Notebook, shipped 2008-04-25
OS: Ubuntu 8.04 LTS, installed 2008-05-03
Wireless card: Intel PRO/Wireless 3945ABG Network Connection

Trouble shooting:
I found and tried to follow: [https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html)

Check for device recognition -> lspci output contained this:
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
(OK, I interpret this to mean the device was recognized.)

Check for driver -> sudo lshw -C network >
  *-network
       description: Ethernet interface
       [ details deleted, it's working]
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

(This looks bad to me, but I don't know what it means.  Was the driver found or not?)

Check device is on -> sudo lshw -C network >

(Now I'm confused. This is exactly the same command I just did to check for a driver.  Well, I got exactly the same output.  Is the device on?)

Check for a connection to the router -> iwconfig >
lo        no wireless extensions.

eth0      no wireless extensions.

( I know that's WRONG. But what is a wireless extension?  End of the trail.)

Other Information:
There is a switch on the front edge of the notebook that turns wireless on and off.
It has had very little use, but some, and it seems a likely suspect.  I tried above 
commands with it in both positions, but it made no difference.

I'm stuck.  Don't know what to try next.

Comments:
I really really appreciate that on-line trouble shooting guide, and I hope this feedback is helpful to improve it.
I also greatly appreciate the forum post on HOWTO post a Wireless issue (ticket).
<http://ubuntuforums.org/showthread.php?p=6183681>

---

### Post by Fizz44 on 2011-03-18
New Information:
   I think my wireless driver has been erased.
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback








iface eth0 inet dhcp

auto eth0
$

HELP!
Questions:
 What, exactly, is the relationship between wireless driver, interface, and extension?
 Is there a way to get a new copy of it onlline?
 If I upgrade from 8.04 LTS to 10.04 LTS, would that get me a new copy of it?

---

