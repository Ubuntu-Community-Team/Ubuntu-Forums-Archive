---
title: "How can I change my sound card from 48000 to 44100?"
date: 2008-08-19
forum: Multimedia Software
---

### Post by potion on 2008-08-19
The sound card is an Echo Indigo IO. I seem to remember that when I set it up, there was a file that had a lot of settings, and one of them was rate=48000. I'd like to change that to 44100. But for the life of me, I can't find the file.

Would I just configure this in one of those optional sound card config files, like /etc/asound.conf? The thing is, at this point, none of those optional config files exist. And as I say, I could have sworn I dealt with a file that already exists, and that already includes a rate setting that I could simply adjust. Only I can't find it anywhere.

Can anyone tell me where to look? Thanks!

---

### Post by potion on 2008-08-19
Bump.

Dunno if a little more information would help, but I'm trying to transfer some cassettes to digital using Audacity. I'll be making CDs, so that's why I'm using 44100. I can set the project in Audacity to 44100 or any sample rate I like, but I believe the sound card itself is still set to 48000, so there's some resampling going on that I'd like to avoid.

Because with the cassette player plugged into the sound card's line in, and my headphones connected to the headphone out, I can listen to the sound from the cassette player running straight through my sound card to my ears, without being resampled (I think). When I record it in Audacity and play it back, it doesn't sound as good. It could be my imagination, but I don't think so.

How can I prevent that resampling from occurring?

Please help if you can! Thanks.

---

### Post by cariboo on 2008-08-19
When recording from tape your qaulity will always be worse than the origional.

Have a look at this page some of the hints may help you cut down on degradation.

[http://www.audacityteam.org/wiki/index.php?title=Recording_from_Cassette](http://www.audacityteam.org/wiki/index.php?title=Recording_from_Cassette)

Jim

---

### Post by potion on 2008-08-19
Thanks for responding, cariboo907!

The thing is though, it's not a question of the cassette playback not sounding good. I'm already doing what I can to make it sound as good as possible, including some of the tricks on that page.

But when I feed the cassette playback into my soundcard, record it in Audacity, and play back what I've recorded, it seems to sound slightly worse than when I feed the cassette playback into my soundcard and right out into my earphones. I could be wrong, it's hard to tell. But I believe what's happening is that the sound's being resampled at some stage, from 48000, which I seem to remember is the default setting on my sound card, to 44100, which is what I've got Audacity set to. I believe it's the resampling that's reducing the quality, not the fact that the source is a cassette.

Does that make sense? I'm a little over my head, so I'm probably not doing a good job explaining it.

But is there any way to set the sample rate on the sound card? Or to find out what it's set to at present?

Really what I'd like to do is guarantee that the sound is at 44100 all the way through the process, and that there's no resampling happening. I'm trying to archive these tapes, so it's important that they sound as good as possible, given the limited source.

Thanks for your help!

---

### Post by potion on 2008-08-19
I should add that it could well be my mind playing tricks on me, but it would be great if I could just verify somehow that the sound wasn't getting resampled at any point.

---

### Post by potion on 2008-08-20
Some good information [here]("http://www.hydrogenaudio.org/forums/index.php?showtopic=47591").

In Audacity, I can set both playback and recording to hw:0,0. If I understand correctly, that bypasses any resampling and gets the sound directly from--or sends it directly to--the sound card. Made that change in Amarok as well.

Whew, I think that might be the answer I was looking for.

But someone please correct me if I'm wrong. :)

---

