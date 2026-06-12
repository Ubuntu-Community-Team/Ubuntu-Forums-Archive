---
title: "Microphone doesn't work on Xubuntu 11.04 (Acer Aspire 4920)"
date: 2011-10-01
forum: Multimedia Software
---

### Post by insecure hyena on 2011-10-01
I can't use the microphone of my laptop by using the actual latest distribution of Xubuntu, namely Natty Narwhal (or if you prefer 11.04).

In my previous experience with Ubuntu the only thing that I had to do to get the microphone to work was to increase the recording volume from the alsamixer, but now this doesn't work.

---

### Post by insecure hyena on 2011-10-04
I try to make a Bump...

---

### Post by insecure hyena on 2011-10-06
Sorry I know that's not a good behavior but considering the urgency I'm actually facing I make another BUMP...

P.S: please I really need the Microphone!

---

### Post by Toz on 2011-10-06
Perhaps this link might help: [http://wiki.debian.org/DebianAcerOne#Audio]("http://wiki.debian.org/DebianAcerOne#Audio").

Its a debian link, but it suggests some settings changes to your **/etc/modprobe.d/alsa-base.conf** file. 

Also, that link links to: [http://ubuntuforums.org/showthread.php?t=1313137&page=2]("http://ubuntuforums.org/showthread.php?t=1313137&page=2") ( posts #16 & #18 ) which document a potential solution to the microphone issue on Acer Aspires using **pavucontrol**. There is another thread here that suggests a similar solution: [http://ubuntuforums.org/showpost.php?p=10147128&postcount=28]("http://ubuntuforums.org/showpost.php?p=10147128&postcount=28").

---

### Post by insecure hyena on 2011-10-06
At first thank you infinitely for your intervention!
I tried all the solutions posted to the links that you've reported but none of them seemed to change the situation.
I must said that I'm not an expert on how the audio is handled on linux (and in particular in Xubuntu) and actually I don't have much time to dedicate to investigate and learn about it. So that's the reason why I asked for a solution here to the community.
However thank you again for your intervention!!! ;)

---

### Post by kumoshk on 2012-02-20
Xfce's mixer has never really worked for me insofar as the microphone is concerned. I solved the problem by using Gnome until now. They switched to Unity (and I like my configuration); so, I switched to Xubuntu. Xubuntu has made a lot of improvements sinced last I used it (back in the Gutsy days or shortly thereafter), but my microphone still doesn't work.

I have a Compaq Presario CQ60-212US Notebook PC. I don't know if the problem is the same as yours. I get segmentation faults when I try to use the gnome-alsa-mixer (which I believe worked for me in times past, too). I'm using Xubuntu 11.10 (64-bit), though (a newer version). One solution might be to install regular Ubuntu so that the mixer works fine and then install Xfce on top of that (instead of vice versa), although that might take a while if your video card clashes as much with Unity as mine does.

Let me know if you ever figure this out. The microphone worked fine for me in Ubuntu 9.10 (which is what I had last).

I might just try either Kubuntu or Fedora to see if they work with it. I could try the 32-bit route, and see if that works any better, but I really hate to do that, as a matter of principle (I promote 64-bit support by using it; somebody has to).

---

### Post by kumoshk on 2012-02-20
I used the following code to get my alsa information:

```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```


Here's the URL with my output, if it helps to solve the problem:
[http://www.alsa-project.org/db/?f=1760d31ed41173a10f4d60d7d374d7a647e4a267](http://www.alsa-project.org/db/?f=1760d31ed41173a10f4d60d7d374d7a647e4a267)


Could someone whose microphone is working on Xubuntu please get their information and post it so that I can compare? Thanks.

---

