---
title: "No Sound in Youtube Videos"
date: 2008-05-06
forum: Multimedia Software
---

### Post by viglin on 2008-05-06
I installed the latest Adobe Flash Player, But still i have no sound in any videos i watch, I even selected the highest volume still no sound!

Help!!

---

### Post by NilsE on 2008-05-06
Try installing libflashsupport from Synaptic.

---

### Post by henriquemaia on 2008-05-06
> **NilsE said:**
> Try installing libflashsupport from Synaptic.

Thanks for pointing this out. I think my aptitude removed that by mistake and I lost sound on flash. That did the trick.

---

### Post by cmlewin on 2008-05-06
If I play a track in rhythmbox, pause it and try to play a video on youtube I get no sound on the video.  If I then close both rhythmbox and firefox (or epiphany) then reopen firefox, the video or any other flash media will play WITH sound.  Is there an easy fix?

---

### Post by NilsE on 2008-05-06
> **cmlewin said:**
> If I play a track in rhythmbox, pause it and try to play a video on youtube I get no sound on the video.  If I then close both rhythmbox and firefox (or epiphany) then reopen firefox, the video or any other flash media will play WITH sound.  Is there an easy fix?
Ironically, the fix is to remove libflashsupport but you may not get sound in flash..

libflashsupport was removed as a dependancy from the flashplugin-nonfree because it was causing FF crashes for most people. If you remove it you may or may not have sound from flash in FF but it will allow multi sounds to play.

Some people have to have it installed to get audio on youtube and others don't.  I do not have it installed and get sound.

---

### Post by NilsE on 2008-05-06
I should have added, try it with and without libflashsupport installed to see what combination works best for you.

---

### Post by Chiaro on 2008-05-08
I installed libflashsupport and I still get no sound. Does it have to do with my sound card only working under OSS?

---

### Post by ukblacknight on 2008-05-09
I'm having exactly the same problems.  Stopping rhythmbox allows sound on flash.  I might try and change the device and see if that makes a difference.

---

### Post by hermes0710 on 2008-05-09
I had the same problem. I removed libflashsupport, reinstalled pulseaudio, disabled "Tell me..." options of ff's security options and everything goes smoothly

---

### Post by wkulecz on 2008-05-09
> try it with and without libflashsupport installed to see what combination works best for you.

Is it just me, or does any one else think we are headed down the road to windows-like dllhell with voodoo crap like this in the distribution?

Pick the one most stable config, fix the issues as they are discovered.  Not try one of three sound servers and hope one works!

--wally.

---

### Post by Zorael on 2008-05-09
Well, developers sadly have limited control over the spaghetti code Adobe creams out, with token linux support for us third-rate customers. :>

You could try Gnash and see if you have better luck with it. Naturally, it won't work on all pages.

[http://en.wikipedia.org/wiki/Gnash](http://en.wikipedia.org/wiki/Gnash)

---

### Post by tmcmurph on 2008-05-09
Unfortunately multimedia is what an OS is measured by for most people. If they can't listen to music and watch videos online then they will dump the OS quickly. For Ubuntu to make any inroads on desktops it will have to get a whole lot better at handling multimedia. For admins like me trying different things until something works is normal but for the other 99.999% of desktop users they fume and give up.

I use VLC, Skype and watch Youtube etc for most of my multimedia. VLC worked and Skype worked but I could only watch and hear Youtube if I closed VLC! If it was paused or stopped I would get no sound in Youtube. 

I know that the plethora of audio and video codecs is mind numbing but this must be resolved. Personally I think Dell did the right thing by putting in a commercial DVD player. If people have problems on audio and video they will only say bad things about your product.

Other than that the upgrade went quite smoothly.

---

