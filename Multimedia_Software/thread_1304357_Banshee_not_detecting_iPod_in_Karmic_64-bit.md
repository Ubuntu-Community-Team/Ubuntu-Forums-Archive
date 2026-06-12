---
title: "Banshee not detecting iPod in Karmic 64-bit"
date: 2009-10-29
forum: Multimedia Software
---

### Post by thomasboleyn on 2009-10-29
Hi there. I installed Karmic RC 64-bit a couple of days ago, and unfortunately Banshee (my usual choice of player/iPod sync..er(?) does not seem to be able to detect my 6th gen 80gb iPod classic, or my 8gb iPod mini. In Jaunty I did not have these problems. Strangely, Rhytmbox seems to be able to detect and sync the mini, but not the classic. Both are detected by nautilus and can be browsed. Any help would be appreciated, thanks.

---

### Post by lian1238 on 2009-10-29
If all else fails, try this script:
[http://shuffle-db.sourceforge.net](http://shuffle-db.sourceforge.net)

Copy your music with nautilus, and run the script in the root directory of the iPod.
The instructions are provided with the script. Read them first.

---

### Post by tmtan on 2009-10-29
I have the same issue

This is a common issue currently being found in Karmic, it has to do with the deprecation of podsleuth vs hal. I haven't been able to find a permanent fix, hopefully someone will come out with a patch or update to fix this issue ASAP as iPod integration is INTEGRAL.

A temporary fix:
In order to get banshee to see the ipod, close banshee then use terminal to killall -9 nautilus (with the ipod disconnected). Then connect the ipod, give it a minute, then you can reinstate nautilus. Most likely nautilus will go ahead and mount it at that point, if not, you may need to manually mount the ipod. From here you can go ahead and start banshee, where it will then recognize the ipod like normal.

Good luck. Let me know of any issues.

---

### Post by nortexoid on 2009-11-01
Having the same problem with my 2nd generation Video iPod (5th generation classic). It is neither detected in Songbird nor Banshee. Rhythmbox sees it fine, but of course it's incapable of syncing. I suspect this is the result of DeviceKit replacing HAL, and that we'll have to wait for players to update their add-ons.

---

### Post by Strongman332 on 2009-11-01
this also happens in kubuntu 9.10

---

### Post by sirish.gauni on 2009-11-02
Having the same problem on Karmic 64 bit with 4G iPod nano! :(

---

### Post by joey-elijah on 2009-11-02
> **tmtan said:**
> I have the same issue

This is a common issue currently being found in Karmic, it has to do with the deprecation of podsleuth vs hal. I haven't been able to find a permanent fix, hopefully someone will come out with a patch or update to fix this issue ASAP as iPod integration is INTEGRAL.

**A temporary fix:**
In order to get banshee to see the ipod, close banshee then use terminal to killall -9 nautilus (with the ipod disconnected). Then connect the ipod, give it a minute, then you can reinstate nautilus. Most likely nautilus will go ahead and mount it at that point, if not, you may need to manually mount the ipod. From here you can go ahead and start banshee, where it will then recognize the ipod like normal.

Good luck. Let me know of any issues.

You, my man, are a god. I've been so annoyed by this. Thankfully Rhythmbox sees it regardless, but use banshee so this makes me happy =) [even if it does involve a lot of faff!]

---

### Post by gamx on 2009-11-02
It works for me too. Thanks!

Now let's hope that the problem is being fixed for good.

G

---

### Post by adamn on 2009-11-06
> **tmtan said:**
> I have the same issue

This is a common issue currently being found in Karmic, it has to do with the deprecation of podsleuth vs hal. I haven't been able to find a permanent fix, hopefully someone will come out with a patch or update to fix this issue ASAP as iPod integration is INTEGRAL.

A temporary fix:
In order to get banshee to see the ipod, close banshee then use terminal to killall -9 nautilus (with the ipod disconnected). Then connect the ipod, give it a minute, then you can reinstate nautilus. Most likely nautilus will go ahead and mount it at that point, if not, you may need to manually mount the ipod. From here you can go ahead and start banshee, where it will then recognize the ipod like normal.

Good luck. Let me know of any issues.

Can someone please help a noob out with this. 

"killall -9 nautilus" is a terminal command, right?
And how do I go about "reinstating" nautilus after killing it?

Thanks for the help with this issue. I haven't installed 9.10 on my desktop yet because I need some way to sync my iPod. I HAVE to have solid sync ability with my iphone because I use it several hours every day. I've been running 9.10 on my notebook for a couple of weeks and I love it.

Thanks > adamn

---

### Post by lian1238 on 2009-11-06
You can just run nautilus (lowercase) in the Run dialog (Alt+F2).

---

### Post by adamn on 2009-11-06
> **lian1238 said:**
> You can just run nautilus (lowercase) in the Run dialog (Alt+F2).

THANKS!
 I didn't even know about the run dialogue. Sweet.

---

### Post by dangman123 on 2009-11-09
> **tmtan said:**
> I have the same issue

This is a common issue currently being found in Karmic, it has to do with the deprecation of podsleuth vs hal. I haven't been able to find a permanent fix, hopefully someone will come out with a patch or update to fix this issue ASAP as iPod integration is INTEGRAL.

A temporary fix:
In order to get banshee to see the ipod, close banshee then use terminal to killall -9 nautilus (with the ipod disconnected). Then connect the ipod, give it a minute, then you can reinstate nautilus. Most likely nautilus will go ahead and mount it at that point, if not, you may need to manually mount the ipod. From here you can go ahead and start banshee, where it will then recognize the ipod like normal.

Good luck. Let me know of any issues.


Great work tmtam!  I was looking for this fix, thank you so much works a treat in 9.10

---

### Post by nortexoid on 2009-11-11
I tried the temporary fix in Karmic 32-bit and it didn't work. What did work is that Songbird 1.2 is now able to detect and mount it. (And, of course, Rhythmbox never had any problems with finding the iPod.)

I'm using a 5th gen "classic" video iPod. Anyone else observing this behavior?

---

### Post by Terad on 2009-11-12
> **tmtan said:**
> I have the same issue

This is a common issue currently being found in Karmic, it has to do with the deprecation of podsleuth vs hal. I haven't been able to find a permanent fix, hopefully someone will come out with a patch or update to fix this issue ASAP as iPod integration is INTEGRAL.

A temporary fix:
In order to get banshee to see the ipod, close banshee then use terminal to killall -9 nautilus (with the ipod disconnected). Then connect the ipod, give it a minute, then you can reinstate nautilus. Most likely nautilus will go ahead and mount it at that point, if not, you may need to manually mount the ipod. From here you can go ahead and start banshee, where it will then recognize the ipod like normal.

Good luck. Let me know of any issues.

thanks a lot!
worked fine

---

### Post by moh980 on 2009-11-15
> **tmtan said:**
> I have the same issue

This is a common issue currently being found in Karmic, it has to do with the deprecation of podsleuth vs hal. I haven't been able to find a permanent fix, hopefully someone will come out with a patch or update to fix this issue ASAP as iPod integration is INTEGRAL.

A temporary fix:
In order to get banshee to see the ipod, close banshee then use terminal to killall -9 nautilus (with the ipod disconnected). Then connect the ipod, give it a minute, then you can reinstate nautilus. Most likely nautilus will go ahead and mount it at that point, if not, you may need to manually mount the ipod. From here you can go ahead and start banshee, where it will then recognize the ipod like normal.

Good luck. Let me know of any issues.

You are the man!
its easy enough to fix it ;)

Cheers!

---

### Post by troyster on 2009-11-15
> **nortexoid said:**
> I tried the temporary fix in Karmic 32-bit and it didn't work. What did work is that Songbird 1.2 is now able to detect and mount it. (And, of course, Rhythmbox never had any problems with finding the iPod.)

I'm using a 5th gen "classic" video iPod. Anyone else observing this behavior?

I'm also using a 5th gen video Ipod (black, 60GB) and TnTan's temporary fix worked for me in Karmic 32-bit.  An odd bug though - no doubt it'll be mopped up in future updates. . . ;)

Quick query - why would Rhythmbox be fine everytime, when other apps struggle to see the Ipod??

---

### Post by fabdango on 2009-11-16
> **joey-elijah said:**
> You, my man, are a god. I've been so annoyed by this. Thankfully Rhythmbox sees it regardless, but use banshee so this makes me happy =) [even if it does involve a lot of faff!]
YEAH!!

I hope this gets fixed real soon :P

---

### Post by Dalek Draco ON LINUX on 2009-11-21
> **tmtan said:**
> I have the same issue

This is a common issue currently being found in Karmic, it has to do with the deprecation of podsleuth vs hal. I haven't been able to find a permanent fix, hopefully someone will come out with a patch or update to fix this issue ASAP as iPod integration is INTEGRAL.

A temporary fix:
In order to get banshee to see the ipod, close banshee then use terminal to killall -9 nautilus (with the ipod disconnected). Then connect the ipod, give it a minute, then you can reinstate nautilus. Most likely nautilus will go ahead and mount it at that point, if not, you may need to manually mount the ipod. From here you can go ahead and start banshee, where it will then recognize the ipod like normal.

Good luck. Let me know of any issues.

  THANK YOU!!! I've been spending hours trying to work out how I'm going to get a PC with itunes so that I can sync my Ipod (I'm used to a drag and drop mp3 player, so much less hassle) now that Banshee recognises the Ipod I just need to convert everything to mp4 :P

---

### Post by nortexoid on 2009-11-21
I don't get why I'm the only for which the temporary fix doesn't work. I've even removed spaces in the mount point label, and Songbird detects the iPod just fine after doing the temporary fix. Weird.

Using daily builds of Banshee and 32-bit Karmic.

---

### Post by Wobblybob on 2009-11-22
Thanks 4 that this works for me on my iPod classic on both gtkpod & Banshee on 32-bit karmic;

Disconnect iPod [unplug]
Close banshee/gtkpod and nautilus windows.
run killall -9 nautilus in a Terminal [just in case].
plug in iPod, give it a minute, then go to [Places] and the iPod now shows up, click to open it in nautilus then close the window again.
Now open Banshee or gtkpod and they now detect the iPod.

I use Banshee to add music and video and gtkpod to add audiobooks

---

### Post by Agnaramasi on 2009-11-23
the temporary fix works for me as well. but more importantly, has someone filed a bug report about this?

---

### Post by silentknyght on 2009-11-23
As I only used Banshee to update my ipod, and not to play files directly off of it, I found a workaround using GTKPOD, where you can force it to find your ipod by directing it to the mount point from within the preferences.  Once I had pointed it to the correct spot, just click "Load Ipod", or whatever the icon says.

Sorry I can't be more precise; not running on my linux box at the moment.

---

### Post by LuisGMarine on 2009-12-06
Temp fix works great over here with a 5Gen iPod Video.  I'm deff going to start recommending this fix for all those people out there experience these issues. 

Thanks! :popcorn:

---

### Post by commonplace on 2009-12-06
Glad I found this thread. I thought something was wrong with the iPod, since it worked under 9.04 and I hadn't yet tried it in 9.10. Thanks so much! Hope it gets REALLY fixed soon. :)

/Kevin

---

### Post by nbv4 on 2009-12-14
I can't get my ipod to work at all with Karmic 64bit. I plug in my ipod and nothing happens. Nothing in Places, nor will any programs see the ipod. It worked fine in Jaunty... Whats weird is that when I plug it in, the actual iPod will say "Connected, eject before disconnecting", so I know the connection is made. It's just the OS that is not seeing it at all...

---

### Post by blazemore on 2009-12-15
Any updates on whether or not this is going to be fixed?
I know in Lucid HAL is being phased out completely, so will definately be fixed by April.
As it stands, I can no longer recommend Ubuntu to my friends and family.
How on EARTH did a bug this big "ipods don't work" get past release candidate?!

---

### Post by dilb on 2010-01-03
> **tmtan said:**
> I have the same issue

This is a common issue currently being found in Karmic, it has to do with the deprecation of podsleuth vs hal. I haven't been able to find a permanent fix, hopefully someone will come out with a patch or update to fix this issue ASAP as iPod integration is INTEGRAL.

A temporary fix:
In order to get banshee to see the ipod, close banshee then use terminal to killall -9 nautilus (with the ipod disconnected). Then connect the ipod, give it a minute, then you can reinstate nautilus. Most likely nautilus will go ahead and mount it at that point, if not, you may need to manually mount the ipod. From here you can go ahead and start banshee, where it will then recognize the ipod like normal.

Good luck. Let me know of any issues.
Thanks for your help, this worked for me.

---

### Post by blazemore on 2010-01-03
How did the bug: "iPods don't work with Ubuntu" get past the alpha stages?
And is this fixed in Lucid yet?

---

### Post by LuisGMarine on 2010-01-03
I hope so I rolled back to 9.04 just because I'm super lazy and don't feel like typing that workaround everytime I want to plug in my ipod to sync it.  Not to mention I've been having some issues managing my ipod from banshee.

---

### Post by boombox1387 on 2010-01-06
> **blazemore said:**
> How did the bug: "iPods don't work with Ubuntu" get past the alpha stages?
And is this fixed in Lucid yet?

This isn't an Ubuntu problem; iPods should be working fine with Ubuntu 9.10 in general.  Instead this is (was, actually) a bug with Banshee, which isn't even a default app in Ubuntu.  Banshee uses Podsleuth to detect iPods, and it wasn't working with with distros that moved away from HAL (which Ubuntu did in the Karmic release).

For those still using the workaround listed here, you'll be happy to know that:

1. You can solve this issue without opening terminal by opening up gconf-editor and un-checking media_automount in apps > nautilus > preferences.  This will stop all devices from automatically mounting, which will allow Banshee to see your iPod.

2. This issue has mostly been fixed[1] in the development version of Banshee.  You can easily update to this version by adding the Banshee-daily PPA[2].

[1] [https://bugzilla.gnome.org/show_bug.cgi?id=586508](https://bugzilla.gnome.org/show_bug.cgi?id=586508)
[2] [https://launchpad.net/~banshee-team/+archive/banshee-daily](https://launchpad.net/~banshee-team/+archive/banshee-daily)

---

### Post by blazemore on 2010-01-06
But ipods don't work in Songbird either

---

### Post by LuisGMarine on 2010-01-06
> **boombox1387 said:**
> This isn't an Ubuntu problem; iPods should be working fine with Ubuntu 9.10 in general.  Instead this is (was, actually) a bug with Banshee, which isn't even a default app in Ubuntu.  Banshee uses Podsleuth to detect iPods, and it wasn't working with with distros that moved away from HAL (which Ubuntu did in the Karmic release).

For those still using the workaround listed here, you'll be happy to know that:

1. You can solve this issue without opening terminal by opening up gconf-editor and un-checking media_automount in apps > nautilus > preferences.  This will stop all devices from automatically mounting, which will allow Banshee to see your iPod.

2. This issue has mostly been fixed[1] in the development version of Banshee.  You can easily update to this version by adding the Banshee-daily PPA[2].

[1] [https://bugzilla.gnome.org/show_bug.cgi?id=586508](https://bugzilla.gnome.org/show_bug.cgi?id=586508)
[2] [https://launchpad.net/~banshee-team/+archive/banshee-daily](https://launchpad.net/~banshee-team/+archive/banshee-daily)

Greatest piece of news I've heard! 

The fix is the best!  All I did was uncheck the auto mount.  plugged my ipod in then opened up banshee.  Then I mounted my iPod by going to Places > and click on my iPod and instantly banshee recognized it.  

Simply great!  Thanks a lot for this!

---

### Post by boombox1387 on 2010-01-06
@blazemore: Sorry to hear that Songbird has the same issue.  It apparently depends on HAL as well, but it's still not a bug in Ubuntu.  Lucid isn't going to solve this problem; it's up to Songbird developers to fix it.

@LuisGMarine: Glad it worked for you!

---

### Post by blazemore on 2010-01-07
This might be a stupid question, but can't Ubuntu developers make sure HAL works?
Why did they break it in the first place?

---

### Post by SKLP on 2010-01-07
> **blazemore said:**
> This might be a stupid question, but can't Ubuntu developers make sure HAL works?
Why did they break it in the first place?HAL is deprecated in 9.10, and it will not be installed in lucid, at all.

---

### Post by boombox1387 on 2010-01-07
> **blazemore said:**
> This might be a stupid question, but can't Ubuntu developers make sure HAL works?
Why did they break it in the first place?

Check out the [freedesktop.org page on HAL]("http://www.freedesktop.org/wiki/Software/hal") if you want more information.  Development has shifted away from HAL (and toward DeviceKit-disks), so it's encouraged that software developers (and Linux distros) stop using it.  As SKLP said, HAL will be completely gone from Ubuntu by Lucid, meaning that software that depends on it (like Songbird, apparently) probably won't work any better.

---

### Post by bostonblond on 2010-02-21
> **tmtan said:**
> I have the same issue

This is a common issue currently being found in Karmic, it has to do with the deprecation of podsleuth vs hal. I haven't been able to find a permanent fix, hopefully someone will come out with a patch or update to fix this issue ASAP as iPod integration is INTEGRAL.

A temporary fix:
In order to get banshee to see the ipod, close banshee then use terminal to killall -9 nautilus (with the ipod disconnected). Then connect the ipod, give it a minute, then you can reinstate nautilus. Most likely nautilus will go ahead and mount it at that point, if not, you may need to manually mount the ipod. From here you can go ahead and start banshee, where it will then recognize the ipod like normal.

Good luck. Let me know of any issues.

Great fix! Thank you :)

---

### Post by boombox1387 on 2010-02-21
> **bostonblond said:**
> Great fix! Thank you :)

Banshee 1.5.3 - released a couple weeks ago - contains a fix for iPod integration. No more need to use hacky workarounds if you're interested in upgrading to the newest version. :)

---

### Post by blazemore on 2010-02-22
> **boombox1387 said:**
> Banshee 1.5.3 - released a couple weeks ago - contains a fix for iPod integration. No more need to use hacky workarounds if you're interested in upgrading to the newest version. :)

Still doesn't work for me.

---

### Post by boombox1387 on 2010-02-22
> **blazemore said:**
> Still doesn't work for me.

Hmmm, strange.  You may have mentioned all of these details earlier, but:
-Which distro/version are you using?  Karmic?
-Where did you get Banshee 1.5.3?  Stable PPA? Daily PPA? Source?
-What kind of iPod are you using?  Does your iPod show up on your desktop/Nautilus/Rhythmbox?  Or is it not mounting at all?

If you turned off media_automount like I had previously suggested, you should be able to turn it back on now.

With your iPod mounted and Banshee running, you might want to open a terminal and run 'podsleuth --rescan' (without quotes).  I hope I'm remembering the command correctly; if I am, this should run Banshee's scanning tool to find iPods on your system.  That output should be helpful.  If you're extra lucky, running that command will find your iPod and you'll never have to run it again.

---

### Post by blazemore on 2010-02-22
> **boombox1387 said:**
> Hmmm, strange.  You may have mentioned all of these details earlier, but:
-Which distro/version are you using?  Karmic?
-Where did you get Banshee 1.5.3?  Stable PPA? Daily PPA? Source?
-What kind of iPod are you using?  Does your iPod show up on your desktop/Nautilus/Rhythmbox?  Or is it not mounting at all?

If you turned off media_automount like I had previously suggested, you should be able to turn it back on now.

With your iPod mounted and Banshee running, you might want to open a terminal and run 'podsleuth --rescan' (without quotes).  I hope I'm remembering the command correctly; if I am, this should run Banshee's scanning tool to find iPods on your system.  That output should be helpful.  If you're extra lucky, running that command will find your iPod and you'll never have to run it again.

I have the same problem with Karmic and Lucid; with all three Banshee PPAs, and my iPod shows up on my desktop, I can mount it and browse it fine. It shows up in Rhythmbox, but not Banshee or Songbird. 
It's an Ipod Video 60gb (5g)

---

### Post by boombox1387 on 2010-02-22
Did you try running 'podsleuth --rescan' from a terminal?  I really think that could help solve your problem (with Banshee; Songbird will be broken until the developers feel like fixing it...)

---

### Post by rob22941 on 2010-03-12
FYI! Banshee has released 1.5.5. I've just downloaded it and it's fixed any Ipod issues I had with 1.5.1 and 1.5.3. I uninstalled all my old version of banshee and installed the new release March 10.

[http://banshee-project.org/download/](http://banshee-project.org/download/)

Good Luck!

---

### Post by bkadoctaj on 2010-04-04
Well, I have to say that I think Rhythmbox has iPod support down better than Banshee.  Sure, you can't sync yet, but the drag-and-drop isn't bad, because it won't add duplicates of the same file.  So, you can just drag all your music in and it will update the iPod without adding every song all over again.  The downside of Rhythmbox is that there's no auto-organize function for your music library like iTunes and Banshee have.  I use Banshee to sort my music and Rhythmbox to add it to my iPod and play it.  Everything's good for now.

---

### Post by ghostborg on 2010-04-26
I saw a few weeks ago that Songbird is dropping linux.

[http://blog.songbirdnest.com/2010/04/02/songbird-singing-a-new-tune/]("http://blog.songbirdnest.com/2010/04/02/songbird-singing-a-new-tune/")

---

### Post by eveningsky339 on 2010-04-28
I just did a clean install of Karmic 64-bit and as far as its concerned, my iPod does not exist.  No workarounds, no recognition in rhythmbox or gtkpod, nothing.  I had 32-bit Karmic installed prior and everything worked fine.

Thank goodness Lucid comes out tomorrow... and I may be going for the 32-bit rather than the 64-bit.  Not worth the hassle.

---

### Post by boombox1387 on 2010-04-28
> **eveningsky339 said:**
> I just did a clean install of Karmic 64-bit and as far as its concerned, my iPod does not exist.  No workarounds, no recognition in rhythmbox or gtkpod, nothing.  I had 32-bit Karmic installed prior and everything worked fine.

Thank goodness Lucid comes out tomorrow... and I may be going for the 32-bit rather than the 64-bit.  Not worth the hassle.

Hmm, that's a bummer.  What's the output of ```
lsusb
``` when your iPod is plugged in?  Does anything on the list look like an iPod?  It's especially strange that programs like Rhythmbox don't see the iPod, since Rhythmbox isn't affected by the issue that broke iPod support with Banshee and Songbird.

---

### Post by eveningsky339 on 2010-04-28
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC WebCam / CNF7129
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
Yup, no iPod...  And no USB remote for my new cordless mouse.  :(  Sad story.  But Lucid arrives tomorrow!

---

### Post by greekodan on 2010-04-29
Thank you! Although I have no idea what "deprecation of podsleuth vs hal" means, your solution worked perfectly!

---

### Post by specimen65 on 2010-05-01
I had this too tonight - a fresh install of 10.04. Rhythmbox, Banshee and Nautilus all couldn't detect my 5th gen ipod classic or my Lacie external until I used this solution. After that, plugging in both the external and ipod were mounted.

Maybe its not just a Banshee problem?

---

### Post by JeryMac on 2010-05-20
I have a 2nd gen ipod and just rebuild Lucid 32. I was having so much trouble with my Ipod that tried to switch to Amarok and Songbird(I didn't hear that they weren't supporting linux anymore), but everything kept turning me back to banshee. Thanks so much for the fix, the media-automount one.

---

### Post by Jezzaroo on 2010-05-30
> **boombox1387 said:**
> This isn't an Ubuntu problem; iPods should be working fine with Ubuntu 9.10 in general.  Instead this is (was, actually) a bug with Banshee, which isn't even a default app in Ubuntu.  Banshee uses Podsleuth to detect iPods, and it wasn't working with with distros that moved away from HAL (which Ubuntu did in the Karmic release).

For those still using the workaround listed here, you'll be happy to know that:

1. [B]You can solve this issue without opening terminal by opening up gconf-editor and un-checking media_automount in apps > nautilus > preferences.  This will stop all devices from automatically mounting, which will allow Banshee to see your iPod.
[/B]
2. This issue has mostly been fixed[1] in the development version of Banshee.  You can easily update to this version by adding the Banshee-daily PPA[2].

[1] [https://bugzilla.gnome.org/show_bug.cgi?id=586508](https://bugzilla.gnome.org/show_bug.cgi?id=586508)
[2] [https://launchpad.net/~banshee-team/+archive/banshee-daily](https://launchpad.net/~banshee-team/+archive/banshee-daily)

This worked for me. 5th gen video ipod and Banshee on Linux Mint 9.

---

### Post by amadis2009 on 2010-06-21
It took forever to get these workarounds to work and in the end they were more headache than they were worth.

I had to set my gnome desktop preferences to never automount any devices thru the gconf-editor and then  manually mount the ipod and then do the killall -9 nautilus thing **everytime** i connected my ipod. NO THANKS! And that was just to get Banshee to recognize the  ipod. Then after all that, it wouldn't save playlists to the ipod.

In the end I got gtkpod. Installed it and then configured it by adding  the repository in the repository/ipod options and make sure it was  looking for the name I gave my ipod. Then everything was a go. I changed  the playlist command to rhythmbox (under  edit>preferences>commands. Just pasted rhythmbox over xmms) cause  the default xmms doesn't work. Now I use the two programs in  conjunction. 

I know, you're thinking *why use two programs?* Well, I'm really  sold on the new Ubuntu One music store which so far only works in  Rhythmbox and Banshee(with a plug-in). Which is why I didn't bother  trying Amarok or any of the other options. It's pretty easy with Rhythmbox and gtkpod actually and I  can drag-n-drop files from one application to the other. 

Hope this helps others.

---

### Post by boombox1387 on 2010-06-21
> **amadis2009 said:**
> It took forever to get these workarounds to work and in the end they were more headache than they were worth.

I had to set my gnome desktop preferences to never automount any devices thru the gconf-editor and then  manually mount the ipod and then do the killall -9 nautilus thing **everytime** i connected my ipod. NO THANKS! And that was just to get Banshee to recognize the  ipod. Then after all that, it wouldn't save playlists to the ipod.

In the end I got gtkpod. Installed it and then configured it by adding  the repository in the repository/ipod options and make sure it was  looking for the name I gave my ipod. Then everything was a go. I changed  the playlist command to rhythmbox (under  edit>preferences>commands. Just pasted rhythmbox over xmms) cause  the default xmms doesn't work. Now I use the two programs in  conjunction. 

I know, you're thinking *why use two programs?* Well, I'm really  sold on the new Ubuntu One music store which so far only works in  Rhythmbox and Banshee(with a plug-in). Which is why I didn't bother  trying Amarok or any of the other options. It's pretty easy with Rhythmbox and gtkpod actually and I  can drag-n-drop files from one application to the other. 

Hope this helps others.

Glad you found a solution that works for you!

As far as the original issue goes (Banshee + iPods), an update probably wouldn't hurt:

The version of Banshee (1.6.0) that shipped with Ubuntu Lucid still had some flaky issues with iPods.  These have mostly been resolved in the latest stable release of Banshee (1.6.1) and its iPod detection program named Podsleuth.  If you're a Banshee user with an iPod, I would highly recommend subscribing to [the official Banshee PPA]("https://launchpad.net/~banshee-team/+archive/ppa"), which will deliver the newest Banshee to you directly through Ubuntu's update manager.

If you happen to use some newer iDevices (like the iPhone and iPod Touch), and you want these devices to work with Banshee, you should be happy to know that a lot of great work has been happening recently to make this a reality.  While the development work hasn't yet been merged with the main Banshee code (as far as I know), you can read about it here: [http://monotorrent.blogspot.com/2010/06/hackwee-day-iv-final-showdown.html](http://monotorrent.blogspot.com/2010/06/hackwee-day-iv-final-showdown.html)  If you're feeling adventurous, I'm sure that the developers wouldn't mind extra people testing the work.

---

### Post by bluebyt on 2010-07-22
I have an iPod Touch 3G 32gigs and my iPod work with Rhythmbox and Gtkpod but not Banshee.

-Turned off media_automount the Ipod still not detected by Banshee.

-I upgraded to Banshee PPA now I have version 1.7.3, Ubuntu version is Karmic 9.10 32bits.

-If I run podsleuth --rescan, I have the following error message:
 No iPods were found in the HAL device tree

---

### Post by boombox1387 on 2010-07-23
> **bluebyt said:**
> I have an iPod Touch 3G 32gigs and my iPod work with Rhythmbox and Gtkpod but not Banshee.

-Turned off media_automount the Ipod still not detected by Banshee.

-I upgraded to Banshee PPA now I have version 1.7.3, Ubuntu version is Karmic 9.10 32bits.

-If I run podsleuth --rescan, I have the following error message:
 No iPods were found in the HAL device tree

See the last part of my post right above yours.  So far, iPod Touches and iPhones don't work with Banshee, but that will change really, really soon.  I can't make any promises -- and obviously the Banshee team won't push a fix out if it isn't ready -- but with any luck this feature should make it into the 1.8 release which should happen at the end of September (assuming the Banshee team is still following the Gnome release schedule).

---

