---
title: "Audacity won't record more than 1 track"
date: 2007-06-19
forum: Multimedia Production
---

### Post by waylow on 2007-06-19
I am trying to record some character voices with my logitech headset.
Audacity lets me record one track fine, it records, I can play it back I can edit it
but if I try to record another track - it says error while trying to open sound device - check that the sample rate and project rate are the same 
yes they are the same

why can't I record more than one track
I really don't want to have to record it in Windows

any one had this problem?

---

### Post by stoodleysnow on 2007-06-19
I have a naff old Dell laptop (Latitude D800) with pentium M 1.4 Ghz and 256MB RAM, it runs Audacity through Ubuntu 7.04 without trouble. If in doubt, try reinstalling the debs/apts/whatevers:)

---

### Post by waylow on 2007-06-19
I have just tried to re-install and still have the same problem

I have also tried to download and install the beta version (the one I use on windows) but I have got stuck with the installation - I can never manage to successfully install from a tar-ball

---

### Post by waylow on 2007-06-20
I couldn't compile the beta version 

but I did managed to the the latest stable version working (the one that comes with Ubuntu studio)

I have to make sure that there is no other programs using the sound card - and had to create a sybolic link to dsp1 according to the "linux issues" page on hte audacity wiki

---

### Post by dabl on 2007-06-21
I use Audacity for recording, and I can confirm that it has a number of "annoyances", including the fact that if Firefox is opened first, then apparently Audacity can't find the sound output device any more, although it can continue recording.  Another annoyance is how it keeps the project name of the last project closed, and if you record a new track, you had better remember to "save as" and change the name, and not "save", because it will overwrite the first project with no warning.

But, I get good results with Audacity when I follow its rules.  :)

---

### Post by Keisad on 2007-06-21
I have a solution to your problem.

Audacity will record more than one track. To do this, go to edit>preferences and make sure "play other tracks while recording a new one is unselected. Than you may record more than one track.

However, the audacity your using relies on OSS drivers to do things. OSS will not allow you to record a track while playing another one.

The beginning of your journey starts here:

[http://www.ubustu.com/globe/2007/04/21/compile-audacity-132-beta-with-feisty/](http://www.ubustu.com/globe/2007/04/21/compile-audacity-132-beta-with-feisty/)

and

[http://audacityteam.org/wiki/index.php?title=Audacity_1.3_beta_testing](http://audacityteam.org/wiki/index.php?title=Audacity_1.3_beta_testing)

Summary:

First, download the beta source for audacity.
Than (through synaptic) doiwnload the required packages as explained in the second link (under the header portaudio version 9)
Follow the compiling instructions in the first link. If your still having trouble compiling, then use these commands:
```
./configure --with-portaudio=v19 --without-portmixer --program-suffix=beta && make
```

followed by

```
sudo make install
```

This is the process I went through. If you get this far, post your progress and I shall give you the last steps, if they are needed.

If you do get it working, than execute the program by using

```
audacitybeta
```

in the command line. You must access it this way.

---

### Post by waylow on 2007-06-21
thanks Dabl,

I didn't notice that on the linux version (I ended up recording what I needed in the windows version - then I went back and got it working in Ubuntu)

Hey Keisad - i will give that a go on the weekend :)

thanks all

---

### Post by waylow on 2007-06-22
i just built the beta version

and it works - which is great because I recorded the voices I need in the windows beta version
and then I couldn't load them in the Linux version I had
didn't want to re-record in linux to do some small edits
now all is good

thanks heaps:D:D

---

### Post by Keisad on 2007-06-22
This is why I love linux. It takes some work, but you aren't force fed by Microsoft lackies anymore. It's a learning process :D

BTW

Irony = spellchecker tries to correct "linux"

---

### Post by stoodleysnow on 2007-06-26
I just installed it from the audacity website, directly. Haven't had any trouble with it yet.
To keisad: I agree. Yes it's more challenging for some of us, but the freedom's great.
Just one more thing to get right: PCs and laptops need to be sold for BOTH OS types, not just M$!:mad:

---

### Post by Keisad on 2007-06-26
But Microsoft couldn't do that! 

It's getting grosser though now... not only do they have the operating system controlled, but now they have infected other things, such as msn messenger. Or should I say, Windows live messenger? They even provide links right through the messenger to keep the masses in an induced state. Sometimes I start picturing them becoming a world superpower. Paranoia!

---

