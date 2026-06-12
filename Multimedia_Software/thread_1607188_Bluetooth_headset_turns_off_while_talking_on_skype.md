---
title: "Bluetooth headset turns off while talking on skype"
date: 2010-10-27
forum: Multimedia Software
---

### Post by dmar0 on 2010-10-27
I've got quite an unusual problem with my bluetooth headset that does not really make sense to me

Here are the details:

1. It turns itself off if I talk over skype, in Ubuntu with a person and not with echo123 after ~38 seconds (variable in fact, less than a minute in general).

2. It does NOT turn itself off when using it under windows.

3. It does NOT turn itself off if I listen to music or record something in Ubuntu.

4. It does NOT turn itself off if I call echo123 (the call lasts ~51 seconds).

It seems as if there is some magic combination of Skype + real person calling + Ubuntu + bluetooth headset.

Any ideas anyone what could cause it?

---

### Post by lilezek on 2010-10-27
My own bluetooth headset turns off when no sound (or the sound isn't loud enought) is playing. So, check if yours works like mine. If it is, then increase the loudness of skype. Or keep doing noise with some app, like a videogame or an audio player.

---

### Post by dmar0 on 2010-10-28
I tried so, put some music on with low volume and tried to talk. Headset turned off after some 20 sec. Normally it takes longer to turn off due to inactivity. Hence, Skype somehow is causing it (or smth around it).

The funny thing is that it works fine if a skype conversation is not going on. I tried 2 different bluetooth headsets and the result is the same for both.

Anybody had the same problems? Anybody has any clue what might cause it?

---

### Post by rsk02 on 2010-11-05
> **dmar0 said:**
> I tried so, put some music on with low volume and tried to talk. Headset turned off after some 20 sec. Normally it takes longer to turn off due to inactivity. Hence, Skype somehow is causing it (or smth around it).

The funny thing is that it works fine if a skype conversation is not going on. I tried 2 different bluetooth headsets and the result is the same for both.

Anybody had the same problems? Anybody has any clue what might cause it?
I am having the same problem with an lg headset. I have tried this on two different machines so far. Amazing, but yes, the bluetooth headset powers down. No idea why either. Will let you know if I find something. Hope you can also post your findings.

Thanks.

Update: You might want to see if unchecking the "Allow skype to automatically adjust my mixer levels" makes a difference. While I haven't tested extensively, it did make a difference for me on a skype-skype call.

Further Update: Unchecking the "Allow skype to automatically adjust my mixer levels" on the Options-> Sound Devices tab appears to have solved the problem for me. I made several skype-skype, skype-phone and skype-in calls (including a webex conf) and the bluetooth headset did not turn off or otherwise disconnect. All calls were at least 5 minutes long.

---

### Post by dmar0 on 2010-11-10
> **rsk02 said:**
> 
Further Update: Unchecking the "Allow skype to automatically adjust my mixer levels" on the Options-> Sound Devices tab appears to have solved the problem for me. I made several skype-skype, skype-phone and skype-in calls (including a webex conf) and the bluetooth headset did not turn off or otherwise disconnect. All calls were at least 5 minutes long.

I've just found exactly the same solution and wanted to post it here. 
Thank you for sharing ;)

Seems that problem is solved! :)

---

