---
title: "Enable recording from sound card, instead a mic"
date: 2016-05-09
forum: Multimedia Software
---

### Post by frank.falco24gmai on 2016-05-09
Hello

I am pretty new to Ubuntu and was wondering how I enable audacity or any recording app to record off me sound card, instead of my mic. In windows you can simply disable the mic and enable the sound card. Wondering if there is something comparable in Linux ?


Thanks !!
fry

---

### Post by Bucky Ball on 2016-05-09
*Thread moved to **Multimedia Software**.*

Welcome. In the top left corner of Audacity you will find a couple of drop down lists to select sound devices. See attached screenshot. Next to the mic, hit the drop down list and your card should be there to select. If it's not, it should be, so let us know.

(In my screenshot you'll see 'default' where the drop-down is. Click that on yours.)

---

### Post by frank.falco24gmai on 2016-05-09
Hi thanks your quick reply. My drop down only contains ALSA, I dont not see my sound card.

Thanks again

---

### Post by Dennis N on 2016-05-09
Hi...I'll give you this on recording streaming audio. It's how I do it.

> Open Audacity and Pulse Audio Volume Control (P.A.). Both are needed to record streaming audio. That's the only type of recording we are talking about here.

Leave the settings in toolbar as ALSA, default, 2(STEREO), default. Settings will be done in P.A.

_Set Up Source and Levels:_

Start playing some streaming audio. In Audacity, click the recording level meter to start monitoring. While monitoring, you adjust the source and recording level in P.A.'s recording tab. See attached screenshot for correct source. Use the slider in the P.A. window to adjust volume to the optimal level as viewed in the recording level meter on the Audacity toolbar.

When you have the settings you want, click the meter again to stop monitoring. Click record to start the real recording.

Pulse audio keeps its settings between uses so you may not need to set up source/levels the next time. You can just open Audacity and start recording.

Good luck with your recordings!

---

### Post by frank.falco24gmai on 2016-05-09
Hi Dennis

This is great detail I appreciate it, however I followed these steps and Audacity is recording audio, but it is recording it from the mic, not the sounds card ?

Am i missing something here

Thanks

---

### Post by frank.falco24gmai on 2016-05-09
Hi Dennis

Please ignore, followed you snapshot and it worked like a charm, thanks again for all your help !!!

Frank

---

### Post by Dennis N on 2016-05-09
> **frank.falco24gmai said:**
> Hi Dennis
...followed you snapshot and it worked like a charm, thanks again for all your help !!!
Frank
Hey..
Glad to hear you are now recording streaming audio. Yes, the screenshot shows the key setting. Otherwise you get nothing. Post back if you have further questions.

---

### Post by mc4man on 2016-05-09
I always think it's worth a mention because it is an excellent app, team page - 
[https://launchpad.net/~audio-recorder](https://launchpad.net/~audio-recorder)

---

### Post by Bucky Ball on 2016-05-10
All good. Please mark the thread as solved to help others and start a new one for any further issues. 

Incidentally, I explicitly said click the drop-down box marked 'default'. That is to the right of the one marked 'ALSA'. No, your sound card won't be in the one marked 'ALSA'. It should be in the one marked 'default'. ;)

---

