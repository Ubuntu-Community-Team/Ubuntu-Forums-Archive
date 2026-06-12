---
title: "Kazam in Ubuntu Studio doesn't record sound"
date: 2021-06-18
forum: Multimedia Software
---

### Post by henrodon on 2021-06-18
I have Kazam 1.4.5 installed in Ubuntu Studio 20.04. It records video but not sound. (From Brave browser) I'm not at all knowledgeable about sound settings, and don't want to change anything that will interfere with using Musescore to write music. Can somebody either show me an easy way to fix this, or explain what setting I need to change and then how to change it back after I record what I want?

---

### Post by monkeybrain20122 on 2021-06-21
Check out the first answer. [https://askubuntu.com/questions/1237571/kazam-no-sound-and-no-rectangular-red-border-during-screencast-in-ubuntu-20-04](https://askubuntu.com/questions/1237571/kazam-no-sound-and-no-rectangular-red-border-during-screencast-in-ubuntu-20-04)

I have managed to get it to work on kubuntu 20.04  but I forgot how and can't find my notes. Will get back later if the link doesn't work for you.

---

### Post by henrodon on 2021-06-21
Thanks for the suggestion. Unfortunately, the explanations there are well beyond my level of understanding. The few times recently I've needed to record something from the screen, I've switched to my other computer (Ubuntu Mate) where Kazam works fine. I hoped to get it working on this machine as well since this is the one I normally use. (The other sits in the bedroom, and is basically only used to watch YouTube and similar.)

---

### Post by monkeybrain20122 on 2021-06-22
Ok, just to be sure you are having the same problem as from the link, can you start kazam from the terminal and post the output?

---

### Post by monkeybrain20122 on 2021-10-29
So for someone who encounter this problem here is the best solution: kazam has not been maintained by the original developer for years so the repo's version suffers from various problems and the version is 1.4.x which is lacking in features. But I just found a branch which is actively maintained and with new features (latest commit was 23 days ago) [https://github.com/niknah/kazam](https://github.com/niknah/kazam)

No installation needed, just clone the git repo or download the zip file from master and run it out of its folder following the instruction from the webpage (basically cd kazam/bin && ./run_local_dev.sh, the .sh file of course has to be made executable) Tested in Ubuntu 20.04 and 21.04, works out of the box. Wayland not supported.

---

