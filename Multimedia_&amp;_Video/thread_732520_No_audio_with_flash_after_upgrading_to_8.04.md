---
title: "No audio with flash after upgrading to 8.04"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by snkngshps on 2008-03-23
I just upgraded to Hardy Heron and I had a few problems. My wi-fi wasn't working. I was able to fix it by downgrading that package. I had a few other issues I've been able to resolve but one that I haven't: the audio no longer works in flash videos. I've found many threads about how to fix it but nothing is working for me. Most of these threads are from a year or two back so I don't know if maybe the fix is different for this version of Ubuntu. Let me know if you know of anything that could help. Thanks!

---

### Post by Kropotkin on 2008-04-21
Yeah,  I am seeing this as well.

---

### Post by beefcurry on 2008-04-21
for me it is solved once every other program that uses sound is shut. That includes Banshee and Totem. seems like there is a conflict somewhere.

---

### Post by panholt on 2008-04-24
Install libflashsupport and go to Preferences > sound and change everything to pulseaudio sound server.

---

### Post by SilverWave on 2008-04-27
My PulseAudio problems.

I had no sound in Totem if I left the "Sound" at autodetect.
Setting to ASLA worked for Totem but not Firefox flash.

Installed the tools and followed the instructions from here:
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
(as per [http://ubuntuforums.org/showthread.php?p=4816406#post4816406](http://ubuntuforums.org/showthread.php?p=4816406#post4816406))

started PulseAudio applet and had a look around - found that the default device was my USB skype phone!

If I listened in on the phone I could hear the flash from the bbc iplayer in firefox!!!

Couldn't find a quick way to change the default device but for the time being just pulled the USB phone.

Rebooted all working including flash!



Note1:
I didn't do this bit:
* Checkmark all three options under Network Access.
* Checkmark Enable Multicast/RTP Receiver.
* Checkmark EnableMulticast/RTP Sender.
Note2:
I installed restricted drivers and libflashsupport.
(Then uninstalled and reinstalled and mucked about until I found the above work around).

Cheers!

---

### Post by tucurious on 2008-04-27
libflashsupport was the answer for me

Thank you.

Art

---

### Post by Kevbocat on 2008-05-20
Hello,

New to Ubuntu and Linux altogether. I've been searching for the past day or so on resolving this problem with no audio in flash and came across this site with this post.

> I performed a fresh install of Ubuntu 8.04 and everything was going great until last night. I was notified that there were 40 updates to pull down, and being the diligent techie that I am I went ahead with the install. Shortly thereafter I noticed that my flash videos had no audio. Standard video and audio files on my PC had audio, just not flash. Thanks to panholt for this post, the issue is resolved. Just follow these steps:

   1. Open a terminal window via Applications -> Accessories -> Terminal.
   2. Type in the below command and hit the enter key:

      sudo apt-get install libflashsupport

   3. Enter your password when prompted and let the package install.
   4. Close the terminal window.
   5. Open Sound Preferences via System -> Preferences -> Sound.
   6. Change the first four drop downs to PulseAudio Sound Server.
   7. Click the Close button.
   8. Restart any applications that utilize sound (FireFox, Totem, RhythmBox, etc).

All applications should now be using one, unified sound system, and there should no longer be any conflicts that cause certain applications to drop audio all together.

Credit goes where credit is due. With the help of Alex and Panholt, I have resolved my issue and everything is working great.

I applaud both of you on your efforts and help.

Link to the site where this was posted in case anyone cares to look.

[http://blog.thegoldfish.net/no-audio-in-flash-in-ubuntu-804/]("http://blog.thegoldfish.net/no-audio-in-flash-in-ubuntu-804/")

---

