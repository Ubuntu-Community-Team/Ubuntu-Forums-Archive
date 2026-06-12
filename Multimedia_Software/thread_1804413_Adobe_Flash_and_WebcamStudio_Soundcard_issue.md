---
title: "Adobe Flash and WebcamStudio Soundcard issue"
date: 2011-07-14
forum: Multimedia Software
---

### Post by eival on 2011-07-14
for the last month or so ive had compatibility issues with these two things.

i had this issue before and i worked around it by just rolling back to Flash 10.2 but that meant i was stuck with buggy flash players on all the sites i go to.

so i just recently went to the WCS site and noticed they have a newer version than the one i installed from the repositories but after i updated, the audio still would show up as HDA Intel instead of "Linux Audio" which it use to say before when it worked but it wont detect the audio from my desktop at all with this HDA Intel

ive even used Flash-Aid to install the latest beta version of Flash 11 and the HDA Intel driver is still being shown.


im assuming that Ubuntu has its own generic soundcard driver which is the "Linux Audio" and i know i have an Intel computer, so perhaps if just uninstall the HDA Intel driver it will only be able to find the default Linux Audio again?

hopefully anyone else who uses this program can help me or even if u can just help me figure out if i can uninstall this HDA Intel driver that might be causing the issue.


or if you know of another program thats more stable that has similar features as WCS or ManyCam(Windows/Mac only) let me know an ill try it out.

---

### Post by no2498 on 2011-07-15
? you look in system , preferences , sound to see what its set at

---

### Post by eival on 2011-07-17
> **no2498 said:**
> ? you look in system , preferences , sound to see what its set at

the settings are the exact same throughout this entire process.

but under hardware tab it says

Internal Audio
1 Output
Analog Stereo Output

the only difference is that now under the Input tab the input level for the audio played on my desktop was called "Microphone 1" and i could see the volume levels moving with the sound.

but now none of the sound inputs work, except my TV audio which i run through my desktop and its plugged into one of the mic jacks. that is "Microphone 2"


and to top it off the actual internal mic on the desktop is working cause if i boost it high enough i hear the white noise and i also see the levels move up, but it doesnt pick up audio from webbrowsers or media played on my desktop


and if i plug in a USB microphone it works

so its something thats changed recently with either WCS or Adobe Flash thats causing this mixup.


seeing as how this programs sole purpose is for use with webcam sites which all use flash, i would think i cant be the only one with this issue

unless as i said, theres a better program that i dont know about, ManyCam is the most popular but they dont support Linux

---

### Post by no2498 on 2011-07-17
in the flash app have you clicked allow and remember
if you click the mic in it the bars move
hope that helps

---

### Post by coffee412 on 2011-12-19
Iam having the same basic problem here with wcs. I get no sound when playing video clips on blogtv. I see that my choices are an intel HD sound device or webcam. I have the intel HD sound device but doesnt produce sound on blogtv thru wcs.

I know this post is old but thought I would add to this. Unfortunately I cannot determine if this is a flash or wcs or sound settings problem.

So, Does anyone use WebcamStudio with Ubuntu? Any sound problems??

Thanks!

---

