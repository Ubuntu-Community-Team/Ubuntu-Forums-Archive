---
title: "Can not stop Jack qjackctl"
date: 2018-07-07
forum: Multimedia Software
---

### Post by kazakore on 2018-07-07
Ubuntu studio 18.04 x64.

Some recent update seems to have made it impossible to stop Jack from qjackctl. This was working perfectly a week or two ago, and all the way back to when I started on Ubuntu with 14.04 before that! Click to stop the audio server and it just hangs! This make it very hard to switch between my internal sound card and my external audio interface!!!

I've had to change the Preference to not start the Jack Server at application start (which is likely to catch me out a lot as I always run through Jack!!)
Then killall qjackctl
kill -9 the jackdbus PID
Restart qjackctl, select the saved config, start server manually.

I should be able to just Stop the server, change saves config, Start the Jack server!

Anybody else having issues? How can we get this working again?

---

### Post by kazakore on 2018-07-07
EDIT: The below is FALSE. It worked about 5 times in a row during testing then stopped working when opened from CLI as well!! :(



[I]Hmmmmm.

Just thought I'd run it from the terminal to see if I get any useful output there and when run from the commandline it works perfectly! Quit, reopened normally, fault returns, try again from opening from terminal and it's fine, repeatable again and again.

How and why could this make any difference?

I have this as one of my StartUp Programs (in XFCE) and as a workaround guess I could edit how this starts the program. Can somebody please remind me how you get an application to start from a (invisible) bash shell, rather than opening normally. Then I will see if this at least fixes it for me.....[/I]

---

### Post by kazakore on 2018-07-07
If I disable D-Bus Interface and Jack D-Bus Interface in the Misc Preferences I *seem* to be able to stop and start the server. But it's clearly still not working right! I can't actually change saved config without quitting and re-opening qjackctl. Even then it will something try and start the jack server automatically even though the Preference setting is set to not do so. Ontop of that no matter if I have dbus enabledI **always** get "/usr/bin/jackdbus auto" listed if i ps ax to see what is actually running. Plus even when it claims it's stopped I still have audio going through it if I leave an application playing!


Has somebody broken Jackd in Ubuntu?


Is it strange that I seem to have both jackd and jackd2 installed and to attempt to remove either wants to remove different selections of packages? Althoughthis can't be the issue as this side of things hasn't changed in the last two weeks and this working as it should do has!

---

### Post by kazakore on 2018-07-07
jack from terminal worked, as did using Cadence. Thus I deleted the config file and it seemed to work, but without my saved settings. Hence I'm sure enough it's a config issues, maybe something I had not compatible with the latest update in the shutdown scripts, so going to work from a blank slate and mark this as Solved.

---

