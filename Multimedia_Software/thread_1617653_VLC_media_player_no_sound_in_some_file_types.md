---
title: "VLC media player no sound in some file types"
date: 2010-11-09
forum: Multimedia Software
---

### Post by miniclip22 on 2010-11-09
Hello all, I have recently found a strange problem with my VLC Media Player, as it only has sound is certain file types, but on others it doesn't. I have tried to run .AVI files, and it plays sound, also tried .flv files, but with no luck. I am running Ubuntu 10.10, thanks in advance!

---

### Post by gordintoronto on 2010-11-09
Did you install VLC from the repositories? Can you play the files using Movie Player? Did you install the Restricted Extras using Synaptic?

---

### Post by pe7er on 2011-02-26
I had a similar problem: VLC didn't play audio from .avi files.
But Movie Player did not play the audio either...

I reinstalled VLC using Synaptic and then it gave the following error:
> Potential ALSA version problem:
VLC failed to initialize your sound output device (if any).
Please update alsa-lib to version 1.0.23-2-g8d80d5f or higher to try to fix this issue.

I searched on "Please update alsa-lib to version 1.0.23-2-g8d80d5f or higher to try to fix this issue." 
and found this solution from user actionparsnip: [https://answers.launchpad.net/ubuntu/+source/vlc/+question/125187](https://answers.launchpad.net/ubuntu/+source/vlc/+question/125187)

With ```
sudo add-apt-repository ppa:ricotz/unstable; sudo apt-get update; sudo apt-get upgrade
``` I was able to solve my audio problem!
Now VLC and Movie Box both play sound in .avi files.

---

