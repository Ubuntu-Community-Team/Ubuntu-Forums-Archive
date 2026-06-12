---
title: "amsynth does not open in ubuntu studio"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by mdl76 on 2007-05-25
I click on the amsynth in the application menu and nothing happens.  Ive uninstalled and reinstalled yet it fails to open.  anyone else see this.

PS im new to linux and this studio ed of ubuntu ROCKS!!!  Ill never go back to windows.

---

### Post by tgoose on 2007-05-25
Go to the Terminal and type in
```
amsynth -d
``` and hit enter (-d is short for debug). It should come up with error messages. If you copy and paste those into here then it should be easier to find the problem. The error message might even be human-readable enough for you to fix it yourself.

Running any Ubuntu software in the command line like that gives it a place to show error messages (not necessarily with the -d switch)

---

### Post by mdl76 on 2007-05-25
Thanks for the help Sir!

After I type in amsynth -d and after the disclaimer I get:

*** CONFIGURATION:
MIDI:- driver:auto channel:0
AUDIO:- driver:jack sample rate:44100



***INITIALISING AUDIO ENGINE...
cannot load JACK libarary

**failed to initialise JACK... aborting : ' ( **


Im getting this error with JACK running.  All of my other apps seem ok though.
Thanks agian.

---

### Post by tgoose on 2007-05-27
I'm afraid I can't get it to run with JACK either! 
To at least get sound, you can run
```
amsynth -a alsa
```
while JACK is **not** running, and then in the future just clicking amsynth in the menu will work, but not while JACK is running (for me, either.) I don't know what to do about this other to complain to the Ubuntu Studio or amsynth developers...

---

### Post by skipkent on 2007-07-10
I'm getting this too.  Why is amsynth not working with Jack?

It's probably because it's looking for 'jacklib-00234.so.conf' whereas it should be looking for jacklib-33430-3409834-so.conf or somthing like that, but unfortunately the debug output doesn't give us a clue.

Can anyone support us on this?  

A large of the packages in Ubuntu Studio fail to run.  What's the point?  All UStudio really seems to be is a realtime kernel and some nifty themes.   A slush-pile of misconfigured apps is something I could have done myself.

I was hoping for something a little more structured and restrained, like Studio-to-Go.  Oh well.  Gift horse and all that...  ; )

---

### Post by skipkent on 2007-07-10
Okay, I figured this one out, thanks to a post elsewhere dealing with Jack.  Apparently a newer/older version of jack changed/deleted a filename.  We just need to create a link:

$ sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so
$ sudo ldconfig
$ amsynth 

amsynth / jack happiness will ensue.

Happy amSynthing!

-skent

---

### Post by tgoose on 2007-07-10
Excellent! Thanks for that!

---

### Post by maximilians on 2007-07-11
cheers skipkent !

---

