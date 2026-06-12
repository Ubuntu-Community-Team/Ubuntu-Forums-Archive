---
title: "No sound but error beeps"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by Frogster on 2008-01-03
I think this has been done to death but any help would be greatly appreciated. I have followed all the recommendations on the threads I can find but none seem to get the sound working on this machine!

---

### Post by Catalyst2Death on 2008-01-03
Could you post the sound card and system specs that go with your card?  There are a lot of hardware specific tweaks and things which can get cards working as long as you know what the card is.  

Do different sound drivers work?  Have you tried to change the driver by going to System > Preferences > Sound  and then under sound playback choose Alsa or OSS. Try playing something on each setting.

---

### Post by Frogster on 2008-01-03
Hopefully this is what you are after:

:~$ cat /proc/asound/cards 
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with VT1616i at 0xdc00, irq 20

If this isn't helpful or you require any further information just say as I am growing to like this OS and the only glitch so far is sound!

Thank you for the response any help will be gratefully received :)

---

### Post by Catalyst2Death on 2008-01-06
have you tried different drivers like I suggested?  Another thing which will screw things up is if you have multiple cards... On my desktop, I had two onboard cards and a 5.1 card and it caused major issues (finally the fix was simple: blacklist the other cards and force the 5.1) This is probably not your problem...

try this in a terminal:
$alsamixer

it should give you a text-based GUI that might help you out... make sure that master and pcm are unmuted and all the way up (at least PCM, master is well, the master control, so you'll blow your eardrums if its up way too loud and you have big speakers) also look through and play with things (but make sure that you remember the default settings, so just change one thing at a time)  it may be as simple as turning something on or off.

Is there any specific problems (only system sounds work, absolutely no sound works, mp3's appear to play but no sound)  these could point to drastically different solutions...

---

### Post by lisati on 2008-01-06
> **Catalyst2Death said:**
> 
Is there any specific problems (only system sounds work, absolutely no sound works, mp3's appear to play but no sound)  these could point to drastically different solutions...
Also, is the beep from the PC speaker or from the speakers hooked up to the sound card?

---

