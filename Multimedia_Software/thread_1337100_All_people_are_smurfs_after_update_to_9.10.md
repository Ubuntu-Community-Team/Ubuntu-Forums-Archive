---
title: "All people are smurfs after update to 9.10"
date: 2009-11-25
forum: Multimedia Software
---

### Post by thor-on-kveven on 2009-11-25
Hi

After upgrading to 9.10 my video worked fine for a day or so.(never mind that my TV tuner doesn't work anymore) Then occasionally when opening video files (.avi and .mp4) the video would start with "blue filter", i.e. all colou/ whole screen in blue spectrum, see the attached screenshot. Initially this was reverted after reboot, but then started persistting after reboot. 

I then accidentally discoverd that colours would normalise if I started the NVIDIA server settings interface while the video was running. But NOT if the interface is already running when I start the video file.If I did that the colours would NOT normalise with re-opening the NVIDIA interface until after a reboot. 

The problem is the same in both VLC and Movieplayer. 

It sometimes works better if I only watch .avi files after reboot, but affects all filetypes after I've watcehd an mp4 file. All files worked well pre-upgrade and for a while after upgrade, so it is not my files that are compromised. 

I'm now in a situation where the discoloration persists despite reboots and fiddling with the NVIDIA interface. I suddenly am stuck with a movie collection of smurfs. I am a little bit over Linux at the moment, suddenly windows' endless patches and virus programs don't seem so bad. At least the problems make sense, this current problem is a bit too random for me. Still, hoping these amazing forums can pull me out of the mud again. My partner has put the XP disc on my desk...

---

### Post by thor-on-kveven on 2009-11-25
For clarity I should probably add that this problem is limited to video files only. Pictures, desktop and embedded video in web browsing are not affected. 

Cheers

---

### Post by bwolf1 on 2009-11-25
I am experiencing the same problem when playing MP4's off of the hard drive.

---

### Post by BelzeBob on 2009-11-25
Yup. I got same problem Everything was dandy until yesterday. Suddenly....everything turned blue.

---

### Post by pleur on 2009-11-25
I had this same problem. I found that in the Totem-preferences the "hue" was turned all the way down.

Solution? Open your totem-player, navigate to "Edit > preferences" and then the "display"-tab. Press "reset to defaults". 

This solved the problem for me

---

### Post by bwolf1 on 2009-11-25
Thanks. That fixed it for me as well. What a strange side-effect of an OS upgrade. And, what a simple fix. Thanks, again.

---

### Post by thor-on-kveven on 2009-11-25
Thanks heaps, worked for me too. Now on to sorting out the TV tuner card. (sigh...)

---

### Post by Zorael on 2009-11-25
I just want to post in this thread because of its *awesome* title.

---

### Post by Resplendent Raven on 2012-02-04
Amazing how this bug showed up for me in 11.10, i checked Totem hue was in the middle.
Turning it all the way down or maxing it out, made everyone look normal again.
Somehow this setting even made it's way into the other mediaplayers, so fixing it in Totem will fix it in Banshee for example.

I guess Ubuntu and Totem really like the Smurfs and the Na'vi :confused::rolleyes:

---

