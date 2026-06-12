---
title: "audacity recording skype calls on ubuntu 10.04?"
date: 2012-05-28
forum: Multimedia Software
---

### Post by ubto66 on 2012-05-28
[SIZE=4]Can't get audacity to record skype calls on ubuntu 10.04 lts.[/SIZE]
 [SIZE=4]It records the caller* but not my mic.  [/SIZE]*I meant the call receiver, the one talked to.
 [SIZE=4]You don't have to ask my to google an answer. I already have. And tried several suggestions. But either the caller part gets recorded or the mic part.[/SIZE]
 [SIZE=4]The pc runs a realtek high definition audio.[/SIZE]
 [SIZE=4]I've also installed pulse audio device chooser and volume control.[/SIZE]
 [SIZE=4]Thanks.[/SIZE]

---

### Post by JOHNNYG713 on 2012-05-28
have you  tried to set your mic as another channel !? it sounds like audacity sees just one input, caller or you, granted both signals are using the same audio card but one is sending and one is receiving, you could try to loop your out put back into your mic with a "Y" cord, but you may have some issues with feed back, just a thought, or have you tried "sound recorder" to see if it might be just a glitch with audacity? or maybe try another recorder. Audacity should see both signals, but I cant say why it doesn't, hmm just wacky the way things should work but don't.  . .  Good luck !

---

### Post by ubto66 on 2012-05-28
> **JOHNNYG713 said:**
> have you  tried to set your mic as another channel !?
How do I do that?
Thanks.

---

### Post by JOHNNYG713 on 2012-05-28
I'm sorry I miss spoke, I meant "track" see if you can set caller to one track, and your mic to another track, I would try it myself, but I have no one to skype ! :( LoL !

---

### Post by shantiq on 2012-05-28
audacity can be a pain in the rear at times for this kind of task


you will find this [**Skype Call Recorder**]("http://maketecheasier.com/record-skype-calls-in-linux/2009/07/06") a lot easier



download deb from [**here**]("http://atdot.ch/scr/download/")

---

### Post by sembagdod on 2012-05-29
Thanks shantiq, this was really helpful

---

### Post by ubto66 on 2012-05-30
Thank you for answering. Before your answer I already installed skype call recorder and this happens:
The call receiver part is recorded, not the mic part.

---

### Post by shantiq on 2012-05-31
> **ubto66 said:**
> Thank you for answering. Before your answer I already installed skype call recorder and this happens:
The call receiver part is recorded, not the mic part.



ok   does it show that on pavucontrol when you try and record when you speak in your mike?   if you use your **inbuilt-audio **     your choice will be

[COLOR="DarkRed"]**analog stereo  **[/COLOR]

[ATTACH]219000[/ATTACH]

---

### Post by ubto66 on 2012-05-31
You ask me to set recording -> built-in audio analogue stereo.
 That exact option doesn't exist.
 There are two settings
 a monitor internal audio analog stereo => the one talking to is recorded, not the mic. The quality is close to ok. The volume level bar in volume control shows no mic deflection.
 b internal audio analog stereo => the one talked to is recorded but low quality. The mic is recorded but the quality is so low, that the mic part is not usable. The volume level bar shows the mic deflection.

---

### Post by Albatrossed on 2012-07-11
Tremendously usefull! Thanks a lot! I'm loving the 21st century already... so many tools! (:

---

