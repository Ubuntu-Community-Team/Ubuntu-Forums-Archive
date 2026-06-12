---
title: "Strange problem with video DVDs..."
date: 2008-12-04
forum: Multimedia Software
---

### Post by night-wing on 2008-12-04
Hello.

I have a strange problem with Video - DVDs on Xubuntu (also appeared in Ubuntu): All Video-DVDs plays fine in powerdvd or vlc. But when I use a DVD, which my DVD-Recorder at my TV burned, it can be played also as root.
Is there any trick to avoid this?

Regards
night-wing

---

### Post by gabril on 2008-12-04
Im not really sure I understand the question? Do you have a problem playing your own recorded dvds? This might be due to a weird codec used by you tv recorder, but if you can play them as root just go by the standard:

$sudo vlc -vo x11 <path to file you want to play> 

Hope i did not misunderstand!

---

### Post by night-wing on 2008-12-04
Hi.
I think you misunterstood me.

The problem is, that I can't play the DVDs as normal user.
When I use a sudo pdvd (for powerdvd) or sudo vlc, I can
play them. I would like to have the ability to play them
as normal user as I can do so with other (bought) DVDs.

I don't think, this is a codec problem, because If it would
be such, I couldn't play any other DVD as normal user.

---

### Post by gabril on 2008-12-04
This is indeed strange...

Run it in terminal and post what errors you get... might lead us in the right direction!

---

### Post by djbushido on 2008-12-04
I have previously had this problem with my MP3 player.  My solution was to reformat to drive, but I'm not sure how to help you.  I would recommend checking the settings in your TV to make sure that something isn't happening.  Try messing with these and see if something works.  Also  to post the results from your terminal, like the previous post and we will see what happens from there.

---

### Post by night-wing on 2008-12-05
Powerdvd and VLC shows not message in the terminal. In gui there is the information message, that this format is not supported.

When I start VLC oder Powerdvd as root, it works without problems.

---

