---
title: "Use Ubuntu as bluetooth speakers in 12.04"
date: 2012-07-03
forum: Multimedia Software
---

### Post by zyberwoof on 2012-07-03
I have been able to successfully pair my phone with my Ubuntu desktop.  When I look in the Sound Settings, I can see my phone listed as an Input device.  When I play music, I see the Input level moving, which shows that the PC is receiving the music from my phone.  However, it does not play through my speakers.

My assumption is that Ubuntu does not play Input devices through the speakers by default.  This would make sense as when doing things like Skyping you don't want to hear yourself through the speakers as it would cause feedback.  I'd like to enable this for my phone (or all input devices).

I am running 12.04 amd64.

---

### Post by zyberwoof on 2012-08-20
Ok, so it looks like no one here knows the answer to this.  My next question would be, "Who should I talk to for information on something like this?"  Should I go to a forum for Alsa, Pulseaudio, Unity, or is there something else?

---

### Post by evilsoup on 2012-08-21
[Jack ]("http://jackaudio.org/")might be useful for this, not sure though.
[]("http://jackaudio.org/")

---

### Post by zyberwoof on 2012-08-28
I found the solution here:
[http://askubuntu.com/questions/2573/can-i-use-my-computer-as-an-a2dp-receiver](http://askubuntu.com/questions/2573/can-i-use-my-computer-as-an-a2dp-receiver)

I actually didn't follow the long, highest rated answer.  I just followed this suggestion from that page:
[INDENT]*I use blueman, installed from Ubuntu software center. Right-clicking on the blueman icon*-> "local services" -> audio-> Check "advanced audio reception" is tipped. Btw I use it to listen in my Ubuntu 11.10 laptop what I play on my android phone.*[/INDENT]

In summary, I installed blueman and then enabled "Advanced audio recemption".  the blueman icon didn't show up until after I ran it manually once.  The change persists between reboots.  Now my HTPC automatically boots to XBMC.  Even with the TV off I am able to connect my phone to the PC and play music through my stereo.

---

### Post by raja1810tamil on 2013-08-01
Thanks it works for me....

---

