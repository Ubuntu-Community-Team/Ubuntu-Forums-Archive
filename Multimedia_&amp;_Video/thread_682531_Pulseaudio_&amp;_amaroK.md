---
title: "Pulseaudio &amp; amaroK"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by tim71 on 2008-01-30
Recently I gave pulseaudio a try and got almost everything to work - even flash has sound (though skype problem still remains).
Now after some testing I have found out few weird issues - if the audio driver in amaroK-xine is set to 'pulseaudio' then all things work, but pausing the playback always freezes amaroK for some time - actually for the time, that took the audio stream to disconnect from pulseaudio server, as it could be observed from Pulseaudio Manager. However stopping playback does not cause this to happen. 
Then I tried to change the driver setting in amaroK-xine to 'esd'. It solved this freezing problem, but caused other, worse thing to appear - channel layout is constantly flipping. Left and right channel are changing places in random times  (I have a two-channel setup). It can be observed better when using headphones.

For now it seems, that the problem is in pulseaudio esd plugin - if this freezing problem would have some solution, then there would be no need for using it. Pulseaudio server is at version 0.9.7 at the moment - will try 0.9.8 out to see, if it solves any of this...

---

