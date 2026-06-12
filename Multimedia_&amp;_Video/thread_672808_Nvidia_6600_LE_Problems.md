---
title: "Nvidia 6600 LE Problems"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by jlabomb on 2008-01-20
I have looked for the for the answer on google and here so I am sorry if this is a repeat. I am also a recent switch from Windows to Ubuntu. 

I have a AMD 4800 X2, 500 GB WD, 2GB RAM, Gigabyte GA-MA69G-S3H Motherboard with an on board ATI Video Card which is disabled, and Gigabyte Nvidia 6600 LE PCI Express.

I wanted to have a dual monitor display when working in programs that need room. I have used this card in a XP system no problem and since my Dad wasn't using it I put it  in mine. The restricted drivers installed fine and after some struggles I got the display at the right resolutions but the secondary monitor has that zoom. The resolution is stuck at 640x480 and it pans around the preferred 1024x768. I am using the gksudo nvidia-settings to adjust but there is no way I can find to get it just show the full resolution. Is that something I am just stuck with?

Also I was wondering about the video out to TV I see no options for it.

And is there a list a video cards compatible for the effects in Ubuntu? I have not been able to get that to work either. 

Thanks for any help.

---

### Post by RomeReactor on 2008-01-20
Hi. Can you please repost your question?

---

### Post by jlabomb on 2008-01-20
bump Post is fixed.

---

### Post by RomeReactor on 2008-01-20
Have you tried going to 'System->Administration->Screens and Graphics' to set the secondary screen's resolution?

---

### Post by jlabomb on 2008-01-21
Yes I have. The only option it gives is 640x480.

---

### Post by oskar2000 on 2008-03-09
Sorry, I know I'm late..
Go to System-Administration-Restricted drivers manager, and install the proprietary driver. That should fix it.
If you don't want it, you can try editing /etc/X11/xorg.conf by hand, and add the resolution you want to the section at the bottom... I can get more specific if the prop. driver didn't help.

---

### Post by jlabomb on 2008-03-22
I do have the proprietary driver installed. I have gotten it closer than before but still not perfect. A little disappointed in the control of dual monitor for Ubuntu. I reinstalled the driver one day and used gksudo nvidia-settings to set the monitor but couldn't get the resolutions to stay where I wanted. But today i logged off instead of shutting down the computer and when I logged back in it was perfect I don't know why, I wasn't even trying to adjust it today.

---

