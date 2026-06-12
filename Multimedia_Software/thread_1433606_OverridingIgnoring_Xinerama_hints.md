---
title: "Overriding/Ignoring Xinerama hints"
date: 2010-03-19
forum: Multimedia Software
---

### Post by alt146 on 2010-03-19
I'm running Ubuntu 9.10 with a PNY nvs450 and four monitors.  I need to have an application run 'fullscreen' across all four heads.

Getting the screens working was simple, using the linux drivers that came with the card and the nvidia-settings program, but I can't get a program to automatically open across all four screens.

I understand that the desired behaviour on multihead displays is to maximise to only a single screen and both xinerama and twinview provide information to X regarding the nature of the connected screens.  I'm looking to override this behaviour so that X only sees a single screen.

I've tried to manually set the size of the program using a command-line argument, similar to --geometry, but the program just maximizes to the active screen if the argument given has a width greater than a single screen.

The closest I've gotten to the desired configuration was by setting up two twinview displays with the NoTwinViewXineramaInfo option and joining them using Xinerama, but this only allows maximization across two screens.

There are several ways I can think of solving the problem, but I'm not sure how to actually implement any of them.

The first would be to somehow force the Nvidia drivers to Twinview across all four screens.  Given that it's called Twinview and the there are two GPUs in the card, I doubt this is possible.

Another option would be to somehow force Xinerama to tell X there is only a single monitor with the resolution of four screens.  I've tried setting this using TwinViewXineramaInfoOverride, but have been unsuccessful.  I can't find any documentation regarding this option, examples where it's used to merge screens rather than partition them, or examples on how to use it with multi-GPU cards.

The other option would be to tell X to ignore Xinerama, but I can't find any information on how to go about doing this.  Maybe changing my window manager to something that doesn't support Xinerama would work, but I gather that most windows managers have had xinerama support for several years now.

Would any of the above be possible?  Most of the suggestions I've seen for similar problems involve buying Dual- or Triple-Head2Go cards from Matrox, but this isn't really an option.  This is a bit of a pet project of mine at work and my boss isn't going to order more specialised hardware unless I can prove it will definitely work.

---

### Post by markbuntu on 2010-03-19
For multiple gpus xinerama is your only option until later this year when the new randr will be available which has support for multiple gpus. You probably need to hand edit xorg.conf to place the monitors in the proper relative positions and set the virtual screen to the size necessary. There is probably some more to this and there are a few threads around here about doing this with nvidia cards. 

I have not tried this myself but good luck and let us know how you make out.

---

### Post by alt146 on 2010-03-20
Thanks, but that's not really my problem.  Getting the monitors placed and setting their resolutions took all of 5 minutes :D

My problem is that if I'm running all the screens 1024x768 and run something like

gnome-terminal --geometry 4096x768+0+0

the terminal snaps to fullscreen in the active window.  I can drag the terminal to that size, but I need it to happen automatically.  Ideally I'd like the application to resize to 4096x768 when the maximise button is clicked, but worst case I can manually set the size and remove the windows decorations with compiz to emulate fullscreen behaviour.

I've read through all the threads about xinerama and multiple screen issues I could find on this forum and a couple of others, most of them deal with stopping the behaviour I am trying to acheive.

---

### Post by alt146 on 2012-04-25
If anyone happens to stumble across this post looking for a solution to a problem that is similar to mine, I eventually managed to implement a solution using [http://home.kde.org/~seli/fakexinerama/](http://home.kde.org/~seli/fakexinerama/).  The package basically lets you override the parameters that Xinerama sends to X by manual configuring screen information in a text file.

---

### Post by zbuffered on 2012-04-26
Thank you so much alt146, you may have saved my sanity!  I needed the exact same thing as you.

---

