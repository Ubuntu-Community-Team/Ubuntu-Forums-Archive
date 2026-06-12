---
title: "Visual WYSYWYG subtitle editor with integrated workflow support?"
date: 2014-09-14
forum: Multimedia Software
---

### Post by sgofferj on 2014-09-14
Hi,

I'm just in the finishing moments for a documentary I shot and I need to subtitle it. I was thinking of using SRT subtitles or something comparable because that SHOULD be easy to convert into anuthing else. I'm looking for a nice subtitle editor which can play a video file and allows we to create subtitles directly linked with the video-file. Ideally, the editor would have some post editing workflow support, such as the ability to invoke ffmpeg/avconv and pass the video file as well as the subtitles to it to create e.g. an mpeg transport stream.

Is there anything like that available for (K)Ubuntu?

-S

---

### Post by Rog131 on 2014-09-16
Something like it ? : [http://kde-apps.org/content/show.php/?content=162048](http://kde-apps.org/content/show.php/?content=162048)

Ubuntu package: [http://packages.ubuntu.com/search?keywords=subtitlecomposer&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=subtitlecomposer&searchon=names&suite=all&section=all)

> Description: Subtitles editor for KDE
 A text-based subtitles editor for KDE supporting basic operations (text,
 time and style edition), realtime previewing and spell checking. Other
 fancy features are delaying all subtitles in the current subtitle file,
 checking errors or creating translations.
 .
 Different backends (GStreamer, MPlayer, Phonon or xine) can be used to play
 the realtime video preview which helps to synchronize the subtitles.

---

### Post by sgofferj on 2014-09-17
Jup, or Gnome Subtitle Editor or AegisSub but they don't have any workflow functions... Besides, AegisSub is the only one which seems to work properly on my kubuntu 14.04. KDE Subtitle editor just dies without comment and Gnome Subtitle Editor complains that GStreamer plugins for h.264 and MP4 AAC are missing but I double-checked and I have all GStreamer plugins that apt-cache can find installed.

Anyways, the workflow is the key here, because converting SRT (or any other open source subtitle file format) together with the video into an MPEG transport stream seems to be tedious at best when done manually.. And I'm not talking about "burning" the subs into the video file but properly encoding them as separate stream in the MPEG TS.

---

### Post by mc4man on 2014-09-17
> Gnome Subtitle Editor complains that GStreamer plugins for h.264 and MP4 AAC are missing but I double-checked and I have all GStreamer plugins that apt-cache can find installed.
It wants gstreamer0.10-ffmpeg
(probably a moot point as likely won't satisfy your needs..

---

### Post by SeijiSensei on 2014-09-18
Is there a reason why you don't want to use MP4 or Matroska containers, both of which support soft subtitle streams?

---

### Post by sgofferj on 2014-09-18
Yeah. The TV-stations here would like to have a DVB-TS :). I have done a small documentary and am trying to prepare it so that the TV-stations can use it :).

Edit:
Trailer: [https://www.youtube.com/watch?v=dE_uhyt7-1U](https://www.youtube.com/watch?v=dE_uhyt7-1U)
Until now, edited completely with open source software under Linux and I'd like to keep it that way :).

---

