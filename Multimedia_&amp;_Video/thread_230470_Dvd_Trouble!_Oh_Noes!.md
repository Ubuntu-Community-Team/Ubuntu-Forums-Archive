---
title: "Dvd Trouble! Oh Noes!"
date: 2006-08-06
forum: Multimedia &amp; Video
---

### Post by Kalinda on 2006-08-06
Okay... this is weird... and has something to do with my system setup, because it works fine on the laptop in Kubuntu, crappy LCD monitor aside.

I've got this one DVD ("Tron", the awesome two disc set one) which won't play right. In Kaffeine Player (V. 0.8.1), it starts, shows the standard "FBI warning, yadda, yadda" stuff and then it stops when it's supposed to go to the menu. The first few times it gave me the standard "No plugin found" error, with the following details:

```
xine: cannot find input plugin for MRL [dvd://0.0]
xine: input plugin cannot open MRL [dvd://0.0]
xine: found input plugin  : DVD Navigator
xine: found demuxer plugin: AVI/RIFF demux plugin
xine: found input plugin  : file input plugin
xine: cannot find input plugin for MRL [dvd://0.0]
xine: input plugin cannot open MRL [dvd://0.0]
xine: found input plugin  : DVD Navigator
video_out: throwing away image with pts 892114 because it's too old (diff : 4165).
video_out: throwing away image with pts 888514 because it's too old (diff : 7765).
video_out: throwing away image with pts 884914 because it's too old (diff : 11365).
video_out: throwing away image with pts 881314 because it's too old (diff : 14965).
video_out: throwing away image with pts 877714 because it's too old (diff : 18565).
video_out: throwing away image with pts 874114 because it's too old (diff : 22165).
video_out: throwing away image with pts 870514 because it's too old (diff : 25765).
video_out: throwing away image with pts 866914 because it's too old (diff : 29365).
xine: found demuxer plugin: AVI/RIFF demux plugin
xine: found input plugin  : file input plugin
audio_decoder: error, unknown buffer type: 01060000
audio_decoder: error, unknown buffer type: 04000000
audio_decoder: error, unknown buffer type: 01060000
audio_decoder: error, unknown buffer type: 04000000
audio_decoder: error, unknown buffer type: 01060000
audio_decoder: error, unknown buffer type: 04000000
audio_decoder: error, unknown buffer type: 01060000
audio_decoder: error, unknown buffer type: 04000000
audio_decoder: error, unknown buffer type: 02000000
xine: found demuxer plugin: DVD/VOB demux plugin
xine: found input plugin  : DVD Navigator
```

So, I threw in another DVD to see if my tampering with settings (which I changed back) earlier had anything to do with it. The other DVD worked fine, menus loaded, everything played, all was well. After ejecting that DVD, I threw Tron back in and whoa! It plays! Except it started the movie automatically, probably picking up where the previous DVD was. I did get it to the menu, though, via the controls.

So I'm watching the movie, all is well.. and then I get to chapter 13, second last chapter... and the thing reaches a certain point and it just stops playing, throwing me this error:

```
The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (Error reading from DVD.)
```

Now, at this point I was getting worried.. I pulled out MPlayer and tried it there and it did the same thing.. then I went to my dad's compy and it works fine in Windoze... and also on my laptop in Kubuntu, as stated previously. So I don't know why it isn't working for me, I have everything I should installed. Although it should be noted that I DID take the nessecary steps so the eject button on my ROM drive would work, but I don't see what this has to do with that. This is the first time this DVD has been played on my compy since I bought it a few days back.

So anyone got any ideas? I'd love to get it to work so I can watch the rest of the movie :)

Thanks!

---

### Post by tparker on 2006-11-25
Sorry I Don't have any ideas to help with this. I found this post while looking for help to solve this same problem so - Bump!

Anyone have any ideas? 

I have the same error messages as the original poster, the disks work fine in other DVD players (on other computer systems and the one at the TV). 

I have had this same trouble with episodes in the middle of series disks (Babylon 5, Buffy, X-files) and in the middle of movie disks (LOTR, various anime). When it crashes in Xine I've tried reloading X, rebooting the machine, and/or switching to mplayer or totem. Sometimes it will play some more, sometimes not. I can't find a good clue to tell me what to track down and fix so any ideas would be greatly appreciated.

In case it helps:
I'm running Ubuntu 6.06(amd64) with all the updates it has told me about. Computer is amd athlon 64 3200, 1g ram, video card is nvidia 7600gs (256mb) with current drivers installed, using the board's built in sound (asus a8n-sli deluxe), dvd rom is an hp dvd 840i.

Thanks

---

### Post by marsbt on 2007-01-02
I noticed similar problems when xine wouldn't read some DVDs and played others fine. Although I couldn't find why this was happening, removing the ~/.xine directory made things work.

---

