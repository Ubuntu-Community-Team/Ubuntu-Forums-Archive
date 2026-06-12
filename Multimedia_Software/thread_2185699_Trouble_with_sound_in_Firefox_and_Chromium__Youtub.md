---
title: "Trouble with sound in Firefox and Chromium / Youtube and Hulu"
date: 2013-11-03
forum: Multimedia Software
---

### Post by td-potter505 on 2013-11-03
I have Netflix desktop running with sound and when I check the sound settings on my computer, the sound check works for both the left and right computer speaker. However, when I try to play videos on either Youtube or Hulu, I cannot hear any sound. I am running Ubuntu 12.04 LTS. I believe I have the Adobe Flash player 11.2.202.310 installed. I am not sure when it stopped working. It may have been after I tried to update the Silverlight plugin when I was trying to get the Xfinity OnDemand video to work. I am willing to share any of my computer settings, but I am still fairly new to Ubuntu and would like step by step help if possible. Thanks in advance for anyone who responds.

---

### Post by td-potter505 on 2013-11-04
I read through a few threads but couldn't get the fixes to work. The one that seemed to have the most promise is this one:
[http://askubuntu.com/questions/312529/whats-happen-suddenly-no-sound-youtubes-videos-are-played-too-fast-in-13-04](http://askubuntu.com/questions/312529/whats-happen-suddenly-no-sound-youtubes-videos-are-played-too-fast-in-13-04)
It didn't quite work for me, but these instructions helped me learn a few more things in Ubuntu. Finally, I read through the readme text file that came with the latest version of the Adobe Shockwave Flash player and found I needed to type this instruction, At the prompt type:
        + sudo cp -r usr/* /usr
I also cleared out my browser cache, but anyway the sound has been restored.

---

