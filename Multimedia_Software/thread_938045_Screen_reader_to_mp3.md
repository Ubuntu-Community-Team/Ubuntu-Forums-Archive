---
title: "Screen reader to mp3"
date: 2008-10-04
forum: Multimedia Software
---

### Post by TFr on 2008-10-04
Hi,

My iBook died so I replaced it with a Dell Ubuntu notebook. I've managed to find alternatives to all the software I used on my Mac except for one thing.

I used a screen reader and the automator to read text files into audio files that I could listen to on my ipod. Is this possible using Orca or any other tool in Ubuntu?

Thanks

TF

---

### Post by cariboo on 2008-10-04
Orca will do what you want, al thought the voice quality needs to be improved. To setup Orca press Alt-F2 and type:

```
orca -s
```

This will open up the setup utility, and you adjust the settings from there.

Jim

---

### Post by TFr on 2008-10-04
Thanks for the response but I don't think I was clear enough

I don't want the screen read to me while I'm sitting at the computer, I want to save the reading as an audio file so that I can listen to it on my mp3 player. 

Is there anything in Ubuntu that will let me make Orca output to a file? Or is there a way to get Orca to work with JACK audio so that I can control where the output goes manually?

---

