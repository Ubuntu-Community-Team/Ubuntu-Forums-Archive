---
title: "Monitor  shows error after first booting after install"
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by Subu on 2006-09-01
Hi,
   I've just installed the ubuntu version 5.10 from the install CD.  
I followed all the instructions, and the first time I boot after the install I get the following message on the monitor:

"out of range signal
cannot display this video mode
change display input to 1600x1200@60"

   The monitor is a Dell 2007FP

I searched on google and added the 

"HorizSync  30-83
 VerticalRefresh 56-76"

lines that were missing from the xorg.cong file, but this doesn't solve the problem. Please help me resolve this - I'm eagerly waiting to start using ubuntu.

Thanks,
Subu

---

### Post by Subu on 2006-09-01
Update:

   after some more google searching, the following fixes the 
problem:

add the line 

 V-freq: 60.00 Hz  // h-freq: 74.69 KHz
Modeline "1600x1200" 170.89  1600 1688 1896 2288  1200 1200 1203 1244

in the monitor section in xorg.conf

a very good website for monitor issues is:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Issue resolved!

---

