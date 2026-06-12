---
title: "Hauppauge 350 PVR remote"
date: 2007-12-07
forum: Mythbuntu
---

### Post by RobotAlligator on 2007-12-07
I tried the autoconfigurations in the mythbuntu control center for the Hauppauge TV Tuner remote control, and I'm getting absolutely no feedback.  I'm not sure if the remote even works, theres no blinking lights or anything on it.  I've tried 4 different batteries as well, so it definately isn't that.  Anyone know of any way I can check to see if it works..is there supposed to be some cable coming off the back of my card so it can send out the infared signals?  It seems 100% dead..

---

### Post by Just4Fun20 on 2007-12-07
Read [http://ubuntuforums.org/showthread.php?t=622161](http://ubuntuforums.org/showthread.php?t=622161) including downloading and reading the zip file (which is a PDF file).  

First, make sure that you've connected the IR cable.  On my PVR 150 WinTV it's an 1/8 inch jack (or so) with a grey cord and then two funny little red things on the end.  This is the IR pickup (receiver) and IR Blaster output (which you don't care about right now).  

If that doesn't fix your problem, run 'irw'.  (Escape key until you are asked if you want to really quit and then quit.  Then right mouse button anywhere on the desktop, 'Accessories' and then 'Terminal'.  Type irw in the terminal.)  

With irw running point the remote at the IR receiver and press buttons.  You should see characters and the name of the button you just pressed.  That should verify that the remote is working or not.

 Good luck and let us know how you do.

---

### Post by troyboy162 on 2008-01-22
i am in the same boat here with a pvr-150 and mythubutu 7.10. thats the grey 45 key remote

ive tryed the auto stuff configure stuff included and chose the right card from the start i think, but nothing happens with the remote. 
irw will not work and the only thing in the dmesg is something about lirc on blah blah 61.

anyone got it to work on 7.10 without issue?

---

### Post by ahood on 2008-01-22
I have both a PVR-350 and PVR-150 in my box. The Hauppauge remote works out-of-the-box. However, in my case, I am not using an IR blaster. I am using a black receiver (about 18" long) that is connected to the last jack (bottom most) on the back of the PVR-350. There are several versions of this remote and I believe I have the A415-HPG (silver).

---

### Post by troyboy162 on 2008-01-22
that is strange. was yours a fresh install with 7.10 or an upgrade? im not too far along to do a fresh install again but its odd that myself and the above poster didnt end up with working remotes after the install. i know my hardware is good because it was all working right with sagetv hours before i did this install. 
well glad it works for someone :) im just being lazy and dont want to troubleshoot it like the old days lol

---

### Post by troyboy162 on 2008-01-22
just an update but after much mindless messing with lirc and following info to test it/modprobe/irw it is working. oddly enough i got fed up and took the pvr-150 out to test in my windows box. all was working with windows so i put it back in the DVR. i have no clue how but it worked when i put it back in. sorry this is no help to those still fighting the issue

---

### Post by dannyboy79 on 2008-01-22
i'm using the pvr-350 remote, it was my understand that the ir receiver that comes with the pvr-350 is only that, a receiver, not an ir-blaster. i purchased a serial ir-blaster to change my SA3250HD STB to the channels I want. I am using mythtv 20.02-fixes in feisty and alll is well. I did however need to run another instance of lircd. Mario (mythbuntu author) said I didn't need to do that but I did it that way and all works.

I recently wiped out my /home directory though so my lircd.conf (or whatever maps the remote buttons to mythtv buttons is gone.) I never use the remote anyway, I only set it up cause I got the remote with the pvr-350.

---

### Post by bredington on 2008-08-31
I think it would be wonderful if someone would post the answers to how to get the Hauppauge 350 A415-HPG remote to work with ANY MythTV application. After over 2 years of weekend research and fresh installs I finally found something while searching for the remote part number itself:

"We have only ever managed to get the Microsoft MCE Remote working completely. We use these with either the MCE Transceiver or USBUIRT Transceiver. Both of these transceivers are usb based devices. We have never managed to get any TV card direct connect transceivers working."

Terminal entries mythbuntu-lirc-generator doesn't work, gnome-lirc-properties doesn't list and can't discover it, irw command returns connection refused.  If ANYONE has gotten the A415-HPG remote that came with Hauppauge 150 and 350 cards to work with either IR receiver that came with same, I think there are a few people out there that would really appreciate you posting what you did.

---

