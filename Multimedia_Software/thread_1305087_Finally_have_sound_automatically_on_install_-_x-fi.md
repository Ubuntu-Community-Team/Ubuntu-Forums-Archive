---
title: "Finally have sound automatically on install - x-fi"
date: 2009-10-29
forum: Multimedia Software
---

### Post by loseby on 2009-10-29
Have a x-fi sound card and did a clean install of 9.10 and sound was installled successfully ( well it was muted at at startup ) by default ie. I had to do nothing whats so ever.

---

### Post by Garyu on 2009-10-29
It works. Kind of.

The only setting that produces sound of some quality is "analog stereo". I have a 5.1 system, but choosing that only produces a lot of high pitch static in the speakers as a backdrop to the music. 

AND, most importantly, my mic isn't working. Best case scenario: mic records exactly what the speakers play. Does anyone have a nice pulseaudio x-fi mic guide handy?

---

### Post by matji on 2009-10-30
Hi. I have an SB X-FI USB and it works with 5.1 but when I start to play another music (closing the player program and reopen), I have to change in Sound Preferences on the hardware tab the X-Fi device profile to something else than "analog surround 5.1 analog" and then change it back.
 
  Does anybody have the same problem??

---

### Post by dr_jaymahdi on 2009-11-02
> **losbey said:**
> Have a x-fi sound card and did a clean install of 9.10 and sound was installled successfully ( well it was muted at at startup ) by default ie. I had to do nothing whats so ever.

Just wondering, which X-Fi you have? PCI or PCI-E?

Thanks in advanced

---

### Post by Garyu on 2009-11-02
> **dr_jaymahdi said:**
> Just wondering, which X-Fi you have? PCI or PCI-E?

you didn't ask me, but I'll answer as well.

I have an X-Fi XtremeGamer PCI.

Sound muted on first boot. Stereo is the only thing that works, until you play around with alsamixer then it is possible to get 5.1 even though alsamixer behaves very odd. Mic is not possible to get working in my experience.

---

### Post by whoop on 2009-11-03
> **Garyu said:**
> It works. Kind of.

The only setting that produces sound of some quality is "analog stereo". I have a 5.1 system, but choosing that only produces a lot of high pitch static in the speakers as a backdrop to the music. 

AND, most importantly, my mic isn't working. Best case scenario: mic records exactly what the speakers play. Does anyone have a nice pulseaudio x-fi mic guide handy?

Exact same issue here... I am using "analog stereo duplex", because any "analog surround 5.1" makes everything sound like bad encoded mp3 (static pitching etc.). Any information on if this is going to be improved?

---

### Post by Garyu on 2009-11-03
> **whoop said:**
> Exact same issue here... I am using "analog stereo duplex", because any "analog surround 5.1" makes everything sound like bad encoded mp3 (static pitching etc.). Any information on if this is going to be improved?

if you start alsamixer (or alsamixer-gui) and fiddle around with the volume controls, you should be able to get 5.1 sound. It worked for me and I was told to do it by someone else, so it seems to be a known fix. Volume sliders behave oddly, sometimes if you touch one the others are muted, etc. But it should get rid of the static pitching and give you nice sound. 

I am REALLY looking forward to someone stepping out with a mic fix right now... :(

---

### Post by whoop on 2009-11-04
> **Garyu said:**
> if you start alsamixer (or alsamixer-gui) and fiddle around with the volume controls, you should be able to get 5.1 sound. It worked for me and I was told to do it by someone else, so it seems to be a known fix. Volume sliders behave oddly, sometimes if you touch one the others are muted, etc. But it should get rid of the static pitching and give you nice sound. 

I am REALLY looking forward to someone stepping out with a mic fix right now... :(

Is there some specific approach to this? Even with all sliders set to zero and just opening one slider a tiny bit, the sound is all pitchy for me. This happens for all speakers (individually and together).

---

### Post by Garyu on 2009-11-04
> **whoop said:**
> Is there some specific approach to this? Even with all sliders set to zero and just opening one slider a tiny bit, the sound is all pitchy for me. This happens for all speakers (individually and together).

it only works for me if I have the volume in the top panel (close to the clock, the small icon volume thingy) set to 100% volume. If I decrease to 99% or anything like that, the static returns. 

So that volume at 100%, the alsamixer volume can still be changed (even main volume) so they are not connected. And when changing volume in alsamixer the static disappears and it is possible to fiddle around to get 5.1 surround sound with subwoofer.

---

### Post by whoop on 2009-11-04
> **Garyu said:**
> it only works for me if I have the volume in the top panel (close to the clock, the small icon volume thingy) set to 100% volume. If I decrease to 99% or anything like that, the static returns. 

So that volume at 100%, the alsamixer volume can still be changed (even main volume) so they are not connected. And when changing volume in alsamixer the static disappears and it is possible to fiddle around to get 5.1 surround sound with subwoofer.

All right,  I seem to have improvement now... thanks man..

---

### Post by drakvakt on 2009-11-20
I've had the issue with the microphone not working in Ubuntu 9.10 since i installed it. Upgrading alsa only seemed to **** things up for me. 
But now I finally got it working!! I'll share what I did with you, but I have very little knowledge of linux, so I won't be able to answer any advanced questions.

First i installed "GNOME-alsamixer" through "synaptic package manager" (found in system -> administration).
Now I found the software in application -> sound & video and started it up.

What I found was that Center/L was muted, and the Mic was all the way down. So I unmute center and pull the Mic all the way up.

Thats it!! After that I tested and everything works fine. I did this with a fresh install of Ubuntu 9.10 (hadn't fiddled with it atleast). My soundcard is a X-fi xtreme gamer

Hope this helps someone.

PS. Here's a screen of all my current GNOME-alsamixer settings: [[IMG]http://img265.imageshack.us/img265/1989/screenshotmfh.th.png[/IMG]]("http://img265.imageshack.us/i/screenshotmfh.png/")

---

### Post by Garyu on 2009-11-22
> **drakvakt said:**
> What I found was that Center/L was muted, and the Mic was all the way down. So I unmute center and pull the Mic all the way up.

Thats it!! After that I tested and everything works fine. I did this with a fresh install of Ubuntu 9.10 (hadn't fiddled with it atleast). My soundcard is a X-fi xtreme gamer

Hmm, so you have the same soundcard as me, but you get it to work while I don't. That should tell me something, but it doesn't. I have of course tried alsamixer with a variety of settings, none of which works. Rather annoying.

EDIT: I notice you have two tabs in your alsamixer. any chance you plugged your mic into your motherboard internal soundcard and that is the one working with your mic?

EDIT2: Just tried it myself, and indeed activating my motherboard soundcard and plugging in a mic there makes my mic work on that soundcard, while sound output works on the soundblaster x-fi. But this way, it is impossible to use the front conntector for anything else than headphones, since the mic has to be connected at the back of the computer. So it makes it impossible to use a headset and it's not a very pretty solution. I would prefer to have my mic working on the X-Fi.

---

### Post by drakvakt on 2009-11-22
Well, my headphones(with mic) are connected to the front connection where I thought only the X-fi card should be wired. Input is also set to X-fi. It does however appear that under preferences both cards work now. It's possible that both cards could be wired to the front connection but previously my internal cards been working well from the back connection, but not the front.

Back connections works for both cards.
Front  connection works.
Any mic-connections sems to return sound whichever card I put in sound preferences


Is there any way to temporarily disable my internal card to check?

Update:
muting Line-in stops all mic-sound. Disabling my internal card in "sound preferences" doesn't change anything. It appears that it is the X-fi that's working.

---

