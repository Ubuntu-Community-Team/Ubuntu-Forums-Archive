---
title: "MythTV Issues and Questions"
date: 2008-10-21
forum: Mythbuntu
---

### Post by Whiplash78 on 2008-10-21
Hi, all.  N00b user here.  Absolutely thrilled with MythBuntu, it's worked better than anything I've tried thus far.  Hugs.

That having been said, I'm running into a few issues.
[LIST]
[*]Sound.  I think I'm losing my sound capabilities during the install procedure, when I choose the Nvidia drivers.  I've seen a few posts on these forums about how in some cases MythTV will mute the sound by default, or how it will see the tuner card as the primary audio device.
[*]Picture Quality.  I have a HD-5500, and managed to get both ATSC and NTSC detected, and scanning for channels.  However, every-single-channel looks terrible.  Even Digital (HD) channels that I know work well from my antenna directly to my TV, look lousy through the tuner.
[*]DVD.  I can pop in a DVD, and it'll show the legal jargon, and then kick me back to the myth menu right before either previews or the dvd movie menu.
[/LIST]

I just started messing with this last night and I'm at work now, so I obviously haven't been able to troll the boards to any great extent.  But if anyone has any suggestions for me to try when I get home, I'd love to hear 'em.  Thanks, and major props to the MythBuntu devs.

Motherboard: [Gigabyte GA-73PVM-S2H]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2691")

Tuner: PCHDTV 5500

---

### Post by newlinux on 2008-10-21
hey whip,
Do you lose all sound or just myth sound?

For your picture quality issue can you describe what looks bad about them? Can you try playing your recordings with mplayer outside of myth and see how they look? If it is just a playback problem, you might try changing your playback profile settings, starting with CPU++ (what cpu are you using?). You may end up needing to create a custom playback profile. For analog recordings you can get a better picture by adjusting the recording profile (both of these can be found in mythfrontend setup->TV Playback. Lot of different settings in there.

You might also want to take a look at your mythfrontend log for playback problems (including your dvd playback if you are using the internal player). Another thing you could try for dvds is to use xine or vlc instead of the internal player.

---

### Post by agamotto on 2008-10-21
> **Whiplash78 said:**
> Hi, all.  N00b user here.  Absolutely thrilled with MythBuntu, it's worked better than anything I've tried thus far.  Hugs.

That having been said, I'm running into a few issues.
[LIST]
[*]Sound.  I think I'm losing my sound capabilities during the install procedure, when I choose the Nvidia drivers.  I've seen a few posts on these forums about how in some cases MythTV will mute the sound by default, or how it will see the tuner card as the primary audio device.
[*]Picture Quality.  I have a HD-5500, and managed to get both ATSC and NTSC detected, and scanning for channels.  However, every-single-channel looks terrible.  Even Digital (HD) channels that I know work well from my antenna directly to my TV, look lousy through the tuner.
[*]DVD.  I can pop in a DVD, and it'll show the legal jargon, and then kick me back to the myth menu right before either previews or the dvd movie menu.
[/LIST]

I just started messing with this last night and I'm at work now, so I obviously haven't been able to troll the boards to any great extent.  But if anyone has any suggestions for me to try when I get home, I'd love to hear 'em.  Thanks, and major props to the MythBuntu devs.

Motherboard: [Gigabyte GA-73PVM-S2H]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2691")

Tuner: PCHDTV 5500

Sound:  Drop into XFCE and find/turn on the volume control.  Make sure that both PCM and Master in the mixer portion are set somewhere ~90%.  Quite often, the Master gets set, but PCM winds up ignored.

Picture Quality:  Not sure on this one, but when scanning for digital channels OTA, double check to see that you are searching for 8-vsb.  This may help, otherwise, be advised that some/many of the digital stations in your area may not be broadcasting at full power until the switchover.

DVD:  The usual problem behind this is not having libdvdcss installed.  Make sure this is installed, and if it continues... not sure.  I have been using Myth in one form or another for four years, and commercial DVD playback is still touchy.  Also, do not be surprised if burning your recordings to DVD does not work.

Welcome to the party, and hopefully the DVD writing issue will be resolved with 8.10

---

### Post by Whiplash78 on 2008-10-21
Thanks guys, I'll be giving these tips a try tonight.

---

### Post by jetpeach on 2008-10-21
could somebody say *how* to get mythtv to use VLC? previous posts on this don't make it clear
[http://ubuntuforums.org/showthread.php?t=753358](http://ubuntuforums.org/showthread.php?t=753358)
they just say use the command line "vlc file://%s vlc:quit" - specifically they say to put this in the video settings of mythtv, the problem i have is their is no video settings preference in mythtv for me! their is "tv settings" but no place inside this configuration area to add a command line...

---

### Post by newlinux on 2008-10-21
You must have mythvideo installed and this is only for mythvideo (using vlc). you can't use vlc for recordings or livetv.

---

### Post by Whiplash78 on 2008-10-22
Well, seems like all I needed was a clean reinstall to get everything working.  Perhaps the difference this time around was that I upgraded my packages *before* I tried to set everything up. :-P  Couple more minor issues, now.  I have my PCM and Master volumes cranked up almost all the way in alsamixer, the sound on my TV almost all the way up, but MythTV doesn't seem overly.. loud.  Not as loud as I was expecting it to have been.  I have noticed some strange 'white noise' coming from my TV now, though.  It's especially noticeable when the HD is chugging.  I've tried muting all my non-sound related connections in alsamixer, maybe I'm missing something here?

Secondly, mplayer is acting goofy.  After enabling libdvdcss2 in MythBuntu ControlCentre (Thanks, google ;-)), I can watch DVD's, but the video is distorted.  if I'm watching a widescreen DVD movie, it's displayed twice, in the viewable area for a widescreen DVD.  So there's two 'movies' playing in the same space, if that makes any sense.  I configured Myth to use xine for dvd's and that's working better, but now I have to figure out how to make it play nice with my streamzap remote.  I think I can figure that out.

Thanks to all for the help getting this working.  It's really turning into something awesome.

---

