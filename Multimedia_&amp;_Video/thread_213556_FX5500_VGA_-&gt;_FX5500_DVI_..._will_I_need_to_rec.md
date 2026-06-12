---
title: "FX5500 VGA -&gt; FX5500 DVI ... will I need to reconfig?"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by ceenvee703 on 2006-07-11
I got a GeForce FX 5500 from Staples (so I could run xgl) and got Ubuntu 6.06 up and running and configured as I wanted. 

Unfortunately, the FX 5500 I got from Staples (a PNY closeout model) only had two VGA ports, no DVI. Guess I know now why they were closing them out. :neutral: 

So, now, I've got a different GeForce FX 5500 card (made by eVGA) coming in on Thursday that has a DVI output. Will I need to change anything in my configuration files, or can I just swap cards and reboot and I'll be good?

I did a search for "VGA to DVI" here in the forums and didn't see any threads that directly addressed this...

Thanks.

---

### Post by Dr. Nick on 2006-07-11
I havent done this before, but as long as they are the same type (nvidia) like they are I think it will work. I have never seen a xorg.conf setting for which output will be used.

The only thing that would matter (probably not in your case though) is if they were different interface types, for example you had a PCI and were getting a AGP version. If it was that sort of circumstance then you would need to change a line in your xorg.conf file.

---

### Post by ceenvee703 on 2006-07-11
Thanks for the super-quick reply and reassurance. Yes, not only did I get another Nvidia, but I got the same model just in case that mattered. Looks like I'll be in good shape--thanks again.

---

### Post by Dr. Nick on 2006-07-11
yeah I would say you would be fine, if something did happen then you could always put the old one back and you shoule be fine, then you can see what needs to be changed before putting the new one in.

---

