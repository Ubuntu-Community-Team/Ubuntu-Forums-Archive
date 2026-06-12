---
title: "DeVeDe in Maverick DVD ISO size issues."
date: 2010-10-23
forum: Multimedia Software
---

### Post by coffeecat on 2010-10-23
In every version of DeVeDe I've used since whenever, it has calculated the final size of the DVD ISO well and the 'Adjust disc usage' button has worked reliably in changing the video bitrate to get all the videos onto the chosen size of disc. Not with version 3.16.9, I find.

I've wasted several hours trying to create a DVD ISO  that will fit on a standard 4.7 GB DVD. I should have known something was wrong when it told me that six 1 hour mpegs, each about 1.5GB, would fit on one 4.7GB disc with room to spare. When I set it up for three such mpegs, and clicked the adjust button, it gave me 71% full of a 4.7GB, but created a 6.5GB ISO. :?

After several unsuccessful attempts, I've at last got a 4.0GB ISO with two 1 hour mpegs by setting the media size to 1.4 GB DVD and clicking the adjust button to get  99%. 99% of 1.4 is 4.0, is it?

Anyone else getting this? Any fixes?

Tbh, I can't remember whether I used DeVeDe in Lucid, but I know that it was reliable in Karmic. I'll try in Lucid next and see which version Lucid has.

**Edit:** posting from Lucid. Lucid has 3.6.18 and I'm probably going to get the same nonsense. Adding just one of those 1.5GB mpegs and leaving the video conversion bitreat at the default 5001 Kbits/sec tells me that a 4.7GB DVD will be 14% full. Which is what I was getting in Maverick/3.6.19.

---

### Post by coffeecat on 2010-10-24
SOLVED - sort of.

Short story. After posting I realised that prior to this I had been using AVIs and perhaps this was why I had not had a problem. This must have been the first time I had used TS-mpegs which has unmasked DeVeDe's inaccuracy in predicting ISO size.

Long story.

This time I had used TS-mpegs from digital TV broadcasts. I had cleaned them up with MPEG-Streamclip in MacOS and snipped the unwanted bits off fore and aft. (BBC transmission - no ads :)). Why had I not used avidemux? Because it should be called avide-let's-see-how-much-we-can-push-the-video-and-audio-out-of-sync-mux.

And the mpegs caused the problem I described in my first post. Googling the issue brought up stuff from people getting too-small ISOs rather than too-large and I found a post from the developer of devede on a Launchpad thread saying the problem was in mencoder, which makes it difficult to predict the final size.

With all my previous efforts I had transcoded the TS-mpegs into Xvid AVIs, partly to get round the sync problem when using avidemux for editing. Avidemux (mostly) edits AVIs OK. Something in the name I guess. :-k So I transcoded two of the 1-hour mpegs to Xvid AVI and this time devede predicted a 120% usage on a 4.7GB DVD. Clicking 'adjust' to bring that down to 99% resulted in a 3.6GB ISO, which at least is usable.

Clearly the disc usage bar is wildly unreliable. Tbh I hadn't noticed that ISOs I had made before were that much smaller. If I had left the disc usage at 120% I probably would have got a 4.4GB ISO.

Food for thought, and I hope this might be useful for others.

---

### Post by pasena on 2011-02-13
I had almost the same problem with my devede on any distributives. After using Adjust disc usage the size bar showed 99%. After finishing encoding DVD i had a size ~3.6-3.8 Gb. Then i started to edit manually video bitrate to have 112-113%. But then i edited file:
sudo gedit /usr/lib/devede/devede_other.py

there you should edit this block to get the size you want:
		if 0==active:
			tamano=170.0
		elif 1==active:
			tamano=700.0
		elif 2==active:
			tamano=750.0
		elif 3==active:
			tamano=1100.0
		elif 4==active:
			tamano=4200.0    <<===== (i have 4600)
		else:
			tamano=8000.0 
after that compile this file:
sudo python -m compileall /usr/lib/devede/devede_other.py

And after using Adjust disc usage button you will have full size dvd 4.2-4.4 gb. Have fun!

---

