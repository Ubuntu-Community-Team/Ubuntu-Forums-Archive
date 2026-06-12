---
title: "Got Teamspeak working"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by kjm61287 on 2008-03-03
I don't know if this has been posted before (at least this way of doing it), but I did go through the forums a bit looking around.
I had an issue where my microphone wasn't recording in TS but I could hear sound and I followed several guides through out the many times I tried getting it working.

I then found a pretty simple of getting it working. All I did was install TS and alsa-oss from Synaptic. After that, it should be a simple thing of typing aoss teamspeak in the terminal or changing the shortcut in Menus to say that.

Hope that helps for any of you still having issues! :)

edit:

okay, so after a while of use I had an issue which was resolved by going to Multimedia Systems Selector in System\Preferences (you have to make it visible first in System\Preferences\Main Menu) and selecting ALSA for everything.

---

### Post by Vinnie_Fits on 2008-03-31
[SOLVED] see next post by me 

I tried this and it still didn't help me. Perhaps it is something with my audio driver? I have onboard sound on an A7V266-E. The sound chip is identified in Ubuntu as C-Media PCI CMI8738-MC6 (model 55). Can anyone give me some tips on how to get the mic working in Teamspeak?

---

### Post by Vinnie_Fits on 2008-03-31
OK I fixed it for my implementation anyway. Some may find this helpful. I went into System > Preferences > Sound and set my preferences as you see them in Screenshot-SoundPreferences.png (attached). 

I then double clicked on my volume control icon on the upper panel. I clicked Edit > Preferences and then turned on all the stuff you see in the Screenshot-Volume Control Preferences.png (attached). I think they key for me was turning on the options for mic boost, mic boost capture, mic in mod, microphone capture, etc. (see image).

Once I did that I saw extra tabs in my volume control. See the other two attached images to help you set up your. I think the most important option was turning on the mic boost and making sure the mic in mode was set to mic-in (and not a speaker output). The card as the option of switching the mic input to a speaker output so you could have 5.1 surround. 

I also did what was instructed in the posts above but that didn't resolve my issue.

So, hopefully, if you are having a similar teamspeak problem with your mic, poking around in your sound preferences will help you as it did me. Ciao and good luck!

---

