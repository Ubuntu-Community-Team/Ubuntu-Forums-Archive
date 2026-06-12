---
title: "Internet DJ Console More Help"
date: 2008-05-08
forum: Multimedia Software
---

### Post by RobbieRob on 2008-05-08
Howdy,

I have visited what seems like every thread on this forum board to find a answer. It seems like I have downloaded every pack I need to download to get it working from other peoples problems but still I have not had any luck.

I have the 0.7.5 version of IDJC I have tried the newer version posted on this forum board but that just crashed anytime I tried to open it saying the mixer failed or was corrupt.

I have uninstalled and installed it many times especially after I have added different codec packs or whatever I do in the terminal to get it to configure for MP3's.

This is my first full day on Ubuntu and I love it but this DJ application is something I really want to get working because its something that I would like to get involved in.

I am a business owner and I wanna give props to the Ubuntu team for make such a stable (sometimes, have a few bugs with mozilla) and clean system! I have offcially switch from Windows after one day of doing business on Linux.

Yall have made me a believer but I would really love to get this DJ system working.

SOO after all of my ranting my problem is simply: I load my MP3 into the DJ console and it wont play. It seems like it freezes for about 5 seconds then it just simple wont play. I opened JACK through the terminal and when I look in console it looks like I get these two errors.

[I]unknown destination port in attempted connection [idjc-sc:lt_in]
unknown destination port in attempted connection [idjc-sc:rt_in][/I]


Now I am a programmer and I know how to debug and this looks like it is a main left and right output problem but I have no idea where I would change these values.

Any help on this would be greatly appreciated.

Thanks,

-RobbieRob

---

### Post by garyedwardjohnston on 2008-05-08
As far as the codecs are concerned I use only one download to get them all...Applications > Add/Remove > [search for "restricted"] and install the Ubuntu Restricted...

As far as your DJ stuff, there are tons of DJ audio stuff out there.  Check out this Ubuntu distro:

[http://ubuntustudio.org/](http://ubuntustudio.org/)

:)

---

### Post by RobbieRob on 2008-05-08
Howdy,

I downloaded those restricted files and it still didnt work.

Im in the process of downloading ubuntu studios though.

Thanks for the link.

Can anyone else help me in maybe fixing the IDJC?

Thanks!
-R

---

### Post by RobbieRob on 2008-05-09
Help?

---

### Post by Steveway on 2008-05-09
It sounds like your sound-setup is not working correctly.
The best would be to install qjackcontrol to configure Jack and remove Pulseaudio if you got that.

---

### Post by RobbieRob on 2008-05-09
Howdy! Thanks for the reply. I do not have pulse... But I was wondering is there a terminal command to download that qjackcontrol?

Thanks!

---

### Post by RobbieRob on 2008-05-09
Howdy,

I figured out its not just IDJC its also DJPlay that wont work.

It seems like anything needing to use JACK is messed up.

Totem and Firefox both work for streaming...

ANy help would be greatly appricated thanks!

-RobbieRob

---

### Post by Steveway on 2008-05-09
You can get it with Synaptic.
Just search for jack, it should be there.

---

### Post by RobbieRob on 2008-05-09
Howdy,

I found qjackctrl and installed it.

When I loaded IDJC it still doesnt send sound.

I need a pro to just come onto my computer and help me...

*sigh*

-RobbieRob

---

### Post by RobbieRob on 2008-05-09
AHHHHH!

I lost all sound now!

Arg!

---

### Post by Steveway on 2008-05-09
You most propably didn't configure qjackctl correctly.
You have to fiddle with the options, can't help you much with that.

---

### Post by RobbieRob on 2008-05-09
Ok... I have sound back...

But I had to install pulse back.

Everything else works but programs taht seem to need JACK, which says that I need to configure jack but I keep getting the XRUN error.

Any idea's on that?

---

