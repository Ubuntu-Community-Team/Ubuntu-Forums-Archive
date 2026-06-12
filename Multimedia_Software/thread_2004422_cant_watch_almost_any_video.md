---
title: "cant watch almost any video"
date: 2012-06-15
forum: Multimedia Software
---

### Post by gabrielaca on 2012-06-15
im on ubuntu 12.04 64b

i just found out jon severinsson ppa for ffmpeg on webupd8 and think i was ok to give it a go, wrong, i compleatly disrrupted my playability, now i cant watch any video i just get the audio; everytime i open a video file a warning pops up, "install multimedia plugins?" i click on install and get a "package dependencies can not be resolved" and dont know how to unistall or if its safe to, this ppa or im i going to get in worse trouble by unistalling? anyway here are two screenees, hope anyone can help.:)

---

### Post by jocefus on 2012-06-15
Use ppa purge to remove the ppa and reinstall official packages.
 
First install it:
```
 
sudo apt-get install ppa-purge

```
Then run:
```

sudo ppa-purge ppa:someppa/ppa

```

More info on adding and removing a ppa:
[http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html](http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html)

---

### Post by gabrielaca on 2012-06-16
thanks josefus, i had to run twice all the comands in order for them to work corrctly, but they did, it worked, by removing the offending ppa and then replacing the dependencies with the ones on the repos, thank you very much, i had allready tried to remove it via synaptic but fail, thank you again, :guitar:i can see clear now the rain is gone, its gonna be a brigth, brigth,  sunshiny day :lolflag:

---

