---
title: "Problem having simultaneous audio from two sources"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by virgiltibbs on 2007-07-02
Hi,
im having some trouble with my Kubuntu Feisty install.
More specifically, i think xine, but i will leave you to make your own mind up,
the symptoms are totally repeatable, are as follows...
[INDENT]I cannont play audio from several sources at once, ie, i cannot play music in amorok, a movie in kaffine, and get notifications from pidgin at the same time.
Sorry, actually that is not Quiteee true, the example where stated above does seem to work, 9well pidgin doesnt do its notifications but the other two consectutivly play music/video
in fact only one of these will make noise, the others will remian silent and refuse to make any noise
I'm using ALSA and the latest version of xine in the feisy repositories.
when i run the official last.fm linux client in command line (it doesnt like working) it closes with the error:
> RtApi: no devices found for given stream parameters:
    RtApiAlsa: pcm device (hw:SI7012,0) won't open: Device or resource busy.
    RtApiAlsa: pcm device (hw:SI7012,1) won't open: No such file or directory.


[/INDENT]SI7012 is of course the name of my onboard sound card. previously, i have had everything fine so it should be possible...
i am willing to do loads of diagnostic stuff... if you could point me in the right direction that would be great...
cheers
Tim

p.s.
i have tied reinstalling xine & amorok &last.fm client but this isnt windows so it is all the same with no before, after change...

---

### Post by virgiltibbs on 2007-07-15
when i try to run LiVES while amarok is running i get this:
> JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns

a problem with my audio driver... or JACK?

---

