---
title: "Trying to get a &quot;recertified&quot; Netgear WG111T USB adapter to work"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-01-01
I recently ordered a Netgear WG111T USB wireless adapter from Tigerdirect.com

My understanding is that this is a refurbished adapter and it does show minor wear and tear but nothing major.

lsusb produces the following:

ID 1385:4251 Netgear, Inc WG111T (no firmware)

The "no firmware" part is... well I don't know what it means, but it seems to stick out.

There is also perminant marker across the MAC address and barcode on the outside of the device.  It came that way...

So I'm wondering if this is a driver issue with Ubuntu and I need to try ndiswrapper (again)... or if this is a missing firmware issue and the thing doesn't know what to be or do because it's been flashed or something?

---

### Post by diablo75 on 2009-01-02
I just tested this adapter out via Windows and it works just fine.  But the drivers I used to install it was the netgear install package exe you get from their website... and I don't know if I can get an inf file out of that for ndiswrapper to use.

So I was wondering if someone knows where I can get a zip file of these drivers bundled together.

---

### Post by nwu on 2009-01-02
The drivers from version 1.2 worked for me: [http://kbserver.netgear.com/release_notes/d102626.asp]("http://kbserver.netgear.com/release_notes/d102626.asp"). You'll want to install athfmwdl.inf and netwg11t.inf with ndiswrapper.

---

### Post by whitters on 2009-02-23
> **nwu said:**
> The drivers from version 1.2 worked for me: [http://kbserver.netgear.com/release_notes/d102626.asp]("http://kbserver.netgear.com/release_notes/d102626.asp"). You'll want to install athfmwdl.inf and netwg11t.inf with ndiswrapper.

Hi,

I'm trying to get a WG111T to work in Ubuntu Intrepid. From a fresh install, I have tried to install the 1.2 drivers with ndiswrapper, but without any luck.... I don't suppose you know what steps you took to make it work?

@diablo - Did you manage to get it working?

Thanks

Whitters
:confused:

---

### Post by nwu on 2009-02-25
Hi whitter,
I don't think I did anything too complicated when setting up my WG111T. Just install athfmwdl.inf and then netwg11t.inf using ndiswrapper, and after that you might want to try unplugging and replugging your wireless adapter to get it started.

---

