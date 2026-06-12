---
title: "Alsa, microphone, mixer, Nvidia problem"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by jrz on 2007-11-06
One year and hundreds of hours of googling, reading, downloading and attempts at solving our problem with no success. We have a Compaq Presario V3042AU notebook, running Ubuntu 6.06 with all recommended updates applied and current. Our last remaining major problem is getting the microphone to work, and we had achieved some success a few months ago by installing the latest alsa version, although the record level was very weak. Recently we updated to the 1.0.15  stable release of alsa, and nothing changed. We still had low record levels. Playback levels have always been acceptable. In looking for a resolution we found many posts mentioning the mixer having a checkbox to give the microphone a 20 DB boost. We found no such option, and then found that there were other mixers on the system that could be brought up in a terminal window. We found them also lacking a 20 DB boost option, but for some reason after looking at them the microphone has now ceased to work at all. Looking at each mixer individually, none have anything muted and the sliders are all at maximum. Another thing we noticed while the microphone was working, was that the microphone slider for both the internal and the external microphones had no effect and we achieved the same record level no matter where the slider was positioned, although the mute function worked and turned the microphones off when we muted them.
Yesterday, in an attempt to get the microphone to record even if at a low level, we tried a complete reinstall of alsa, but that did not work either. Now we are at a complete loss as to how to proceed. We have viewed many posts, tried numerous solutions, none of which helped, followed the alsa wiki, and asked for help, to no avail on the alsa irc channel. Not being a Linux guru, we are not certain as to where to look for information on the system that might indicate what is the cause of our problem. There appears to be files which contain information related to the sound system in various locations, and perhaps one has some erroneous info causing our problem?
Any help would be greatly appreciated, and we have searched and tried all we can find that sounded like it might be significant in the Ubuntu forums with no success.

Our soundcard shows as an Nvidia MCP51 High Definition Audio
and a Conexant CX20549 codec

---

### Post by kennedyjch on 2007-11-06
jrz: Unfortunately I do not have a solution to your problem. My only recommendation would be to download some of the 7.04 or 7.10 LiveCDs and see if they solve the microphone problem.

I have a Nvidia mobo and it was working (accellerated graphics, microphone and all) under Ubuntu 7.04 i386 installation. It WAS working until I made the fateful click to upgrade to 7.10. From then on it was 1 week of failure and frustration until this past weekend. I reinstalled 7.04.

All I can contribute (as I'm one of the newest of linux newbies) is some basic advice.

1) If it's not broken, dont fix it - even if it's an upgrade.
2) test everything with live cd's before installing (fortunately we in the linux world can do this). My decision on a linux distro (7.04) was made by taking Ubuntu, freespire, Knoppix and some others and seeing which ones worked on my hardware setup (graphics, sound, microphone, etc.). 
3) If you are a newbie or "just want it to work" you may strongly consider whether using "bleeding edge" features and technologies (viz., AMD64 installations)  are appropriate for you. I have a mobo that has dual code Athlon 64's. But I've shied away from the AMD64 installation as there may not be 3'rd party apps that will install effortlessly without major expert interventions (i.e., Skype, Slimserver, etc.).
4) With Linux, you need to find your appropriate balance between "learning by doing" and your wife's need to have the damn box work. 

Apologoes if I'm just exposing my complete naievete here. Hopefully I'm not giving out bad advice (if I am, please flame me).

---

### Post by jrz on 2007-11-06
Thanks for the response, but I've not been convinced that another distribution would be the solution as it appears to be related to alsa and integrating the mixer, and many others are having the same or similar problems with other distributions of Linux as well as other versions of Ubuntu.
We began with many problems, and this one remains, so we would like to work it out before making any major system changes.

---

### Post by dutchcow on 2007-11-07
On my v3000 machine, running any 7.xx results in no sound at all, or some sound sometimes. I been thinking of downgrading back to 6.xx just to get sound working. I've seen some tricks like booting up the laptop withoutthe AC in or suspend and then unsuspend without AC to get sound to work, but none of those work for me. I sugest you stick with 6.xx as 7.xx will only give you more problems. See also the posts in [this]("http://ubuntuforums.org/showthread.php?t=239995&page=13") thread. Also there are bug reports filed at launchpad and at alsa, but after one year i given up hope on working sound under ubuntu, which is a pitty tho. Guess fixing bugs to get sound to work on a chipset that many laptops use is not a priority at alsa. Bummer :)

---

### Post by jrz on 2007-11-07
We've run across the same suggestions you mention, and although find no reason for them to help, gave them a try also. We have always had sound, but have only got the microphone to record (weakly), after installing later alsa software. It has since ceased to function again, and we're trying to determine what has occurred causing this and would like to get it to work even with low levels once again, and then proceed in trying to find a solution which will increase the level. It appears to be the HW and alsa being incompatible and it is difficult to find someone working on alsa to converse with. We just keep plugging along in hopes of eventually finding a solution.

The wireless was also difficult to get to work, but after months of trying we found knowledgeable help and were able to solve that. Kernel updates require a little extra effort as they seem to break the fixes we apply, but we are trying to document the steps necessary to be taken to quickly solve them.

The microphone is our last major problem related to Ubuntu directly, and then we will begin to look into playback of various video formats which is the only other problem we are currently aware of.

---

### Post by lha79 on 2007-11-27
Hi,

I also had weak sound capturing from the microphone, I have found 20Db microphone boost. It is:
1) Right click on Volume Applet -> Open Volume Control
2) In Volume Control window select Edit -> Preferences
3) Check "Microphone Capture" and "Mic Boost (+20db)"
4) on Options tab make sure relevant options are checked
5) Test with sound recording

BTW: I have ATI video card.

Cheers

---

### Post by jrz on 2007-11-27
Thanks, but we knew where the 20 db boost is supposed to be displayed, but it is not and we have been unable to find a way to make it appear.

---

### Post by lha79 on 2007-11-29
Hi,

That is the thing, Step 3 was describing the way in which you make the 20db boost check box to appear. Initially this check box was not displayed for me as well, I selected the option for it to be displayed (via Volume Control -> Edit -> Preferences, after you check it in preferences, this 20db check box had appeared on the tab in Volume Control).Only after that I was able to see it and tick it. 

Cheers

---

### Post by jrz on 2007-11-30
Sorry if I wasn't clear, but it doesn't appear there either. We've tried numerous fresh installs, 3 versions of alsa, and still no luck.

---

### Post by hsam007 on 2007-12-05
Try this, it solved my problem.

1) Right click on Volume Applet -> Open Volume Control
2) In Volume Control window select Edit -> Preferences
3) Check "**Capture**"
4) on Recording tab make sure the microphone is not disabled
5) Test sound recording


I solved my microphone problem tanks to lha79 his guide led me in the right direction.

---

### Post by jrz on 2007-12-05
We are still trying to find a way to make the option to enable a 20 DB boost appear in the mixer. Other than that everything is working, but the record level is much too low to be usable.

---

### Post by Red Moose on 2007-12-12
Does the 20db option show up in alsamixer?

---

### Post by jrz on 2007-12-13
No, it does not and that is what we are trying to solve.
Under 6.06 we tried Alsa 1.13 which enabled the microphone to record, Alsa 1.14 and Alsa 1.15, both ofwhich added nothing new. We now have 7.04 installed and it uses Alsa 1.13 and the microphone records, but still no 20 db boost showing, or an option to do so.
We believe the problem to be associated with the Conexant CX20549 codec chip which Alsa appears not to support well, if at all.

---

