---
title: "Make Rhythmbox stop playback when receiving a call"
date: 2010-05-25
forum: Multimedia Software
---

### Post by clrg on 2010-05-25
Hello guys

I often listen to music while working. I also use Skype for communicating.

Is there a way to tell Rhythmbox to pause the playback when I receive a call, and continue it as soon as I hang up? Is there an addon or functionality available in either program?

Or is there some kind of event/trigger I can look for? I wouldn't mind implementing it myself, if there's nothing available.

In pseudocode, I would like

while(true) {
  if(alsa gets io from skype) {
     if(rythmbox.isStarted()) {
        rhythmbox.pause();
     }
  }
  if(! alsa gets io from skype) {
     if(rhythmbox.isPaused()) {
         rhythmbox.start();
     }
   }
   sleep(2000);
}


Thanks a ton!

---

