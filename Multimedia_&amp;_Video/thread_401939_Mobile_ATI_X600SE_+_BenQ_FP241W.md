---
title: "Mobile ATI X600SE + BenQ FP241W"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by justinphilpott on 2007-04-05
Hi,

I'm running a very nice new BenQ 24inch screen from my Toshiba M40 laptop with ATI X600SE. I'd like some advice on how to get Ubuntu Edgy to run at 1920x1200 which is the LCD's native res.

I'm guessing this will involve altering the xorg.conf but don't know exactly how... If someone could give me some details/advice/examples/links that would be great :)

Thank you!

Justin

---

### Post by 1337_n00bxor on 2008-07-08
Hi!

I don't know if the solution is still relevant to you or not, but anyway maybe it might be helpful to somebody else. I just got the same monitor and I also had a problem at first how to set it up to correct resolution. My problem was, that I had already modified the xorg.conf file for my previous monitor where I left only limited resolution options. If that is the case with you as well, try this:

sudo dpkg-reconfigure -phigh xserver-xorg

What this does according to the xorg.conf file is
"If you have edited this file but would like it to be automatically updated again, run the following command: "

After entering the above command, just restart X or reboot and afterwards select the desired resolution in System->Preferences->Screen resolution.

I hope this helps ... even though the response is slighty (a year) late. :)

p.s.: Do note that I'm using 8.04 Ubuntu version.

---

