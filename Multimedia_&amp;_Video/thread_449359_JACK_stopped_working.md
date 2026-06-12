---
title: "JACK stopped working"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by digglah on 2007-05-20
Hi

A last week i was using jackd with ardour2 in realtime mode and it worked fine.
Now, without having done any changes to the system(wich i can remember), it wont start any more.

i get this error (snippet):

++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
11410 waiting for signals
jackd watchdog: timeout - killing jackd
Aborted


Its the same when i run it as root as any other user.
Any suggestions?

---

### Post by ricrac on 2007-05-20
Not enough info supplied.
  
The error may imply an alsa error, but it's probably just a bad jack config. Given that it was once working

Will alsa play sounds without jack?
How are you starting jack, by hand in terminal or qjackctl?

This, among others, comes up in a forum search on your error...
[http://ubuntuforums.org/showthread.php?t=401620&page=3](http://ubuntuforums.org/showthread.php?t=401620&page=3)

---

