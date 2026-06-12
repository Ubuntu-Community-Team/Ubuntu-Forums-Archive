---
title: "alsa configuration for jack"
date: 2006-05-13
forum: Multimedia &amp; Video
---

### Post by stoa on 2006-05-13
hello!

I have ubuntu 5.04 with alsa and jack installed
When I'm starting qjackctl and try to start jack I'll receive this error:
"Could not connect to JACK server as client." and in the message box: 
"jack_creat_thread: error 1 setting scheduler parameters after thread creation: Operation not permitted
cannot start watchdog thread
cannot load driver module alsa"

I think this has something to do 
with the loading module of alsa at start up, but I'm not sure 'cause I'm new not only to alsa and jack, but to linux too :) 

What should I do?

Thanx

---

### Post by pdobrev on 2006-05-13
Umm... I once had a similiar issue. I think you're running jackd as root and trying to connect to it through qjackctl as normal user, that's why you get the permission denied message. If that's the case, try running jackd as a user.

Hope this helps,
Petar.

---

### Post by dolson on 2006-05-13
If you run QjackCtl, there's really no reason to run jackd separately. Just look at the options in QjackCtl.. [http://ubuntustudio.com/wiki/index.php/Breezy:JACK_Configuration](http://ubuntustudio.com/wiki/index.php/Breezy:JACK_Configuration)

It sounds to me like the issue is the same thing we all had about a month ago. Deleting ~/.asound* solved the issue for me. If you haven't customized those files at all then I think you can safely delete them. Otherwise, just move them temporarily and try again.

---

