---
title: "Analog TV Cards a thing of the past?"
date: 2011-02-02
forum: Multimedia Software
---

### Post by ijumpship on 2011-02-02
Is Analog TV Cards a thing of the past?

Recently I upgrade to Maverick (Mythbuntu 10.10 with Mythtv protocol 0.23.1) and notice that the analog tv crds are not able to be used in recording as there is no way to configure (/dev/dsp) the sound in either the backend or front end and that you only option is to plug the output from the TV card to the line/mic in on your sound card.
This result in the sound from the tv card always being heard even when you play music.

Since ALSA seems no longer to be in maverick then my conclusion is that analog cards are no longer supported and that you have no chose but to by one of the newer digitial cards.Just hope I am wrong!

Can some shed light on this as it means I will have to reconfigure all my boxes to meet this.

I HAVE UPGRADE TO PULSE AUDIO AND THERE IS NO ERROR IN MY BACKEND LOG.

Thanks for your reply

---

### Post by ijumpship on 2011-02-02
Just some clarifications.

The sound works fine on my system. except that 

[LIST=1]
[*]When you record tv,there is video but no sound
[*]The line in /mic input passes sound to the sound card but you can always hear the TV in the background when you playback video,dvd or music.
[*]There is no /dev/dsp to configure as sound in the front end or backend
[/LIST]


I have used these links in the passes and have success in recording.It was  not until I did an upgrade I notice this.
I have done a clean install and this still occur.

[http://linuxtv.org/wiki/index.php/Btaudio_kernel_instructions](http://linuxtv.org/wiki/index.php/Btaudio_kernel_instructions)

[http://linuxtv.org/wiki/index.php/Snd-bt87x_(alsa_bt878_driver](http://linuxtv.org/wiki/index.php/Snd-bt87x_(alsa_bt878_driver))

---

### Post by ijumpship on 2011-03-05
So here is my conclusion on Analog TV Cards.

Read this

[http://www.mythbuntu.org/wiki/hardware](http://www.mythbuntu.org/wiki/hardware)

and

[http://www.mythtv.org/wiki/Category:Hardware](http://www.mythtv.org/wiki/Category:Hardware)



You just have to move with the time.

A P111 machine has limitations,just as the Newest machine,however its best to research at the planning and preparation stage.It might save you a hell of headache.Sometimes spending a $40 (like buying a new card instead of trying to get the onboard one to work.) is better than 2 whole nights trying to solve an unsolvable problem.

---

