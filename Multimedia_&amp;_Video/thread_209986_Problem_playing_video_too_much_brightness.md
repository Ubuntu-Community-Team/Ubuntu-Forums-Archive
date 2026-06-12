---
title: "Problem playing video: too much brightness"
date: 2006-07-06
forum: Multimedia &amp; Video
---

### Post by fledylids on 2006-07-06
I have an Intel video card using the i810 driver and when I play things back using xv, the brightness and contrast are way too high even though the media players are set to defaults. This occurs in every media player I try (totem, gxine, and mplayer, regardless of format (any type of video file at all, or playing a DVD). Using any other video mode (i.e. gl) fixes this, but that limits my ability to do fullscreen or other things. What's the problem, how can I fix it?

Note that when I try to adjust the brightness/contrast/other stuff manually, I can't seem to get them to a combination that would feasibly "fix" the problem (if such a thing is possible).

---

### Post by H.E. Pennypacker on 2006-07-08
I was going to advice that you manually fix the problem, but I see you've already done that.  Trust me, if I knew of an automatic solution, I wouldn't be having the same problem either.  It's a real pain to do it manually, because you just can't do it perfectly like a computer can.  I'd be really nice to just watch a video, and not have to mess around with brightness.

Let me know if you ever find a solution.

---

### Post by cweinman on 2006-08-27
anyone have a solution for this, I too have a similar problem.

---

### Post by theadventuresofanidealist on 2006-08-28
same problem here

---

### Post by kairu0 on 2006-08-29
I've always had this problem in Xine but never in Mplayer or VLC. I use XV, too, and I have the 915 chipset, by the way.

Not much to say; just trying to narrow this all down

---

### Post by mordox on 2006-09-09
i had the same problem too 

i tried changing the gamma value using xgamma but that didnt help

I checked up /etc/X11/xorg.conf

WOlla.. I found out that the default depth was set at 16 ... i need 24 ... changed that. 

Now all the video plays just fine.

:KS My /etc/X11/xorg.conf is attached

---

### Post by siggisiggibangbang on 2006-11-23
This is not a solution to this problem.  It may be ok after you restart X.  But, when you cold start you computer the problem will reappear.  This seems to be a problem related to the XV driver.

---

### Post by indeterminate on 2007-03-04
I have this problem too.

Restarting X does fix it temporarily, but after 1 video has been played and the player is closed, the next video I open is too bright again. Restarting X every time you want to watch a video gets old pretty fast.

edit: This problem is present in xine, mplayer and VLC. Well, like siggi said, it's a problem with the xv driver. I can change the video output on VLC to something else, and the problem goes away, but other video modes are more buggy or lower quality (no anti-aliasing).

---

### Post by whayong on 2007-03-06
Yikes!  I was hoping there was a fix to this.  I've got the same problem and thought VLC would do the trick, so I was going to try it later but I guess not.

Is there any more info on this?

---

### Post by silkstone on 2007-03-12
Same problem here - using Intel on-board graphics - video replay far too bright and highlights burnt out with most applications. BUT... Real Player works fine and doesn't have this problem.

---

### Post by velo on 2007-03-27
Got the same Problem on Edgy with totem (which I do not use) and vlc - the picture is just too bright or it has got too much alpha. 
The Card I am using is an Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)


**However**: I found out that when displaying two videos at the same time, only the first one gets all brightened up. So I made a quick shell script to just open the file in vlc twice and kill the first one after 3 seconds:

```
#!/bin/bash
vlc $1 &
pid=$!
vlc $1 &
sleep 3 && kill $pid
```

(don't forget to chmod +x)

Then I just told gnome to open my video files with the script (via rightclick on an avi file -> properties -> open with). Kinda works for me - you might want to change the number of seconds if the first vlc instance is killed before the second one starts to play. 

That is, if the "open twice trick" works for your configuration to begin with.

I hope this helps anyone.

---

### Post by Laen on 2007-03-28
Thanks, velo, that's perfect. Good observation too!

Otherwise, just for the record, I'm also using the i810 driver and get the excessive brightness with each video player. Hopefully this is fixed soon.

---

### Post by velo on 2007-04-01
Thanks for the kind words ;)
I'm glad this helped someone but myself. 
It's not a perfect workaround (but which workaround is), especially because opening vlc two times takes a bit longer - if anyone has got a better idea: please, please share.

for some people, the bug (if it's the same?) seems to be fixed in feisty: [https://launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/32963]("https://launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/32963")

I'm keeping my fingers crossed (since I'm not going to install a pre-final feisty on my girlfriend's laptop just to test stuff :) )

---

### Post by icemanblues on 2007-04-05
Just to keep this thread fresh.  I also have this problem, running on a Dell Inspiron E1505 with the i945 chipset.

Velo's script works like magic!  It'll do until Feisty. Thanks!

---

### Post by meist3r on 2007-04-10
I've got the same problem on my Lenovo Thinkpad R60 running Edgy.

---

### Post by meist3r on 2007-04-11
It seems the problems stems from the totem video player gui which sets the XV_CONTRAST variable too high. The default is 64 and it puts it to 126 or something (that's what I found on launchpad). There is an "easier" workaround (definitely less annoying than a second video window for 3 seconds) than the script proposed earlier.

Get the 'xvattr' package from the repositories. Then open a terminal and do:

```
xvattr -a XV_CONTRAST -v 64
```

to reset the contrast to the regular default of 64. This should make your picture look normal again. Usually you will have to do this once but when totem resets the value obviously you will have to do it again. Works fine for me.
Because I don't exactly know under which circumstances totem sets the false value for XV_CONTRAST I can't tell you how often you'll need it but I went with using VLC for ALL videos and so totem will never be opened anyhow.

Let me know if that worked out for you.

Links:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/32963](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/32963)
[https://launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/32963/comments/84](https://launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/32963/comments/84)

---

### Post by sudo-fu on 2007-04-12
thanks meist3r, this worked fine. but it looks like totem is resetting the value everytime i start it...

---

### Post by benjaminzsj on 2007-04-15
I'm using Feisty, this problem still exists but not in VLC.

---

### Post by soro2005 on 2007-04-18
Same here, with Feisty. Looks like opening Totem Movie Player and manually moving the slider for "Contrast" in preferences a little throws totem off its sinister contrast skewing routine. Since I'm playing with that setting, the other players using xv seem to be able to set their own (correct) values for contrast. But I haven't reinitiated my X session yet.

*Edited: Well, gxine also seems to set the contrast value to 128, without resetting it to 64 after terminating*

---

### Post by Rick123 on 2007-05-15
Hi i got the same problem, have tryed all media players out there all are to bright, so i could accept that i then needed to make the contrast and brightness less, but when i stream videos from internet with media player i cant changes the brightness, or dont know how to do. so what is the finale solution on this problem? I use the new ubuntu fiesty or what the name is.
I am a real noob at this things, so for me the only solution to fix this problem if someone take me step to step how to fix it, the only thing i can do is open the terminal and copy text to it. :) 
So if its not any solution i hope Ubuntu developers working on it, i think the hole system how to instal codecs and mediaplayers need to be made even easier then it is now, because its one of the most important things noobs like me do, stream and  surf internet, i had just luck, the codecs and media playsers worked, first time i tryed to install it it dint, so i ended up intaling fiesty again :( 

So anyway, i hope we can work something up cheers. thumbs up
:guitar:

---

### Post by soro2005 on 2007-05-15
Solution: Do as [described in this post above]("http://ubuntuforums.org/showpost.php?p=2437462&postcount=16"), then open your Totem --> Preferences --> Display and crank down the "Contrast" setting to about a quarter of the full scale to prevent Totem from resetting the contrast to its skewed default. Not sure this works on Edgy, though, and there might be other video players which also screw up the contrast setting. Try to identify the culprit by resetting contrast and playing a video in each of the players, one by one.

"Get xvattr package from repository" translates as:
```
sudo apt-get install xvattr
```
in a terminal. But that much you might have learned already. :-)

---

### Post by srt4play on 2007-05-16
The "video brightness bug" just bit me, but only because I installed gxine to give it a test run.  All my other players (xine, mplayer, vlc) do fine but gxine turned on the brightness.

---

### Post by mjukis on 2007-07-12
I have this problem too. I'm running Fiesty. The problem occours both in VLC and Kaffeine.

The trick mentioned earlier in this thread, starting a second instance of VLC, works but is no solution. Anyone have any better solution for this problem?

---

### Post by ev5unleash1 on 2007-08-03
I have the problem but none of the solutions above help me out. This started happening when I installed pacific things to make DVDs play. I'm not sure if that has anything to do with it.

---

### Post by jalanbuntu on 2007-09-13
Actually for totem you can set its xv contrast value through the gconf-editor at

/apps/totem --> contrast

For my laptop, I set its value to 16400 (for about half of the default value)
It will be set the contrast just like using the "xvattr -a XV_CONTRAST -v 64" command.

---

### Post by flamacue on 2007-12-10
Appears to be [_[COLOR="Navy"]this bug[/COLOR]_]("https://launchpad.net/ubuntu/+source/xserver-xorg-driver-i810/+bug/32963/+index").

I believe there are some thoughts for workarounds in the comments/discussion in the meantime, but I don't have time to sort through them atm...

---

### Post by asnd16 on 2008-03-23
> **meist3r said:**
> It seems the problems stems from the totem video player gui which sets the XV_CONTRAST variable too high. The default is 64 and it puts it to 126 or something (that's what I found on launchpad). There is an "easier" workaround (definitely less annoying than a second video window for 3 seconds) than the script proposed earlier.

Get the 'xvattr' package from the repositories. Then open a terminal and do:

```
xvattr -a XV_CONTRAST -v 64
```

to reset the contrast to the regular default of 64. This should make your picture look normal again. Usually you will have to do this once but when totem resets the value obviously you will have to do it again. Works fine for me.
Because I don't exactly know under which circumstances totem sets the false value for XV_CONTRAST I can't tell you how often you'll need it but I went with using VLC for ALL videos and so totem will never be opened anyhow.

Let me know if that worked out for you.

Links:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/32963](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/32963)
[https://launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/32963/comments/84](https://launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/32963/comments/84)

This seemed to work fine for me , although I had to install xvatter out of the package manager. :lolflag:

---

### Post by Blingin2Mingin on 2008-04-03
I've suffered this problem too, It seems to be Totem Xine that causes it. My memory is so poor I can never remember the syntax and values without looking them up so I've now refined the cure to single click.
I installed xvattr as described above. Then I created a text file  and placed my desired xvattr values in it, saved it and named it xvattr.sh then I made it executable. (Thunar lets you do this from properties tab). All I did then was add a custom application launcher to the Gnome panel that then calls the script.
So now when any xv display values get corrupted a single click puts it right instantly.

Just for reference I'll post the contents of my xvattr.sh.  (These values are right for my laptop 17" wxga Truelife   monitor) your mileage may vary. Hope this is of help to someone.

xvattr -a XV_BRIGHTNESS -v -23

xvattr -a XV_CONTRAST -v 60

xvattr -a XV_SATURATION -v 128

xvattr -a XV_PIPE -v -1

xvattr -a XV_GAMMA0 -v 526344

xvattr -a XV_GAMMA1 -v 1052688

xvattr -a XV_GAMMA2 -v 2105376

xvattr -a XV_GAMMA3 -v 4210752

xvattr -a XV_GAMMA4 -v 8421504

xvattr -a XV_GAMMA5 -v 12632256

---

