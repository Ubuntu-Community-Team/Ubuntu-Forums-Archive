---
title: "Error Message: Failed to start the X server"
date: 2005-10-21
forum: Multimedia &amp; Video
---

### Post by DaBruGo on 2005-10-21
Hi Folks,

I have an external USB drive at home that I got Ubuntu successfully installed and running on the other night. (I even went through the install process twice on the drive to make sure I wrote down the steps correctly and to make sure it really did install/run properly)  

I brought the external USB drive to work this morning and fired it up and got this error message screen

"Failed to start the X server. It is likely that it is not setup correctly. Would you like to view the X server output to diagnose the problem"

When I checked the output logs, there was this error that I noticed ...

(EE) No devices detected


HERE IS A LITTLE BACKGROUND INFO ...

My computer at home has a crt monitor and an ati radeon video card in it. 
(which works just fine with ubuntu)

My computer at work is a DELL with embedded video and a flat panel monitor.
(which loads all the way to this error message)


So ... is there an issue with the embedded video card and/or flat panel monitor on my work pc OR is there some setup utility I will need to run everytime I use this external USB drive on another computer system OR is there a setting in ubuntu that I need to tweak.

Any help greatly appreciated,

DAVE

---

### Post by Kamping_Kaiser on 2005-10-21
you can either use " sudo dpkg-reconfigure xserver-xorg" or manualy edit the /etc/X11/xorg.conf (thats case sensitive that X), and change the driver to 'vesa'. im not exactly sure if this is your problem, but it may be. the other option is (as you say) the embeded monitor.

---

### Post by DaBruGo on 2005-10-21
Kamping Kaiser, thanks for the reply!

So, please don't laugh at this newbie when I ask you this question ...

How do I get to where I need to be to enter the command you mentioned? 
(sudo dpkg-reconfigure xserver-xorg)

Do I just do the Ctrl-Alt-F1 or Ctrl-Alt-F2 thing. Or do I need to be entering it somewhere else?

I also happen to have the Install CD with me. Am I supposed to run this command on the currently running startup (that is giving me this error message) or do I reboot with the install CD and go into rescue mode? Or is it something completely different?


I am thinking that what really happened was the install program loaded the drivers for an ATI card (for my home PC) and didn't load some generic drivers that are compatible with more video cards.

Thanks again for your reply,

DAVE

---

### Post by RoshanDawrani on 2006-04-18
If you are trying out Ubuntu 5.10 with a live CD, then instead of trying to modify the /etc/X11/xorg.conf to change the driver from default to 'vesa', you may enter the boot process in expert mode by entering 'live-expert' at the prompt at the start of boot process [don't press Enter to enter into the default mode]. It then asks you questions relevant to various steps of booting process. At the video hardware detection step, chose not to autodetect. It then shows you the list of drivers. Chose 'vesa' in this list and proceed with defaults with rest of the steps. For me, changing the default video driver to 'vesa' this way helped and Ubuntu 5.10 came up nicely and identified my USB disk, on-board sound-card, etc quite neatly.

Hope it'll help you too.

Regards,
Roshan Dawrani

---

### Post by DaBruGo on 2006-04-18
[QUOTE=RoshanDawrani]If you are trying out Ubuntu 5.10 with a live CD, then instead of trying to modify the /etc/X11/xorg.conf to change the driver from default to 'vesa', you may enter the boot process in expert mode by entering 'live-expert' at the prompt at the start of boot process [don't press Enter to enter into the default mode]. It then asks you questions relevant to various steps of booting process. At the video hardware detection step, chose not to autodetect. It then shows you the list of drivers. Chose 'vesa' in this list and proceed with defaults with rest of the steps. For me, changing the default video driver to 'vesa' this way helped and Ubuntu 5.10 came up nicely and identified my USB disk, on-board sound-card, etc quite neatly.

Hope it'll help you too.

Regards,
Roshan Dawrani[/QUOTE]

Roshan Dawrani,


Thanks for your reply. I will give that a try.

Do you know if the install CD (not the live cd) has a similar option for the server install?


DAVE

---

### Post by btnheazy03 on 2006-04-19
[QUOTE=Kamping_Kaiser]you can either use " sudo dpkg-reconfigure xserver-xorg" or manualy edit the /etc/X11/xorg.conf (thats case sensitive that X), and change the driver to 'vesa'. im not exactly sure if this is your problem, but it may be. the other option is (as you say) the embeded monitor.[/QUOTE]
Thanks much, that fixed my setup. :cool:

---

### Post by Dan400Man on 2007-12-03
> **Kamping_Kaiser said:**
> you can either use " sudo dpkg-reconfigure xserver-xorg" or manualy edit the /etc/X11/xorg.conf (thats case sensitive that X), and change the driver to 'vesa'. im not exactly sure if this is your problem, but it may be. the other option is (as you say) the embeded monitor.

Just a note to add for prosperity, that this reconfig command also helped me in the situation where my AGP video card failed, and I replaced it with a PCI video card.  Got the "Failed to start the X server" display, which is what I searched for to get to this thread.  FWIW, this was on Ubuntu 7.04.

Thanks!

---

