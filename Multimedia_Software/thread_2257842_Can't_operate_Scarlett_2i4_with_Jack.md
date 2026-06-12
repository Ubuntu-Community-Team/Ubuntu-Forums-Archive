---
title: "Can't operate Scarlett 2i4 with Jack"
date: 2014-12-23
forum: Multimedia Software
---

### Post by fernando39 on 2014-12-23
[SIZE=4]Hi everyone, how are you?[/SIZE]
Like the title says, First of all I want to say that I want to record things from my guitar, I guess that's important to mention..
I'll explain it step by step what I did:


1st: connected the Focusrite Scarlett 2i4 through USB.
2nd: downloaded the Jackd and QjackCtl to operate it. Then proceed to press "Start"
3rd: I went to "Connections" and in the Audio tab, displays in the Input "System.- Capture 1" and "Capture 2", and in the Output "System.-playback 1" and "playback 2"
(I have no picture of this, cause I installed a package that modifies it. In few steps you'll know why.)

4th: I proceed to open the Guitarix (that I downloaded before the Jackd). This little guy automaticly links itself to Jack.
5th: In the "Connections" from Jack, in the audio tab there are two more options in the input and output: "gx_head_amp" and "gx_head_fx"

I saw some tutorial that explains How to connect Guitarix to Jack to play with effects, etc... here
[http://blog.desdelinux.net/guitarix-excelente-amplificador-de-guitarra-electrica-para-linux/](http://blog.desdelinux.net/guitarix-excelente-amplificador-de-guitarra-electrica-para-linux/)

Is in spanish... 'cause that's my mother tongue.
I will translate a bit from it:

Now, grab the "system" entry from "Output ports" to the "Guitarix_amp" (aka "gx_head_amp") from the "Input ports". Then, in case you want to listen live the sound with effects, connect the entry "system" from "Input ports" to the entry "Guitarix_fx" (aka "gx_head_fx") from the "Output ports". This may be like this:

[IMG]http://lh5.ggpht.com/_F1QjWOihm3Q/TFy-mCpUvnI/AAAAAAAAAqY/Lj-8yBPNaZ0/Conexiones%20-%20JACK%20Audio%20Connection%20Kit_003.jpeg[/IMG]


But when I did this, I realized that the sound that goes in, in system (from Capture 1, and Capture 2), is the internal mic from my notebook.

So, what I learned from this?: Maybe PulseAudio is working with my Focusrite 2i4, and Jack is working with the mic and speakers from my notebook?
I need to disable PulseAudio on anyway?
------------------------------------
Then, investigating in forums and pages, like this one [http://dragly.org/2014/01/12/focusrite-scarlett-2i2-flawlessly-working-on-ubuntu-with-jack/](http://dragly.org/2014/01/12/focusrite-scarlett-2i2-flawlessly-working-on-ubuntu-with-jack/)
I learned that I can install something called "PulseAudio Jack Sink", I did not understand correctly whats the porpouse of it, but I thought this would allow me to detect my Scarlett with Jack...
but it doesn't.. kind of.. I guess?

[IMG]http://s21.postimg.org/6wv985k7r/this.jpg[/IMG]

I dont know how to continue... I'm really lost.. Help me please :(

---

