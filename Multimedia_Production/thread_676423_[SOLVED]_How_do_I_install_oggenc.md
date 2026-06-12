---
title: "[SOLVED] How do I install oggenc ?"
date: 2008-01-23
forum: Multimedia Production
---

### Post by NovaAesa on 2008-01-23
How do you install oggenc? I have had it installed previously on a different install, but on this new one I can't remember how I installed it. I tried installing using apt-get but that didn't work:

```
ps@inspiron:~$ oggenc
The program 'oggenc' is currently not installed.  You can install it by typing:
sudo apt-get install vorbis-tools
bash: oggenc: command not found
ps@inspiron:~$ sudo apt-get install oggenc
[sudo] password for ps:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package oggenc
ps@inspiron:~$ 
```

Anyone know how to get it installed. The only differece between this install of Ubunut and my last one is that it's on a different computer (shouldn't make any difference) and its Gutsy 64 bit rather than Gutsy 32 bit (I think this might be the issue).

Thanks in advance to anyone who might know what the problem is.

---

### Post by logos34 on 2008-01-23
you were close.

read the third line down.

sudo apt-get install vorbis-tools

---

### Post by NovaAesa on 2008-01-23
Gosh I feel silly :S I just worked it out. It was sudo apt-get install vorbis-tools.

EDIT: Thanks logos34 for helping out.

---

### Post by logos34 on 2008-01-23
hey, no prob.

I make little mistakes all the time on the command line.

---

