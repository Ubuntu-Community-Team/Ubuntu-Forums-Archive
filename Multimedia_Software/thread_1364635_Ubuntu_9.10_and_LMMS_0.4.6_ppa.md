---
title: "Ubuntu 9.10 and LMMS 0.4.6 ppa"
date: 2009-12-26
forum: Multimedia Software
---

### Post by hugues72 on 2009-12-26
Hello, 
I have recently installed Ubuntu 9.10, then LMMS 0.4.5, then Ubuntu Studio for Ubuntu 9.10. and finally upgraded LMMS 0.4.6 ppa-3

2 issues:

1. 
I now have lost all sound, even at startup.
when i do 
sudo /etc/init.d/alsa-utils stop
sudo alsa force-reload
sudo /etc/init.d/alsa-utils start

it works once, then it does not work anymore at the next startup

2. 
When I try to follow the LMMS tutorial, [http://lmms.sourceforge.net/wiki/index.php?title=Fr:Your_First_Song_with_LMMS](http://lmms.sourceforge.net/wiki/index.php?title=Fr:Your_First_Song_with_LMMS) , I have got LMMS who freezes.

i have probably have too many sound devices or managers installed. 
What can i do to re-establish a good environment?

thx u very much for any help.

---

### Post by hugues72 on 2010-01-01
when i look into more details, it seems that there are one or several processes lmms, who remain stuck even after closing the lmms or forcing to close lmms. 

when i kill these processes and restart lmms, after playing one sound it freezes again...

any ideas on what to do next?
thx

---

### Post by philip5 on 2010-01-01
> **hugues72 said:**
> when i look into more details, it seems that there are one or several processes lmms, who remain stuck even after closing the lmms or forcing to close lmms. 

when i kill these processes and restart lmms, after playing one sound it freezes again...

any ideas on what to do next?
thx

I'm not sure if it helps but I also have the latest LMMS 0.4.6 on my repo for 9.10/Karmic and you could give my packages a try to see if that help with your problem:

[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

Maybe worth a shot?!?!

Regards,

Philip

---

