---
title: "Low mic volume on realtek"
date: 2013-12-03
forum: Multimedia Software
---

### Post by toxicious on 2013-12-03
Hey guys,

I've been trying for days to get at least one of my sound cards to work to no success...I'm ready to give up and return to Windows :( (I really don't want to)
I've put the focus on my built-in realtek ACL889 since it seems like I have a bigger shot at fixing that one rather than my creative x-fi card.

So my problem is that the raw input from my headset mic (PC360) is really low. It is crystal clear, but simply too low for me to be heard in mumble etc. So the solution is to turn on the mic boost via the control panel, if I set it to max I can be heard clearly. But there is a problem with that too: the sound quality is **** and it picks up ALL the noises I make (keyboard etc.).

Why is the input volume so low in Ubuntu when it is normal-high in Windows 7?
...and more importantly: what can I do to fix it?

Here is the output from the alsascript:
[http://www.alsa-project.org/db/?f=ccacc87795b8566ee02067c8426e514640d9bdf2](http://www.alsa-project.org/db/?f=ccacc87795b8566ee02067c8426e514640d9bdf2)

---

### Post by monkeybrain20122 on 2013-12-03
Have you install gnome-alsamixer and pavucontrol (pulseaudio volume control) and fiddle with the settings? I had same problem a few days ago  and solved it by trial and error (Not on Ubuntu but some other Linux, Ubuntu always work out of the box for me)

---

### Post by toxicious on 2013-12-03
Yes. gnome-alsamixer just crashes, but I have tried with QasMixer and pavucontrol to no success. Lots and lots of trial and error. F the chip makers for not making native linux drivers even though the year is 2013.

---

