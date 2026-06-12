---
title: "Why is pidgin so unstable under Natty?"
date: 2011-02-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by clivejo on 2011-02-22
I have noticed that Pidgin is crashing a lot and the entire system seems very unstable (hangs) when its running.

Any ideas what's going on?

---

### Post by cariboo on 2011-02-22
How new is your install? How up-to-date are you? I noticed with today's Unity update it is much more stable than yesterday, I can now use the applications and places menus without the system locking up

---

### Post by Funnnny on 2011-02-23
Long-time pidgin user here and no problem since alpha 1 :D

---

### Post by clivejo on 2011-02-23
Its a distribution upgrade via Update Manager.  I run Update Manager and its up to date as of yesterday.  I am unable to see Unity due to having Nvidia graphics.

---

### Post by cariboo on 2011-02-23
> **clivejo said:**
> Its a distribution upgrade via Update Manager.  I run Update Manager and its up to date as of yesterday.  I am unable to see Unity due to having Nvidia graphics.

If you are using the nouveau drivers, you could try installing libgl1-mesa-dri-experimental, i'm currently using that combination on a 9400GT with much success.

---

### Post by clivejo on 2011-02-23
Yes Im using the nouveau drivers at the moment.  

I think the system freezes are X related.  The display freezes and system does not accept input from keyboard (even the power button, CTRL-ALT-DEL or CTRL-ALT-F1)  However, the mouse still moves the pointer on-screen.

It seems the kernel is still functioning as it recently happened in the middle of an update, the hard-disk continued to work.  I left the system powered on for a bit and the updates installed successfully.

The only way to gain control again is to force power down (hold power button for 5 seconds) and restart.

---

### Post by Coplen on 2011-02-27
Pidgin crashes out on me so quick these days. I have two conversations going and when I switch back and forth it crashes. It's so bad I've gone to Empathy for now.

Edit: The crash seems to take place when switching between someone in yahoo and someone in msn. Never mind. It crashes period if I have two tabs going and then click on any other program. This is so weird. I updated from 2.7.9. to 2.7.10, but it acts the same way.

---

### Post by Coplen on 2011-02-27
I solved this by removing the Pidgin ppa and uninstalling pidgin, then I did sudo apt-get autoclean to be sure I didn't have some odd lingering packages for pidgin left. I reinstalled without the ppa and it works fine now.

I think the ppa might be too bleeding edge at the moment.

---

### Post by clivejo on 2011-02-28
I'm not using any ppa, but the behaviour is almost the same.  Seems to crash when flicking between conversations or if the instant message window is hidden and I bring it to focus.

---

### Post by PaulW2U on 2011-02-28
> **clivejo said:**
> I'm not using any ppa, but the behaviour is almost the same.  Seems to crash when flicking between conversations or if the instant message window is hidden and I bring it to focus.
I've had quite a few crashes too. I'm not doing anything out of the ordinary, just using the program normally. I've reported a couple of the crashes as bugs but the last time I looked they were marked private so there's no point in asking anyone else to look at them.

---

### Post by Coplen on 2011-02-28
> **PaulW2U said:**
> I've had quite a few crashes too. I'm not doing anything out of the ordinary, just using the program normally. I've reported a couple of the crashes as bugs but the last time I looked they were marked private so there's no point in asking anyone else to look at them.

I reported one crash several days ago, but thanks for reporting. Hopefully they'll fix this soon. It [Pidgin] still keeps acting really weird for me. Empathy works, but I like the Pidgin interface better! :D

---

