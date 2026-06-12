---
title: "DVD back-up quality not good"
date: 2013-02-02
forum: Multimedia Software
---

### Post by unknown user on 2013-02-02
I have tried to back-up my dvd collection so that I can put it all on HDD. I have used K9, Throggon and AcidRip. Each time the quality of the back-up file is good, but not great. It seems to be a bit piculated in places. The original is great when played in the same dvd player.

Has anyone found this before of have any ideas, as if the back-ups are not of good quality, there is no point doing it.

---

### Post by SeijiSensei on 2013-02-02
Strange that you have not tried Handbrake, an excellent DVD ripping program.  You should use John Stebbins PPA for Handbrake like this:

```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake*

```

You can choose either the MP4 or the Matroska (MKV) container.  I generally use the latter if I am ripping subtitled materials, but MP4 is more widely supported by notoriously proprietary manufacturers like Sony.

Handbrake uses H.264 encoding and AAC audio by default.  

I recommend installing [smplayer]("http://smplayer.sourceforge.net/") from the repositories for playback.  However your computer's specs are a bit weak for high-quality video performance.  Take one of the files you have already created and play it in someone else's computer with more horsepower.  Any better?  If so, you should consider using something that can create XviD-encoded files in the AVI container.  There are Windows programs like [AllToAVI]("http://alltoavi.sourceforge.net/") for this task, but on Linux I rely on running mencoder from the command prompt as described [here]("http://en.gentoo-wiki.com/wiki/Mencoder#XviD").

---

