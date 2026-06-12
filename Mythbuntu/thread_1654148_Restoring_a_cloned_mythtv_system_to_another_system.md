---
title: "Restoring a cloned mythtv system to another system"
date: 2010-12-27
forum: Mythbuntu
---

### Post by 4romany on 2010-12-27
I have 2 servers - both Asus motherboards and 64 bit AMD processors.  These are different models one about 2 years old - the other one perhaps 3.  I use the newer faster box as my backend.  If I clone the entire drive on the newer server (via Clonzilla {great program btw}) - and "restore" this image to the older system you would expect perhaps some minor tweaking might have to be done - but when I go into mythtv-setup I only have one card defined (there should be 4 - no Video Sources (there should be 8), etc.   Why does this occur??  When I booted up the "cloned" system there were no physical DVB device connected (there are 2 in the production box) - but I would have think that is not the issue here.  WHAT AM I MISSING??

---

### Post by ian dobson on 2010-12-28
Hi,

Is the cloned backend attempting to connect to the original backend? Did you change the computer name on the cloned backend? If so you need to setup the video sources/tuners again (Video souce/tuners are tied to one host).

If you didn't change the ip address/host name and both boxes are on the same network mythtv will get totally confused.

Regards
Ian Dobson

---

### Post by 4romany on 2010-12-28
No - I unplugged the network cable from this system so as to avoid duplicate address on my internal network.  I've tried this more then one time over the last couple of years - never sucessfully.  It's always given the same results.  Now if I restore back to the original box it works great.   It's not a big deal I guess...I could probably install mythbuntu on it - and just bring up a copy of my original mythconverg db - but I would like to understand what is going on....

---

### Post by ian dobson on 2010-12-28
Hi,

So the network interface wasn't up, I'd imagine that the network post didn't get an IP address (even if it's a fixed address). So maybe mythtv can connect as the host is not contactable.

The best thing to do is have a look at the log files (/var/log/mythtv) to see what's really going on.

Regards
Ian Dobson

---

### Post by 4romany on 2010-12-29
I'll look at that and see what I get - it might show something.  If I have any insights I'll post an update.  Thanks for your responses...

---

### Post by 4romany on 2010-12-29
Think I figured it out.  The production box - which was the source for the cloned image - used eth0 for it's nic.   Since I live in a house that cries out for lighting damage the other test server had a bad eth0 (onboard) and I installed a PCIe eth1.  Once I corrected the /etc/network/interfaces file from eth0 to eth1 - and rebooted - the system came up and I was able to see my capture cards, etc.

---

### Post by ian dobson on 2010-12-29
Hi,

Linux would see a different network card (based on the MAC address) as a new ethX device, so even if you had exactly the same motherboard it'll get a new eth.

I think hal/udev is responsible for assiging a eth to a network device/mac address.

Regards
Ian Dobson

---

### Post by mymythtv on 2011-01-04
Try looking at /etc/udev/rules.d/70-persistent-net.rules - it creates you interface based on MAC address

Use "ifconfig -a" to find the MAC address :-)

( Some prefer that it's eth0 all the time ;-)  )

---

