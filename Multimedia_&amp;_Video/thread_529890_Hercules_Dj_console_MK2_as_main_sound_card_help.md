---
title: "Hercules Dj console MK2 as main sound card help?"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by soapytheclown on 2007-08-19
Hello all,
i recently got myself a hercules dj console which is super fun to use in windows but im having some problems getting to work in ubuntu (im hoping to get going with an svn version of mixxx 1.6.0 or if its possible at all to get going with a wine-d virtual dj)

okay firstly my setup is rather different i assume to most people that would use the hercules dj mixer, i have the hercules plugged up to my pc and wired to it i have an external mixer, which has my speakers plugged into it:

PC--->Hercules DJ Console MK2----> External Numark Mixer--->Speakers

The console itself acts as my external soundcard in windows and since ive had no problem with external sound cards before i wouldnt think it would be a problem in Ubuntu, but alsa doesnt pick it up like any other external usb sound card, all sound preferences seem to think that theres no sound card available to control. 
however when i run:

nash@Dragon:~/mixxx$ asoundconf list
Names of available sound cards:
Mk2

and sound does actually play (oddly)

which kind of confuses me.... however since im using the external mixer i can control volume using the faders there not really an ideal fix by anymeans

then i have my 2nd problem:-

The console itself has 4 outpt points;1,2,3 and 4:- 1 and 2 represent channel 1 left and right 
                                                                              :- 3 and 4 represent channel 2 left and right


In the current config only points 2&3 seem to work at all during sound play. 2 for my right speaker and 3 for my left speaker. 

does anyone have any clue to make the 1&4 points work on this? 

i have a feeling that if anyone can help me to get the sound options to pick this up then i might be able to get the other 2 points to work.

and finally, ive been having so much trouble getting software to work correctly with this, ive used virtual dj in wine but the sound glittches and slowness in general make it a pain to use. and Mixxx SVNis a complete resource hog infact just before writing this it bought my system to an unuseable state :(

ive searched high and low for over a month now and had little luck i hope one of u guys can help!!

---

### Post by surfed on 2008-02-25
bump

---

### Post by nemofbaltimore on 2008-03-21
well dude, i saw alot of other post's about this issue, no real result...
im working off a similar timecode cd setup
but with the pionner djm-800 instead

im guessing you got a dm-950 for numark with axis 4's

i currently use them and refuse to spend more money on equipment for music at the moment

i got two st-150' from stanton on the phono on the mixer with the hercules mk2 on the line jack's

i already know you know enough about the rest as we share same setup

well....

i bump this post and offer friendship to share ideas

visit [http://www.myspace.com/nemlive](http://www.myspace.com/nemlive) to contact
catch the mix's at [http://radio.djpnuemo.com/weekly.html](http://radio.djpnuemo.com/weekly.html)

best of luck and looking forward to some reply's

chao buddy

:-(

---

### Post by nemofbaltimore on 2008-03-21
bump

---

### Post by Toet on 2008-04-12
I have a normal Hercules DJ Console (not mark anything) and it works under Ubuntu after adjusting the alsabase-file. Added usb-snd-audio as first sound card and commented out the usb lines at the bottom of the file.

Can't show you the edits I made exactly, cause I'm running Debian now, and it works out of the box.

I have working: midi, all output lines, and it's joystick as well ;)

---

