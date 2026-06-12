---
title: "surround sound not working in 9.10 ALC883"
date: 2009-10-30
forum: Multimedia Software
---

### Post by PsyWolf on 2009-10-30
stereo output seems to work fine for the most part, but when I go into the sound settings and change my setup to 5.1, all that happens are the front 2 speakers get way too quiet, but there still isn't sound coming out of any of the other speakers.  

It worked fine in 9.04.  All you had to do was go into alsamixer and change the setting from 2 ch to 6 ch.  

in 9.10, it looks like 2ch isn't even and option and changing settings in alsamixer doesn't seem to actually correlate with the settings in the audio preferences.  Anybody have any ideas?

---

### Post by jackmetal on 2009-10-30
I'm having the same problem.  My Front speakers work, but the rest of the 7.1 aren't.   I'm searching around now to see if I can find the issue (I remember in a previous version, I had to manually edit one of the sound files to tell it about all the speakers, but I can't remember what I did - should have taken notes)..  :-(    I'll let you know if I find it.


---edit---
OK, Here's what 'might' help you, (didn't help me, I'm still not getting sound out of my surround, rear or LFE).

1) Edit your "/etc/pulse/daemon.conf" and change the line- "; default-sample-channels = 2" as follows:
Uncomment/remove the ; , then change the channels from 2 to 6 (since you are 5.1).  
2) Then $ pulseaudio -k
3) check your $ alsamixer
4) and do the soundtest :$ speaker-test -c 6.

Hopefully that helps you.

If anyone has any ideas to help me with getting the rest of my 7.1 speakers working, it would be greatly appreciated.  Sometimes I regret upgrading, as it was all working perfectly in jaunty.  :-(

---

### Post by jfsimon1981 on 2009-10-30
Hello All,

Same comment for me, on previous version it was very easy but now I struggle to find out how to configure properly the 5.1. I could use the line input either.

Thanks to help on that matter.

---

### Post by jfsimon1981 on 2009-10-31
Installing GNOME Alsa Mixer (for controlling the different levels) and restarting solved the problem. 5.1 needs to be selected from the default mixer of Ubuntu 9.10

Regards,
JF

---

### Post by PsyWolf on 2009-10-31
that fix didn't work for me.  I'm still only getting sound out of my front 2 speakers even though all my settings in gnome-alsamixer are at max and unmuted.

---

### Post by jackmetal on 2009-11-01
> **PsyWolf said:**
> that fix didn't work for me.  I'm still only getting sound out of my front 2 speakers even though all my settings in gnome-alsamixer are at max and unmuted.

I'm still having that same problem too.  Haven't been able to find a fix yet.  Hopefully some of the audio guru's will catch this thread and give us a little help.  :-)

I've regretted my upgrade since 8.10..  Back then "Everything" worked and I didn't have the Remote Desktop/Compiz issue (which STILL isn't resolved in 9.10) and these sound issues.  If I can resolve those two things, I'll be very happy with the new version.  It's all 'standard' hardware from HP systems, so I'm surprised about the issues.

---

### Post by qepsilonp on 2009-11-03
I dunno if this would help because you probably tried doing it and i was being retarded but if your using alsamixer theres a buttons under the bar contols called Sync which now i know means mute i guess because when i pressed the right once it un-muted the surround and fount... yeah i know retarted right but why label them Sync rather than Mute and yes i do have to have it spelled out to me but the rest of you used alsamixer before so you probably didnt make the same mistake... just thought it could be that so... what ever if it doesn't help then i have only make my self look like an idiot fount of a few people i will probably never meet

---

### Post by PsyWolf on 2009-11-05
I tried the fix that Jackmetal put into his first post and it doesn't help either.  And thanks for the suggestion qepsilonp.  I've made more stupid mistakes than in the past.  In this case however, I am certain that none of my channels are muted.


Someone please help.  As it stands, my nice 5.1 speakers have less bass than a crappy set of 2.1s.  This is unacceptable.  I don't want to have to downgrade just to have bass.

---

### Post by jackmetal on 2009-11-06
Hey PsyWolf, I'm still in the same boat as you. :-(  I wish you all the luck in the world in getting your issue resolved!  I've actually grown tired of having to fight to get everything working after every single ubuntu release and I'm moving all of my systems back to a combination of PCLinuxOS and ArchLinux.  These last 2 releases have not been up to par!  There's a known fix for the Remote Desktop/Compiz bug and yet they never applied it in Jaunty and didn't apply it in Karmic either.  There are some w32codec issues now, VLC issues, these Sound Issues pop up after every release; jeez....I just want to get back to having normal, working systems again. LOL   You would think these types of things wouldn't be an issue in a well developed distro like ubuntu..  I mean, all of my hardware is "standard" off the shelf (typical vendor built systems): HP, Toshiba, Dell, etc..  

I really don't mean to come off sounding like I'm busting on ubuntu.  I am very thankful and grateful for any and all distributions and the hard work that goes on behind the scenes that everyone is doing for "free"!  Ubuntu (and all other releases) have a daunting task, and for the most part, they pull it off quite well.  I just miss the stability I had on some of the other distributions and not having to upgrade every 6 months, etc...

So, I guess I've got a few laptops, desktops, media centers, netbooks and ultra mobiles to rebuild: Not the way I would typically want to spend my weekend when there will be some good MMA on TV.  ;-)

---

### Post by PsyWolf on 2009-11-07
well jackmetal, you could stick to the LTS releases, but i'm the type of person that likes to be on the cutting edge.  I don't mind a few crashes or apps that don't quite work right, but i do kindof require my hardware to function correctly.

You would think that they could at least implement a way keep with the older sound server if they knew that the upgrade was going to break this many systems.  I'm sure that it isn't that simple, or they probably would have done it, but there has to be a better medium between cutting edge and completely stable.

---

### Post by PsyWolf on 2009-12-10
I still haven't gotten it working yet, but I've seen that alot of people have with the info on this page, so i figured i'd pass it along

[http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)

let me know if you guys have any luck

---

### Post by AlienUFO on 2009-12-11
I have found a fix, or well for me it works (I had the same problem).

Okay, so basically follow these steps: ;)

Go to Terminal and enter:

```
$ sudo gedit /etc/pulse/daemon.conf
```

Then go to:

```
; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right
```

And replace it with:

```
default-sample-format = s16le
default-sample-rate = 44100
default-sample-channels = 6
default-channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe

```

Hope it works. :popcorn:

---

### Post by AlienUFO on 2009-12-12
@jackmetal:

I think you can basically just change:

```
; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right
```

To:

```
default-sample-format = s16le
default-sample-rate = 44100
default-sample-channels = 8
default-channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right
```

Hope it works.:D

---

### Post by AlienUFO on 2009-12-15
I have found this HOWTO, if my method above doesn't work. [http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

---

### Post by EagleDM on 2010-01-09
No need to go into edit files.

Just change the sound setup in Sound Preferences to the "max" Channels your soundcard support and Just use the channels you have.

For example, my X-Fi Titanium supports 7.1,  even when I have 5.1 I setup 7.1 for pulse and Mixing is correct, otherwise no other option works correctly.

Give it a try.

---

### Post by jackmetal on 2010-01-10
Thanks, but yeah, I had tried that.  I have a 7.1 configuration and I had it set to 7.1.  I even tried 5.1 just for the heck of it, but no matter what I had it set to, sound only came out of my front speakers (Although it worked perfectly fine before the move from 8.10 to 9.04 and 9.10 - I should have just stuck with 8.10.. :-) ).  I ended up moving that server to ArchLinux though, and all is working perfectly.  It's really weird as Ubuntu has always had some strange sound issues on varied systems.  Like this one which is a digital fiber connection to the receiver; so maybe there are some Ubuntu hick-ups with that. ?  Anyway, thanks a lot for trying, but like I said, this one is now on Arch and running faster and better than ever so I'll stick with that.  I used to use Arch exclusively, a few years ago, so it's actually good to get back to it as I had only left it to play around with Ubuntu when it was getting to be really big.. :-)

I still have Ubuntu on a few systems, but moved the majority of them back to Arch.

---

