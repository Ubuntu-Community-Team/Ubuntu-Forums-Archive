---
title: "How to speed up mp3 files?"
date: 2013-02-13
forum: Multimedia Software
---

### Post by Jestry on 2013-02-13
> **goodrench said:**
> ```
sudo apt-get install libsox-fmt-all
```That did it. I should have looked harder.
Thanks ad_267.

I used sox in a nautilus-script to speed up podcasts that I listen to. Some of them are just too long.

If anyone wants to use it, here is the script.
Just drop it into ~/.gnome2/nautilus-scripts/ and chmod +x to make it executable.

Just alter the settings as you need to.

```
#! /bin/bash

# this script will speed up audio using sox.
# speed up is 1.5  and pitch is lowered by -700 to try to keep the original voice
# This will keep the original and put the new one in a new folder called audio

# Check for and create audio directory if necessary

if test ! -d audio
      then
      mkdir audio
fi
input=$1
terminator -e "sox --show-progress ${input} audio/${input} speed 1.5 pitch -700"


```

I know this is a really old thread, but I'm also trying to speed up podcasts on ubuntu, and was wondering if anyone could help me out.

I don't really understand command line that well, but Audacity is taking a ridiculously long time to convert my file, so I figured I should try something else.

So far I've:
1. Copied the above code in geddit and saved it as "speedup". 
2. Copied file into ~/.gnome2/nautilus-scripts/ 

Say I have a file called "Lecture 7" on my desktop. What exactly do I type in terminal to make the script execute on the file?

What does "x" mean in "chmod +x"?

---

### Post by oldos2er on 2013-02-13
Post moved to its own thread.

---

### Post by tgalati4 on 2013-02-13
Open a terminal:

```
cd
cd Music
mplayer --speed 2 fileyouwanttospeedup.mp3
```

You can use values from 0.1 to 100.

The "x" means executable privilege.  The chmod +x command adds executable privilege to the script in this case, so you can run it from the command line.  By default, new scripts are not executable--to prevent self-inflicted damage, and reduce virus propagation.  So you have to take a manual step to add executable privilege.

The audacity method will speed up and preserve pitch.  Other methods with only speed up, and you will get higher (and annoying) pitch, with can hinder intelligibility.

---

