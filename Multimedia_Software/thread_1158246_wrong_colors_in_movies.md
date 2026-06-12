---
title: "wrong colors in movies"
date: 2009-05-13
forum: Multimedia Software
---

### Post by eragon100 on 2009-05-13
Hello :)

I have a nvidia card, a 512 MB GeForce 8 8600 GT, and the latest stable driver from Nvidia. In every movie player I try, all the colors are wrong. The screenshot I attach with this post clearly shows it: the girl doesn't have blue hair, the entire video has far too much blue over all. There is no yellow. It is as if the color values are "shifted" :(

II already did a search on this forum and followed someones suggestion of changing video player hue settings to either min or max levels, but that didn't help either. 

I have to say that it's solved as soon as I open the nvidia settings window, but I don't want to do that every time I play a video (which is quite often, Bleach isn't exactly the only series I watch :D )

Anybody got a clue ??

---

### Post by uhop on 2009-09-24
I have exactly the same problem (wrong order of colors) with Nvida 8800GTS running Karmic. And it is "miraculously cured" by running Nvidia Settings.

Did you find a real solution to this problem?

---

### Post by cor2y on 2009-09-24
Its a bug with totem and nvidia closed source drivers (the open source noveau drivers are not effected by this) the hue settings were reversed and no one told totem about it.
To fix it requires you go into totem's settings and either set the hue settings to the maximum or minimum values and the video should now look like its supposed to.
Strange though nvidia fixed this in their 185 drivers and gnome compensated for the problem by updating their app are you using totem-xine or totem-gstreamer?
I cant recall if it was only totem-gstreamer that was effected and not totem-xine or if both were, its been a few months since i have had this problem ever since i updated to the stable 185 drivers and a semi recent totem build 2.26.3
Jaunty uses 2.26.1 i believe so that should be recent enough.

---

### Post by joris1977 on 2009-10-10
> **cor2y said:**
> I its been a few months since i have had this problem ever since i updated to the stable 185 drivers and a semi recent totem build 2.26.3
Jaunty uses 2.26.1 i believe so that should be recent enough.

Weird that 185 drivers fix the problem for you. I just upgraded from jaunty to karmic and this problem started, because karmic uses the 185 driver Downgrading from 185 to 173 driver fixed the problem for me. I used EnvyNG for downgrading the driver.

I have a

01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)

BTW

---

### Post by kartal on 2009-10-31
After the Karmic I upgrade I have the same problem. Has anyone found a real solution without downgrading driver?

---

### Post by camurgo on 2009-11-06
I have a 9500 GT, and I too started having this problem since upgrading to 9.10.

What **solved it for me** instantly was running *gstreamer-properties* and selecting "X Window System (No Xv)" instead of "Autodetect" for the *Default Output*.

I found about this fix here: [http://www.linuxquestions.org/questions/linux-hardware-18/wrong-colors-w-videos-gforce-8800-gt-675505/](http://www.linuxquestions.org/questions/linux-hardware-18/wrong-colors-w-videos-gforce-8800-gt-675505/)

I suspect that before my upgrade I was using xine instead of gstreamer during and the upgrade that was changed without my explicit consent. But that's alright..

---

### Post by stephanecharette on 2009-11-08
> **kartal said:**
> After the Karmic I upgrade I have the same problem. Has anyone found a real solution without downgrading driver?

Click on:  Application -> Sound & Video -> Movie Player
The click on:  Edit -> Preferences -> Display -> Reset To Defaults

Stéphane

---

### Post by EmilyRose on 2009-11-16
Just a thankyou to stephane! I just ran a video for the first time after upgrading and was immediately like "WTF?!" But that fixed it beatifully:)

---

### Post by weremichael on 2009-11-17
Stéphane,

Your fix worked for me. Another thank you coming your way.

Thanks,

Michael

---

### Post by kosy on 2009-11-18
Thank you, thank you...worked for me as well...

---

### Post by undertakingyou on 2009-11-22
Similarly, if you are having this issue and are using VLC you can fix it by going to TOOLS=>Effects and filters=>Video Effects=>enable and put the Hue slider to the center. Works like a charm. Only bummer, it is only for that VLC session. I'm looking for a more perminant solution.

---

### Post by stephanecharette on 2009-11-22
> **undertakingyou said:**
> Similarly, if you are having this issue and are using VLC you can fix it by going to TOOLS=>Effects and filters=>Video Effects=>enable and put the Hue slider to the center. Works like a charm. Only bummer, it is only for that VLC session. I'm looking for a more perminant solution.

My solution *is* a permanent solution!  You'll only have to do it once.  And I also only use VLC, I don't normally use the Movie Player.  You should try it:

Click on: Application -> Sound & Video -> Movie Player
The click on: Edit -> Preferences -> Display -> Reset To Defaults

Stéphane

---

### Post by jarlz0r on 2010-01-03
> **undertakingyou said:**
> Similarly, if you are having this issue and are using VLC you can fix it by going to TOOLS=>Effects and filters=>Video Effects=>enable and put the Hue slider to the center. Works like a charm. Only bummer, it is only for that VLC session. I'm looking for a more perminant solution.

A permanent solution can be found by modifying the config! 

Open ~/.config/vlc/vlcrc in a text editor.

Search for "video-filter", and set that line to
video-filter=adjust

Search for "hue=", and set that line to
hue=180

neither row should start with a "#". Save and close the file, and vlc should be showing correct colors!


An alternative solution is to supply these options to the command:
vlc --video-filter=adjust --hue=180

---

### Post by sanakan on 2010-01-10
Worked for me as well!

Note: Changing back to defaults in Movie player will effect all other programs you watch films in and solve the problem everywhere. I never use Movie Player but it solved the problem in VLC for me as well, just in case someone's wondering :) Thank youuu!!

---

### Post by WockaNation on 2010-01-21
> **stephanecharette said:**
> Click on:  Application -> Sound & Video -> Movie Player
The click on:  Edit -> Preferences -> Display -> Reset To Defaults

Stéphane

This worked to fix my issue as well, and I have not had a problem since.

---

### Post by pvfloripa on 2010-01-27
Thanks for posting the solution. It also worked for me!

Respect! \m/
:D

---

### Post by Pelgar on 2010-01-29
Does anyone know where  Edit -> Preferences -> Display -> Reset To Defaults has gone to? I'm running Ubuntu 9.10 and there is not a Reset to Defaults there. I've looked in Movie Players help and it says it's there along with some color setting. All I have under the Display Tab is: 
Display
  Auto Resize window.... check box
  Disable Screensave when playing... check box

Visual Effects:
  Show visual effects when... check box
  Type of visualization list box
  visualization size list box.

That is all there is in the Display tab.
I've looked in every tab there and Reset Defaults is not to be found.

I just uninstalled Movie Player, reset, then reinstalled; still no Reset Defaults???

---

### Post by rkeefer on 2010-02-10
Unfortunately, your fix did not/cannot work for me.  All of the people in my movies/videos on Totem look like Na'vi!

For some reason, my version of Totem does NOT have a "restore defaults" button, or anything allowing me to adjust hue, etc.  When I go to Preferences/ Display button, all I see is a "Display" section (with 2 check boxes) and a "Visual Effects" section (which has to do with visual effects for music).

What's my solution?  I just ran
sudo apt-get install totem-gstreamer
and was told my totem is up to date!

(Just installed 9.10; it is fresh).

Any help, thanks.

---

### Post by no2498 on 2010-02-10
try a webcam if you have 1 that used v4l1 it comes up grb not rgb
only 2 programs i can get to change any thing is vlc and cheese
its in the new v4l1 to v4l2 that we use now
i put in a bug report for it
if you videos start running slow look in your usb's
you had a bad unmount of some kind
hope this help some 1

---

### Post by bsergiu on 2010-05-24
This works fine for me :

Start NVIDIA X server settings: **System** -> **Administration** -> **NVIDIA X Server Settings**.

Select **X Server XVideo Settings** . Press the **Reset Hardware Defaults** button.

Make sure the **Hue** value is zero (somehow it got set to -1000 after driver installation). This should help all the video players to display the value correctly. I have checked the following players: VLC, MPlayer, Movie Player, Gnome Subtitle (which starts a movie player as well), Skype (Web camera).

I hope it helps !

Sergiu

---

### Post by bsharet on 2010-06-11
Thanks Sergiu and jarlz0r,

jarlz0r's solution solved it for vlc, but Sergio's solved it for all of them.

---

