---
title: "Automatically patch netjack to main out in jackd?"
date: 2010-06-01
forum: Multimedia Software
---

### Post by Defrector on 2010-06-01
How do I get netjack to automatically patch to the (physical) system outputs when it connects to jackd?

Currently I have to open qjackctl manually and route netjack every time I log in. Is there a terminal interface for jackd or a special switch arg on netjack so I may automate this from a script?

---

### Post by Defrector on 2010-06-01
Thanks to the jack-devel list:KS

The solution is to use the jack_connect terminal command.

########### SOLVED ####################

---

