---
title: "only some speakers work"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by tombug on 2007-04-20
Ok, i have a SB live! 24bit, and sound will only play  from the front right/left speakers, and i have 5.1, and i would like all the speakers to work. I can cant figure it out for the life of me. So if anyone knows how i can fix i be so happy:).

i have sb live! 24bit, all speakers are plugged in and do work, sounds on and up, nothing muted
any advice??

thanks ahead of time

---

### Post by TorchSoul54 on 2007-04-20
I am also having this problem, same setup SB Live! 24bit. Any help would be greatful. I miss my 5.1 :(

Thanks for any help

---

### Post by tombug on 2007-04-20
nvm fixed it
id did this below and then it worked

sudo gedit ~/.asoundrc

and add the following lines

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}

---

### Post by blindcavefish on 2007-04-22
> **tombug said:**
> nvm fixed it
id did this below and then it worked

sudo gedit ~/.asoundrc

and add the following lines

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}
I tried this and now have NO sound at all. How do I undo this?

---

### Post by tombug on 2007-04-22
> **blindcavefish said:**
> I tried this and now have NO sound at all. How do I undo this?

go to your home folder, press ctrl + h, then look for ".asoundrc" and then delete it, that should bring your sound back if you did what i said fixed sound for me

---

### Post by blindcavefish on 2007-04-23
> **tombug said:**
> go to your home folder, press ctrl + h, then look for ".asoundrc" and then delete it, that should bring your sound back if you did what i said fixed sound for me

Thank you for answering Tombug. I followed your instructions and my sound is back. I learned a bit about the terminal in the process of following the first advice. Desperation to get this whole soundcard to work drove me to actually trying something that involved....THE TERMINAL. I think next I will try an older version of Ubuntu, that is, unless you have any other ideas for getting a Soundblaster live model ct 4760 to work. 
Anyway, thanks again. Sorry if this post is lame. I'm totally new to this forum thing. And for that matter the Linux thing. It's frustrating, but fun.

---

