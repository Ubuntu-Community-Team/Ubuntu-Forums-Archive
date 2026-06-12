---
title: "how to diagnose video problems in VLC"
date: 2009-06-26
forum: Multimedia Software
---

### Post by happyisland on 2009-06-26
Hello Ubuntu People,

For many months my wife and I have been using her laptop to watch videos streamed over a home network on a projector in our living room. Typically these are avi files that I download, such as Conan O'Brien. Until about a week ago, the laptop had Ubuntu 8.04 on it and everything was dandy.

Then I upgraded to 9.04 (via the normal updater, upgrading to 8.10 first). Everything seems to be working fine. The problem is now with video. The exact same files are now playing somewhat unreliably in VLC. They play normally, but periodically the video freezes (the sound continues) and then starts again, correctly synched after about 3 seconds of nothing happening on screen.

If anyone knows exactly what is happening and how to fix it that would be wonderful, but my real question is the one posed in the subject line of this thread:

"How do you diagnose any problems you have with VLC?"

Which is to say, when video freezes or something else looks or sounds weird, how do I go about figuring out what is wrong and fixing it?

---

### Post by starcraft.man on 2009-06-26
The answer to your last question is experience and detective skills. Conan Doyle said it best: 
	
Once you eliminate the impossible, whatever remains, no matter how improbable, must be the truth.

Basically eliminate everything you can until you isolate it.

This doesn't sound to me like a VLC problem. In fact, I think it's a networking issue. To quickly rule that out, please download or share a file over to this labtop and make sure it's completely on the hard drive, then play it. Does it still lose sync? If not, I'm almost positive it's a wireless issue. Please try a few different files from different sources/encodings to be sure. If it does lose sync, can you make sure your gfx drivers installed properly and vlc configured correctly to use them in preferences > Video. Try a few different outputs, like X11 or openGL. Turn off video acceleration. See if it persists.

Assuming it is an issue with wireless, please answer the following: What's the set up of your network (machines, n,g,b?, walls?)? Are there any sources of interference? Did you assign the machines streaming and receiving in question fixed IPs by DHCP reservation in the router for example (probably not the issue, but helps sometimes)? Did you make any changes to vanilla networking in the previous version of Ubuntu that you didn't replicate in the new install?

That should be a good start, took some typing.

---

### Post by happyisland on 2009-06-29
Well I guess the real answer is that I just need to go to ubuntu ninja school or wherever you learned to (apparently psychically) diagnose my computer's ailings from afar. Turns out that VLC, as you predicted, is NOT the culprit. Turns out the wireless network has gotten a little strange since upgrading the laptop to 9.04.

I still don't know exactly where to start, but at least you helped my eliminate the blame-it-on-VLC train of thought I was on. 

Now I'm off to start a thread along the lines of "how to diagnose problems with a home wireless network"...

Thanks for your thoughtful feedback. I really appreciate it.

_HI

---

### Post by starcraft.man on 2009-06-29
Psyonic abilities developed from too much STARCRAFT!!!

Hehe, glad to help :).

---

