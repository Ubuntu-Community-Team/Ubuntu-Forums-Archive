---
title: "[SOLVED] Getting the bc43xx driver work...Help!"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by mariane_08 on 2008-12-26
I had a previous version of Ubuntu and someone else configured the wireless driver for me. I've just installed Intrepid and now need to do it for myself. Can someone walk me through the essential steps...please" I've thought I couls figure it out from all the posts on the subject but have just got more confused

I have the infamous Broadcom driver BC4318 and a clean version of Intrepid installed today. I have a hard wired connection set up temporarilly.

From what I read I have two choices: to use bcfirmware cutter (first choice) and ndiswrapper (second choice)

How do I do this? I went to synaptic package manager but could not find bcfirmwarecutter. In fact TBH I'm not sure I was using package manager corectly as I couldnt see how to download them (kept telling me I hadn't selected any)

And once I've got fccutter how do I use it?

Thanks
Mariane 

Mariane

---

### Post by LiamPreston on 2008-12-26
I also use the Broadcom driver BC4318 (Linksys WRT54GL) and Intrepid, and avoided using ndiswrapper. The following page was an immense help to me:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by bruce64 on 2008-12-26
You might also check under System -> Administration -> hardware drivers.  Should auto detect and you can choose to download the firmware for this driver.  I have a 4318 Broadcome Airforce 1g as well and I had no problem setting this up for wireless

---

### Post by mariane_08 on 2008-12-27
> **bruce64 said:**
> You might also check under System -> Administration -> hardware drivers.  Should auto detect and you can choose to download the firmware for this driver.  I have a 4318 Broadcome Airforce 1g as well and I had no problem setting this up for wireless

OK call me stupid if you like but exactly how do I do this? Yesterday imediatly after installing Intrepid I did take a quick look there but couldn't quite see what to do.

Do I need to boot up with the live CD to do this?
Or do I just use my wired connection?

Once in Package Manager specifically what do I do there to find the driver? I mean do I use the search box or what?

Yes you are right it probably is not difficult (hopefully!)

Many Thanks
Mariane

---

### Post by AJB2K3 on 2008-12-27
In the top of the screen you should see
```

Application   Places   System
```

Click on system.
Click on Administration,
Click on Hardware Drivers.

A pannel should come up with broadcom b43** (fwcutter) click on that then click on enable ( at the bottom).
It will ask to download the drivers - Say yes.

It should download and enable the driver via the fw cutter method.

---

### Post by bruce64 on 2008-12-27
After you download the firmware, you will need to reboot your machine.  When the machine starts up you will notice the wireless light is on this time.  You should be ready to go after that.  Good luck!

---

### Post by mariane_08 on 2008-12-27
> **AJB2K3 said:**
> In the top of the screen you should see
```

Application   Places   System
```

Click on system.
Click on Administration,
Click on Hardware Drivers.

A pannel should come up with broadcom b43** (fwcutter) click on that then click on enable ( at the bottom).
It will ask to download the drivers - Say yes.

It should download and enable the driver via the fw cutter method.

OK guys..Thanks! I was looking under Package Manager not Hardware Drivers.

But... when I go to Hardware Drivers it says "No proprietary drivers in use" (only thing listed is a graphics driver not enabled) So I'm assuming its not auto detecting? What do I do next then?

...The other thing, and dont know if this has anything to do with the bc4318?, is the graphics driver. My display is just fine but I thought I'd click on activate the ATI/AMD Proprietary Diver. I do and it does the download/install thing for about 2 secs and at the end its still not activated. Does  this shed any light on the above?

---

### Post by mariane_08 on 2008-12-27
> **bruce64 said:**
> After you download the firmware, you will need to reboot your machine.  When the machine starts up you will notice the wireless light is on this time.  You should be ready to go after that.  Good luck!

OK I don't know what I missed but after setting up a couple of other things and rebooting I went back to Sys>Admin>Hardware Drivers and there it was! Downloaded and installed and I can put my ether cable back where it belongs in the closet :) Thanks a million guys!

The only other nigling little thing is the problem I had under Hardy. Maybe I should start a new thread but if anyone knows the solution please let me know. After bootup the box with "nm-aplet needs access to default keyring....enter password" pops up. I'd love to automate this but never succeded in geting rid of it under Hardy. Someone told me this happens if the passwords are not the same but they are now...so any ideas?

---

