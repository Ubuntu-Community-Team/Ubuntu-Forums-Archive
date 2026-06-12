---
title: "PCMCIA Token Ring"
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by snevets on 2012-02-17
Greetings all.

I am trying to set up an IBM Turbo 16/4 pcmcia token ring card on Ubuntu 11.4. In case you're wondering I am aware that it's not 1989. We support specialized equipment that still runs token ring and our field engineers carry Windows laptops today. I would strongly prefer they were running Ubuntu.

I know there is a driver for the card, I found it on [http://manpages.ubuntu.com/manpages/dapper/man4/ibmtr_cs.4.html](http://manpages.ubuntu.com/manpages/dapper/man4/ibmtr_cs.4.html) but unfortunately I don't know how to configure it. I don't see the card when I execute lspcmcia so I assume it's not just plug and play and I'm missing steps. 

Any pointers would be much appreciated.

Thanks!

---

### Post by jonobr on 2012-02-17
Wow,

Token ring,

I have been networking for a long time and only came across 1 token ring network.
Then again,that may be not the norm experiece

Any way
try posting the results 
```
tail -f /var/log/message
``` 
plug it in, and see what pops up,
it may give you seome info which may be useful.....

Token ring,. wow,
(I just had to say it again:-)  )

---

