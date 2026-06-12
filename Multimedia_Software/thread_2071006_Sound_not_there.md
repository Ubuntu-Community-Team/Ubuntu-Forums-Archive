---
title: "Sound not there"
date: 2012-10-14
forum: Multimedia Software
---

### Post by Future Warthog on 2012-10-14
Ok, I am running Ubuntu 12.04 on a Toshiba Satellite A105 S4384 and for some reason, unknown to me, it won't play sound. 
I just upgraded from I think it was 11.10, but I don't remember if it played sound or not. It probably was there but I wasn't paying attention.  I have tried going through ```
alsamixer
``` but nothing happens.

Any help is appreciated.

---

### Post by Yellow Pasque on 2012-10-14
More info please: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by UltimateCat on 2012-10-14
Make sure that the columns are not muted {mm} in the alsamixer-

Try a sound test too and see if that helps after adjusting all the columns in the alsa mixer.

Check on your sound card and see; it might need a driver to work-

---

### Post by Future Warthog on 2012-10-14
Ok, I just made the stupidest mistake.
The manual speakers dial was off #-o

Thanks for trying to help :)

---

### Post by okkie on 2012-10-16
I have just installed 12.04 as well and no sound.Everything is of course strange as can be expected.I supplied the info to alsa as requested above but what now?
Please tell me where I can find alsa mixer to try and sort out my problem and how do I know if I perhaps need a driver. I only have the computer onboard sound system.
Thanks

ps    

Is there a guide that tells us where to find things on 12.04 ? After years of Ubuntu I don't know where I am.

---

### Post by Yellow Pasque on 2012-10-16
> I have just installed 12.04 as well and no sound.
You should probably start your own thread, unless you have the same hardware as OP.

> I supplied the info to alsa as requested above but what now?
Now you copy and paste the link the script gave you.

> Please tell me where I can find alsa mixe
Go to the terminal and enter:
```
alsamixer
```

---

### Post by okkie on 2012-10-17
Thanks.Alsamixer in terminal.....no such file or directory.

I started a new thread as it appears this is going to take some time.

---

