---
title: "Audio not working in Amarok or Rhythmbox"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by fordp on 2008-02-09
Well I have been using Ubuntu since the first version. I kicked Windows off years ago as it was wasting disk space ;)

I have a guest login on my machine and I noticed that that log in could see all the files in my home directory.

I thought no problem I will change the permissions on every thing in my home directory and all will be well.

That was a big mistake. I could not even log in to Gnome on my next Reboot. I got round that with a bit of command line hacking, as I said above I have been using Linux for years.

My machine is an Old NForce Athlon XP Based system with on board graphics and Sound Storm audio. This should be pretty good hardware sound wise but as others will know you have to use the open source drivers and not use the hardware to it's full or install NVidia drivers (compiled from source) and you end up using the hardware but having to use the older OSS drivers.

Well getting to the point after I changed the file permissions on my home folder I thought Audio was totally broke. I have found out recently that it is not and gxine actually works fine both in video and audio.

My favorite audio application is Amarok and that does not start these days and has the problem as in this post [http://ubuntuforums.org/showthread.php?t=232682](http://ubuntuforums.org/showthread.php?t=232682)

I have searched this forum and tried all the suggestions all to no avail. I even looked at the hidden Amarok related configuration files in my home directory and deleted them but nothing seems to bring it back to life.

I tend to do a clean install once a year after the spring release so I thought I would just use Rhythmbox for the next few months. I have used it before and it is OK, no where near as good as Amarok but usable.

When I play tracks on Rhythmbox all I get is noise out of my speakers. Not hiss you understand but loud random noise.

My computer is connected to my Amp using a Optical Spdif connection by the way.

Sorry for the long post but I was just wondering if anybody had any ideas how to get a decent music player working on my machine again.

All the best fellow Ubuntu users :).

---

### Post by fordp on 2008-04-25
Well I persevered in the hope that 8.04 would fix my problems, which I still have.

I do have more information however.

When I installed 8.04 I got audio from my analog connections of my computer fine. I have my headphones plugged in there. A Rhythmbox actually worked. Yay !

My NForce Sound Storm system has never worked well on Open Source drivers (NVidia's fault). I therefore installed the closed source NVidia Soundstorm drivers using this page as a guide :-

[http://ubuntuforums.org/showthread.php?t=253725&highlight=nvnet](http://ubuntuforums.org/showthread.php?t=253725&highlight=nvnet)

It is quite a lot of work but works well. I have done this on every version of Ubuntu so far.

I then went to the Sound configuration and select everything as OSS.

I am then back to exactly the same problem as the last version with Random data being passed out of SPDIF making very loud noise through my powerful Mission 737R speakers :(

So it seems Rhtthmbox does not work through OSS for me.

Amarok stopped working when I change the permissions for some files in my profile (well most of the files actually). I just cannot seem to get it back working.

Xine works fine.

I logged into Kubuntu and the whole thing is stuffed with lots of errors coming up and nothing in the programs menu.

I am away from my machine right now I will report later.

When I get it working I will report the fixes so others can learn from my issues.

Cheers.

---

### Post by fordp on 2008-04-25
Wow I have fixed [B]Rhythmbox.

I siwtched on cross fading in Edit->Playback->use cros[/B][B] fading  backend (requires restart).

I then restarted the app and now it works.

Yes.

I will try and fix Amarok next.
[/B]

---

