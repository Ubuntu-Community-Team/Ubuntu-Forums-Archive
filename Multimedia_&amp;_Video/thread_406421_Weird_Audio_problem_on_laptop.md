---
title: "Weird Audio problem on laptop"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by Bigsam411 on 2007-04-10
Hello. I have searched everywhere for a solution to this problem and could not find a solution. My problem is as follows:

I just installed Edgy Eft a few days ago on my Toshiba U205 Laptop and most everything has gone well except for the fact that I cannot mute my speakers or change the volume at all. The volume appears to be stuck on max even if I use the volume control. The volume control on the side of the case is detected and Ubuntu actually shows that my volume is going up, down, or is muted. Even when I plug Headphones in the speakers stay at max volume.

Oh and my Audio chipset is the intel Ihc7 one.

I sure hope someone knows a fix for this and Thanks in advance.

oh and Btw I know my way around Linux a little bit but im still somewhat of a noob aside for the couple of linux courses I have taken.

---

### Post by RomeReactor on 2007-04-10
Hi. Open you audio player of choice and start a track; now open a terminal and enter

```
alsamixer
```

play with the values of the different channels a bit until you find which one lowers and raises your speakers' volume. Then right-click on the volume applet in the top panel and choose "Select master channel" to assign it the correct one.

NOTE: If you don't want to do that from the terminal, install either **alsamixergui** or **gnome-alsamixer**.

---

### Post by amboss on 2007-04-21
Just got the same laptop (called U200 in Denmark) and got the same problem. Fixed with alsamixer though, but I would love to be able to use the external volume control wheel but google isn't helping. Any ideas anyone?

OK, the volume control wheel works in gnome after (re)mapping the wheel in the system->preferences->keyboardshorcuts, but it still won't work in fluxbox.

---

