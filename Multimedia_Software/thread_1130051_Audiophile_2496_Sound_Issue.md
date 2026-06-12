---
title: "Audiophile 2496 Sound Issue"
date: 2009-04-19
forum: Multimedia Software
---

### Post by Mr_Sunshine on 2009-04-19
Hi All...long time reader, first time poster.

After many hours of trial and error, I have finally got sound with my PCI M-Audio Audiophile 2496. I followed the tutorial I found on a different posting and uninstalled ALSA then installed OSSv.4. Also, added OSSmix.

Sound is ok, but while playing music with Rhythmbox in the background I get alot of draggy/jerky music when I'm doing other things such as opening/closing programs or min/max Firefox. 

I use this setup in Windoze for music production and would like to eventually get something going with my current installation of Ubuntu 8.10, so if you guys can help me with the sound issues and give me any tips as to other things that I may to add or remove to be able to eventually work with MIDI, etc (Jackd??), I would greatly appreciate it.

Thanks,
Chuck

---

### Post by markbuntu on 2009-04-19
Don't bother, the rt kernel is broken in Intrepid and probably won't get fixed. Jack will not work with OSS4 as far as I know.

But....there are lots of people using the 2496 with great succes with unbuntustudio in Hardy 8.04 without having to resort to OSS4. If you are not in a hurry, Jaunty will be out soon and the rt kernel is in much better condition for that release. 

The multimedia production forum is where you need to be. It is a little slow sometimes but the people there really know what they are talking about.

---

### Post by Mr_Sunshine on 2009-04-20
Thanks...I appreciate the response.

Should I go with Ubuntu 8.04 or the new beta release? Also, should I consider the Studio version?

Thanks again...

---

### Post by markbuntu on 2009-04-20
Hmmm. that is a tough question right now. Jaunty will be released in a few days. There is an ongoing thread about UbuntuStudio in Jaunty in the Development and Programming forum here /Jaunty jackalope testing. You might want to check it out.

You can install the ubuntustudio packages over a regular ubuntu install. That is what I usually do in case there is trouble with the rt kernel I can use the generic kernel from the ubuntu install as a fallback.

The best thing would be to get a ubuntu live cd and run that first to make sure everything works before installing.

---

### Post by Mr_Sunshine on 2009-04-21
...installed 8.04 and sound is still draggy/jerky while doing other things. If I open a Youtube vid and minimize the browser, the sound drags...Help!!

---

### Post by markbuntu on 2009-04-21
Go here to get your sound dialed in correctly

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by leifjonny on 2009-04-25
Sound is still jittering in jaunty. Was perfect in some earlier version when I bought the card (edgy or feisty perhaps).

---

### Post by electrovalent on 2009-05-14
Hi i am also having problem to make my audiophile 2496 soundcard to work.Any solusions?

---

### Post by QwUo173Hy on 2009-05-20
This card is working so far for me in Jaunty. I'm only playing mp3s and testing out Audacity so far.

---

