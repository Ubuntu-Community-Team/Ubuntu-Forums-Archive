---
title: "weak wireless connection on 11.04"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by REMIX8604 on 2011-04-11
i been using 11.04 on my netbook. the wireless connection is considerably less than in past versions. are the drivers any different? what if i install 10.10 then upgrade from there? will the drivers stay the same?

---

### Post by KegHead on 2011-04-11
Hi!

Try:

system...admin..additional drivers.

There may be drivers available to you.

I have a mini 9 w/no issues.

KegHead

---

### Post by REMIX8604 on 2011-04-11
it said they were no additional drivers found

---

### Post by KegHead on 2011-04-11
Hi!

Try:

control center...start up applications and make sure network manger is clicked.

Then click on the network manger on the top of your screen and search for connections.

I've logged on to someone else's wifi. If this has happened to you, just select your's.

KegHead

---

### Post by REMIX8604 on 2011-04-11
im sure im connected to my normal network. im not the only person with this issue. this is the only other thing i could find by search. 

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2781904.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2781904.html)

---

### Post by cariboo on 2011-04-11
It would help if you shared the info about your wireless device with us. What make/model?

---

### Post by 5149.5 on 2011-04-12
> **REMIX8604 said:**
> im sure im connected to my normal network. im not the only person with this issue. this is the only other thing i could find by search. 

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2781904.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2781904.html)

I find it illogical that an OS could affect a wlan connection that way. It's not impossible but improbable.There are other things at play that have nothing to do with the OS. Are you running on the same channel on both OSs?

---

### Post by REMIX8604 on 2011-04-12
i have a dell mini 1012. not sure what the exact make and model of card i have. id be happy to run whatever code and post results if that helps?

---

### Post by KegHead on 2011-04-12
Hi!

Please see post #6 and advise.

KegHead

---

### Post by walt.smith1960 on 2011-04-12
> **REMIX8604 said:**
> i have a dell mini 1012. not sure what the exact make and model of card i have. id be happy to run whatever code and post results if that helps?

I think we're looking for the results of the command "lspci" assuming this is an internal card. If it were a usb "dongle" the command would be lsusb (ls=list)

---

