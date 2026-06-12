---
title: "Java for Webex in Ubuntu 12.04 LTS?"
date: 2012-09-04
forum: Multimedia Software
---

### Post by JPR65 on 2012-09-04
If I didn't post this in the right sub-forum, my apologies. 

My problem is simple: Earlier this week I found that I needed Java to participate in a webex lecture. I did some research, and installed OpenJDK and Iced Tea from the software center. To check that java actually ran, I tried a java-based webpage (runescape). Lo and behold it worked. Unfortunately, today, when I attended the lecture, webex would not recognize my headset, and would not let me call in via my computer. I also could not hear any audio. I know that the java I installed is opensource, and was wondering if you guys could guide me through uninstalling what I have, and installing the java from oracle. (at least I think this is the right way to go about it; I just want webex to work for me!). My computer is running Ubuntu 12.04. Thanks!

---

### Post by JPR65 on 2012-09-09
Can nobody help me with this? This can't be that uncommon of a problem!

---

### Post by Cheesemill on 2012-09-10
To install Oracle Java:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```
No need to uninstall OpenJDK first.

All of this information can be found in the Ubuntu Wiki:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by JPR65 on 2012-09-11
Thanks so much! I followed your instructions and it appears that oracle java has successfully installed! I'll post again once I try out webex.

---

### Post by JPR65 on 2012-09-20
Still can't get webex to work...but that's ok, I'm going to install a virtual windows machine inside of ubuntu, and I'll run webex in there.

---

### Post by xjohnthomasx on 2013-01-11
Did anyone ever get a solution, besides using Window$? Seriously, that's the best we could do?!

Bump!

---

### Post by slickymaster on 2013-01-11
> **xjohnthomasx said:**
> Did anyone ever get a solution, besides using Window$? Seriously, that's the best we could do?!

Bump!

[http://askubuntu.com/questions/217578/webex-audio-doesnt-work-on-12-04-lts-32-bit](http://askubuntu.com/questions/217578/webex-audio-doesnt-work-on-12-04-lts-32-bit)
Take a look. Who knows? When we make an effort, most of the times we manage to get things working.

---

### Post by ewr2san on 2013-03-08
In Ubuntu 12.10 64 bit, I installed the icetea-7-plugin and it seems to be working ok for me.

sudo apt-get install icedtea-7-plugin

Im using chromium Version 24.0.1312.56 and it also works on Firefox 19.0.

> **JPR65 said:**
> If I didn't post this in the right sub-forum, my apologies. 

My problem is simple: Earlier this week I found that I needed Java to participate in a webex lecture. I did some research, and installed OpenJDK and Iced Tea from the software center. To check that java actually ran, I tried a java-based webpage (runescape). Lo and behold it worked. Unfortunately, today, when I attended the lecture, webex would not recognize my headset, and would not let me call in via my computer. I also could not hear any audio. I know that the java I installed is opensource, and was wondering if you guys could guide me through uninstalling what I have, and installing the java from oracle. (at least I think this is the right way to go about it; I just want webex to work for me!). My computer is running Ubuntu 12.04. Thanks!

---

### Post by joaopinheiro on 2013-05-25
> **Cheesemill said:**
> To install Oracle Java:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```
No need to uninstall OpenJDK first.

All of this information can be found in the Ubuntu Wiki:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

This worked for me. Thanks! :-D

---

