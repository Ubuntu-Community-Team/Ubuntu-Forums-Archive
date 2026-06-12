---
title: "Configuring multiple hauppauge tv tuner cards"
date: 2010-08-15
forum: Mythbuntu
---

### Post by HudsonHawk04 on 2010-08-15
Ok, just want to get this out there. I have been searching and searching and have yet to find a way to fix my problem, I am attempting to configure two hauppauge tv tuner cards one is older and I cannot remember its clasification and the other is a dvr-1600. 

Here is a screen shot of what my tv looks like when I attempt to watch tv:

[[IMG=http://img823.imageshack.us/img823/8315/screenshotjl.png][/IMG]]("http://img823.imageshack.us/i/screenshotjl.png/")
 
Uploaded with [ImageShack.us]("http://imageshack.us/")

and debug log:

[=== Xsession Errors === /etc/g - Anonymous - PKb1M44U - Pastebin.com]("http://mythbuntu.pastebin.com/PKb1M44U")

Right now the only things that I can think of off the top of my head as to why this is not working would be 

1. I borked the running of coax somewhere (I am going to test my wiring today hopefully)
2. I need to get my hands on an amplified splitter.

Thanks for all the help and feedback I really appreciate it.

---

### Post by ian dobson on 2010-08-15
Hi,

It looks like a "bad/weak" analog signal (I had something similar with a PVR500 and very long cables).

Maybe try playing the video on a different PC to see if the problem is recording or playback.

Regards
Ian Dobson

---

### Post by HudsonHawk04 on 2010-08-15
I will double check my coax cables, are you saying that I should also look into an amplified splitter to boost the signal?

---

### Post by HudsonHawk04 on 2010-08-15
I was able to clear up the picture by doing some re wiring but I still have a double image (see screen shot below) and the system is not very happy with me when I try and change channels. 

[[IMG]http://img153.imageshack.us/img153/1337/screenshot1pk.th.png[/IMG]](http://img153.imageshack.us/i/screenshot1pk.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by ian dobson on 2010-08-16
Hi,

The double image is a ATI problem. I think there's a fix for it but I can't find the link at the moment.

edit: Thinking about it maybe try configuring a different deinterlacers. Changing your playback profile to 'Slim' should fix the issue.

Regards
Ian Dobson

---

### Post by HudsonHawk04 on 2010-08-16
I am teaching myself as i go, how would one go about changing the play back profile to slim or configuring a different deinterlacers? I am going to have a meeting with my friend "Google" today as well to see if i can figure this out on my own, any other assistance you all could provide would be greatly appreciated.

---

### Post by HudsonHawk04 on 2010-08-16
changed the playback profile to slim and the screen is now one picture, I am however now facing a problem that I assumed would fix itself but has not, I cannot change channels, when I attempt a channel change it kicks me out of the live tv and back to the main menu. Do I need to delete my channel lineup and build a new one. I am pulling my tv info from schedules direct.

---

### Post by tgm4883 on 2010-08-16
Would need to see your backend log. Likely, you switched to a channel that cannot be tuned either because it is too weak, or non-existant.

---

### Post by HudsonHawk04 on 2010-08-16
having a hell of a time pulling my back end logs, i think I will do a complete reinstall tomorrow to hopefully fix the problem.

---

### Post by HudsonHawk04 on 2010-08-17
I did a complete reinstall this morning and purchased a 4 way ampliffied splitter, needless to say I can now change channels with no problem, but when I try to change tuner cards by pressing C on my keyboard I can't change tuners. When I check the system specs there are two tuners listed. 

I am also attempting to us gparted to format a second drive for storage and I am hitting a brick wall, it is giving me a weird message I cant remember it off the top of my head. I will see if i can get it to reproduce. The two hauppauge cards I have both have audio out lines, in order to get sound on the recordings do they need to be plugged into the pc? I only have one audio out on the back and it is connected to my tv, if i need them to be connected would getting a three way splitter work? and finally I have a HDHomerun digital tuner would someone be kind enough to point me in the direction of information to get it setup and working properly. 

Thanks so much guys for all your help, I seem to be learning at a pretty rapid pace hopefully soon I will be able to give back to this community.

I will post a log as soon as possible

---

