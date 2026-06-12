---
title: "Audio completely garbled when attempting a Skype conference call"
date: 2010-05-14
forum: Multimedia Software
---

### Post by unc0nn3ct3d on 2010-05-14
This just started happening recently.. I have no problems with 1on1 skype calls but as soon as I try to bring in another party all of my skype audio just sounds like some really really bad video game from the 70's.  Just beeps and borks.  The other people on the call can hear each other just fine and dandy, but on my end I can't hear anything except for beep boop beep boop.  Anyone else have this problem?

Using 10.04 btw

---

### Post by Tossu on 2010-05-20
I got exactly same problem. Using Ubuntu 10.04 also. When I do conference call peoples can still hear me correctly but others sound like robots for me.

---

### Post by quill3033 on 2010-08-24
Any solution to this problem? 
I log out of the Ubuntu session, and log in as another user on my computer and then log into Skype as the same id I always have and I have no problems with that pc user's configuration which makes me think it is something that should be easy to solve...

---

### Post by quill3033 on 2010-08-24
ok this worked for me but I can't give any guarantees because when I try to reproduce it, it doesn't give me the same problem.

I went to Applications -->Sound&Video --> PulseAudio Device Chooser
and this gave me an icon on the system tray. 
I then clicked on it and in the drop down menu, I went to "Configure Local Sound Server".

There in the Simultaneous Output tab, I de-selected the option: 

"Add virtual output device for simultaneous output on all local sound cards."

It was for some reason ticked but as I have an eee-pc with I believe only one sound card I figured it wouldn't hurt to deselect and it worked. Skype conference is no longer giving me that very bad disco music :-) 

I tried to tick this setting back (on another of my profiles in this pc as I didn't want to mess with a good thing) but it didn't then cause garbled sound on conferencing so ... not able to reproduce but still, deselecting that setting worked for me. Hope this helps somebody.

---

### Post by unc0nn3ct3d on 2010-09-18
Strnage enough that was already unticked for me.   What I tried, just out of curiosity was hooking an ethernet cable in instead of running off wifi and it seems to have solved the problem.. This might be due to a lack of bandwidth, although I'm getting a solid Mbit up and 5 mbits down but perhaps the quality was bad.

---

