---
title: "[SOLVED] DVD playback quality is TERRIBLE!!!"
date: 2008-07-13
forum: Multimedia Software
---

### Post by happyisland on 2008-07-13
Hi,

When I play either a DVD or ripped iso off the hard drive the video quality is terrible. It looks like a jpg that has been compressed to the max - the edges of everything are jagged, movement is somewhat laggy, etc.

So the question is, why? I recently bought the computer that I'm using, and although the video card is just Intel's GMA 3100 I thought it would work fine for simple video stuff. 

What should I look at to try to fix the situation?

Thanks!

---

### Post by mc4man on 2008-07-13
I don't have any onboard video adapters like yours but what i would try is install vlc if not already. Open it up and go settings -> preferences -> on bottom right check the advanced options box. Then on left expand the video (little arrow ) and highlight output modules. In the drop down change from default to X11, _click save_ and try a video.

---

### Post by happyisland on 2008-07-13
Thanks for the idea. I tried it, but now the video quality seems to be EVEN WORSE!!! I'm talking "bad webcam" quality. I just do not understand this.

---

### Post by mc4man on 2008-07-13
Well it won't hurt to try the the OpenGl or Xv. You can always click the reset button to put you back to where you started.(first post)
You may want to post some info about your pc (make, model) and whether your using compiz.
Doing an advanced search in _individual forums_ (including archives) using some appropriate keywords may prove fruitful.

I wouldn't doubt you'll see more useful advise being posted, give it some time.

---

### Post by happyisland on 2008-07-14
Now I've got VLC set on XVideo and the video is now watchable! Thanks for the idea - I didn't even know about that menu. If anyone out there has any ideas on optimizing my system for watching DVDs and ripped .iso files please let me know.

---

### Post by fenian on 2008-07-14
Are you using the Intel driver?You can install it with the command...

> sudo apt-get intall xserver-xorg-video-intel

---

### Post by mc4man on 2008-07-14
> Now I've got VLC set on XVideo The default is usually Xv, but i've noticed that sometimes switching from Xv to something else and back works. Go figure that. 
If you have any sound quality issues do the same thing in sound (output module), switch from default to something else, usually alsa. Small note - alot of the settings in vlc are under advanced, to turn that on all the time click on interface and enable it there.
Always click save 
Any issues with some occasional titles that won't play back post up with title name and we'll see.

---

### Post by happyisland on 2008-07-14
> **fenian said:**
> Are you using the Intel driver?You can install it with the command...

Yep - it's installed. Thanks for the idea though!

---

