---
title: "Control Bar in some Audio and Video no longer display"
date: 2016-08-18
forum: Multimedia Software
---

### Post by findlj52 on 2016-08-18
I'm running Ubuntu 14.04 and am finding that on some websites I cannot control video or audio playback.That is, the control bar showing the pause, play, stop buttons and the  playback location bar (shows where you're at in the playback timewise) no longer appear. 
 This is a new issue in that the problem websites were working properly just a couple weeks ago.     Note that in that timeframe,  I have recently installed pipelight to get video on nbcolympics.com to play.  While it's certainly possible this install initiated the problem,  I cannot say for certain that this issue did not exist before the pipelight installation.   Other websites, like YouTube.com, for example, currently still work fine.

Here are the steps I used to get pipelight working...
sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --update
sudo pipelight-plugin --enable flash
sudo pipelight-plugin --create-mozilla-plugins
 
Examples of websites where the problem occur are playing back audio and/or video on redbulltv.com and adventureriderradio.com.

Does anyone have an idea what this issue may be?:confused:

Thanks for the help in advance.

---

