---
title: "Strange sound problem"
date: 2008-11-15
forum: Multimedia Software
---

### Post by flOOi!ghenTM on 2008-11-15
Hy i have a bit of an interesting problem i have a sound blaster live 5.1 card witch worked fine until i tried to install "widoze" after that it just stoped working i did a fresh install and the stange thing is that i have sound in flashplayer (youtube) and in System>Prefrence>Sound  when i click test it works but when i try to play a movie or mp3's in amarok there is absolutely no sound at all

---

### Post by chkneater on 2008-11-15
Try this, close out everything related to sound including any web pages that have music or movie players. Then goto System/Admin/System Monitor.  Find the tab with processes and right click and choose "Kill Process" for every process that has to do with sound.   Be careful what you choose, usually they have obvious names like VLC is VLC in processes.  Anything that has to do with sound Kill It!  This is not a cure but it should get your sound devices working again.  Until you open that certain app thats causing the sound devices to stop outputting.  I'll bet you can even see the progress bar move but still no sound right?  I have not determined the solution.

---

### Post by flOOi!ghenTM on 2008-11-15
I killed everything that had to do with sound even the volume-manager wich  i can't seem to get working now and nothing else changed the sound problem is still there

---

### Post by chkneater on 2008-11-19
Yeah, don't kill the volume manager.  Anything starting with gnome should stay.  Sorry my bad, shoulda told you that.  I'm not saying that will fix your problem, but either reboot or restart X to restart it IF it doesn't start on it's own.  Still don't have an answer to your problem though.

---

### Post by psyke83 on 2008-11-20
You should ensure your PulseAudio server is configured correctly. See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by cmckee1980 on 2008-11-20
wow, i have the exact opposite problem.  Flash in Firefox, and Youtube, etc, i am getting zippo for audio.  same in the sound pref's i cant get any sound when i hit the test arrows.... I can though get sound in RBox when playing MP3s or LAST.FM.  I have an ATI card built on my motherboard with HDMI out.  Strange...

---

### Post by psyke83 on 2008-11-20
> **cmckee1980 said:**
> wow, i have the exact opposite problem.  Flash in Firefox, and Youtube, etc, i am getting zippo for audio.  same in the sound pref's i cant get any sound when i hit the test arrows.... I can though get sound in RBox when playing MP3s or LAST.FM.  I have an ATI card built on my motherboard with HDMI out.  Strange...

You also need to configure PulseAudio correctly - see my last post.

---

### Post by cmckee1980 on 2008-11-20
thanks, but, does this support my ATI HDMI output, i dont see that anywhere in PulseAudio, ill keep trying though, but so far all i am seeing for choices in my PulseAudio setup while following those instructions are Analog sources for playback...

---

