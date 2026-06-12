---
title: "yuy2 problem with ati card trying to use tv card"
date: 2005-12-29
forum: Multimedia &amp; Video
---

### Post by Fibre on 2005-12-29
I've placed a program called tv time on Ubuntu. When I try to run it I get this :-

Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/username/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.


My card is a ati sapphire radeon 9550 256mb I can't see why it can't work.

Perhaps if I have what ever is related with -

*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)

I have very little knowledge on terminal use, so I'm not sure how to go about solving this problem using the http site above?

If anyone could give me a step by step that would be helpful to me I would greatly appreciate it.

Thanks for any and all help

Fibre

---

### Post by Zyphrexi on 2006-02-04
well if it make you feel any better, i've been using linux for 5 years or so, but it's a bit tricky for me too. gatos is the driver (afaik) that allows ati aiw cards to capture video (or tv, whatever) So you could install that from synaptic. And then you'll be right around where i am... scratching my head, as I repeatedly try to modprobe gatos... lol

---

