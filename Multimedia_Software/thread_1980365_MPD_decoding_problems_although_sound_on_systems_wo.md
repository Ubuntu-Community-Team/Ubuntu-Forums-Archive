---
title: "MPD decoding problems although sound on systems works perfectly"
date: 2012-05-15
forum: Multimedia Software
---

### Post by maqNR1 on 2012-05-15
Hello everyone,

I'm using Linux since about 10 years, switched to Ubuntu about 5 years ago. So I'm not a total noob although feeling like one at the moment. I've been running mpd successfully on different systems. But this time I'm out of ideas...

I'm trying to get mpd to run on my PC (Ubuntu 12.04, also tried Linux Mint LMDE). On both systems the sound works perfectly when playing a mp3 in e.g. rhythmbox. On both systems I installed mpd from the repositories. I've run mpd as user "mpd" as well as user "myUser". Mpd successfully creates its database. I can connect from another PC via GMPC to mpd and browse my collection.
But as soon as I try to play a song I only get the message "MPD reported the following error: problems decoding XYZ.mp3".

The log level has been set to verbose, but (from my understanding) no meaningful logs can be seen. All files and directories related to mpd are "rw" for everyone.

I spent the last three evenings googling through help pages and forums, but unfortunately I have not found the solution.

One big question is: Does the error message might be related to a wrong setup of my audio devices or is the decoding of the files completely independent from the audio setup?

What might be the best strategy to track down the error? If additional information about my system setup is required I'm happy to provide it.

Some help is very much appreciated!

---

### Post by Yellow Pasque on 2012-05-15
Do you have libavcodec-extra-53 installed?

---

