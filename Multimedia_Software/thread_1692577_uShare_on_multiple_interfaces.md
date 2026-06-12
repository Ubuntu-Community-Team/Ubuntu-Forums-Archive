---
title: "uShare on multiple interfaces"
date: 2011-02-21
forum: Multimedia Software
---

### Post by nubias on 2011-02-21
So I have been searching for a while now and cannot seem to find any information on my issue and was hoping someone here may be able to help.

I have a uShare server up and running great, streams fine to Ps3 and 360 using wlan0 (wireless).  

I have recently added another Xbox 360 downstairs and would like to stream media to this Xbox also.  

The problem is I do not have a wireless adapter for the new Xbox, so I hard wired it to my pc downstairs via eth0, and am using the pc to serve internet to the 360.

The xbox gets online fine, the problem is my uShare is only serving on wlan0.  I can switch it to eth0 and it streams fine to the new Xbox.

Is there anyway to setup uShare, or maybe install another uShare server to run side-by-side, to simultaneously serve through eth0 and wlan0 interfaces?

---

### Post by nubias on 2011-02-22
So I was able to circumvent this problem by setting up a wireless bridge between two routers and hard wiring my xbox downstairs.

Thank you DD-WRT!

---

