---
title: "SSH key Authentication"
date: 2011-04-15
forum: Networking &amp; Wireless
---

### Post by Ceiber Boy on 2011-04-15
If this is a in the wrong location or a reoccurring discussion a apologise and ask that it be moved...

Is SSH secure from bruit force attacks, spoofing or any other type of unauthorised login if **key Authentication** is solely used? (i.e. password Authentication disabled).

---

### Post by joberly on 2011-04-15
In theory, the short answer is no. 

However, in practice, SSH keys are damn near impossible to break. Brute force attacks basically attempt every possible combination of keys. Currently, even 128 bit keys are out of reach for conventional hardware, nevermind the 2048 bit default SSH key length.

A couple of good resources:
[http://en.wikipedia.org/wiki/Brute_force_attack](http://en.wikipedia.org/wiki/Brute_force_attack)

[http://en.wikipedia.org/wiki/Cryptographic_key_length](http://en.wikipedia.org/wiki/Cryptographic_key_length)

---

