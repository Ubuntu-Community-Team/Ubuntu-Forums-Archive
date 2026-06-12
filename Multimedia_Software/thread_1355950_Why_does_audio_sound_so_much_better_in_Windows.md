---
title: "Why does audio sound so much better in Windows???"
date: 2009-12-15
forum: Multimedia Software
---

### Post by ThinkEntropy on 2009-12-15
I've searched, and searched, and searched, and I can't find a good explanation as to why my sound quality is awful in Ubuntu 9.04.  In most of the searching I did, it seemed like issues like these are often attributed to mixer levels being too high (particularly PCM), but I've spent weeks dicking with all of the different settings options and nothing seems to fix the problem.

The best way I can describe the sound is it sounds like one of my equalizer channels are maxed out, but they're not so far as I can tell.  If I switch into Windows, the problem disappears.  I also have to turn the sound up much higher on my audio receiver in Ubuntu to get the same volume that I do in Windows.  Very weird.

```

00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

```Every channel in Alsamixer is muted save for Master, PCM, and IEC958.  Both Master and IEC958 are at maximum, and PCM is at 71%.  As I said earlier, I've tried different combinations of the levels and nothing seems to get rid of the problem.

What do you guys suggest that I do to figure this out?

---

### Post by Sin@Sin-Sacrifice on 2009-12-15
Your driver and/or player configurations are wrong. I've never heard clearer or better audio than what I hear with pulse audio in Karmic. I would look first at the player for EQ settings and mess with them. What player are you using?

---

### Post by GuiGuy on 2009-12-15
> **ThinkEntropy said:**
> 

What do you guys suggest that I do to figure this out?

I bought Windows 7 after the [sound stopped working ]("http://ubuntuforums.org/showthread.php?t=1354493&goto=newpost")in my Mythbuntu based home entertainment system nearly a week ago. I just couldn't cope with the intermittent Ubuntu/ Linux breakdowns anymore.  (Sorry, fanboys). 

Within an hour everything was working.

---

### Post by ThinkEntropy on 2009-12-17
> **Sin@Sin-Sacrifice said:**
> Your driver and/or player configurations are wrong. I've never heard clearer or better audio than what I hear with pulse audio in Karmic. I would look first at the player for EQ settings and mess with them. What player are you using?


I agree that the sound shouldn't be like this, but I don't know what to do to fix it.  As I said I've been playing with the EQ settings, but to no avail.  I've tried using different media players thinking that might help, but there was no change (I'm using VLC now).  I also googled my audio hardware, but I couldn't find any commonalities with the hardware and this issue I'm having, which makes me believe, as you said, that this is a configuration issue.

So which driver do you suggest I try?


Edit:  I just tried bringing all my VLC EQ settings back to nominal, and the only change was that I needed to turn my receiver up higher to get the same volume, and the crackling was still there.

---

### Post by saltmore on 2009-12-17
> **GuiGuy said:**
> I bought Windows 7 after the [sound stopped working ]("http://ubuntuforums.org/showthread.php?t=1354493&goto=newpost")in my Mythbuntu based home entertainment system nearly a week ago. I just couldn't cope with the intermittent Ubuntu/ Linux breakdowns anymore.  (Sorry, fanboys). 

Within an hour everything was working.

Sadly nothing is perfect. If it were not for nagging virus issues then would be using Windows myself. You might try removing pulse. Pulse is ok but not perfect.

---

### Post by ThinkEntropy on 2009-12-17
> **saltmore said:**
> Sadly nothing is perfect. 

Actually, I'm quickly finding this to be true :P

> **saltmore said:**
> 
If it were not for nagging virus issues then would be using Windows myself. You might try removing pulse. Pulse is ok but not perfect.

I hear you!  I recently made the switch to Ubuntu and I really do believe that it is a better operating system.  Unfortunately, like you, I have one or two other niggling issues that I can't seem to remedy.  If I could, I'd never ever look back at Micro$oft.

I will try removing pulse, and see if that helps.  I've never tried this before, so hopefully it'll relatively straightforward.  Thank you for your input saltmore!

---

### Post by saltmore on 2009-12-17
Thankfully pulse is mostly ok on my system, but here is a little bit on it.

[http://www.ubuntumini.com/2009/09/fix-most-audio-problems-remove.html](http://www.ubuntumini.com/2009/09/fix-most-audio-problems-remove.html)

---

### Post by ThinkEntropy on 2009-12-17
> **saltmore said:**
> Thankfully pulse is mostly ok on my system, but here is a little bit on it.

[http://www.ubuntumini.com/2009/09/fix-most-audio-problems-remove.html](http://www.ubuntumini.com/2009/09/fix-most-audio-problems-remove.html)

Great, I'll give that a shot, thanks again.

---

### Post by ThinkEntropy on 2009-12-17
WOOOOOOHOOOOOOO!!!!!!!!!!!!!!!!!!!!!!!!

:guitar:

Removing PulseAudio did the trick.  It sounds fantastic!!  Thank you so much saltmore for taking the time to point me in the right direction.

---

### Post by saltmore on 2009-12-17
Glad could help.

---

### Post by VertexPusher on 2009-12-18
> **GuiGuy said:**
> I bought Windows 7 after the [sound stopped working ]("http://ubuntuforums.org/showthread.php?t=1354493&goto=newpost")in my Mythbuntu based home entertainment system nearly a week ago. I just couldn't cope with the intermittent Ubuntu/ Linux breakdowns anymore.  (Sorry, fanboys). 

Within an hour everything was working.
This is exactly why I consider PulseAudio harmful. It p*sses people off to the point that they ditch Linux and go back to Windows.

This thread should be made sticky. Maybe it should be tacked to Lennart Poettering's forehead.

Of course PulseAudio can be removed, but it's intimidating for new users to do so. We need a one-click solution for this. A PulseAudio emergency bail-out switch.

---

### Post by saltmore on 2009-12-18
> **VertexPusher said:**
> This is exactly why I consider PulseAudio harmful. It p*sses people off to the point that they ditch Linux and go back to Windows.

This thread should be made sticky. Maybe it should be tacked to Lennart Poettering's forehead.

Of course PulseAudio can be removed, but it's intimidating for new users to do so. We need a one-click solution for this. A PulseAudio emergency bail-out switch.

Sadly in a way agree with you. In theory it is great, and once get it going it is just ok. Jack of all trades. Master of none. :(

---

