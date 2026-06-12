---
title: "Totem opening everything in firefox or deluge despite not being affected to MIME"
date: 2008-04-22
forum: Multimedia Software
---

### Post by semon on 2008-04-22
Hello****, 

I want to open video files with **Smplayer** and audio files with **amarok**. So i changed the default applications for these files (in nautilus, right click, properties, open with, ...) I made sure totem was not in the list anymore. In nautilus everything works fine.

here is my problem :

When i try to open movie files or audio files in firefox (for a downloaded file) or deluge torrent **totem** is always called. That's annoying since i don't like totem.

Anyone can help ?

(i'm on hardy, with gutsy I never had this problem)

---

### Post by cor2y on 2008-04-22
it may be that totem is associated with torrent files and that the totem webbrowser plugin is installed , i'd suggest removing it via synaptic and installing  mplayer's media plugin then restart firefox.
In firefox3 or firefox2 go to Edit->Preferences->Applications and look up what the browser does for those file types, i'd set it to always ask with bittorrent files and you can either save to disc or tell it to use the torrent client of your choice (you can find the executable in usually /usr/bin or /usr/local/bin) for the audio mime types if its plugin streams set mplayer plugin should be default after the restart and need no changing, for downloading it should default to ask.

---

### Post by semon on 2008-04-22
i'm sorry but in think you misunderstood me. I don't have problems opening torrent files or streaming medias.

the problem is, when i double click on a downloaded file (a mp3 or avi) in the firefox's download manager, the file open in totem. (i've checked the mime type in firefox and they are all set to mplayer but i think those settings are irrelevant to my problem).

And it is the same when trying to opening a avi in deluge torrent. It always opens in totem even when the mime type is set to smplayer in nautilus.

I hope it is more clear like that.

---

### Post by cor2y on 2008-04-22
Well theres the quick way to set your mime types.
take a look at your ~/.local/share/applications folder and look at the launchers in there to see what you will need to edit.
You want smplayer to handle all video and deluge torrents, then you will need to edit your mimeapps.list in that folder.
Open it with gedit look for the file types and change to the application you wish to use.
Example
```
video/x-avi=totem.desktop;
```to ```
video/x-avi=smplayer.desktop;
```if its already set that way then totem should not be able to take over when double clicking now if there is more than one entry example ```
video/x-avi=totem.desktop;smplayer.desktop;
``` the remove the totem one remember to leave the ; at the end of the entry, ```
video/x-avi=smplayer.desktop;
```save and then try it.
If it still does it then i don't know.

---

### Post by semon on 2008-04-22
as i said i've already set the mime types in nautilus , here is my ~/.local/share/applications

```
[Added Associations]
video/x-msvideo=smplayer.desktop;
video/mpeg=smplayer.desktop;
video/x-ms-wmv=smplayer.desktop;
application/x-quicktime-media-link=smplayer.desktop;
video/mp4=kde-amarok.desktop;
audio/mpeg=kde-amarok.desktop;
x-content/video-dvd=smplayer.desktop;
x-content/audio-player=kde-amarok.desktop;
x-content/image-dcf=f-spot.desktop;

[Removed Associations]
video/x-msvideo=mplayer.desktop;totem.desktop;
video/mpeg=totem.desktop;mplayer.desktop;
video/x-ms-wmv=kde-amarok.desktop;totem.desktop;mplayer.desktop;
video/mp4=totem.desktop;
audio/mpeg=rhythmbox.desktop;smplayer.desktop;mplayer.desktop;totem.desktop;

```

But even with these associations totem always show when opening a media file on firefox or deluge torrent (and probably other applications)

---

### Post by semon on 2008-04-23
does this mime list look correct to you ?

video/x-msvideo is avi right ?

and audio/mpeg mp3 ?

---

### Post by cor2y on 2008-04-27
The list is correct its a "feature" of firefox3 thats the problem in the old days of firefox 1 and 2 you could go the mime type list via Edit->Preferences and select the Content Tab select file type look for your file type right click on it and edit if it was streamed , downloaded opened with an app or even which app launched it when saved.
See this page for what i mean [http://support.mozilla.com/en-US/kb/Managing+file+types](http://support.mozilla.com/en-US/kb/Managing+file+types)
Firefox3 seems to have streamlined or removed that option.

---

