---
title: "Why does Audacity now hate me?"
date: 2008-03-22
forum: Multimedia Production
---

### Post by muhkayoh on 2008-03-22
Hello,

I have occasionally used Audacity to record/edit dialog for my amateur cartoons.  I haven't made one in a while and in the interim Audacity got upgraded to 1.3.4 beta.  I never had trouble before but now I can't get Audacity to record or play.  I'm getting an input device error, but I've literally tried every combination now of input/output settings and none of them work.  I've been combing through the threads on Audacity here and have already tried reinstalling Audacity and deleting the config file to no avail.  All other sound in all other programs work fine. I can even record with the basic sound recorder that comes with Gnome/Ubuntu - just not with Audacity.  I have ALSA sound and oss-alsa installed.  I don't have Jack installed because I don't use any of the more complex packages like Rosegarden that need it.

All i really need is a good way to record and edit dialog and sound effects for my silly cartoons.  Can anyone either help me figure out why Audacity is no longer working or suggest a good alternative?  I'm on Gutsy.

Thanks,

Matt

---

### Post by Oysterville on 2008-03-23
I've had similar problems as well, and at one time it was resolved for me by installing esound.  Don't know why, it just did.

---

### Post by muhkayoh on 2008-03-23
Thanks for the suggestion.  I gave it a try but it didn't change my Audacity problem.

The thing is, I liked using Audacity precisely because it was easy for a non-sound guy like me to get my head around so that I could edit and manipulate dialog for my cartoon characters.  I never even had to do anything like choose the proper input device before - it just worked.  

Matt

---

### Post by luke.johnston on 2008-03-24
have you tried running audacity with this command?
```

aoss audacity
```

---

### Post by muhkayoh on 2008-03-24
Yes, thanks, I had already tried that as well.  

The good news is that I'm able to run the windows version of Audacity under Wine and it works fine, so the urgency of fixing the problem is somewhat lessened.  I'd still like to figure out what's wrong, though.

Thanks,

Matt

---

### Post by jsilas on 2008-05-08
I'm just learning about Ubuntu so please, eat something bitter when you read this.I'm in that same boat though. Sometimes I can get Audacity to work by logging out and logging back in. Sometimes I need to restart Audacity. As far as your input device goes. Open Audacity, pull the "edit" menu, choose "preferences". A window (sorry to use that word) will pop up. Choose "audio I/O" on the left side of the window (sorry again) You will see a couple of options. Two being "playback" and "recording. Pull the "playback device" menu and select your audio output device. That could be your sound card or an audio interface. You'll have to choose your Recording Device also, that would be pretty much the same, thats just your mic or whatever your using as an input. ANYWAY. I'm just learning about Ubuntu so please, eat something bitter when you read this.

---

