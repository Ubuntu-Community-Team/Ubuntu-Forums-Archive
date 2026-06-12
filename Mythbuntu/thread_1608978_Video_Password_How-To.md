---
title: "Video Password How-To"
date: 2010-10-29
forum: Mythbuntu
---

### Post by elgordo123 on 2010-10-29
I finally came up with a workable solution to prompt for a password before it plays a video.   The built-in parental controls/levels are fine, but in some cases not practical. 

I am not a programmer. It might not be the best way, but it works for me.  I couldn't find anything that would do this so I had to hack together something for myself. 

When you select a certain video it will open a small xterm window in the middle of the screen.  You use your remote to enter in a password.  If it matches it will open the video in vlc (with LIRC enabled), if not, or when the video finished/exited it will go back to the video list. 


1- Create a lirc entry for irpty 
cd /home/youname/.lirc/
nano irpty (or whatever you want to name it) 
use this code: 
```
begin
    remote = hauppauge_pvr
    prog = irpty
    button = Ok
    config = \r\n
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = irpty
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = irpty
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = irpty
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = irpty
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = irpty
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = irpty
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = irpty
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = irpty
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = irpty
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = irpty
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

```

2- edit /home/yourname/.lircrc and add a line to include that file (like the others but with ipty at the end) 

3- Create a new file "vidpwd1.sh" in your home directory with this code.   This will "hardcode" your password of 1234 and launch your video using vlc with LIRC enabled.  (You'll have to setup create/setup your own vlc lirc file). 
```
#!/bin/bash 
echo "Enter password:" 
read vMyCode
echo $vMyCode
if [ $vMyCode == "1234" ];  then 
vlc -I lirc /var/lib/mythtv/videos/IronMan.mp4 
exit
fi 
exit
```

4- Final step, in each video that you want to use this password, go into the metadata and in "Unique Player Command" put in this: 
```
xterm -geometry 50x10 -e irpty /home/yourname/.lirc/irpty -- /home/yourname/vidpwd1.sh
```

You will have to create a new "vidpwdX.sh" file for each video, and of course change the video name and player command. 

If you are curious about vlc, you just have to add a new file, vlc to the /home/yourname/.lirc folder and also add an include entry in your /home/yourname/lircrc  file.  
Here is mine: 
```
begin
    remote = hauppauge_pvr
    prog = vlc
    button = Go
    config = key-audio-track
    repeat = 0
    delay = 0
end

begin 
    remote = hauppauge_pvr
    prog = vlc 
    button = Back/Exit
    config = key-quit
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Ch+
    config = key-nav-up
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Ch-
    config = key-nav-down
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Vol-
    config = key-nav-left
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Vol+
    config = key-nav-right
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Ok
    config = key-nav-activate
    repeat = 0
    delay = 0
end

begin 
    remote = hauppauge_pvr
    prog = vlc
    button = Yellow
    config = key-vol-down
    repeat = 0
    delay = 0
end

begin 
   remote = hauppauge_pvr
   prog = vlc
   button = Blue
   config = key-vol-up
   repeat = 0
   delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Mute
    config = key-vol-mute
    repeat = 0
    delay = 0
end

begin 
   remote = hauppauge_pvr
   prog = vlc
   button = Blank
   config = key-toggle-fullscreen
   repeat = 0
   delay = 0
end

begin
   remote = hauppauge_pvr
   prog = vlc
   button = Full
   config = key-subtitle-track
   repeat = 0
   delay = 0
end
    
begin
    remote = hauppauge_pvr
    prog = vlc
    button = Rewind
    config = key-jump-extrashort
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Play
    config = key-frame-next
    repeat = 0
    delay = 0
end

begin 
   remote = hauppauge_pvr
   prog = vlc
   button = Pause
   config = key-play-pause
   repeat = 0
   delay = 0
end 

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Forward
    config = key-jump+extrashort
    repeat = 0
    delay = 0
end

#begin
#    remote = hauppauge_pvr
#    prog = vlc
#    button = Stop
#    config = key-quit
#    repeat = 0
#    delay = 0
#end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Replay
    config = key-jump-short
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Skip
    config = key-jump+medium
    repeat = 0
    delay = 0
end

```

..Enjoy!..
:guitar:

---

### Post by tgm4883 on 2010-10-29
nice, although this will fail to work when external players are no longer supported. Why didn't parental controls work? Or setting them as hidden?

---

### Post by elgordo123 on 2010-10-30
If mythtv locks things down like external players and becomes more closed then I might as well use any other locked down closed platform.  I don't see that happening if it does goodbye mythtv.

---

### Post by tgm4883 on 2010-10-30
> **elgordo123 said:**
> If mythtv locks things down like external players and becomes more closed then I might as well use any other locked down closed platform.  I don't see that happening if it does goodbye mythtv.

It's not locking down, it's moving to a new feature called storage groups. None of the main mythtv devs use external players so the new code that is being written for storage groups doesn't included external player support. You can use closed platforms if you want, but in my research MythTV still does far more than they do. Threatening to not use MythTV is hardly going to get external player support added.

Oh, and it is happening. Unless someone steps up and codes the portion for external players.

---

### Post by nickrout on 2010-10-30
> **tgm4883 said:**
> It's not locking down, it's moving to a new feature called storage groups. None of the main mythtv devs use external players so the new code that is being written for storage groups doesn't included external player support. You can use closed platforms if you want, but in my research MythTV still does far more than they do. Threatening to not use MythTV is hardly going to get external player support added.

Oh, and it is happening. Unless someone steps up and codes the portion for external players.

Not on my reading of the mailing list archives. As i read it (and it may have changed again) there will still be an option for an external player. One external player, so if you want to choose based on, eg, file extension, you will have to use a wrapper script.

---

### Post by tgm4883 on 2010-10-30
> **nickrout said:**
> Not on my reading of the mailing list archives. As i read it (and it may have changed again) there will still be an option for an external player. One external player, so if you want to choose based on, eg, file extension, you will have to use a wrapper script.

Hmm, perhaps. So they are now able to provide the file to other players via storage groups?

---

### Post by nickrout on 2010-10-30
All I know is what i read here:

[http://www.gossamer-threads.com/lists/mythtv/users/436989#436989](http://www.gossamer-threads.com/lists/mythtv/users/436989#436989)

---

### Post by iamlindoro on 2010-10-30
I am the sole MythVideo maintainer.  We do not have any manner of feeding storage group content to external players at the moment.  Future versions of MythVideo will use storage groups exclusively.  

Unless someone writes code to teach external players to use storage groups that is *not* a hack (ie, no fuse filesystems or other ugliness) then the ability to use external players will disappear at that time.  Even *if* such a thing is done, the ability to associate a specific extension with an external player is going away for sure.  When MythVideo is Storage Group only, the only potential option to use one will be an option in the context menu to invoke a single fallback player for the selected item.  And, as mentioned above, that's not happening if I'm left to my own devices.

---

### Post by elgordo123 on 2010-10-31
Wow. What was the reasoning not to include external players?   What happens if for some reason we run into a video that isn't compatible?  I have run into quite a few times where audio sync for example is off in one player (and adjusting don't work) but fine in another. 
One of the great things about myth was being so open and configurable.  However I haven't seen or used the latest (or future) internal player, so if it works on almost everything that is awesome.
I know the devs put a lot of love and thought into these things.   No one would work hundreds of hours for free and not put a lot of thought into it.    Big changes like that are scary, but we haven't been let down yet!
Thanks for comments.

---

### Post by tgm4883 on 2010-10-31
> **elgordo123 said:**
> Wow. What was the reasoning not to include external players?   What happens if for some reason we run into a video that isn't compatible?  I have run into quite a few times where audio sync for example is off in one player (and adjusting don't work) but fine in another. 
One of the great things about myth was being so open and configurable.  However I haven't seen or used the latest (or future) internal player, so if it works on almost everything that is awesome.
I know the devs put a lot of love and thought into these things.   No one would work hundreds of hours for free and not put a lot of thought into it.    Big changes like that are scary, but we haven't been let down yet!
Thanks for comments.

It's disappearing because the only person that writes code for mythvideo doesn't use external players, therefor has no reason/time to add code to get it to work. If someone else comes along and is able to add the code for that then it should go in, providing it isn't a hack.

---

### Post by iamlindoro on 2010-10-31
> **tgm4883 said:**
> It's disappearing because the only person that writes code for mythvideo doesn't use external players, therefor has no reason/time to add code to get it to work. If someone else comes along and is able to add the code for that then it should go in, providing it isn't a hack.

In fairness to all involved, it's not *quite* as cut and dry as that (though there's a certain element of this that's true too).  I maintain a lot of code in MythVideo that I don't use-- I've even written quite a lot of features in MythVideo that I never use, simply because I saw a reasonable use-case.

Let me put it in a different way.  If MythTV was producing recordings that it couldn't play, or if you had a music file that MythMusic choked on, you'd submit a sample and bug about that particular file and ultimately, we would fix it.  If you have a file that Myth's internal player does not play properly, we really, really need you to open a ticket.  When .24 is released, probably on the 8th of November, people really owe it to themselves to use the Internal player exclusively, at least for a short period of time.  I realize that for some, the breaking of muscle memories may be the hardest part of this.  You've used mplayer/xine/vlc/whatever for years and there may be some getting used to doing the same things in the Internal Player.  Then again, many of the functions you expect may just need you to go bind keys on your remote to them.  Come to the mythtv-users mailing list and we will *happily* help make the changes necessary to your configuration files to have the same experience.  Better still, using the internal player with video content will present a unified and attractive OSD interface that matches the one you're using for recordings.  If you're not able to find a binding for something (though this would be a surprise), nearly all of our player functionality is available from the OSD menu (MENU when in playback) and that's a WAF++ in anyone's book.  If you want things bound to remote keys instead, it's all there for the taking, it might just take you a half hour of tinkering to get the same results.

Even in this last release cycle, the Internal player has come a mind boggling distance, and now supports just about anything you can throw at it as well as any external player.  Add to that the fact that DVD playback has been nearly rewritten, the OSD and video playback has been completely refactored for stability and ease of maintenance, and support for multiple new hardware acceleration interfaces, and (shameless plug) the fact that I wrote initial support for Blu-ray BDMV/dics playback, and there is less reason than ever to use an external player.

MythVideo has some legacy cruft holding back moving in a simple and easy to use direction, and the biggest part of that is the fact that I am forced to write and maintain large portions of code to account for a local file path (required by external players) as well as Myth's very nice internal streaming interface (currently "spoken" only by the Internal player, commonly known as the myth:// protocol or Storage Groups).  There is no clear path to move forward with using only our streaming interface (as we do for recordings) while still supporting external players, and there are a ton of good reasons to use them, but the obvious wins are the fact that adding a new frontend requires *no* configuration of the nice, shared video library, metadata library, image library, and everything else shared via SG, and the fact that you can spread your storage around as many backends as you like without RAID and without ever configuring any sort of network mounts.  The more complicated your setup is backendwise, the more Storage Groups make sense.  We will also be able to move forward with making the uPnP player use the streaming interface and provide a single shared uPnP library of your entire Myth media.  It's neat and it's a direction we really want to go.

I hope this helps people understand why the small perceived sacrifice leads to greater wins in the end.  If you have *any* file which does not play properly on the Internal player found in .24/trunk, please open a ticket with a sample that shows the issue, as well as logs with the -v playback option ("mythfrontend -v playback" from a terminal) and we will fix it.  But I suspect that most people who have long since abandoned the internal player will be majorly surprised, if not awed.

Robert

---

### Post by nickrout on 2010-11-01
> **iamlindoro said:**
> I am the sole MythVideo maintainer.  We do not have any manner of feeding storage group content to external players at the moment.  Future versions of MythVideo will use storage groups exclusively.  

Unless someone writes code to teach external players to use storage groups that is *not* a hack (ie, no fuse filesystems or other ugliness) then the ability to use external players will disappear at that time.  Even *if* such a thing is done, the ability to associate a specific extension with an external player is going away for sure.  When MythVideo is Storage Group only, the only potential option to use one will be an option in the context menu to invoke a single fallback player for the selected item.  And, as mentioned above, that's not happening if I'm left to my own devices.

The simplest thing would be to well define storage groups so you can access a file in a storage group the same as any other file - including pumping it to stdout from where it can be slurped up by an external player...

---

### Post by iamlindoro on 2010-11-01
> **nickrout said:**
> The simplest thing would be to well define storage groups so you can access a file in a storage group the same as any other file - including pumping it to stdout from where it can be slurped up by an external player...

If you think that's simple, we'll look forward to your patches.  The above is only simple from a user perspective, not from a code one.

---

### Post by nickrout on 2010-11-01
> **iamlindoro said:**
> If you think that's simple, we'll look forward to your patches.  The above is only simple from a user perspective, not from a code one.

Ha! Foisted by my own petard! 

Wasn't meaning to be disrespectful, just thinking that if I can use wget -O - on an http server, what is the equivalent for storage group servers?

---

### Post by iamlindoro on 2010-11-01
> **nickrout said:**
> Ha! Foisted by my own petard! 

Wasn't meaning to be disrespectful, just thinking that if I can use wget -O - on an http server, what is the equivalent for storage group servers?

It's not to say that it's impossible, just that maintaining such a thing subverts all the other advantages of moving to an assumption that all video is storage group hosted (namely, no longer having to maintain two code paths for all of MythVideo that pertains to image loading, file browsing, video playback, trailer playback, file types, etc.).  It's a big mess of legacy code that I keep having to extend every time I want to add something (Like when I added fanart/etc. support, rewrote metadata downloading, etc) that prevents some of features mentioned above from ever getting done.  More or less, we can limit ourselves to a fairly limited and basic set of features and hobble our efforts to make setup much simpler, or we can really try to be innovative and insist that video playback in MythVideo follow the same rules and behaviors as in MythMusic and recording playback (and at the same time score a consistency win).

---

