---
title: "Volume slider changes microphone volume, not speaker volume? Help"
date: 2007-04-07
forum: Multimedia &amp; Video
---

### Post by txgeek on 2007-04-07
I installed Feisty on a new PC a couple of weeks ago and everything worked great other than Alsa didn't even see a microphone on the built in sound (ECS PT890T-A, VIA VT1708A chipset).  I figured it was the cheap onboard sound, so yesterday I installed a new sound card, a Creative Audigy SE. 

I couldn't get the microphone working there either.  I tried everything in the forums, and ALSA documentation, and even  let the update manager install a huge 498MB update since there were a few reports of wierd microphone problems in Feisty in the forums.  Nope, not happening, nothing would fix the problem.  So I gave up and pulled the card.

Sound works fine now, ALSA reports the card correctly, it even sees the Microphone now even though it doesn't work.  There's just one little problem - if I change the volume with the slider in Gnome it doesn't change the speaker volume, it changes the Microphone volume.

If I double click on the volume button and then slide the volume up and down I see it changing the Microphone volume, not the Master volume.  

Anyone know how to fix this?

---

### Post by solar george on 2007-04-07
Right click on the volume control and you will see an option that lets you choose the channel to be controlled, set this to master and it should work OK.

---

### Post by TheeWasp on 2008-07-02
hmm doesnt work for me, either that or Im stupid

I can choose the device and control to track, but no matter witch one I choose its always the mic volume that changes.

edit: its not actually the small volumeslider that I have problem with but with the keyboard shortcuts in Ubuntu under System > Preferences. I have the volume up, down and mute bounded to the media buttons on my laptop but the volume changed is the mic volume, not the master volume

---

