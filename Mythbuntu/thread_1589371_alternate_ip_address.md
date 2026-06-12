---
title: "alternate ip address"
date: 2010-10-06
forum: Mythbuntu
---

### Post by Coda2010 on 2010-10-06
My primary backend is at times on a wireless network.  I want to know if I can enter an alternate ip address for when this occurs, rather than manually changing the configuration each time I switch network interfaces.

eth0 - 10.9.8.103
wlan0 - 10.9.8.109

I apologize in advance if my ignorance is of a simple solution and look forward to learning.

Thanks-

Stuart

---

### Post by ian dobson on 2010-10-06
Hi,

I don't think mythtv supports a "mobile" backend. It expacts the IP address to be always the same.

Regards
Ian Dobson

---

### Post by lviperz on 2010-10-06
If you don't need the eth0 interface when using the wlan0, you could assign the same ip to both interfaces and just disable the interface not being used. When you need to switch just disable one and enable the other. Just don't have both enabled at the same time.

---

### Post by LowSky on 2010-10-06
Ian is right, Mythtv isn't very forgiving when it comes to changing IP addresses.
You really need to set up a static address for the machine and choose a permanate option for the address. i don't think you can se the same address for a wireless and wired connection even for the same machine, but worth looking into.

If its a problem with not enough wired ports on the router, just buy a cheap switch to add more machines.
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100010066&IsNodeId=1&bop=And&ShowDeactivatedMark=False&Order=PRICE&PageSize=100](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100010066&IsNodeId=1&bop=And&ShowDeactivatedMark=False&Order=PRICE&PageSize=100)

---

### Post by Coda2010 on 2010-10-06
I could place a switch at this jack, it is essentially a point of aesthetics, and yet another piece of hardware.

My backend is in a portion of the house where I installed one jack, but which is also poorly covered by my primary wireless access point, so, when wireless is needed "here", I use the jack for a second access point and the backend's wlan.

Perhaps I'll pull some more wire.

I think static ip address same on each interface could only occur if one is disabled, (as lviperz mentioned), comparably cumbersome to entering myth setup, but will look if there is a utility to do the task automatically.

Thanks to you all.

Stuart

---

