---
title: "there be transformers in my HDMI audio!!"
date: 2011-01-21
forum: Multimedia Software
---

### Post by mahalos on 2011-01-21
right then.... i've tried figure this one out myself and haven't had any luck. i did a clean install of 64bit 10.10 on my ASUS K52J laptop the other day, just to have a clean slate. The problem i have is with hdmi audio to my TV. I get audio fine, it's just that I have a strange sound that appears every 10 seconds, it's sounds like something off Transformers.....seriously. It's only there for a split second, but very noticeable.

things i've tried are
- booting into WIN7 to see if the same problem is there....nope all good, so cable and TV aren't the issue.

- tried outputting audio to the TV via the headphone jack (analogue)....all good, no strange sounds.

- tried turning down all volumes in alsamixer on the laptop incase something was to loud...no difference.

- tried various applications for sound and video...no difference

So i'm stuck, obviously it's some kinda digital output issue....but how to fix it??

I've included a rough recording so you may hear what i'm talking about...you may need to turn your volume up!!

any help appreciated.

---

### Post by vidtek on 2011-01-25
> **mahalos said:**
> right then.... i've tried figure this one out myself and haven't had any luck. i did a clean install of 64bit 10.10 on my ASUS K52J laptop the other day, just to have a clean slate. The problem i have is with hdmi audio to my TV. I get audio fine, it's just that I have a strange sound that appears every 10 seconds, it's sounds like something off Transformers.....seriously. It's only there for a split second, but very noticeable.

things i've tried are
- booting into WIN7 to see if the same problem is there....nope all good, so cable and TV aren't the issue.

- tried outputting audio to the TV via the headphone jack (analogue)....all good, no strange sounds.

- tried turning down all volumes in alsamixer on the laptop incase something was to loud...no difference.

- tried various applications for sound and video...no difference

So i'm stuck, obviously it's some kinda digital output issue....but how to fix it??

I've included a rough recording so you may hear what i'm talking about...you may need to turn your volume up!!

any help appreciated.

Had a listen, it is strange, I think as it's a laptop, you may have a tsr or resident programme loaded which is running in the background.  Check and see if there is anything which polls your machine in sync. with these funny noises.  It may be something as silly as a battery monitor or email client.
There maybe a clue in the fact that it's ONLY hdmi that gets it, is there something in the video driver that does any polling at 10 sec intervals?  Maybe you could try an older video driver see if that does it too.
Best of luck, Tony.

---

### Post by mahalos on 2011-01-26
Thanks for the tips Tony. I'll certainly be taking a closer look at your suggestions.

Cheers
Carl

---

