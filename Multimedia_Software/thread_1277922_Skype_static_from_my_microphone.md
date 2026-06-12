---
title: "Skype static from my microphone"
date: 2009-09-28
forum: Multimedia Software
---

### Post by Masterofpsi on 2009-09-28
Hi all, running Jaunty on a Dell Inspiron 1545.

OK, so I know full support for Skype can't be offered because it's not free software, but I have a problem and I was wondering if anyone could help.

This is how it goes: after booting my laptop up, if I call someone using Skype, everything works fine. **But**, anytime I make a call or receive a call after that first time, the person on the other end can only hear static from my end. They can see my picture fine, and I can see and hear them, but we can't get the sound to work.

My comes with an integrated webcam/microphone on the lid. I'm not sure how to get the hardware specs for that, but lspci gives me:

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```

Can anyone help me with this? It's really annoying having to restart every time I want to talk to someone. Help would be much appreciated.

---

### Post by Masterofpsi on 2009-09-29
No one? :(

---

### Post by Musicologynut85 on 2009-09-30
I'm having the same problem. However, I've noticed a few things:

If I reset my computer, the sound is good for the first call I make, anything after that and it goes back to static. See if it works that way for you? We can see if we can figure this out.

---

### Post by Masterofpsi on 2009-09-30
> **Musicologynut85 said:**
> I'm having the same problem. However, I've noticed a few things:

If I reset my computer, the sound is good for the first call I make, anything after that and it goes back to static. See if it works that way for you? We can see if we can figure this out.

Yeah, I said I have the same symptom. I don't understand it.

---

### Post by MrWES on 2009-10-16
> **Masterofpsi said:**
> Yeah, I said I have the same symptom. I don't understand it.

Anyone ever come up with a solution to this? I'm experiencing the same problems between my Ubuntu Skype and a Windows Skype machine.

Bill

---

### Post by Claus7 on 2009-10-16
Hello,

almost every single time I open skype, I have to configure my audio device in order to be able to have a descent conversation. Are you sure, that while trying a second connection, something is not messed up with your audio configurations? 

I have sound from the others, yet till I configure my microphone and such, they do not hear me.
Check options and sound devices and also alsamixer. Sometimes these options dislocate...

Regards!

---

### Post by CamiloSmurf on 2009-10-25
I've been experiencing the same problems listed here. I'm an uber-newbie at linux. I installed the netbook remix on my Acer Aspire One, but got fed up with some problems, so I switched and am now running 9.04 on the same machine. Most of the problems have been cleared up but Skype is still being problematic. 

When you go into the skype audio device settings there is no choice for anything other than pulseaudio.

---

### Post by Claus7 on 2009-10-31
Hello,

> **CamiloSmurf said:**
> 
When you go into the skype audio device settings there is no choice for anything other than pulseaudio.

you are clear on what you are saying, yet, do you have sound from other applications? I have to admit that checking skype 2.1 beta after the final updates of karmic I get only pulsuaudio as options. Yet, I have sound. May be if you configure correctly pulseaudio, you will have sound in skype too. I cannot think anything else by now.

Regards!

---

### Post by Brokerjoe24 on 2010-02-21
I have the same problem.  My first skype test call works fine, but the second one is only static. So, this is what I did:

1.) Went to open volume control and selected Realtek ALC888 as the device 
2.) and then went to preferences and added in-gain,
3.) and then I increased the in-gain. 

Now, when I do the Skype test calls, I can hear my voice each time during the tests with no static.  I don't sound super clear, but its a lot better than static.

---

