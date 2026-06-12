---
title: "sound-recorder takes 9 seconds to return"
date: 2008-10-12
forum: Multimedia Software
---

### Post by Mariane on 2008-10-12
Hi everybody, 

I need to record multiple sound files (samples) and I am thinking of using sound-recorder. I tried audacity, which didn't install properly (told me my screen had not enough columns or something) and krec (which does not seem to have a timing option, or then it's not documented in the --help or man). 

sound-recorder -k -S 00:03 try 

Works fine, but though the -S 00:03 limits the file length to 3 seconds it doesn't actually return until 9 seconds later (so this is 12 seconds in all). It says "press control C" to stop, but even that doesn't stop it immediately, and I don't know how to script a "control C" command. I tried typing "exit" instead of "control C" but this doesn't work either. 

I wouldn't mind waiting one second between samples, but 9 seconds is a nuisance. Plus if my program sends another command to the terminal before sound-recorder has finished it may get eaten. When I type a new command it gets eaten. 

Please help, either by suggesting another program which would do the trick, or by telling me how I can force it to exit when it's supposed to exit. 

Mariane

---

