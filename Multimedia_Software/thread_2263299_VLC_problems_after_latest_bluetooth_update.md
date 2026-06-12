---
title: "VLC problems after latest bluetooth update"
date: 2015-01-30
forum: Multimedia Software
---

### Post by Evil Wayz on 2015-01-30
When I pair my headset after this latest software update, the volume in my headset goes immediately to 200 percent, and blasts my ears out.  Also, the scroll wheel no longer adjusts the volume, only clicking on the volume bar  at the bottom does. Anyone else experience this issue?

---

### Post by mc4man on 2015-01-31
Ubuntu's implementation of bluetooth, at least as far as audio devices, currently is quite bad. 
Don't think it has anything to do with vlc per se, at least here it's - 

Every time the device is reconnected it's not immediately controlled by the sound panel. This causes either no sound or worse,  max volume. 
I now always go to Sound setting > make sure the device is selected & adjust the volume *before* actually using the speaker.

One bug I have on this though I don't have much hope Ubuntu will or can fix (though if they want to be a player in mobile they better do better...
[https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1404729](https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1404729)

---

