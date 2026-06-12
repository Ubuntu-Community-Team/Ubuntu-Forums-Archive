---
title: "Jerky Video"
date: 2008-08-05
forum: Mythbuntu
---

### Post by hellaid on 2008-08-05
I've got myth fully working but I seem to have a problem where the tv picture is very jerky and shudders a lot, its like this if i'm watching digital tv or a dvd which plays fine in other applications, now i can't watch tv like this so is there any settings i can adjust toget it working right?

System Specs Are:
AMD Sempron 2500+ (1.8ghz clock speed)
MSI KM4M -V Socket A Mobo(using built in gfx for this)
2 Gb Ram
500gb Seagate HD
Creative SB Audigy SE
Asus Lightscribe DVD rw
Hauppage Wintv Nova t-500

---

### Post by Qchan on 2008-08-05
> **hellaid said:**
> I've got myth fully working but I seem to have a problem where the tv picture is very jerky and shudders a lot, its like this if i'm watching digital tv or a dvd which plays fine in other applications, now i can't watch tv like this so is there any settings i can adjust toget it working right?

[b][color=darkred]
Seems like more of a hardware issue to me. Check your TV tuner card.
[/b][/color]

---

### Post by hellaid on 2008-08-05
how would that initerfere with the dvd playback though?

---

### Post by Qchan on 2008-08-05
> **hellaid said:**
> how would that initerfere with the dvd playback though?

[b][color=darkred]
What are you using to play your DVDs?
[/b][/color]

---

### Post by hellaid on 2008-08-05
the myth front end, i think this may be a problem with refresh rates after searching around on the internet, yet i am unsure how to adjust it, i have got a toshiba 19" widescreen hd ready tv going via vga input from an msi mobo running an amd chip, my problem is the at seem unable to adjust the refresh rate for the tv to stop the jerking.

---

### Post by Qchan on 2008-08-05
> **hellaid said:**
> the myth front end, i think this may be a problem with refresh rates after searching around on the internet, yet i am unsure how to adjust it, i have got a toshiba 19" widescreen hd ready tv going via vga input from an msi mobo running an amd chip, my problem is the at seem unable to adjust the refresh rate for the tv to stop the jerking.

[b][color=darkred]
Try using S-video.
[/b][/color]

---

### Post by hellaid on 2008-08-05
unfortunatly i don't have that option atm as i'm using the mobo's onboard graphics

---

### Post by Qchan on 2008-08-05
[b][color=darkred]
Now, it depends on how you have your PC set up. You're saying you're using onboard graphics. So, I'm assuming that's the video out. However, what about the video in?

If its acting funny, it could just be the video in. I'd suggest using a S-video input in that case.
[/b][/color]

---

### Post by Moridin333 on 2008-08-05
if you have a separate front end and back end it could be many different things.

Tv card on backend

speed of network

drivers on frontend

These might be a few things to check.  if it is indeed separate do you put the dvd in the frontend or the backend?  are there other frontends you can test?  perhaps a laptop that you can quickly install mythfrontend in?

---

### Post by Lester_Burnham on 2008-08-06
Some hardware details would be good.
Restricted drivers?
Have you tried different playback profiles?

---

### Post by hellaid on 2008-08-06
I've updated my first post with the systems specs, I'm not using any restricted drivers as its onboard gfx, I don't really know how to adjust the playback profiles either.

---

### Post by Lester_Burnham on 2008-08-06
Hi,

You might need to hunt around and make sure XvMC is working properly on that chipset.

Lester

---

### Post by Trollslayer on 2008-08-08
Check playback settings - the internal DVD player may be too slow, try Mplayer instead.
Certainly I change to Mplayer because of this.

---

