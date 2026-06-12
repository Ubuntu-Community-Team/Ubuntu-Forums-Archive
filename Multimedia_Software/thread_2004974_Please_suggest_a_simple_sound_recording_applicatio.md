---
title: "Please suggest a simple sound recording application"
date: 2012-06-16
forum: Multimedia Software
---

### Post by marinara on 2012-06-16
Let's say I want to use my microphone with LUbuntu.
I'm used to having a small application that records the microphone in a single click, so I can play it back with the play button.
Is there anything like that for Lubuntu?

I'm thinking something not for myself, but for new or average users of skill.
TIA

---

### Post by shantiq on 2012-06-17
yes there is    sox


open terminal     > sudo apt-get install sox libsox-fmt-all


to get an mp3                               ```
rec  -C 320  nameyouwant.mp3 
```    
to get an ogg                                ```
rec  -C 10  nameyouwant.ogg     
```  
to get a flac                                   ```
rec   nameyouwant.flac
```     


now to play back       simply enter  ```
 play   nameyouwant.flac     or ogg or mp3
```



**Could not be simpler:KS**


[B]====================================
[/B]



if gui is more attractive







there is also sound recorder which is installed natively i think



find it under applications/sound and video

it does not play back but any player will or    install > sudo apt-get install gnome-sushi


and if you save to desktop simply hover over saved file and click spacebar    your recorded voice will play

---

### Post by robert shearer on 2012-06-17
Audio recorder works well.....
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

---

