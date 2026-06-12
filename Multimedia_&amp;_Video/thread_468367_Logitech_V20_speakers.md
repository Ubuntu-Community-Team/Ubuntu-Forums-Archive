---
title: "Logitech V20 speakers"
date: 2007-06-08
forum: Multimedia &amp; Video
---

### Post by Angelbeast on 2007-06-08
Okay well it seems that just as soon as i resolve one issue with Ubuntu another pops up.

Now i am having trouble with my logitech v20 usb speakers. They were working fine until now. When they re plugged in sometimes in the sound preferences it will say they are not connected. Then i have to unplug and plug them back in a few times then it will show they are cnnected. But even then i get no sound out of them. The sound always comesout of the built in speakers and in the volume control icon it says they are headphones, no matter what i set the prefs to. But now at least the buttons on the top work...ha...does ANYONEe know how tofix this?

---

### Post by Angelbeast on 2007-06-08
it looks like i am getting sound through the usb speakers from pidgin alerts. i did reently change from totem gstream to totem xine for the dvd support...would that have any effect?

---

### Post by Angelbeast on 2007-06-10
anyone? any ideas?

---

### Post by barrykooda on 2007-06-11
I'm waiting anxiously for a response to your problem since I've been having the same issue.
Good luck!
Somebody.... HELP!!

---

### Post by mcduck on 2007-06-11
Since they are USB speakers, they have soundcard of their own. So, you to either set them as the default sound interface of Ubuntu (In System/Preferences/Sound if I remember right) or choose them as the sound card used in application settings (for all applications you want to use those speakers).

Also if you want the volume control applet and your keyboards volume keys to control volume of those speakers instead of your computers soundcard, you need to go to that applets settings and choose your USB speakers as the sound interface.

---

### Post by barrykooda on 2007-06-11
`I tried that but still no go. I also tried the "passthrough" option. When I "TEST" the tone comes through the Logitechs so loud that they distort but that's the only sound I can get them to produce. Oddly, the volume and mute controls on the Logitechs do work on the laptop speakers.

---

### Post by barrykooda on 2007-06-11
Hey Angelbeast,
I found this post and it seemes to have worked for me.
I entered the code and got a slightly different list but then entered the "sudo asoundconf set-default-card Speaker" and my speakers started working.
Thanks, Deltafoxtrot!

> **deltafoxtrot said:**
> Check out this link: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_default_soundcard]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_default_soundcard").  Worked for me (I'm also using the Logitech V20 speakers). 

```
$ sudo asoundconf list
Names of available sound cards:
ICH6
Speaker

$ sudo asoundconf set-default-card Speaker
```

Presto chango...  Restart any apps requiring a soundcard that may have been open prior to changing the default.

Good luck!

---

### Post by Angelbeast on 2007-06-14
> **barrykooda said:**
> Hey Angelbeast,
I found this post and it seemes to have worked for me.
I entered the code and got a slightly different list but then entered the "sudo asoundconf set-default-card Speaker" and my speakers started working.
Thanks, Deltafoxtrot!

ooooo...i'll give this a try, thanks...i didn't realize there were any more replies...i stopped getting notifications *LOL*

---

### Post by Angelbeast on 2007-06-14
No luck...What would make them work when someone signs on and off in pidgin but not for movies and music? I posted about this in the logitech help forums and got a real nice reply from one of the support people...

"Try using them on what they were designed to run on"

now if the speakers themselves were defective would i even be getting sound from pidgin on them?

---

### Post by barrykooda on 2007-06-14
Wow!
That's pretty friendly tech support.
I still don't have everything working with the speakers like I'd like but that post was the first one that actually made them work at all.

---

### Post by Angelbeast on 2007-06-16
> **barrykooda said:**
> Wow!
That's pretty friendly tech support.
I still don't have everything working with the speakers like I'd like but that post was the first one that actually made them work at all.

well i just don't understand why i am getting instant messenger sound through them just fine but nothing else...

---

