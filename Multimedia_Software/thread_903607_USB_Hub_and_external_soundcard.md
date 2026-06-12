---
title: "USB Hub and external soundcard"
date: 2008-08-28
forum: Multimedia Software
---

### Post by koolcracker on 2008-08-28
I have an external soundcard gthat took me forever to make default, but now when i plug it in through a USB hub with other devices, it stops working. I determined that if I only plug in a mouse, it will work, but once I introduce a keyboard, the sound will cut out on me.

Im startign to think that there is no solution to my problem, but it works fine under windows, so what do i do? Ive tried everything, is there some sort of default USB hub port? Ive tried them all, but the soundcard just does not seem to want to cooperate with the rest of my computer.

Any help will definitely be appreciated.

---

### Post by djRobbieF on 2008-08-28
It sounds like you need to upgrade to a *powered* USB hub.  You're drawing too much power from the USB port.

---

### Post by koolcracker on 2008-08-28
It is a powered USB Hub, I just can't explain why the keyboard throws it off. Not enough power? I figure that since USB alone can power each individually, a powered one could handle them both. Thanks for the time though.

---

### Post by koolcracker on 2008-08-29
Sorry to bump this, but I am going away to University tomorrow and would like to have this problem fixed before I get too busy.

If I start the computer with the sound card plugged in with everythign else, then there is no sound whatsoever. If I start the computer with only my sound card plugged in, then there is sound. Its not a power issue, Is there any way my computer confuses my keyboard as the soundcard? is there any way to set that straight? Ive fiddled aroudn with this so much, and I just cannot come up with a solution.

Seriously, any help whatsoever will be greatly, greatly appreciated.

---

### Post by djRobbieF on 2008-08-29
Well, because it's a powered hub, you've got me stumped.  ;)  In this situation, I would personally try a different brand hub just to test, but perhaps that's not an option for you.

---

### Post by koolcracker on 2008-09-09
I upgraded to the alpha of Intrepid, and it must be something with the new USB implementation, but the soundcard is now partially working. It will remain functional without shutting off and I can configure it as plugins for both Amarok and VLC, but I cannot make it the default no matter what settings I change. I just thought Id post this update.

I am happy enough that I can get it to work with ym music and movies, and i edited the alsa base file to change the order, but the card still is not default for sounds or firefox or anything. When i tried to set is using asoundconf, I get this error:

graeme@graeme-laptop:~$ asoundconf set-default-card Xmod
Traceback (most recent call last):
  File "/usr/bin/asoundconf", line 430, in <module>
    exit_code(set_default_card(sys.argv[2]))
  File "/usr/bin/asoundconf", line 348, in set_default_card
    (j, k) = sep.split(i)
ValueError: need more than 1 value to unpack

Does anyone know what that means? Im haviong trouble with it.

---

