---
title: "New Gateway PC, wired Ethernet issues"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by dientamin on 2009-06-11
Hey, I just bought a new Gateway PC w/ Vista on it and immediately installed the latest release of Ubuntu on a separate partition.  The wired connection worked immediately, but then I soon realized that all but 2 gigs of the new partition was set for the swap space.  I then used gparted to add space to the small Ubuntu partition (taking away space from the swap), booted into Ubuntu, and now my wired connection doesn't work.

Any help appreciated, just let me know what information you need!  :p

---

### Post by Iowan on 2009-06-11
How big was the new partition? 
Check (post) results of **ifconfig -a** and **lshw -C network**.  If you're using DHCP for IP address, you might also add results of **sudo dhclient eth0**.

---

### Post by tavzz on 2009-06-12
> **Iowan said:**
> How big was the new partition? 
Check (post) results of **ifconfig -a** and **lshw -C network**.  If you're using DHCP for IP address, you might also add results of **sudo dhclient eth0**.

Hi All,

I have even enjoying the Ubuntu 9.04 Juanty for quite sometime now ever since Jaunty was released. Lately I have a problem with my WIRED network adapter that says "device not managed" in due to that I cannot connect to internet in wired, I preferred the wired connection because of it's speed and stability. 

Can anybody help me to make my WIRED NETWORK active again, I checked the Network tools it says it has an IP address but when I checked it my IP is not the one that it is being used to connect to the net. And besides, the wired is " not managed" anyway...

Please help...Thanks in advance.




TavzZ

---

### Post by superprash2003 on 2009-06-12
hope this fixes the not managed error [http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html](http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html)

---

