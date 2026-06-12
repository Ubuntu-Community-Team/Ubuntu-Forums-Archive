---
title: "VLC 0.8.6 Mozilla Plugin Keyboard shortcuts / Controls"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by ariel on 2007-08-26
(note: I asked this in VLC forums but not reply so yet...)

Hi, I'm using VLC 0.8.6 on Feisty; it works great. I'm also using vlc-mozilla-plugin, as it is the only plugin in my system that does not stutter when playing back BBC news embedded content. (both mplayer & totem-gstreamer plugins stutter badly with embedded video)

The plugin is a little barebones in the sense that it does not seem to have any visual interface. I know it offers a javascript API but that does not help in my BBC News use-case. Basically I would like to be able to "Pause" and video, and display the Total and Running durations.

I noticed that some pressing some keys produce effects. For instance, "f" does full screen. The Space-Bar displays a little OSD with the pause sign but it does not stop the video. Is this a bug? or is there any other way to Pause the plugin? 

Also: is there any key combination that would display the Total and Running lengths of the video being played back?

Alternatively: is there any other mozilla plugin that would use VLC as backend but is more feature rich than vlc-mozilla-plugin??

Thanks!!

---

### Post by ddrichardson on 2007-08-27
These commands can be embeded as Javascript in the site you're viewing but of course the BBC isn't going to have put them there.

The only others I know of are:
[LIST]
[*] Page Up/Page Down/Shift + Right Arrow/Shift + Left Arrow: seek (10 secs)
[*] Home/End: Beginning/End of file
[*] Space: Pause
[*] f/F: fullscreen
[*] q/Q: quit vlc
[*] Esc: exit fullscreen/Stop input[/LIST]

---

### Post by ariel on 2007-08-29
DD, is the pause function working for you in the plugin? if so, what is the plugin & vlc version you are using?

It doesn't seem to work in feisty's default version; pressing p displays the pause sign for a second over the video, but the stream is not stopped.

---

### Post by ddrichardson on 2007-08-30
Yes pause works, VLC 0.8.6a, FireFox 2.0.2 - not at the Ubuntu box today so can't tell you what  plugin version, but whatever the current Fiesty one is.

---

