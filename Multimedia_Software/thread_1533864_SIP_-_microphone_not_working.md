---
title: "SIP - microphone not working"
date: 2010-07-18
forum: Multimedia Software
---

### Post by kingdavid.schell on 2010-07-18
I have installed and tested several SIP clients for my SIPgate account. I make the call from google voice, and the softphone "rings." Then the call goes out, and I can hear the person I'm calling, but they can't hear me. I'm confused about why this isn't working. The sound recorder that came with the distro works fine, but none of the softphones I'm using pick up sound from the mic! Any suggestions? And let me know what else you need. I have used google with skill for hours and gotten piles of suggestions that were absolutely worthless. Figured it was time to ask for help. Thank you so much!


=====================DETAILS====================
SOFTPHONES TRIED: Ekiga, Twinkle, QuteCom, Empathy. I tried all the input settings in each program (except "no sound." I knew that wouldn't work...)

DISTRO VERSION: Ubuntu Netbook Remix 10.04

MAKE AND MODEL: Acer Aspire One ZG5

ALSA INSTALLED: Yes.

PulseAudio installed: Yes.

---

### Post by lidex on 2010-07-18
Check out this post - just replace skype with whatever you're using:
[http://swiss.ubuntuforums.org/showpost.php?p=9604850&postcount=2]("http://swiss.ubuntuforums.org/showpost.php?p=9604850&postcount=2")

---

### Post by kingdavid.schell on 2010-07-18
I had installed the PulseAudio Volume Control... and couldn't really find anything that made sense. There weren't a lot of options besides volume going up and down; nothing was muted, and there was nothing to "select" besides the default. Any more ideas?

---

### Post by kingdavid.schell on 2010-07-20
*bump*

---

### Post by YannBuntu on 2010-07-27
Have you tried Ekiga with a ekiga.net account ?

Can you record sound via Sound&Video->Sound recorder ?

---

### Post by kingdavid.schell on 2010-08-02
I have indeed tried the sound recorder. It works fine.

I have not tried an ekiga.net account. I don't think it will make any difference. I have, however, tried numerous other programs as described in my first post. If it helps, I have Skype, and Skype has the same problem.

---

### Post by YannBuntu on 2010-08-03
If you use Ubuntu 10.04, go to System->Preferences->Sound, Input tab, and check that you selected your mic before using any softphone.

---

### Post by kingdavid.schell on 2010-08-19
Yup, it's selected all right. There's only one, and it's selected. It's been selected... nothing's changed.

---

### Post by lidex on 2010-08-19
Try this from a terminal:
```
ubuntu-bug audio
```
And reference this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by Ernie S. on 2010-08-28
I have the same issue. I got Skype to work once a few months ago, but I have since reformatted :). In Pulse Audio select the input devices tab then click the lock to unlock the sliders. Then bring the right slider down all the way. This should enable your mic (you'll see the input bar jumping). This will work with GV except I have to do it every time I make a call since GV resets it. If anyone can find a way to either lock down PulseAudio or stop GV from resetting it, I would be grateful...

---

### Post by gradinaruvasile on 2010-08-28
To the OP:

You say the sound recorder works. Right-click on the tray volume icon, select preferences -> input tab. Tap the mic and see if the input level shows anything. If it does, the mic works.
In this case the problem doesnt has to do with the programs.

Here likely you have a SIP-related problem. SIP as a protocol doesnt always work when in a random (internet for example) environment. It works great in a routed  internal network.
Typical problems are when speaker 1 hears speaker2, but speaker2 cannot hear speaker1. This also applies to echo tests - you speak but cannot hear it back.
Unfortunately there is no simple solution. Some SIP providers work better then others. Same with the SIP programs - some work better, some not that great.
Some of the ones i tested:
Good SIP programs - Linphone, Sflphone, Zoiper (this doesnt work well with PulseAudio sometimes), Sip Communicator (best routing support, but its a development version, so you may have some issues - make sure you select portaudio as souns system)

Bad SIP programs: Ekiga, Qutecom - bad SIP routing, no sound etc. Empathy uses some autoconfiguration options that sometimes work sometimes not.

Alternatives:
Skype - good sound quality, low bandwidth, native PulseAudio support.
Gmail web interface with Google voice/video plugin (Firefox and Chrome) - seems to use low bandwidth and has good sound/video quality 
Pidgin - Jabber/GTalk accounts in with the voice/video plugin (Pidgin's internal plugin, not the previosly mentioned browser plugin).
Empathy - Jabber/Gtalk accounts (when it works that is).

---

