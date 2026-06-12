---
title: "i have problems please help"
date: 2011-04-06
forum: Multimedia Software
---

### Post by chevyd6687 on 2011-04-06
i am new to ubuntu. i just installed ubuntu studio 10.04. i cant seem to run any of the programs for recording music. my computer tells me it cannot connect to jack server. i used to use pro tools on windows but now i have an older laptop that had alot of viruses and i cleared it out to put ubuntu on it. i gues what i am trying to say is i cant do all the things with the terminal that most can. i looked through the forums for answers and probably did find an answer but i came up with no results. can somebody please help me at least get started then i can figure the rest out. Thanks

---

### Post by Joe of loath on 2011-04-06
You need to start jack.

Look in the audio production menu for jackctl, and you should simply be able to click start, then start doing stuff with audio apps and patchage.

---

### Post by chevyd6687 on 2011-04-06
thanks for your help. but unfortunately it wasnt enough. first i couldnt find jackctl. but i did find jack control. i assume it is the same thing. i open it and hit the start button. then a message screen come up with this:

p, li { white-space: pre-wrap; } [COLOR=#999999]13:37:05.966 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]13:37:06.140 Statistics reset.[/COLOR]
 [COLOR=#66CC99]13:37:06.163 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]13:37:06.397 ALSA connection change.[/COLOR]
 [COLOR=#999999]13:37:12.273 Startup script...[/COLOR]
 [COLOR=#990099]13:37:12.274 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]13:37:12.677 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]13:37:12.678 JACK is starting...[/COLOR]
 [COLOR=#990099]13:37:12.678 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]13:37:12.687 JACK was started with PID=2010.[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 [COLOR=#999999]13:37:12.705 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]13:37:12.706 Post-shutdown script...[/COLOR]
 [COLOR=#990099]13:37:12.707 killall jackd[/COLOR]
 Your system has an audio group, but you are not a member of it.
 Please add yourself to the audio group by executing (as root):
   usermod -a -G audio (null)
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 jackd: no process found
 [COLOR=#999999]13:37:13.140 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]13:37:14.825 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

[COLOR=#FF0000][/COLOR]
[COLOR=#FF0000][COLOR=Black]it somewhat looks like spanish to me but if you could walk me through what to do next i would greatly appreciate it. [/COLOR]
[/COLOR]

---

### Post by Joe of loath on 2011-04-06
```
Please add yourself to the audio group by executing (as root):
usermod -a -G audio (null)

```

Looks like you need to run

```
sudo usermod -a -G audio
```

If that doesn't work, check you're booting into a realtime (RT) kernel. If not, disable realtime mode in the jack preferences.

---

### Post by chevyd6687 on 2011-04-06
thanks that worked. now all i need to do is play around with it. i got alot of new programs to get used to lol.

---

### Post by Joe of loath on 2011-04-06
Yup, it's pretty tricky to use, but you can get some awesome sounds. Not found anything better for live recording!

---

