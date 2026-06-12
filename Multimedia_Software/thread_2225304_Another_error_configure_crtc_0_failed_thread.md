---
title: "Another error configure crtc 0 failed thread"
date: 2014-05-20
forum: Multimedia Software
---

### Post by mrslig100 on 2014-05-20
Hi.
Ive seen these threads all over the Internet but none with a real solution.
Im using a AMD (ATI) HD 6870 with a sony trinitron w900 trying to get 2560x1600 @59hz.
Want me to post anything from xrandr ect just ask.
Thanks for looking.
Hope a solution for this problem without removing my driver will be found :)

---

### Post by QIII on 2014-05-20
Hello!

Could you describe the undesirable behavior you are observing?

---

### Post by mrslig100 on 2014-05-20
Hi and thanks for the quick reply :)
I went into xrandr to set a custom resolution of 2560x1600 @ 59fps
I managed to install the resolution and it shows in my resolutions list but when I try to set my monitor to that resolution:
slig@sligsbeast:~$ xrandr --output CRT1 --mode 2560x1600_59.00
xrandr: Configure crtc 0 failed

---

### Post by mrslig100 on 2014-05-26
Bump?

---

### Post by oldos2er on 2014-05-26
Moved to Multimedia & Video.

---

### Post by mrslig100 on 2014-05-26
Thanks for shifting the thread im still getting used to the forum :P
I had one more go at trying to sort out the problem and managed to solve it.
Heres how I did it for any ATI users in the world left with this problem (And possibly nvidia and intel but I cant guarantee it: 

1:
Go into Additional Drivers.
2:
Select the X.org driver.
3:
Go back into xrandr and set up your custom resolution as you would normally.
4:
Impying that this worked you should now have your custom resolution
5:
Go back to your fglrx ATI driver in the custom resolution.
This worked for me and was able to reboot in that resolution.
I hope this works for you too. :)

---

