---
title: "Creative Zen X-Fi 2"
date: 2009-12-24
forum: Multimedia Software
---

### Post by gabrielitos on 2009-12-24
Hi All!
Have anybody some positive feedbacks for the correct working of Creative Zen X-Fi 2 on Ubuntu? I've seen some threads about the X-Fi but nobody has written about the second version.
Thanks

---

### Post by odysseusjak on 2009-12-25
Same for me.  I just got one for Christmas!  It mounts on the desktop, but it doesn't show up in Rhythmbox or Banshee.  I'm manually transferring music through Nautilus.

---

### Post by gabrielitos on 2009-12-26
If you mount it as an external device, are the songs inserted correctly recognized by the player with the tags?
Did you try this procedure, stated as working for the first version of the device?

[http://ubuntuforums.org/showthread.php?t=896653](http://ubuntuforums.org/showthread.php?t=896653)

---

### Post by gabrielitos on 2009-12-27
Bump!

---

### Post by odysseusjak on 2009-12-29
I have tried all of the things listed for the X-Fi and none of them are working for the X-Fi2.  The only consolation is that the X-Fi2 auto mounts as an external hard drive.  None of the media player apps (Banshee, Rhythmbox, etc.) recognise it as a media player.  Since it mounts as an external drive, I can browse to it and play music from it.  I can even copy music to the Music folder on the X-Fi2.  However, I can't sync it with Banshee because it does not see it.  I'm thinking it's because it so new that there hasn't been a 'fix' for it yet.  That's the only thing I can think of.  So, I'm still stuck.  Any insights on this would be great.

For now, I have music on it and can play it just fine.  I just wished it would work 'out of the box' with a media player app.

---

### Post by gabrielitos on 2009-12-29
It's not a bad situation! The mp3 is working and if you want Ubuntu recognizes it correctly as a media player you should modify this file:

```
/usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi
```

adding a line for this mp3 player! I can not do it now, I just ordered it and I'm waiting for the delivery, but I will do it soon and let you know. By the way, if you make it working, post your result!

---

### Post by odysseusjak on 2009-12-29
Thanks for the tip but I don't know what to add to that file.  Any suggestions?

---

### Post by odysseusjak on 2009-12-30
Okay, I got Banshee to recognize the X-Fi2.  I followed the comment of **gabrielitos** and added it to that file.  What I did was copy another Zen device and then changed the USB ID to 2020.  I then rebooted my system and then plugged in my device.  It launched Nautilus but nothing else happened (it didn't ask me what I wanted to do with it).  I then launched Banshee and after a second, it showed up in the left pane!

I keep you updated on it progress.

---

### Post by odysseusjak on 2009-12-30
Here is the code to add to that file:

<!-- Zen X-Fi2 -->
	<match key="@storage.originating_device:usb.product_id" int="0x2020">
            <addset key="portable_audio_player.access_method.protocols" type="strlist">storage</addset>
	    <append key="portable_audio_player.output_formats" type="strlist">audio/ogg</append>
            <append key="portable_audio_player.output_formats" type="strlist">audio/mp3</append>
	    <append key="portable_audio_player.output_formats" type="strlist">audio/x-ms-wma</append>
	    <append key="portable_audio_player.output_formats" type="strlist">audio/flac</append>
	    <append key="portable_audio_player.output_formats" type="strlist">audio/x-wav</append>
	    <append key="portable_audio_player.input_formats" type="strlist">audio/x-wav</append>
	    <append key="portable_audio_player.audio_folders" type="strlist">Music</append>
	    <append key="portable_audio_player.audio_folders" type="strlist">Playlists</append>
            <append key="portable_audio_player.audio_folders" type="strlist">Video</append>
	    <append key="portable_audio_player.audio_folders" type="strlist">Pictures</append>
	    <append key="portable_audio_player.audio_folders" type="strlist">Recorded</append>
	    <append key="portable_audio_player.playlist_formats" type="strlist">audio/x-mpegurl</append>
	    <append key="portable_audio_player.playlist_path" type="string">PLAYLISTS/%File</append>
          </match>

Banshee is telling me that the device doesn't support playlist so I'm not sure what the deal is with that.  Although, I just noticed that the string states the format is 'x-mpegurl' while the format of the player is actually m3u.  So I'm going to try editing that and see what happens.

[EDIT] Changing the format to m3u didn't help.  Banshee still states that it doesn't support playlists.  I'll now try to see if I can sync it!

---

### Post by odysseusjak on 2009-12-30
IT WORKED!!!

I just synced my Zen X-Fi2 with Banshee!  It removed 13 tracks and added 30.  I searched for 'Unknown Caller' by U2 before I did the sync and it wasn't there.  I searched again after the sync and it was there!  I even played it from the player within Banshee!

Open Source software is absolutely amazing.  I couldn't have done it without it.

Now if we can just figure out how to get playlists to work and I'll be set.

---

### Post by odysseusjak on 2010-04-11
I think we need to mark this as unsolved.  I'm testing 10.04 and this 'fix' doesn't work.

---

### Post by odysseusjak on 2010-05-01
Actually, it did work.  I suppose it had something to do with HAL being re-added.

---

### Post by Barrettr33 on 2010-05-27
I purchased the Zen X-Fi2 and as far as playing music and videos, its fine.
But, the Contacts and Tasks icon are there for show. They **do not function** at all.
I have spoke to many techs and they have confirmed the those features are there for show the Creative Central has **no support** for those features.

---

### Post by niyam on 2010-07-20
oh! i so badly want to use the 'contact's and the 'calendar' feature on my new xi-fi 2 under ubuntu 9.04. i tried manually adding a .ics file to check if it would get recognized. the device just rebooted. don't have or use windows to know what their software is supposed to do. have to grab a windows machine from somewhere to install the firmware upgrade, maybe that might solve the issue a bit. anyone has had any luck with this?

niyam

---

### Post by niyam on 2010-07-21
Does the firmware upgrade brick it? have read some random reports on cnet's site by readers. some have dutifully followed the firmware upgrade to find it bricked. just downloaded the 15 july 2010 upgrade, but am twitching nervously on this one. 
on the other hand, what firmware version are you using, and any problems or freezes?
please tell me.


thanks
niyam

---

### Post by shug0131 on 2010-11-01
Hi

I followed the suggestions made about making Banshee sync with the player. These seem to do what they say. Thanks ! 

I used this to do the intial upload to the player  of all my tracks (having had the memory wiped previously) so about 4000 tracks.

So Banshee displays all the track tag information, but as far as the player is concerned it doesn't get the tag information, so  I can't search by album or artist and just have a load of tracks titled "01.mpg, unknown artist, unknown album".:(

Maybe there is some problem with the tags/format I've used on my PC? I think I got round this previously by using my Windoze PC at work with a Tag Editor program to use the directory structure to infer albums/artists. Is there a better way out there? What Tag Editors are known to work with Ubuntu/Creative Zen X-Fi? 

Thanks

---

### Post by labinnsw on 2010-11-13
> **odysseusjak said:**
> Actually, it did work.  I suppose it had something to do with HAL being re-added.

What do you mean by "re-added?" [I have done everything you have done up to this point]("http://ubuntuforums.org/showthread.php?t=1617280") with a Zen Style 300, but it is still not seen as an audio player. (Tried your code block and when it did not work I tried another one.)

---

### Post by labinnsw on 2010-11-30
[See this link if you have a Creative Zen Style 300]("http://forums.mycreativefansite.com/zen-style-100-300/zen-style-playlist-problem/msg29912/#msg29912") Read from that point forward to get this application working on Linux.

---

