---
title: "JACK not showing up in applications (and not working in general)"
date: 2008-05-17
forum: Multimedia Software
---

### Post by omnibot on 2008-05-17
So I installed Ardour for audio production but I get an error message when opening a file saying that JACK could not start due:

> There are several possible reasons:

1) You requested audio parameters that are not supported..
2) JACK is running as another user.

Please consider the possibilities, and perhaps try different parameters.

when i tried to do some research to fix the problem i came across this page

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

and the first step is to open JACK from the applications menu, which isn't in my applications menu

what am i doing wrong? :confused:

---

### Post by alexforcefive on 2008-05-18
The easiest way to get jack working is to install qjackctl from the repositories. It's a GUI frontend for the jack server. It'll show up in your "sound and video" menu as "JACK control"

---

### Post by omnibot on 2008-05-19
oh, ok. great. so i downloaded that and got the GUI. 

However, Jack itself is still not working. this is the error message i got

09:01:42.583 Post-shutdown script terminated with exit status=256.
09:01:44.276 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by Stochastic on 2008-05-19
When starting JACK, make sure any other audio app (including firefox) has been closed.  If that doesn't fix the problem post a screenshot of your settings window in qjackctl.

Also, you may want to post issues with Ardour to the Multimedia Production section of the forums, quite a few more pro-audio guys hang out there.

---

### Post by omnibot on 2008-05-19
oh ok, i didn't understand that FF was getting in the way. 

so now ardour and JACK are running, but when i import a .wav file i'm getting really bad playback like there's a buffer problem. 

I've been playing with different settings but the stuttured playback is not affected. 

Thanks, Stochastic..I'll post another thread in production forum :)

---

### Post by Stochastic on 2008-05-20
yuppers, I'm pretty sure it's the flash plugin (possibly some other plugin) in FF that likes to hold onto the audio stream once it has it.

---

