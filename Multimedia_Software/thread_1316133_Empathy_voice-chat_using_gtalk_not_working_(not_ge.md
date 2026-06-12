---
title: "Empathy voice-chat using gtalk not working (not getting sound)"
date: 2009-11-05
forum: Multimedia Software
---

### Post by sexyclient on 2009-11-05
I'm using Ubuntu 9.10 and I can't chat (with gtalk in empathy.  My mic input and speaker output are configured properly (as far as I can tell,) but I can't get anything to work.  I've got sound working perfectly well in everything else, so I don't know what's the problem.

There are instances where I can use the mic (when using gizmo5, for example, my input works,) but getting sound to come out fails.  Anyone experience this issue found a workaround?

---

### Post by sexyclient2 on 2009-11-06
bumpity-bump-bump,

am I the only one?

---

### Post by wilcoxjay on 2009-11-06
I have a similar problem. I can hear and see my friends, and they can see me, but they cannot hear me.

I'm looking forward to a solution. Let me know if you need data.

James

---

### Post by sexyclient2 on 2009-11-07
So I tried pidgin and the same thing happened...  At this point I began to think that, because I use gtalk on a google domain apps' account with gizmo5 and gtalk2voip.com, there was a misconfiguration in one of these services so I logged into windows (which, at this point I'm very glad I didn't delete) and tried gtalk there.  The result?  It was an overwhelming success; things worked perfectly...

My next step is to test my current config on windows' pidgin to see if I erred somewhere there.

---

### Post by wilcoxjay on 2009-11-07
I have also tested this with pidgin, and got the same results. Furthermore, the same thing happens with skype. However, non-chat programs like audacity do fine. Skype and Pidgin both work fine for me (full video and audio) under windows.

Edit: I also filed the following bug: [https://bugs.launchpad.net/bugs/477752](https://bugs.launchpad.net/bugs/477752)

---

### Post by sexyclient2 on 2009-11-07
Sweet.  Bug-reporting has always been too complex for me, but I'm glad that at least now the issue is documented.  I'll keep my eye out for updates, cuz it looks like this issue won't be resolved any time soon...

---

### Post by 78ufzniyE4 on 2009-11-11
:-/ Voice is working great and clear but video is not. :(

---

### Post by sexyclient2 on 2009-11-11
> **linuxbrother11 said:**
> :-/ Voice is working great and clear but video is not. :(
I'm curious: are you using the 64 or 32-bit koala?

---

### Post by crichard on 2009-11-16
> **wilcoxjay said:**
> I have a similar problem. I can hear and see my friends, and they can see me, but they cannot hear me.

I'm looking forward to a solution. Let me know if you need data.

James

Even I'm having the same problem. I can hear my friends voice but they can't hear mine.
Any solutions?

---

### Post by sexyclient2 on 2009-11-16
Unfortunately not.  Apparently fixing voice-chat isn't a very high priority...  Might I ask what version Koala you're using, crichard?  32 or 64-bit?

---

### Post by wilcoxjay on 2009-11-16
No solutions yet. I filed the following bug report (which has been silent for a few days now). 

[https://bugs.launchpad.net/bugs/477752]("https://bugs.launchpad.net/bugs/477752")

If you have an Acer Timeline laptop, I encourage you to mark the bug as affecting you. If you have different hardware, I encourage you to file a separate bug (you can use 'ubuntu-bug alsa-base' on the terminal).

Hopefully we'll find something out soon,

James

---

### Post by crichard on 2009-11-17
> **sexyclient2 said:**
> Unfortunately not.  Apparently fixing voice-chat isn't a very high priority...  Might I ask what version Koala you're using, crichard?  32 or 64-bit?

I'm using 32 bit.

---

### Post by crichard on 2009-11-22
> **crichard said:**
> Even I'm having the same problem. I can hear my friends voice but they can't hear mine.
Any solutions?

Hi guys,
Good news for us. Audio chat in gtalk is working now. I've reinstalled telepathy-gabble using Synaptic Package Manager.So, it works.
FYI, I've attached screenshots of my sound preference here.(System->Preferences->Sound).
Try it. Let me know if it works. Thank you.

---

### Post by wilcoxjay on 2009-11-22
Reinstalling telepathy-gabble doesn't fix it for me.

---

### Post by crichard on 2009-11-22
> **wilcoxjay said:**
> Reinstalling telepathy-gabble doesn't fix it for me.

OMG, Sorry 2 hear this. Itz working here without any problem.

---

### Post by sexyclient2 on 2009-11-22
Mines also failed.

---

### Post by crichard on 2009-11-22
> **sexyclient2 said:**
> Mines also failed.

Try 2 reinstall Telepathy Mission Control 5 also. For me, I just reinstalled telepathy-gabble & it works. Hav u chked ur mic? Can u able 2 record ur voice?
In my 2nd attached image, (Input tab) Input level progress bar is there. R u getting any bars while u r using ur mic?

---

### Post by sexyclient2 on 2009-11-23
I reinstalled everything empathy/telepathy and still got nothing - meant to post that sooner, though I got distracted.  I haven't yet tried on the new kernal I installed today, so after I try that out I'll update.

---

### Post by sexyclient2 on 2009-11-24
OK, so there's been an update to telepathy-missioncontrol5 (or something like that, forgot the package name) but now in empathy I can actually hear sound from the other end!  Still can't chat, though, so it's just like in gizmo5...

I guess that this is the ubuntu error.

---

