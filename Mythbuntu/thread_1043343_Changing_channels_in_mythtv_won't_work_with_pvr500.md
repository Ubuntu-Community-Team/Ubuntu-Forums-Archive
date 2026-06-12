---
title: "Changing channels in mythtv won't work with pvr500"
date: 2009-01-18
forum: Mythbuntu
---

### Post by Triptol on 2009-01-18
I finally have all my boxes unpacked in my new place, so it was time to get the mythbox up and running again. Getting there included performing an upgrade from feisty to intrepid.

All seems to be working great again except for two annoying little issues regarding the Hauppauge PVR500:
[LIST]
[*]The picture quality is not good. I know this might be due to the "Samsung chip problem", it also might be fixable with some finetuning. This is not major yet, but it might be related.
[*]Changing channels just doesn't work.
[/LIST]

When I do change a channel I get the following results:
[LIST]
[*]The sound changes to the new channel (huray!)
[*]I get three 'striped' pictures of the new channel at the top of the screen (looks like only every second line of the signal is displayed and the picture is repeated three times)
[*]The original channel (the one I came from) is partly displayed as a vibrating frame at the bottom left
[*]Another channel is also displayed as a vibrating frame at the bottom right
[/LIST]

When I leave TV View and return, the channel I chose works correctly. But here as well: moving to another channel gives the same problem.

Using tv-viewer to tune the ivtv card I do not get the same issues, so it seems to be realted to mythtv.

Any thoughts?

---

### Post by Triptol on 2009-01-19
I changed the recording settings to 720x480 for all MPEG2 recording profiles (see this post: [http://ubuntuforums.org/showthread.php?t=1041695](http://ubuntuforums.org/showthread.php?t=1041695) kinda fixed my problem.)

I can change channels now, but after channel change I still see a green blob at the bottom 1/3 of my screen. Maybe I need to play a little with the correct PAL resolution here.

---

