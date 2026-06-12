---
title: "Skype Audio Problem"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by deejayts on 2007-12-09
I have got 2 sound cards in my system running Ubuntu 7.10 Gutsy: one is NVidia CK8S onboard, and the second one is an Audigy2 ZS installed in a PCI slot. 

RecentIy I have installed Skype from the .deb file downloaded from Skype homepage. Now, I use my Audigy2 for music, connected to my loudspeakers, and I have a pair of headphones and a mic connected to the NVidia CK8S, which I would like to use in Skype. 

So I made my Audigy2 the default sound card using the command:

```
asoundconf set-default-card Audigy2
```

This guarantees that any application uses the Audigy2 as a default.
However if in Skype settings I select NVidia CK8S it doesn't work and the Call Test keeps telling me that there is a problem with Audio Playback.

If I make NVidia CK8S the default sound card any application uses it as default, including Skype, but I am not able to make apps such as Rhythmbox use the Audigy2, neither using **System > Preferences > Audio**, and setting the fields Sound Events and Music and Movies appropriately.

As it appears to me single applications do not manage to make a correct use of the selected sound card, if this one is not the default.

Could anybody help me please? :-?:-?:-?

---

