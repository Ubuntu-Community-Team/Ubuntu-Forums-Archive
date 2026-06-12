---
title: "ndisgtk problem"
date: 2006-02-01
forum: Networking &amp; Wireless
---

### Post by XFlamez on 2006-02-01
hi, im new to linux, like a major noob
but i've been reading alot in this forum before i registered

sorry if this was mention, but i definitely appreciate the help
i really want to learn how to use linux

from what i read
i can just install ndisgtk without ndiswrapper for my  linksys WUSB54G to work right?

if thats the case, how do i install ndisgtk
i put the ndisgtk_0.5-1ubuntu1_all.deb on the desktop

what do i do now?
i know i have to go to terminal. 
do i type  > sudo dpkg -i ndisgtk_0.5-1ubuntu1_all.deb

or i have to type something else?

cuz i tried to type the above and i didn't get anything

Thanks

---

### Post by jannol on 2006-02-01
isn't ndisgtk in the repos?

have you tried

sudo Desktop/dpkg -i ndisgtk_0.5-1ubuntu1_all.deb

??

---

### Post by XFlamez on 2006-02-01
thanks for the quick reply, the computer is off right now
i'll definitely give it a try tomorrow

and please forgive me if my question is dumb or anything like it

I AM A TOTAL NOOB
this is my first time running linux
so even the appearance is still new to me

---

### Post by XFlamez on 2006-02-02
[QUOTE=jannol]isn't ndisgtk in the repos?

have you tried

sudo Desktop/dpkg -i ndisgtk_0.5-1ubuntu1_all.deb

??[/QUOTE]

i think i got it to work

---

### Post by jannol on 2006-02-02
you really should explain what you tried and how etc as it is nearly impossible to consider every angle of what the problem is.

also do you use dapper or breezy, if breezy you could add

[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

to your repos in synaptic

---

### Post by XFlamez on 2006-02-02
well i got the WINDOW WIRELESS DRIVERS showing in admin
but i can't seem to install anything
it won't show up

i downloaded drivers from [http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/)
i downloaded rt2500, and theres no INF files for me to install
so im stuck

---

### Post by XFlamez on 2006-02-02
also i am using breezy

---

### Post by jannol on 2006-02-02
the inf file is on the install cd but I guess you don't have that, well it might be possible to download them and unpack/install in windows so you can copy the inf file. Maybe you could ask a friend with win to help you out...

---

### Post by XFlamez on 2006-02-02
well i have the linksys cd driver
which has the INF file
but when i tried to use it
ubuntu doesn't do anything, no messages or anything, as soon i click install, nothing happens

---

### Post by jannol on 2006-02-02
you must choose only an inf file and if I remember correctly there must must be a sys file in the same directory as the inf, for some cards, I do not know about linksys.

That got messy, what i ment was, one should select the inf file from the directory that holds it along with other files.

---

