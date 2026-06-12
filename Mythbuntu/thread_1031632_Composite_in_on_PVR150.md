---
title: "Composite in on PVR150"
date: 2009-01-05
forum: Mythbuntu
---

### Post by Senkoboy on 2009-01-05
I have my tuner up and working with cable tv but am trying to use the composite in to hook up a VCR or a digital converter box.  I can watch live tv, but when I push C to change inputs I get nothing. Have tried several times to create a new input & video source but can't seem to get any feed.  Why does it want me to do a channel scan when there is no channel, just feed? I am running the latest 64 but Ubuntu with mythtv. Don't know what to try next.

Thanks Mike...

---

### Post by jlagrone on 2009-01-05
It's been a long time since I tried to use the component input so I don't remember exactly what I did, but I do have this bookmarked, so it was probably useful ...

[http://www.gossamer-threads.com/lists/mythtv/users/44731](http://www.gossamer-threads.com/lists/mythtv/users/44731)

Also, on my machine pressing C just tells me what tuner it is using (I think).  Pressing Y actually changes the tuner, but then I remapped the keys at some point, but it's worth trying.

---

### Post by ian dobson on 2009-01-05
Hi,

You need to create a video source then a tuner (For the composite input) then link the two together and create a channel with a dummy frequency. Have a look here:- [http://threebit.net/mail-archive/mythtv-users/msg38202.html](http://threebit.net/mail-archive/mythtv-users/msg38202.html)

After restarting myth-backend you should be able to change video source.

Regards
Ian Dobson

---

### Post by Senkoboy on 2009-01-05
Thanks that seems to have done the trick.  I told it the channel was 100 and input composit video.  I can go hit c on keyboard and it will switch to composite. Set it to manually record channel 100 for 30 min. Looks like it will work. Thanks again, I am sure that won't be my last question.

Mike.....

---

