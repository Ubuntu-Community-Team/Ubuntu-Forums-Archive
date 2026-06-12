---
title: "turn off wireless"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by blackløtus on 2012-05-11
hi,

I'm using ubuntu 10.04 and recently instaled a wired connection to my router, but the wireless is still working. I disable it clicking the top right icon and clicking active wireless option. The problem is every time that I restart the PC it is active another time.
I have searched the net but still I have not found a solution. All people have problems with how make work the wireless, but I want the opposite, so

how can I disable the wireless connection permanently?

---

### Post by kc1di on 2012-05-11
> **blackløtus said:**
> hi,

I'm using ubuntu 10.04 and recently instaled a wired connection to my router, but the wireless is still working. I disable it clicking the top right icon and clicking active wireless option. The problem is every time that I restart the PC it is active another time.
I have searched the net but still I have not found a solution. All people have problems with how make work the wireless, but I want the opposite, so

how can I disable the wireless connection permanently?

Go to the network icon right click you should see an entry that says something like edit connections.  

I don't have 10.04 install on anything so names may vary a bit.
click on wireless tab >
when there look for a check box that says connect automatically and uncheck it.  
that should do it :)

---

### Post by kurt18947 on 2012-05-11
What kc1di said will work.  If you want to disable the wireless adapter permanently, you could blacklist the module that drives it.  I did this with an notebook Wifi G adapter that interfered with a USB N adapter.  The module(s) name(s) vary with the adapter.  You can open a terminal and type the following "lspci" and look for something like 'network controller' or similar.  'lspci' lists modules/drivers in use for integral devices, 'lsusb' lists USB devices.

---

### Post by blackløtus on 2012-05-11
@kc1di thanks for the response. I had already made this, but what i want is to disconnect completely the wireless device

> **kurt18947 said:**
> What kc1di said will work.  If you want to disable the wireless adapter permanently, you could blacklist the module that drives it.  I did this with an notebook Wifi G adapter that interfered with a USB N adapter.  The module(s) name(s) vary with the adapter.  You can open a terminal and type the following "lspci" and look for something like 'network controller' or similar.  'lspci' lists modules/drivers in use for integral devices, 'lsusb' lists USB devices.

Ok thanks so only add the module that drives the device to the black list
What about if I extract directly the module with modprobe? but really that's not necessary at all isn't it?

---

### Post by kurt18947 on 2012-05-12
> **blackløtus said:**
> @kc1di thanks for the response. I had already made this, but what i want is to disconnect completely the wireless device



Ok thanks so only add the module that drives the device to the black list
What about if I extract directly the module with modprobe? but really that's not necessary at all isn't it?

If I understand you correctly, you shouldn't have to remove the module. If you blacklist the module for the device you want to disable then restart, the module for the blacklisted device will not load and the device would be inoperative.

---

### Post by blackløtus on 2012-05-13
> **kurt18947 said:**
> If I understand you correctly, you shouldn't have to remove the module. If you blacklist the module for the device you want to disable then restart, the module for the blacklisted device will not load and the device would be inoperative.

thanks for the help!

---

### Post by Bezukhov on 2012-09-22
> **kc1di said:**
> Go to the network icon right click you should see an entry that says something like edit connections.  

I don't have 10.04 install on anything so names may vary a bit.
click on wireless tab >
when there look for a check box that says connect automatically and uncheck it.  
that should do it :)

I hope you don't  mind another thank you. Every time I booted up both adapters kicked in, and it was driving me nuts.

---

