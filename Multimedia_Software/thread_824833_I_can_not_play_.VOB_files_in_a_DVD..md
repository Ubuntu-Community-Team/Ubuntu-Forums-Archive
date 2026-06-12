---
title: "I can not play .VOB files in a DVD."
date: 2008-06-10
forum: Multimedia Software
---

### Post by betoco on 2008-06-10
Hello,

    I need help with the following problem. When try to play DVD (Aplication sound&video movie player) get the follwoing message:

Totem cannot play this type of media (DVD) because it does not have the appropiate plungins to be able to read from the disc.

I have a Dell XPS 700 machine configured with a Sound Blaster board X-FI Pci SB0460.  I don´t know if I need a driver, plugins or any other software.

Could you help me to fix this?

mcc

---

### Post by TenPlus1 on 2008-06-10
First, follow this quick guide on enabling medibuntu repo's:

[http://ubuntuforums.org/showthread.php?t=713009](http://ubuntuforums.org/showthread.php?t=713009)

Then goto synaptic package manager and install the following:

totem-xine 
libdvdcss2
libdvdnav4
libdvdread3

This will install the working libraries and totem back-end that will let you play DVD's without a problem...

---

### Post by betoco on 2008-06-10
Hi tenplus1,

   Thanks for your post.  I want to tell you that I installed only totem package and totem movie player work fine.  Previusly i had installed build-essential package.  When execute totem movie player it ask me for plugins, i checked OK (the machine now was connected to internet) the system download "anything" and player work.

Note: I don´t now why but work so I´m not install totem-xine.

Thanks
mcc

---

### Post by betoco on 2008-06-10
Sorry, I forgot to say you that sound doesn´t work. I can watch the movie but i can´t listen sound.

Could you tell me what could be the problem?
mcc

---

