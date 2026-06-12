---
title: "Control Center &gt; sound"
date: 2011-03-30
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Billxyzzy on 2011-03-30
Good day I have a problem with control center > sound.
When I attempt to set a selection for Internal audio
I have a problem setting the mic level.
Sequence to follow in set up
Select > hardware
    Internal Audio
    1 Output / 1 input
    Analog Stereo Duplex

Select > input
    Input volume slider for mic
    Move to right to set level
The problem: as soon as I have set the level it
returns to the left (minimum)
At one time there was a setting box for overriding
the automatic sound level setting for the mic.
This check box now no longer exists so I can't
set a specific level.
Has anyone else seen this problem?
How do I specify a bug?  What package does this
fall under to use ubuntu-bug?
While this might be seen as a small problem,
If you are doing sound work it is a major problem.
Any ideas or suggestions?

---

### Post by cariboo on 2011-03-30
Have you tried using alsamixer to set the volume levels you need. Open a terminal and type:

```
alsamixer
```

use the arrow keys to navigate and set the levels. Once you have set everything to your liking, press esc to close the program, then in the same terminal type:

```
sudo alsactl store
``` 

to save the settings

---

### Post by Billxyzzy on 2011-03-31
This problem is getting more interesting.
I tried alsamixer to adjust mic levels.
They are reset properly and 
issued sudo alsactl store so assume that was ok
Going back to the sound selection and
selecting input for mic the slider sets a level
then the level drops to near zero again.
Recording a test message demonstrates the dropoff of the
mic level.
Seems to be no connect between alsamixer and the sound
subsystem.

---

