---
title: "Dapper Color..very poor"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by hellmet on 2006-06-04
Just upgraded to Dapper.
The first thing I noticed is that the Colors are not at all natural.
Every Color seems to be Reddish..and very High Gamma'ad
I noticed this only for Videos and TV.
Colors on the Desktop(GUI) are fine.
My monitor wasn't recognised properly by Xserver....
it was fine in Breezy.
Is it a bug or something??
I've got 915GAV mobo.

---

### Post by hellmet on 2006-06-04
the correct way to put it wud be..that the colors are BLEEDING.
Is it a problem with the codecs??
What do I d o now?

---

### Post by skinnygmg on 2006-06-04
any other dapper users seeing  this?

---

### Post by net_benjo on 2006-06-04
I am having the same problem.  I'm running Dapper on HP Pavillion dv4000 laptop which has onboard graphics.  I didn't have problems watching videos in Breezy, but in Dapper video colors look bad.  It looks like a problem with too much gamma or something like that...

Other than for videos, colors look great.  Is this issue specific to some graphics cards or is it general?

---

### Post by Lord Illidan on 2006-06-04
[quote=net_benjo]I am having the same problem.  I'm running Dapper on HP Pavillion dv4000 laptop which has onboard graphics.  I didn't have problems watching videos in Breezy, but in Dapper video colors look bad.  It looks like a problem with too much gamma or something like that...

Other than for videos, colors look great.  Is this issue specific to some graphics cards or is it general?[/quote]

I usually change the video output to opengl. Try it with xine, it is easier to do.

Change yourself to Master of the Universe ( I like it, hehe), and then go to video tab, and change to gl.

---

### Post by hellmet on 2006-06-04
Dude..
could you explain what u talked about above there??
Didn't understand..

---

### Post by mrvw0169 on 2006-06-11
Wow, I have the EXACT same problem. Though it only appeared after I got laptop back from warranty service from Dell and after dist-upgrading to final Dapper. Everything was working fine before that (was using Dapper since the Flights)...

But now the colors are so horrible - all bright, or washed out colors; the worst being movies in totem-xine where it's totally white/bright. I thought maybe it was Dell's fault in manhandling my laptop so I sent it back to get my LCD replaced - we'll see how that goes once I get it back Monday.

---

### Post by hellmet on 2006-06-11
Do let us know..
well I have also filed a bug for it..
dunno what'll happen...:sigh
Well I downgraded to Breezy again..
those colors made me feel sick...
even things around me felt like they were in Dapper
till a few days..
I'll stick with breezy till the next Ubuntu release.

---

### Post by mrvw0169 on 2006-06-13
I HATE the auto logoff feature of the forums... This is my 3rd time typing this...

I'm glad to say everything looks nice now, but it involved a dist-upgrade first... The reason for this seems to be with this bug, as it seems a patch was submitted while my laptop was gone: [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/32963](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/32963)

What Lord Illidan was saying depends on your video player (sounds like he was using gxine from the "Master of the Universe" bit)... But if you are using the totem (gstreamer) that is included in Dapper, you can try to run gstreamer-properties and change the output driver under the Video tab (to gl, x11/xshm, xv, etc)... If you are using another player, it's typically under Edit>Preferences/Settings>Video...

Hope you try Dapper again soon... It's much better and pulled me from ArchLinux...

---

### Post by lnicolao on 2006-06-20
[QUOTE=Lord Illidan]I usually change the video output to opengl. Try it with xine, it is easier to do.

Change yourself to Master of the Universe ( I like it, hehe), and then go to video tab, and change to gl.[/QUOTE]

I was having the same problem with my Toshiba laptop (Intel Integrated Graphics). Colors were awful when playing embedded quicktime videos in FireFox (MPlayer plugin, but same thing with Totem). I changed  the output to opengl in each player and everything works fine. Thanks Lord Illidan.

---

### Post by hjt4vdr on 2006-08-10
hi,

i have the same problem and an workaround for ubuntu dapper, but isn't fine.

apt-get install xserver-xorg-driver-i810=1:1.4.1.3-0ubuntu6
then restart (X), Ctrl+Alt+BS

this version works fine.
the new version in dapper (1:1.5.0.1-0ubuntu2) is buggy, update yesterday (09. Aug. 2006), i must go back to xserver-xorg-driver-i810=1:1.4.1.3-0ubuntu6

i hope someone find a better way

bye
Horst

---

### Post by mrvw0169 on 2006-08-10
Something is very wrong in the last few updates that is causing incorrect color balance settings (contrast waaay too high) when viewing movies only when using Xv (via totem, mplayer, vlc, gxine)... It wasn't like this say, last week... Anyone have a clue why? I have to manually set contrast down half way just to make videos watchable...

I really just want to use Xv since it gives me the best performance/quality (X11 is just awful) and opengl doesn't work nice for me though they do not suffer the color issue...

---

### Post by hellmet on 2006-08-11
are u having to do this everytime you play a video??
or after every restart of the computer??

---

### Post by mrvw0169 on 2006-08-11
I'm sure that every restart it will lose the contrast/brightness settings, and *most* of the times when I'm playing videos (there are some rare instances where it will remember the settings but will only get reset again on the next run)

---

