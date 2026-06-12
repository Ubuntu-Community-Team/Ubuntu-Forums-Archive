---
title: "All video playback looks to be in fast forward"
date: 2011-03-04
forum: Multimedia Software
---

### Post by Gosport on 2011-03-04
After working properly for over a year my videos started playing in fast forward.  This can be on the internet (as in wwww.wimp.com) or my video clips located on my hard drive.  

Also, on a different note my volume control stopped working.  My keyboard has a volume control wheel that I used to use to control the volume of music and videos.  First it gave out on my side and continued to work on my wife's side and now it doesn't work on ether.  (the volume level bar pops up on the screen but doesn't affect the output)  (The volume can still be controlled with the mouse though by clicking on the volume bar on whatever web page I am looking at.)  Any idea what might be causing this?  Are these two problems related?

---

### Post by Gosport on 2011-03-04
Actually, I can't hear any audio in these fast playing videos.  The sound situation above pre dates the fast forward issue.

---

### Post by Gosport on 2011-03-06
System>Preferences>Sound>Output Then select "Internal Audio Analog Stereo Stereo"

I don't know why but this seemed to fix the Video problem.

My volume control on the keyboard still doesn't actually adjust the volume, though the volume graphic does pop up and move up and down as if it was.

---

### Post by trivio on 2011-04-03
Thank you soooo much, Gosport, for coming back after solving your problem, and posting the solution. 

I had the very same (and rare) problem, and after searching the web and finding no solution I finally came to this forum and read your self-solved issue ;)

Going to System>Preferences>Sound>Output and then selecting "Internal Audio Analog Stereo Stereo" worked perfectly! Now video and audio play normally. 

I've registered just to thank you!

:popcorn:

---

### Post by narrit23 on 2011-05-17
thank you so much Goscort for the simple solution, soo helpful after trying all these crazy other solutions

---

### Post by kalle-saltis on 2011-05-21
Goscort, you are my hero. Thank you.

---

### Post by JesusJaquez on 2011-07-10
> **Gosport said:**
> System>Preferences>Sound>Output Then select "Internal Audio Analog Stereo Stereo"
 
I don't know why but this seemed to fix the Video problem.
 
My volume control on the keyboard still doesn't actually adjust the volume, though the volume graphic does pop up and move up and down as if it was.
 
 
Dose this fix the problem for Win XP?  or what do i have to do to fix it.  Its driving me crazy!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! PLZ help.

---

### Post by rcaracaus on 2011-10-09
Thankyou gosport!

---

### Post by xuzhou on 2011-12-06
I tried System>Preferences>Sound>Output but there is only HDMI to choose from. Can't find "Internal Audio Analog Stereo Stereo" anywhere. :confused:

Am I missing any driver?

---

### Post by mblahay on 2012-12-18
This worked for me too. My Windows VM running on Ubuntu was doing the same thing. Changing this setting fixed all of it.

Any one know why this worked?

---

### Post by thistrain on 2013-01-28
from [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)

HDMI output will work if you edit grub

=== Workaround 1 ===
 Edit /etc/default/grub and change this line:


 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 

to this line
 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"
 

Now run "sudo update-grub", then reboot your computer.


Doing this fixed HDMI output for my PC. Videos no longer play in fast forward and sound is enabled.

---

