---
title: "How can i get multi channel sound in linux"
date: 2009-01-01
forum: Multimedia Software
---

### Post by deepakbm on 2009-01-01
i have a motherboard that support multi channel sound,where can i get drivers which support realteck Ac'97

---

### Post by secondstage on 2009-01-01
If your sound is not working at all, please take a look at [this guide]("http://ubuntuforums.org/showthread.php?t=205449"). It covers almost all of the bases. But if you already have the sound working, but need muli-channel sound, most audio programs (Rhythmbox, Banshee, Totem, etc...) have options in their setting to adjust for surround sound and the such.

---

### Post by NeonBible on 2009-01-12
Where is the surround options in Rhythmbox? This is the one thing I cannot get working.

---

### Post by secondstage on 2009-01-12
In doing more research, I found that Rhythmbox uses Pulse Audio for its output. So to set it up...

1. Hit Alt-F2 on your keyboard. This will open up a Run dialog.
2. Type "gksudo nautilus /etc/pulse". Without the quotes.
3. There should be three files. Find the daemon.conf one.
[INDENT]a. Copy and Paste it to the same directory.
b. Rename the copy "daemon.conf.backup". Without the quotes (w.o.t.q.)
c. Right-click the Original, and choose "Open with Text Editor". W.O.T.Q.
[/INDENT]4. Hit CTRL-F. Type "default-sample-channels". W.O.T.Q. and hit enter.
[INDENT]Note: This will find the line that tells Rhythmbox how many channels to use.
[/INDENT]5. Change the value to the total number of speakers in your system. For example, if you have a 5.1 system. the number would be 6. If you had a 2.1, the number would be 3 etc.
6. Save (in the top bar area) and Exit.
7. Exit the file navigator Nautilus.
8. Restart your computer.
9. Once you're up again. Hit Alt-F again.
[INDENT]a. If you have a 6.1 system, type "speaker-test -Dplug:surround51 -c6 -l1 -twav". W.O.T.Q.
b. 2.1, type "speaker-test -Dplug:surround51 -c3 -l1 -twav". W.O.T.Q.
c. For any other, replace the number behind -c with the total number of speakers.
Note: This sends signals to all of your speakers, at this time you should go around and check all of them for functionality.
[/INDENT]10. If you did not get a signal on speaker(s), then right click the volume meter in the system bar positioned at the top or bottom, and click "Open Volume Control". 
11. Make sure that the Alsa mixer device is choosen. 
12. Go to Preferences (either a button, or under the Edit menu).
13. Check the boxes that pertain to your speaker system. Master, Front, Surround, Center, and LFE (and rear and side if you have a 7.1 or greater system.
[INDENT]Note. Now you will have the independent volume controls for each speaker.
a. Make all channels that are muted or have low volume be unmuted, or mid-high volume. 
[/INDENT]14. Repeat Step Nine, changing the volume levels as you want.
15. Forgive me for these ridiculously long instructions. Hopefully they will clear any problems


PS. Something interesting is to hit Alt-F2, and type "pavumeter", and hit enter. This is the Pulse Audio Volume Monitoring System. You can use this to check if an audio problem is hardware, or software, or external.

--secondstage

---

