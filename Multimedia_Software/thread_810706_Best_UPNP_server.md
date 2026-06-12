---
title: "Best UPNP server"
date: 2008-05-28
forum: Multimedia Software
---

### Post by bogoliubov on 2008-05-28
I recently bought a for Pinnacle Showcenter 200 and want to stream music, video and photos to it. Does anyone have any recommendations regarding the server software to use? I'll need transcoding since the Showcenter 200 has some weird ideas about Dolby Digital.

So far I am aware about:
MythTV
MediaTomb
GeexBox (ushare)
Fuppes
Gmediaserver
myiHome
wizd

I have only tried (quickly) MythTV, Mediatomb, Gmediaserver and uShare.
To me it seems that MythTV is a bit to much for simply streaming stuff. Mediatomb seems OK, but not very easy to set up.
uShare seems easy, but doesn't to my understanding have transcoding. Gmediaserver seems to only support some formats...

Any recommendations? Any way of making Mediatomb easy to configure?

Also: can I transcode only the sound in a video file?

Doesn anyone have any experience with the Showcenter 200? It seems some settings can only be accessed from the Windows software (which doesn't run easily under Wine).

Any help is greatly appreciated!

---

### Post by bogoliubov on 2008-05-29
Perhaps this was the wrong section for such a question !?

---

### Post by mini_g on 2008-05-29
> **bogoliubov said:**
> Perhaps this was the wrong section for such a question !?

This is the right section.  Some threads just take longer to answer.

Unfortunately, I have no experience in this area, but after doing some searching, it seems that you have hit the major options.

I don't know if this will help, but here's [Mediatomb's forum]("http://sourceforge.net/forum/?group_id=129766").

Good luck!

---

### Post by bogoliubov on 2008-05-30
Yeah you're right. Thanks though!

---

### Post by amgat on 2008-05-31
I've been using fuppes. Works OK for me. It has a simple web interface that you can rebuild the media index with. but it lacks subtitles support so I will try ushare in the near future.

---

### Post by bogoliubov on 2008-05-31
Ok, anyone who knows how to setup subtitle support in Mediatomb?

---

### Post by amak79 on 2008-05-31
> **bogoliubov said:**
> Ok, anyone who knows how to setup subtitle support in Mediatomb?

If the subtitles are embedded in an MP4 file for example then it's completely up to your device to display them. If your device doesn't support subtitles then you can use MediaTomb's transcoding feature to merge the subtitles and video together. This method can also be used for external subtitles such as SRT.

You will find a VLC based video transcoding script that supports both embedded and external subtitles on the [Gentoo Linux MediaTomb Wiki]("http://en.gentoo-wiki.com/wiki/MediaTomb#VLC"). You might need to set the **SUBTITLE_LANGUAGE** variable in the script to the language you require.

---

### Post by bogoliubov on 2008-06-01
> **amak79 said:**
> If the subtitles are embedded in an MP4 file for example then it's completely up to your device to display them. If your device doesn't support subtitles then you can use MediaTomb's transcoding feature to merge the subtitles and video together. This method can also be used for external subtitles such as SRT.

You will find a VLC based video transcoding script that supports both embedded and external subtitles on the [Gentoo Linux MediaTomb Wiki]("http://gentoo-wiki.com/HOWTO_MediaTomb#Using_VLC"). You might need to set the **SUBTITLE_LANGUAGE** variable in the script to the language you require.

Thanks, I'll have a look at this!

---

### Post by NineseveN on 2008-07-03
I got Mediatomb working without any problem and fairly quickly, but needing a script to make a playlist is a bit much. I really don't want to deal with that right now (have no clue how to make a script yet), but it works well anyway.

I'm trying XboxMediaServer tonight.

Of course, I don't even know if it's possible to send a playlist to my PS3 via UPnP (i.e. so I don't have to scroll through the songs and play them manually each time a song ends). I guess I'll find that out.

But, Mediatomb is very easy to get running and not a bad piece of software at all.

---

