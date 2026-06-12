---
title: "Java and other sound application problem."
date: 2008-10-06
forum: Multimedia Software
---

### Post by Truckerpunk on 2008-10-06
I just made a fresh install of Ubuntu Hardy Heron, and almost everything work perfect. I only have one problem with running applications that use audio playback, while running a java-program that also uses the sound device(java bloodbowl). If java was running first this keeps on having sound, but the new application(like Amarok) wont work... And if Amarok is running and I start the Java application it wont have any sound. It seem only to be a problem with java applications... I've searched 'round the forum and found numerous threads that try to solve this problem, but none of them have worked... I don't know what could cause the problem other than those I found in other threads. On my old install of Hardy I had no problem at all. Hope I don't have to try a reinstall. Any help is greatly appreciated.

---

### Post by markbuntu on 2008-10-06
Are you using 32 or 64?

---

### Post by Truckerpunk on 2008-10-06
I'm currently running 32

---

### Post by Truckerpunk on 2008-10-06
Sorry for the double-post. I can't figure out how to delete my post above.... 
 
I'm currently running 32. I haven't solved this problem yet, but narrowed it down to being a hardware/Ubuntu problem. The current soundcard is an onboard NVidia CK804( Or thats at least what I think... Its the one listed in the System -> Preferences -> sound-tab). If I have the java-application running and try to press the test-button in the sounds-tab I get; "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application"... So I think my next try will be to install my old SoundblasterLIVE card and see if it solves the problem... Hopefully it does... Or else I'm screwed.:)

---

### Post by Truckerpunk on 2008-10-07
I was wrong... And jumped to conclusions. This didn't solve my problems after all... That one session it worked, but next time I started my computer it crashed at the login. After removing the soundblasterLIVE card it started without problems. Other than still not being able to play other audio when the java-application is running. I'm running out of hope here. Maybe I'm forced to install stupid Windows just because of how difficult it has proven to be to set up a sound device properly in Ubuntu... Sadly. I still hope I can fix it... But hope is disappearing fast. I can hope this problem is fixed in Ubuntu 8.10.

---

