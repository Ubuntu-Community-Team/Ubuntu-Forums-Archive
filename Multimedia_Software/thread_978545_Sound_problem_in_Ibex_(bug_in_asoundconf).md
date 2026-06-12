---
title: "Sound problem in Ibex (bug in asoundconf?)"
date: 2008-11-11
forum: Multimedia Software
---

### Post by Wilseus on 2008-11-11
Hello, I've been having an annoying problem ever since I upgraded to Kubuntu 8.10 (from 8.04.) 

The problem is, is that I'm getting no sound from my SB Audigy card. Nothing actually goes wrong, I just don't hear anything. I've had this problem on previous versions, and was always solved by using the 'asoundconf' command to set my default card to 'Audigy', as it by default selects my HDMI graphics card.

However, this no longer seems to work, and it is still (I suspect) sending all sound to the HDMI output on my ATI graphics card. I understand that sound is now handled in a different way, and if so, is asoundconf now obsolete? If that is the case, how do I now change my default sound card?

By the way, I did not do a distribution upgrade, I completely reinstalled my OS, as in my experience it causes less problems.

---

### Post by Wilseus on 2008-11-11
I've just discovered that I can set the preferred sound card in System Settings. I'm still getting absolutely no sound from my Audigy card. Looks like I will have to go back to Hardy Heron.

---

### Post by mc4man on 2008-11-11
Take a look here, maybe works, maybe not. worth a shot though

[http://ubuntuforums.org/showthread.php?p=6140130#post6140130](http://ubuntuforums.org/showthread.php?p=6140130#post6140130)

---

### Post by Wilseus on 2008-11-12
Thanks for your reply, but I already tried un-muting everything in sight! I'm pretty much convinced that it's still trying to talk to the HDMI out on my graphics card.
Tonight I'm going to try removing the ATI drivers and see if that "fixes" it.

---

### Post by Wilseus on 2008-11-13
I've managed to get my sound working. I suspect it's due to a bug in this new version. Whether it's present in other Ubuntu variants I have no idea. I will post my workaround later if anyone's interested.

---

### Post by Kevbert on 2008-11-13
There's a new bug in kernel 2.6.27-7 which you may have if you're using Intrepid or Jaunty which can be found [[COLOR="Red"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/296738"). Please post if you find a workaround.

---

