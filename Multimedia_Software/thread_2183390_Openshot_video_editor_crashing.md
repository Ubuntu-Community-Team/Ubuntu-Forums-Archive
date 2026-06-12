---
title: "Openshot video editor: crashing"
date: 2013-10-24
forum: Multimedia Software
---

### Post by Coder88 on 2013-10-24
I am playing with Openshot video editor to see how video editing may have improved with linux, and it has come a long way from even a year ago. But openshot is crashing (it and its gui just vanish off the screen) if I try to render a video clip project as anything other than native ogg vorbis or dvd mpeg. Any suggestions on what might be going on? Why is it vanishing, seems like a serious code flaw in openshot; better to display a popup rather than just vanish like a supernatural being, popping out of the linux desktop dimension. :)

Any ideas what I might try to remedy this? I do have codecs installed such as for playing a dvd movie ,etc, and i have the restricted libs and restricted extras libs. What more might I install so openshot does not crash?

xubuntu 13.10 AMD64, AMD six core cpu, 16 gb RAM.

---

### Post by Linuxisfast on 2013-10-25
Do you have video card? If so have you installed its drivers? I edit AVCD format movies whose sizes are over 3GB and never face any crashes with Open shot. This looks like a driver issue. Start Open Shot from terminal and it will then display whats causing the error.

---

### Post by patrickregister on 2013-10-25
I'm with you. I love OpenShot and have had no problems till my Ubuntu 13.10 upgrade. Now it crashes on both of my computers. It happens when I stop a video. As soon as I either click stop or the video finishes the whole thing just freezes. Sometimes I get a crash report and sometimes my whole system freezes and I have to just shut off the computer with the power button. This happens in both Ubuntu 13.10 and Lubuntu 13.10.

---

### Post by Linuxisfast on 2013-10-25
This looks like classic compiz/driver issue.

---

### Post by vanadium on 2013-10-25
It crashes because you are trying to render a video with the H264 codec. On Ubuntu 13.10, H264 encoding broken with avenc, and thus for any video progrm relyinig on it. [https://bugs.launchpad.net/ubuntu/+source/x264/+bug/1241772](https://bugs.launchpad.net/ubuntu/+source/x264/+bug/1241772)
It probably won't be long before the fix lands in Ubuntu 13.10.

Apart from that, video editing in linux remains crashy by default. The only way to proceed is to save the video project after each action, so that when it crashes, you do not lose alle the work.

---

### Post by mc4man on 2013-10-25
A fixed libx264 is in saucy-proposed now  &  will be moved to saucy-updates at some point, maybe very soon, maybe a bit down the road

---

### Post by Coder88 on 2013-10-27
I switched to trying the Flowblade video editor and so far no crashes with flowblade; very nice NLE video editor by the way, looks to be even better than Openshot. Until openshot runs without crashing, or perhaps even regardless, I am going with Flowblade.

---

