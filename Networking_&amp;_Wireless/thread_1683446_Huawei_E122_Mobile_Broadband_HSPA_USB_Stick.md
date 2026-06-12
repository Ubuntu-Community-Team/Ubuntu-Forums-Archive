---
title: "Huawei E122 Mobile Broadband HSPA USB Stick"
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by ni ni on 2011-02-07
I have a Huawei E122 Mobile Broadband HSPA USB Stick  on three ireland.

i can't get it to connect.  but i think the problem might be, when i stick it in nothing happens.  it doesn't show up under lsusb.

i don't think it "mounts"

i am an absolute beginner and haven't a clue what to do :-/

thanks in advance xxx

---

### Post by Brosset on 2011-02-16
Hiya,

Same problem here, same 3G USB key on three Ireland.

Been check the web for it for a day or so and I've got this far :

- Nothing happenned at first when I plugged it in, but I installed usb-modeswitch *(type sudo apt-get install usb-modeswitch in a terminal (apps -> accessories -> terminal))* and now at least I have the mobile broadband connection set up.
-But, when it connected I dont know what happenned, it crashed right away and now I can't get it to work again.

I've seen something about adding a rule or something on some other thread in French (which is not a problem since I am French).

I'll give it a try and keep you posted

EDIT : Well, the Udev rule thingy isn't necessary. I unpluged the stick, rebooted and pluged it again and now it work great. Only thing is you can't keep track of your usage like you can on windows...
Hopefully I have a dual boot and will be able to have a look once in a while.

Hope you get yours to work.

---

### Post by AfrikaDietmar on 2011-02-17
> - Nothing happenned at first when I plugged it in, but I installed usb-modeswitch *(type sudo apt-get install usb-modeswitch in a terminal (apps -> accessories -> terminal))* and now at least I have the mobile broadband connection set up.Hi Brosset, that piece of advice really helped me to get my broadband umts Huawei stick running.

In addition, what i did is that on my desktop i did a right click on network connections and added there my mobile broadband details.  I only inputed number to connect with, APN and pin, thats it, then once i plug in the usb broadband umts mobile modem thing, it gets detected thanks to you and then i just right click to connect with my EMTEL provider and it works. Really happy that its running in ubuntu now. Maybe similar work around might help you guys ?

---

