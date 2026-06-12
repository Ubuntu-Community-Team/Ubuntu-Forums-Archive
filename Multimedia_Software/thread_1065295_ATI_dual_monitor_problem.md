---
title: "ATI dual monitor problem"
date: 2009-02-09
forum: Multimedia Software
---

### Post by xeddog on 2009-02-09
OK, another thread regarding ATI drivers.  I have looked through this forum and have not found an answer for my problem (At least, one that I can understand).  

So, I was using the driver from the repros for my dual displays.  It was "working" but it sucked.  My primary monitor is a 21' job, and my secondary monitor to the left of this one is a 17".  With these drivers, every application and dialog that was opened were initially displayed on the 17" secondary monitor so I had to move almost every one of them over to the primary display.  If they did not open on the secondary, they would open in the center of the virtual display, or in other words, half on the 17" and half on the 21".  Had to move all of those too.  And of course, the wallpaper was displayed in the center too.  Total pita.

So I went to ATI and downloaded their latest driver package.  It looks like they call it 9.1 but it installs version 8.7 something.  I installed it following the ATI instructions and it was working too.  Better, but not good yet.  Nothing opened up in the center any more, and some applications would open on the primary too, but not all.  And the wallpapers were still screwed.

Now I should have left well enough alone but of course I did not.  I wanted to try Xinerama to see what it was like.  But any time I opened the Catalyst Control Center (CCC) the option for Xinerama was greyed out and I could not enable it.  The only part that was not greyed was a message telling me that I only had one desktop configured.  I tried several things and could not get passed that message.

Then I decided that using the CCC I would configure each monitor as a separate display.  When I selected independant display, the screens went black for a few seconds, came back on, and I had a message asking me if I wanted to apply the change.  When I applied the change and restarted, the computer came back up in low graphics mode and I thought "that can't be good", and it wasn't.  When I tried to launch CCC, I got an error message telling me that the ATI driver was either not installed or not functioning.

I spent the next few hours trying to get it working again and nothing worked.  Then I went to /usr/share/ati and ran the uninstall script and rebooted again.  Computer came up cleanly so I re-installed the 9.1 driver again and rebooted.  CCC came up ok again so I changed the config again using CCC.  I was presented with a message telling me to reboot which I did, but the computer came up in low graphics again.  

That is basically where I am now.  I can remove the drivers, install the new ones and I am ok.  But if I make any changes using CCC and then reboot, the driver crashes and the computer boots to low graphics mode again.  When the computer gets up, the two monitors are cloned to each other, and I can't seem to change it any more.

So I here are my questions.  1) My graphics card is an ATI Radeon 9600 which is a dual head card.  Can a dual head card run each monitor as an independent monitor, or do I have to do something like "big desktop"?  2)  How do I fix my computer so it will use both monitors again?? 

 
TIA,

xeddog

Ubuntu 8.10 32-bit, 1GB ram, 3.0Ghz Intel cpu, Radeon 9600 graphics.

---

### Post by cditty on 2009-02-10
I can't help you with the fix, but I can tell you that you will have to get used to the "big desktop".  My setup is exactly like yours.  My WS is my main and my 17 is email and etc.  The 17's resolution is off and nothing I can find will fix it.  

I don't know if it is a Ubuntu problem or a ATI problem, but it looks like independent monitors under ubuntu isn't possible for ATI 9600s.

---

### Post by xeddog on 2009-02-10
Thanks for the reply.

I think the answer is to go out and buy an nVidia card.  If I remember correctly, Twinview was a lot better than the big desktop in ATI.

I have finally got my two monitors back to a useable state.  All by editing the xorg.conf file, but even that has been a journey to say the least.  At one point I had the big desktop working again the way it originally did.  Then I started trying to get Xinerama working again and . . .well . . .expletives would fit nicely here. 

But the last thing I did was to uninstall all video drivers, reboot, install the lastest ATI driver again like I have done on several occasions.  I even copied the xorg.conf file that was working ok back and then rebooted.  Guess what?  The left monitor came up disabled and the big one on the right came up 640x480.  WTF!?!?!?!  An exact replication of a configuration that was working at one point now all of a sudden does not.  [Insert your favorite EXPLETIVES here]. Took another hour, but I finally managed to get it all back together again.  Don't know how, but I ain't messin with it any more.

xeddog

---

### Post by cditty on 2009-02-10
Yup.  That is the same as what I did.  

I'm thinking about nvidia too, but which one?  Will the one I get be ubuntu compatible?  Will I since another $100 into a card that won't give me anything better than I already have?

---

### Post by xeddog on 2009-02-10
Yeah, I certainly cant give you any advice on that.  I think I might just pop out the vVidia card from my backup machine and try that again.  It's an older 5200 or 6200, don't remember which.  But if I don't like it then I have to go back and try to get this ATI card working again.  I don't really feel like wasting another two or three days doing that.  Besides, that would be a pita.

xeddog

---

