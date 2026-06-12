---
title: "TV tuner/capture cards and video quality"
date: 2007-11-20
forum: Mythbuntu
---

### Post by gsrcrxsi on 2007-11-20
ok i have a happauge pvr-150 tv tuner card and there is a noticeable difference in tv quality between watching live tv/recordings from mythtv or watching tv from the tv itself. watching from the tv itself is better quality. i assume this is due to the pvr-150 card, but what i want to know is is there any tuner card that will give the same video quality as the tv's internal tuner gives?

i dont have this problem with dvd's, recorded dvd's on the backend have the same video quality as if i was playing them from my dvd player.

---

### Post by newlinux on 2007-11-20
I answered this for you over on the mythtvtalk forum, but others here might be interested in my response:

Y ou probably just need to adjust the recording profile of your card.

Settings->TV Settings->Recording Profiles->MPEG-2 Encoders (PVR-250, PVR-350)-> LiveTV->Video Compression settings (you'll probably want to change you default recording profile for recordings)

For me, I have found the stream-type DVD-Special 2 to yield the best picture quality, you may want to play with the bit rate as well. Also, change the resolution in there to 720x480. By default it is 480x480, but in my experience 720x480 works much better.

For analog cards, the PVR-150 provides the best quality in my opinion. At first it looked really grainy, but after I made adjustments it looks as good as the analog stations from my cable box.

---

