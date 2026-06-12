---
title: "i guess my sound card is JACKED up??"
date: 2008-04-14
forum: Multimedia Production
---

### Post by mjp216 on 2008-04-14
As you guessed by the pun in my title... im having JACK problems.
i have an Acer laptop (4620z) and i have a Realtek HD Audio card. which comes up as "Realtek ALC268" (OSS Mixer).
I installed Ubuntu Studio on my GNOME desktop (btw, i have hardy) and i cannot start JACK server... i hardly understand this stuff so, help would be greatly  appreciated.

---

### Post by Stochastic on 2008-04-14
Well the first step would be to post a little more information for us to understand your problem.  1) What method are you using to start Jack (command line?, qjackctl?) 2) What's the output of Jack when you attempt to start it? 3) What settings are you using?  4) Does sound work without jack? 5) How did you manage to get a Hardy version of Ubuntu Studio if it hasn't been released (I assume you've installed the Studio Meta Packages ontop of the regular Hardy beta)? 6) If you're running Hardy why are you testing programs you know nothing about? (ok, so now I'm getting off track of the post's issue, but really, it's beta for a reason)

---

### Post by mjp216 on 2008-04-14
well, im using JACK control which came with ubuntu studio, Sound works fine without JACK, ur correct about the meta packages, and i do know all about ubuntu studio, exept i didnt know that some programs require JACK drivers... i used JACK before when i used to run freespire and i never got it to work 100%.... truth is, i hate JACK, and because of the troubles i had with it, i never took the time to learn about it.

---

### Post by mjp216 on 2008-04-14
and one more thing i forgot... i get an error wen trying to connect to the JACK server 
> could not connect to jack server as client
 -overall operation failed
 -unable to connect to server
please check messages window for more info

---

### Post by Stochastic on 2008-04-14
Please post a screenshot of your settings panel in qjackctl.  Also if you could, turn on the verbose messages output in settings, then post the full output of the messages panel.  Jack can be tricky but it's well worth the learning curve.

---

### Post by edm1 on 2008-04-14
I occasionally used to get this trouble till i realised that before starting JACK you must close any application that might want to use the server. In my case it was usually rhythmbox.

---

