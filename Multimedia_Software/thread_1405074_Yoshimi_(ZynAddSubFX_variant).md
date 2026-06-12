---
title: "Yoshimi (ZynAddSubFX variant)"
date: 2010-02-12
forum: Multimedia Software
---

### Post by hardcopy on 2010-02-12
has anyone got any experience with yoshimi? its a variant of zynaddsubfx that apparently works better with jack... im currently having a few stability problems with zyn so am thinking of trying it out.

its a compile from source jobbie tho so any info & advice people have to help will be gratefully recieved.

[http://yoshimi.sourceforge.net/](http://yoshimi.sourceforge.net/)

[http://sourceforge.net/projects/yoshimi/files/](http://sourceforge.net/projects/yoshimi/files/)

edit: oops i should have probably put this in the other multimedia forum? i hope people still see it :)

---

### Post by VertexPusher on 2010-02-12
Thanks! I never noticed instability of Zyn with JACK, but I do miss an option to send each part (i.e. instrument) through a separate JACK sink instead of mixing them all down into one. Does Yoshimi implement that? The site doesn't have much info about its improvements.

---

### Post by hardcopy on 2010-02-12
im not really sure if theres an option for seperate outs for each instrument, would definately be a nice feature though (as well as the effects sends on seperate outs too) i guess i'll try to install it and report back, that might take a while though, im not exactly pro at this whole compiling from source business :)

i get xruns when saving / loading parameters, and i like to fine tune sounds on the fly which often crashes jack- very annoying. maybe its just my setup though :(

one feature i'd love is full automation of EVERY parameter in zyn- its such a shame that theres so little midi control with the depth and breadth of sounds possible, i will probably resort to recording 'live' performances of parameter tweaks, which might be frustrating due to the instability im getting when doing that.

---

### Post by VertexPusher on 2010-02-12
> **hardcopy said:**
> one feature i'd love is full automation of EVERY parameter in zyn- its such a shame that theres so little midi control with the depth and breadth of sounds possible
[http://zynaddsubfx.sourceforge.net/doc_3.html](http://zynaddsubfx.sourceforge.net/doc_3.html)

It's not that bad in my opinion. Controlling everything is simply impossible because Zyn is so complex.

---

### Post by hardcopy on 2010-02-12
> **VertexPusher said:**
> [http://zynaddsubfx.sourceforge.net/doc_3.html](http://zynaddsubfx.sourceforge.net/doc_3.html)

It's not that bad in my opinion. Controlling everything is simply impossible because Zyn is so complex.

i want to automate harmonic content controls, all the parameters on the filters, effects controls without having to use nrpn, etc

rather than hardcode controllers for each parameter, i would prefer to be able to assign any parameter to any controller, control multiple parameters from one controller, and set upper and lower bounds for controllers, allowing fine control. maybe it is asking a bit much, but its definately not *impossible* :D (personnaly i dont think its asking too much, this sort of complex automation is absolutely demanded by the industry these days)

---

### Post by hardcopy on 2010-02-12
ok i had to update some dependencies but now the install fails when i do 'make'

heres the terminal output if anyone can help :)

```
[  1%] Building CXX object CMakeFiles/yoshimi.dir/Effects/Distorsion.cpp.o
/home/graham/yoshimi/yoshimi-0.055/src/Effects/Distorsion.cpp: In member function ‘void Distorsion::setvolume(unsigned char)’:
/home/graham/yoshimi/yoshimi-0.055/src/Effects/Distorsion.cpp:293: error: ISO C++ says that these are ambiguous, even though the worst conversion for the first is better than the worst conversion for the second:
/usr/include/bits/mathcalls.h:154: note: candidate 1: double pow(double, double)
/usr/include/c++/4.2/cmath:357: note: candidate 2: float std::pow(float, float)
/home/graham/yoshimi/yoshimi-0.055/src/Effects/Distorsion.cpp:293: error: ISO C++ says that these are ambiguous, even though the worst conversion for the first is better than the worst conversion for the second:
/usr/include/bits/mathcalls.h:154: note: candidate 1: double pow(double, double)
/usr/include/c++/4.2/cmath:369: note: candidate 2: float std::pow(float, int)
make[2]: *** [CMakeFiles/yoshimi.dir/Effects/Distorsion.cpp.o] Error 1
make[1]: *** [CMakeFiles/yoshimi.dir/all] Error 2
make: *** [all] Error 2

```

---

### Post by maghoxfr on 2010-05-10
Just a question: I got yoshimi yesterday from [here]("https://launchpad.net/~falk-t-j/+archive/lucid") but I'm strugling to connect it via jack control or patchage to my midi usb controller (Oxygen 61). I think it should be via midi through port but I can't hook it up. Anyone know how to use yoshimi to my keyboard? Thanks

---

### Post by cchhrriiss121212 on 2010-05-10
You don't need to connect to midi through, just connect the green box labeled yoshimi to the one labeled oxygen 61 in patchage.

---

### Post by maghoxfr on 2010-05-10
it doesn't let me to hook them up, here's a screenshot of my patchage.

---

### Post by cchhrriiss121212 on 2010-05-11
Change the midi driver to alsa in yoshimi settings.

---

### Post by maghoxfr on 2010-05-11
I hate to be asking this but I can't find any documentation on Yoshimi. How do I change to midi alsa on yoshimi's settings? I see a box next to it but it's not a deployable menu so, do I have to type? Here's a picture of the settings right now.

---

### Post by maghoxfr on 2010-05-11
DONE!!! This is what I did: 

In the jack connections windows under the _ALSA tab_ I connected the OUT of my midi keyboard to the IN of the Midi through, then, under the _MIDI tab_ I connected the OUT of the system (MIDI capture 1) to the IN of Yoshimi, and finally under the _Audio tab_ I connected the OUT of Yoshimi to the system playback.

---

### Post by tripomatic on 2010-05-24
Where is the midi through coming from? :)

I have a midisport midi device, but i don't have anything like midi through in my alsa tab. 

I suppose it's a software thing the midi through but i never so it before.

---

### Post by tripomatic on 2010-05-24
nvm. It's a kernel module that's was missing.
Recompiling right now :).

---

