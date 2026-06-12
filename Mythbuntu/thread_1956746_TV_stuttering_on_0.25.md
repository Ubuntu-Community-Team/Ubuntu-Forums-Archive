---
title: "TV stuttering on 0.25"
date: 2012-04-11
forum: Mythbuntu
---

### Post by utar on 2012-04-11
Hi


I've upgraded to 0.25 and I first want to say thanks to all the developers for their hard work.

I have a minor issue with TV playback.  Basically there is stuttering on live TV.  I believe this is an issue with the buffering as if I bring up the new playback data overlay when watching TV the available buffer is 0%.  If I pause TV for a few seconds and then play the buffer stays around 40% and playback is smooth.

I have tried increasing the HDD buffer setting in the backend but this hasn't helped.  I haven't found any other setting that I thought would help.  Does anyone have any ideas?

It's not a big problem as I can work around it by pausing live TV but it would be good if it worked.


Cheers.

[Edit: My frontend log becomes full of these when I start playback.  If I pause and then play no more appear.]

```

Apr 11 19:09:00 mythbuntu-desktop mythfrontend[13662]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(2): Waited 102ms for video buffers AAAAAAAAUUUUUUuUULUuAAAAAAAAAAAP
Apr 11 19:09:01 mythbuntu-desktop mythfrontend[13662]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(2): Waited 204ms for video buffers AAAAAAAAUUUUUUuUULUuAAAAAAAAAAAP
Apr 11 19:09:01 mythbuntu-desktop mythfrontend[13662]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(2): Waited 102ms for video buffers uAAAAAAAAAAAAAAAAUAAUUUUUUuUULAP
Apr 11 19:09:02 mythbuntu-desktop mythfrontend[13662]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(2): Waited 102ms for video buffers AAAAAAAAUAAUUUuUULUUAUuAAAAAAAAP
Apr 11 19:09:02 mythbuntu-desktop mythfrontend[13662]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(2): Waited 205ms for video buffers AAAAAAAAUAAUUUUUUuUULUUAULAAAAAP
Apr 11 19:09:02 mythbuntu-desktop mythfrontend[13662]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(2): Waited 103ms for video buffers UULUULUUAUUAAAAAAAAAAAAUAAUAUUUP
Apr 11 19:09:04 mythbuntu-desktop mythfrontend[13662]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(2): Waited 102ms for video buffers UUAUUAUUAUuAAAAAAAAAAAAUAAUAAuLP
Apr 11 19:09:05 mythbuntu-desktop mythfrontend[13662]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(2): Waited 102ms for video buffers AAuAALAAAUUAUUAUUAuAAAAAAAUAAUUP
Apr 11 19:09:08 mythbuntu-desktop mythfrontend[13662]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(2): Waited 102ms for video buffers AAUAAuAALAAAAAAAAAUUAUUAUUAUuAUP
Apr 11 19:09:09 mythbuntu-desktop mythfrontend[13662]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(2): Waited 103ms for video buffers UUAUUAUUUuAUAAUAAuAALAAAAAAAAAAP
Apr 11 19:09:12 mythbuntu-desktop mythfrontend[13662]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(2): Waited 102ms for video buffers AAAAAAUUUUUUUUuUuLAAAAAAAAAAAAAP
Apr 11 19:09:13 mythbuntu-desktop mythfrontend[13662]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(2): Waited 102ms for video buffers UUUUUuUULAAAAAAAAAAAAAAAAAAAUUUP
```

---

### Post by williammanda on 2012-04-14
Is this on a remote frontend?

---

### Post by utar on 2012-04-14
No it's a local frontend.

---

### Post by nickrout on 2012-04-14
what version?

---

### Post by utar on 2012-04-15
I'm using the latest version from the fixes branch from the Mythbuntu repositories.

The stuttering doesn't always happens, or perhaps it's just not always noticeable.  The worse are news channels as the stuttering is very apparent in the scrolling text.

The buffer showed under playback data is always "0% of 4MB" even if I can't see a stutter.  Pausing for a few seconds always fills the buffer and stops the stuttering.

---

### Post by kingmoffa on 2012-05-14
Any update on this?

---

### Post by desmane on 2012-07-16
same here, any ideas how to fix this?

---

### Post by Rotak on 2012-07-16
Same problem here.

But there is no log output like shown in utar's post.

Instead, I can fix it by hitting the pause key and let it "buffer" 3+ seconds. Then playback works fine.

Any ideas?

I found a bug related to this posted at MythTV Bug Tracker. This bug matches my issue, though (with the buffer trick):
[http://code.mythtv.org/trac/ticket/10869](http://code.mythtv.org/trac/ticket/10869)

Maybe somebody wants to extend it. I don't know what additional info to add, because I see absolutely nothing in the logs which could be related to the stuttering. :(

---

### Post by nickrout on 2012-07-16
> **Rotak said:**
> Same problem here.

But there is no log output like shown in utar's post.

Instead, I can fix it by hitting the pause key and let it "buffer" 3+ seconds. Then playback works fine.

Any ideas?

I found a bug related to this posted at MythTV Bug Tracker. This bug matches my issue, though (with the buffer trick):
[http://code.mythtv.org/trac/ticket/10869](http://code.mythtv.org/trac/ticket/10869)

Maybe somebody wants to extend it. I don't know what additional info to add, because I see absolutely nothing in the logs which could be related to the stuttering. :(

have you tried the latest 0.25-fixes? What version are you running?

---

### Post by Rotak on 2012-07-18
> **nickrout said:**
> have you tried the latest 0.25-fixes? What version are you running?

Yes I am. 


```

dpkg -l myth* | grep ii



ii  mytharchive                          2:0.25.1+fixes.20120717.4e44650-0ubuntu0mythbuntu2 create and burn DVD's from MythTV - binary file
ii  mythbrowser                          2:0.25.1+fixes.20120717.4e44650-0ubuntu0mythbuntu2 A web browser for MythTV
ii  mythbuntu-common                     0.59-0ubuntu1                                      Mythbuntu application support functions
ii  mythbuntu-control-centre             0.63-0ubuntu1                                      Mythbuntu Configuration Application
ii  mythbuntu-default-settings           1.00-0ubuntu2                                      default settings for Mythbuntu
ii  mythbuntu-desktop                    0.65                                               The Mythbuntu standalone system
ii  mythbuntu-gdm-theme                  0.6-0ubuntu1                                       Mythbuntu GDM theme
ii  mythbuntu-lirc-generator             0.25-0ubuntu2                                      Mythbuntu Lirc Configuration Generator
ii  mythbuntu-log-grabber                0.9-0ubuntu1                                       Mythbuntu diagnostic utility
ii  mythbuntu-repos                      9.6-0ubuntu0+mythbuntu                             Mythbuntu repository installer
ii  mythgallery                          2:0.25.1+fixes.20120717.4e44650-0ubuntu0mythbuntu2 Image gallery/slideshow add-on module for MythTV
ii  mythmusic                            2:0.25.1+fixes.20120717.4e44650-0ubuntu0mythbuntu2 Music add-on module for MythTV
ii  mythnetvision                        2:0.25.1+fixes.20120717.4e44650-0ubuntu0mythbuntu2 A Internet Video Player plugin for MythTV
ii  mythtv                               2:0.25.1+fixes.20120717.4e44650-0ubuntu0mythbuntu2 A personal video recorder application (client and server)
ii  mythtv-backend                       2:0.25.1+fixes.20120717.4e44650-0ubuntu0mythbuntu2 A personal video recorder application (server)
ii  mythtv-backend-master                2:0.25.1+fixes.20120717.4e44650-0ubuntu0mythbuntu2 Metapackage to setup and configure a "Master Backend" profile of MythTV.
ii  mythtv-common                        2:0.25.1+fixes.20120717.4e44650-0ubuntu0mythbuntu2 A personal video recorder application (common data)
ii  mythtv-database                      2:0.25.1+fixes.20120717.4e44650-0ubuntu0mythbuntu2 A personal video recorder application (database)
ii  mythtv-frontend                      2:0.25.1+fixes.20120717.4e44650-0ubuntu0mythbuntu2 A personal video recorder application (client)
ii  mythtv-theme-arclight                2:0.24.2+fixes.20120409.e9a0ecb-0ubuntu0mythbuntu3 The arclight MythTV Theme
ii  mythtv-theme-graphite                2:0.24.2+fixes.20120409.e9a0ecb-0ubuntu0mythbuntu3 The graphite MythTV Theme
ii  mythtv-theme-mythbuntu               2:0.25.1+fixes.20120717.4e44650-0ubuntu0mythbuntu2 The mythbuntu MythTV Theme
ii  mythtv-transcode-utils               2:0.25.1+fixes.20120717.4e44650-0ubuntu0mythbuntu2 Utilities used for transcoding MythTV tasks
ii  mythweb                              2:0.25.1+fixes.20120717.4e44650-0ubuntu0mythbuntu2 Web interface add-on module for MythTV

```Like described in the MythTV bug, this doesn't happen always. When I switch channels or launch LiveTV, and it takes a few seconds longer, then the buffer has 4+ seconds and no stuttering happens. Also, it's only the picture which stutters, not the sound.

If I'd only had more time to work into the code. I've had a similar issue in one of my tools. But the possible sources of this issue are too numerous to make a guess. :-(

---

### Post by utar on 2012-07-19
I managed to miss the replies to my post.

I personally managed to fix it my switching to the vdpau decoder.  I previously was only using this for HD content and not SD.

The buffer shown under playback date is still very low but it seems to be just enough to keep playback smooth.

On a slightly different subject occasionally when watching (high bitrate) bluray content there is also an odd stutter, say once or two during a film so it's not a major issue.  I think this is linked to the buffer as well.  It's just a pity that the read ahead buffer can't be changed.

---

### Post by Rotak on 2012-07-19
> **utar said:**
> I managed to miss the replies to my post.

I personally managed to fix it my switching to the vdpau decoder.  I previously was only using this for HD content and not SD.

...snip...


I've switched to the "VDPAU High Quality" profile, too. For now, the problem is gone. I didn't see the 0.25 update was resetting the profiles to "default". I hope that finally fixes the issue.

"Unfortunately", today came an update as well, so I need to test whether the update fixed it or the switch of the profile. But I guess it was the profile. :)

---

### Post by tgm4883 on 2012-07-19
> **Rotak said:**
> I've switched to the "VDPAU High Quality" profile, too. For now, the problem is gone. I didn't see the 0.25 update was resetting the profiles to "default". I hope that finally fixes the issue.

"Unfortunately", today came an update as well, so I need to test whether the update fixed it or the switch of the profile. But I guess it was the profile. :)

The day-to-day updates aren't going to change your profiles. I'm unsure if upgrading from 0.24 to 0.25 would change it, but I doubt it.

---

### Post by Rotak on 2012-07-20
> **tgm4883 said:**
> The day-to-day updates aren't going to change your profiles. I'm unsure if upgrading from 0.24 to 0.25 would change it, but I doubt it.

Well, I found out why that happened. I indeed upgraded from 0.24 to 0.25, but 0.25 comes with new profiles, which replaced the old ones. And therefore, the profile was reset to "default". I guess this wouldn't have happened if I'd have created one on my own.

---

### Post by nickrout on 2012-07-21
> **Rotak said:**
> Well, I found out why that happened. I indeed upgraded from 0.24 to 0.25, but 0.25 comes with new profiles, which replaced the old ones. And therefore, the profile was reset to "default". I guess this wouldn't have happened if I'd have created one on my own.

Some options disappeared with 0.25, so many of the old profiles made no sense any more.

---

### Post by utar on 2012-07-27
I see there has been a livetv buffering fix to 0.26:

[https://github.com/MythTV/mythtv/commit/483e06f6b8a9066f66cef3fcf0a5f844519f51f9](https://github.com/MythTV/mythtv/commit/483e06f6b8a9066f66cef3fcf0a5f844519f51f9)

I'm not a coder but it looks like the min buffer was too low by a factor of 1,000.  Hopefully someone may backport this to 0.25-fixes.

---

