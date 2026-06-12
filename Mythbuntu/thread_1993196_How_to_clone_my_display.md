---
title: "How to clone my display"
date: 2012-06-01
forum: Mythbuntu
---

### Post by fatmonk on 2012-06-01
I have an onboard nVidia GPU on my motherboard and a PCIe nVidia GPU installed.

I'd like to 'clone' the view on both so that I can output Myth via my AV amp and also directly to the TV, however the 'clone' option seems to have gone from nvidia-settings...

Is this because I am trying to clone across two different GPUs? Is this not possible?

Is there any way to output the Myth screen on both outputs?

Thanks,

FM

---

### Post by Lester_Burnham on 2012-06-03
Hi,

Just curious. Are you trying to bypass the AMP when you don't want to use it?

Lester

---

### Post by fatmonk on 2012-06-03
Yup, you got it.

The amp is mainly for use when using a projector fed via the amp. I'd like a direct feed to the TV so that the amp doesn't need to be touched for general viewing.

I have the motherboard hdmi output working, but it's just showing he xfce mouse logo at the moment.

-FM

---

### Post by Lester_Burnham on 2012-06-03
Hi,

It's a wonder these AMP's don't do pass through. Or be nice if they did. Might have to create a xorg.conf for each and combine them, making the TV output the primary.
Does the motherboard also have DVI out? Might be easier using one video chipset.

Lester

---

### Post by fatmonk on 2012-06-06
The amp does do pass through.. it passes through the last selected source when it's in standby.

Problem being that when it's in standby you can't see which was the selected source so there is scope for confusion. If, for example the satellite receiver was the last selected source you'd have to switch on the amp, switch it to the Mythbox then power the amp off again.

I'm trying to bypass the whole confusion things by just supplying a completely seperate feed to the TV. The TV has 4 HDMI inputs so I may as well use them.

It all worked OK with S-Video into the old telly, but I also want to take advantage of all of the pixels on the new telly when using the Mythbox.

M/B ony has the DVI output (and S/PDIF which is nice!).. I might end up having to buy a cheap replacement video card with DVI and HDMI out to the replace the current one which has DVI, VGA and S-Video.

Thinking about it, the onboard graphics chip may not be able to handle the full screen HD video anyway, so maybe a replacement GPU card is the right thing to do...

That way dual view off a single card should be trivially possible I guess.

-FM

---

### Post by Lester_Burnham on 2012-06-06
Hi,

Maybe a nvidia GT 430 and use both DVI and HDMI outputs if possible?
Not sure about the audio side, but you have SPDIF onboard, so quite possible. Asus ENGT430 1gb

I retired my onboard 7100 ages ago :)

The other option if you had a programmable remote would be to have a button setup to switch AMP to the correct output, before being turned off. This could be just as hard though. I hate Logitech remotes!

Lester

---

