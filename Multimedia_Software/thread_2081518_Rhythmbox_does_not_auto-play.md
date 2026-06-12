---
title: "Rhythmbox does not auto-play"
date: 2012-11-07
forum: Multimedia Software
---

### Post by ebekkema on 2012-11-07
Hi there,

For whatever reason I cannot manage it to get Rhythmbox automatic start to play. 

[LIST]
[*] Tried the startup-script option ([link]("http://greeennotebook.com/2010/06/rhythmbox-startup-script-for-ubuntu/")). But without the playlist. 
[*] Tried to startup with "/usr/bin/rhythmbox --play"
[*] Tried to start Rhythmbox with --play-pause commandline option"
[/LIST]

In all cases Rhythmbox does start, but does not play automatically.
There are songs in the list and when I press the play-button it starts playing.

What could be the problem??? 

Hopefully someone has the solution :) Thanks.

---

### Post by davidmohammed on 2012-11-08
The best plugin I've found for this is called *RememberTheRhythm*

You just activate it - when you close rhythmbox and restart it, it continues from what was last playing.

You can find the plugin from [GitHub]("https://github.com/owais/remember-the-rhythm")

I've also packaged this in my PPA - instructions on [Ask Ubuntu]("http://askubuntu.com/questions/147942/how-do-i-install-third-party-rhythmbox-plugins").

---

### Post by lymanlai on 2013-04-17
actually the command should be:  rhythmbox-client --play
I just do it like this ;)

---

