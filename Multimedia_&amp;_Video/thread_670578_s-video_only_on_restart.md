---
title: "s-video only on restart"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by drkm_4_frm on 2008-01-17
Hi,

I'm having 1420n and i'm not able to get success when i try to get s-video out in to my tv (samsung analog). But when i restart the machine i'm able to get video on my laptop and tv. This is causing me to restart every time i want to take video out in to my tv. I tried manually with the following command 

**xrandr --output LVDS --auto --output --VGA --auto --same-as LVDS**

But all i get is only a flickr. Can any one suggest me how i accomplish this thing.

---

### Post by alexandersk on 2008-01-17
I have had the same problem whenever I tried any kind of TV-out, using Windows too. It seems like some cards doesn't activate the TV-output unless there is something connected to it when booting. My VGA output has actually the same problem, when booting without any screen attached I have to reboot if I want to use one.

Sorry that I couldn't give you any solution, just wanted to tell you that I've had the same problem with a lot of cards (and even VGA output). This doesn't mean that it can't be solved =)

Good luck!

cheers,
Alex

---

### Post by DrMega on 2008-01-17
As mentioned, I think it has to be connected when you boot. My machine does this. In my case it is not an issue though as it is permanently connected (its a media center setup).

---

