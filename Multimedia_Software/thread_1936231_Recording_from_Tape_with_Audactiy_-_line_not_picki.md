---
title: "Recording from Tape with Audactiy - line not picking up?"
date: 2012-03-05
forum: Multimedia Software
---

### Post by ChrisNZ on 2012-03-05
I'm running Ubu 11.10, and Audacity (current version from Synap's) I have not been able to get the line in to pickup for recording in Audacity.
I have the output of a tape deck plugged into the 'Line in' jack on the back PC, tried the front but same result. I could get the 'Mic' to record just not the 'Line in'.

I have spent hours with 'Input Device' options and 'Output Device' yet not seem to get the right combination as simply a case of selecting "Line" for recording.

I have made sure the 'Additional Drivers' are loaded, I loaded 'Alsamixer' and tried a combo of setting changes there and the basic 'Sound Options' menu. Still nothing - Only getting the 'Mic'to pickup on one setting.

Can you help?

---

### Post by ajgreeny on 2012-03-05
Run alsamixer in terminal and check that the levels of outputs are not set too low or muted.
Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
In capture page use spacebar to enable the different input devices (mic, line, CD, video).
Esc will save and exit.

If you have already tried that without success open **pulseaudio volume control** and try changing the settings in that from **Internal audio analogue stereo** to **Monitor Internal audio analogue stereo**, assuming that is the choice available to you.  You will have to have audacity running and recording for that option to appear, I think.

---

### Post by cortman on 2012-03-05
If you just run your cable from the mic out on the stereo you could record mic in Audacity with full quality.

---

### Post by oga on 2012-05-23
I'm also having trouble getting "line in" to work to record via Audacity. Did you eventually get it working?

---

### Post by shantiq on 2012-05-23
ran into same a year ago; worked it out on my system   and wrote[**this**]("http://ubuntuforums.org/showthread.php?t=1705651")  might be of use

---

### Post by shantiq on 2012-05-23
----------------------------duplicate -----------------

---

