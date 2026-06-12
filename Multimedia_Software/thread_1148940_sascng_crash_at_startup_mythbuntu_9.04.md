---
title: "sascng crash at startup mythbuntu 9.04"
date: 2009-05-04
forum: Multimedia Software
---

### Post by jsvens on 2009-05-04
Hello all,

What are the changes in the boot sequence as sascng crashes at startup.
Also the virtual tuners are unrecognizeable by the myth-backend and thats the reason why I think that the speeded boot sequence is the reason.

Is there anyway to go around the problem?

Can I slow down the boot sequence?

I was wery happy with the 8.10 dist but I wanted ext4 support and I also wanted the improvements regarding alsa sound and better support regards to my motherboard.
I do not want to step back to 8.10.

Greatings 

Johan

---

### Post by qwerdy on 2009-05-06
I'm having the same problem.

Can't get open-sasc-ng to start at boot in 9.04.
I have tried with a init.d script and adding it to /etc/rc.local

If i run /etc/rc.local manually, everyhing works

---

### Post by mrbaze on 2009-06-05
> **jsvens said:**
> Hello all,

What are the changes in the boot sequence as sascng crashes at startup.
Also the virtual tuners are unrecognizeable by the myth-backend and thats the reason why I think that the speeded boot sequence is the reason.

Is there anyway to go around the problem?

Can I slow down the boot sequence?

I was wery happy with the 8.10 dist but I wanted ext4 support and I also wanted the improvements regarding alsa sound and better support regards to my motherboard.
I do not want to step back to 8.10.

Greatings 

Johan

Hi Johan,
1. What do you mean by "the virtual tuners are unrecognizable"? I can add them as usual, although one of my cards has been messing up, I don't know if that was because of 9.04 or the card just broke. Need to look into that..

2. Other than this I have gotten it to work. I have a script starting sasc and then mythbackend (had that before also) but now I had to add "sleep 3" before continuing for it to work from boot. When running the script again it works without the sleep.

Cheers
baze

---

### Post by mrbaze on 2009-06-05
> **qwerdy said:**
> I'm having the same problem.

Can't get open-sasc-ng to start at boot in 9.04.
I have tried with a init.d script and adding it to /etc/rc.local

If i run /etc/rc.local manually, everyhing works

Hi,
try running the script from ~/.config/autostart/mythtv.desktop (change the Exec: line) and add "sleep 3" at the beginning of the script, worked for me ;)

/baze

---

