---
title: "Play plotted sine curve as sound"
date: 2009-09-02
forum: Multimedia Software
---

### Post by qrwe on 2009-09-02
Hi,

This topic was a little hard to categorize, by I decided finally to put it into multimedia. It's a matter of playing sound after all. OK, here we go:
Is it possible somehow to play a plotted sine curve (created by e.g. octave) as an output sound? PC speaker or computer louders doesn't matter.
Thanks!

PS. A friend told me that on Solaris machines/operating systems, there was a possibility to pipe (or loop) a given frequency directly to /dev/sound, which instantly triggered the PC speaker to ring. "Funny when a new workmate visited in the server hall" he added smirkingly :-)

---

### Post by Nepherte on 2009-09-02
I know for sure that it works in Matlab Simulink, an expensive alternative for octave. You just have to sample your sine wave at a certain frequency, generating discrete values and put it in a matrix. Accompagning your *data* matrix, you need the corresponding time values in another matrix. You input both matrices in a Simulink model and you're done.

I'm not sure if octave can do it to, but since it is pretty similar to matlab, you have a shot.

---

### Post by jpkotta on 2009-09-10
```
sudo apt-get install octave-audio
```
You might need the sox package too.

```

t = linspace(0,1,2^13); % 1 second at default sampling rate
x = 0.5*sin(2*pi*440*t); % 440 Hz sine wave
sound(x) % play the sound

```

---

### Post by qrwe on 2009-09-11
That octave solution was exactly what I was looking for. Truly cool, thanks a lot!

---

