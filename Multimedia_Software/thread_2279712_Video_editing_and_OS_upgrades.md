---
title: "Video editing and OS upgrades"
date: 2015-05-25
forum: Multimedia Software
---

### Post by Evan_B._Howard on 2015-05-25
I am pretty new to Ubuntu and I am about ready to produce 20 video lectures  for a graduate school course and I need  some advice on video editing  programs. I did a few lectures earlier using  Open Shot. The program worked pretty good but it  does not enable me to do a few things I would like. So, after a  little bit of homework, I suspect  Kdenlive might be my best option in terms of capabilities. 
         But - it may not be best suited for Ubuntu 12.04. I am a little nervous  after reading reports of crashes and such. The Kdenlive Developer site  states that, "Since we are now based on Qt5/KF5, you NEED KDE Frameworks  5 to run Kdenlive." How can I find out if I have this or not? 12.04  came with my computer and Ubuntu is now up to 14.04.2 LTS and 15.04  non-LTS. Should I just go ahead and update Ubuntu and then try Kdenlive (what might  happen to everything else if I update?)? Should I try Kdenlive on 12.04  and just see what happens? Should I try a different VideoEditor?   Suggestions?

---

### Post by Bucky Ball on 2015-05-25
If you were running Kubuntu, you'd be set. You can install KDEdenlive from the repositories and it should drag in everything it needs, but be prepared, as that may be a LOT of dependencies from KDE and Kubuntu.

---

### Post by Evan_B._Howard on 2015-05-25
Thank you so much for the advice. I wondered about Kubuntu. I'll do some homework on the advantages and disadvangages of Kubuntu/Ubuntu. But I still have this question  (am I now on the wrong Forum?) -- what does "a LOT of dependencies" entail? What should I be looking for? Is there some link to guide me through this, or is it actually pretty straight forward, even though it might involve a lot of downloads?

---

### Post by Bucky Ball on 2015-05-25
If you install Synaptic Package Manager> launch it> search for Kdenlive> tick the box to install> it will show a list of things that will be installed to run Kdenlive. You can also right click on the app and 'Properties' and have a look around at what it will drag in. 

I just had a look and it needs a ton of stuff. If you want to try it, though, just give it a go (at your own risk :)). If you don't like, just purge/remove/autoremove. Lots of people seem to use it and I'm guessing they are not all using it in Kubuntu.

---

### Post by Evan_B._Howard on 2015-05-25
Thanks. I really appreciate the help.

---

### Post by kryten35 on 2015-05-26
Theres also LIGHTWORKS for linux.You have to register and download it from there website.The free version has only one output 
720p which are compliant for you tube.But you get the full editor.It has a steep learning curve though.Just google it.

Theres also CINELERRA, you need to get it it through a ppa
```
sudo add-apt-repository ppa:cinelerra-ppa
```
```
sudo apt-get update
```
```
sudo apt-get install cinelerra-cv
```

Openshot is ok,but a bit basic.

---

### Post by Bucky Ball on 2015-05-26
I notice you've marked the thread as solved. Please share with the community what you've decided on. It may help future travelers. ;)

---

