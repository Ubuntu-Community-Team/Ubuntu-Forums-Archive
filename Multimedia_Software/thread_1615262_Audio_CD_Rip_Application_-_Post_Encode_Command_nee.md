---
title: "Audio CD Rip Application - Post Encode Command needed"
date: 2010-11-06
forum: Multimedia Software
---

### Post by ozzyoli on 2010-11-06
Hi,
     I run the technical department of my local radio station and am stuck.

    Our radio broadcasting software maintains a digital library. Audio files can be added to the digital library using a simple bash command.

    What I need is a CD Ripping tool that can be configured to call a bash command when it has finished ripping a CD.

   ABCDE does this BUT the people who do the CD Ripping do not understand how to use a terminal or command prompt.

   Ideally I need a nice simple GUI ripper such as Sound-Juicer, Grip or RipOff that users will find easy to use. After songs are ripped I need it to call a bash command (rdimport..) with the newly ripped file/folder as a parameter.

  Does anyone have any suggestions.
  I could hack away at the source code for Sound-Juicer or Grip but I don't think that is a very tidy solution.

Many Thanks,
Oli

---

### Post by mc4man on 2010-11-06
If you can set abcde up to do as you wish then just create a simple script and set that as the default (autorun) for Cd Audio - ie. put the disk in and the script runs.
(your 'after rip command' can can set up in abcde or part of script.

Here i have both abcde and rubyripper available as default/autorun choices for CD Audio
The only possible 'hang up' w/ abcde is if there are multiple cddb choices, a -N option takes care of that.

At it's simplest for abcde

#!/bin/bash
gnome-terminal -e "abcde -N"

Edit: technically you wouldn't need a script - using just a custom command (creates an userapp.desktop) would also work but it would run in the background - having the script use a terminal at least allows visual confirmation all is going/went well

If you didn't wish it to autorun but be a pop up choice then just set the pop up as screen 1 (uncheck the always.. box

Initially when set as an autorun choice the name displayed was the name of the script (arip2) - screen 2, easy to change so it reflects what is being used  - screen 3, also changed arip1 to what is uses -  Rubyripper

---

