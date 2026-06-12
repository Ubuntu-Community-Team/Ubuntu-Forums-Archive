---
title: "pure data : probleme with make after ./configure --enable-jack"
date: 2011-12-27
forum: Multimedia Software
---

### Post by caracteriel on 2011-12-27
Hi

  When I compile pd-extended after ./configure --enable-jack
I get : 

etc…………
… undefined reference to `jack_port_register'
/home/caracteriel/Pd-0.42.5-extended/pd/src/s_audio_jack.c:341: undefined reference to `jack_port_register'
s_audio_jack.o: In function `jack_connect_ports':
/home/caracteriel/Pd-0.42.5-extended/pd/src/s_audio_jack.c:210: undefined reference to `jack_port_name'
collect2: ld returned 1 exit status
make: *** [../bin/pdextended] Error 1

I use Ubuntu.
Jack is installed with .deb
Any Ideas ?

Cdt

---

