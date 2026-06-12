---
title: "MSI 785GTM-E45 Compatability With MythBuntu 9.10"
date: 2010-01-06
forum: Mythbuntu
---

### Post by jquintana on 2010-01-06
Hello all. I am new to Mythbuntu and have spent the past couple of days trying to get a working system.

I have read through the Hardware Functional/Non-Functional thread but have not found a suitable combo. I would like an AMD board with built-in HDMI. 

I bought an MSI 785GTM-E45 today and was very surprised that the HDMI output worked out of the box. I actually installed Mythbuntu on my 50" plasma. However, I cannot get audio over HDMI. The board uses the ATI 4200 HD chipset -- can someone confirm that this chipset will actually allow audio over HDMI?

If not, what are my options?

Thanks!

---

### Post by djstevens on 2011-02-21
jquintana,
 
Did you ever receive a reply on this, or have any luck?
 
I have just built a system on this same board, and am having the same problem.  No audio through the HDMI.
 
any help is appreciated.
 
Dan

---

### Post by LowSky on 2011-02-22
in the general settings on the frontend (page 4) scan for audio devices choose the one that gets you sound over HDMI... more than likely you will have to playin the terminal withe the command ```
aplay -l
``` which will list all audio options..

But just play with what options will work on the frontend. Mine took a few tries till it worked.

---

