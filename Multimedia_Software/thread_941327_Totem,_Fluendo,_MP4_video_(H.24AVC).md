---
title: "Totem, Fluendo, MP4 video (H.24/AVC)"
date: 2008-10-08
forum: Multimedia Software
---

### Post by kumoshk on 2008-10-08
EDIT: It's supposed to say H.264 instead of H.24 in the subject.

I bought the Fluendo proprietary codecs (the complete pack), to support those codecs on my computer legally.

However, I've come across a problem when trying to play MP4 video files (with the H.24 / AVC video codec and the MPEG-4 AAC audio codec).

Generally speaking, the Fluendo codecs work very well&#8212;and I'm thinking this might not be a codec problem.

Fluendo is supposed to be able to play these files&#8212;I even emailed them and asked. I can get the audio to play on some players, but the video doesn't seem to work. I've tried it in both Totem and Realplayer 11 for Ubuntu.

I use Gnome.

Here's the error I get when I try to play some such file in Totem:
    An error occurred
    Location not found.

It just tells me it's not supported if I try to play it in Realplayer 11.

Now, it should be noted that this is not a streaming file and it is already downloaded onto my computer. When I look at the file properties in Totem, it tells me that the duration is 0 seconds. That's weird, since it is definitely longer than 0 seconds, and the audio does play in other players.

It also gives 0 x 0 for the video dimensions.

Any ideas on what's going on?

---

### Post by kumoshk on 2008-10-08
Fluendo found the problem for me.

I needed libstdc++5 installed. It's available through apt-get, of course.

It works fine, now.

---

