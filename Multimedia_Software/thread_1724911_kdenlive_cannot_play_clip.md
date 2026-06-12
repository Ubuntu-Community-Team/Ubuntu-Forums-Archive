---
title: "kdenlive cannot play clip"
date: 2011-04-08
forum: Multimedia Software
---

### Post by balkibalkibul on 2011-04-08
Hello everyone, i am new on ubuntu. i am using maverick 10.10 and just install kdenlive 0.7.8-0ubuntu0~sunab~maverick9 . But when i am trying to edit, i cannot play the clip that i have imported (blank screen) but when i click the timeline i can see the clip, but still cannot play it,,please help
i installed kdenlive with this command:
sudo add-apt-repository ppa:sunab/kdenlive-release  
sudo apt-get update  
sudo apt-get -y install kdenlive

---

### Post by nush on 2011-04-15
hi
i had the same problem, the partial fix for me was

start kdenlive
click on settings, select configure kdenlive, select playback.
then on the video driver option select x11.
then apply and save, hope this helps
nush

---

