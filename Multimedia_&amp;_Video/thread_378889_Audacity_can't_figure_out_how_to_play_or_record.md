---
title: "Audacity can't figure out how to play or record"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by chimerical_brio on 2007-03-07
So I have Audacity installed, and I'm looking to record some stuff. I have a mic, it's plugged into my computer, and I have speakers that work, but when I try to play/record in Audacity, it has a problem with that. and can't find a device to use. How can I fix this? I can't select anything for those devices under preferences, either.

On a side note, is there any sort of plugin I can get for Audacity so it will export in .m4a? I need this to put ringtones on my phone. If that's not possible, is there another program that can do that? Thanks.

---

### Post by disturbedite on 2007-03-08
audacity currently uses oss.  (unless you compile it to use alsa or whatever).  it can be quite greedy about using your sound card.  (it doesn't play well with others, or at all for that matter).  basically, you have to make sure that you don't have any other apps open that are using oss when you try to play back or record.  i knew that, cuz it tells you that, but it took me a while to find out which apps of mine were causing audacity to complain that it was in use.  (other than the obvious ones).

i think thats prolly what situation you're in.

as for the m4a plugin, i don't know if there is one...

---

### Post by chimerical_brio on 2007-03-08
Well, I got it to work, I just had to go to sounds in preferences, and turn off system sounds. Even though that part is on now, Audacity works great!

Do you guys know of any sound programs that can output into m4a? Thanks a lot.

---

