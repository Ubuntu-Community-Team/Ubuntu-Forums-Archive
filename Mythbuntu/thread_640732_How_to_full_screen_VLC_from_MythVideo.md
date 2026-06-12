---
title: "How to full screen VLC from MythVideo?"
date: 2007-12-14
forum: Mythbuntu
---

### Post by NickGray on 2007-12-14
When I play any video file within MythVideo (using VLC as the default player), VLC opens as a small window. Using VLC in MythTV 0.20.2 (Ubuntu 7.10) as my internal player:
```
vlc file://%s vlc:quit
```
** How can I make the video files play full-screen using VLC as my internal player in MythTV?**

---

### Post by balserodeluxe on 2008-07-15
See point #3 in [http://mythtvbox.blogspot.com/2006/10/switching-from-mplayer-to-vlc.html](http://mythtvbox.blogspot.com/2006/10/switching-from-mplayer-to-vlc.html)

it worked for me. 

I cannot seem to get it to be the default player though. Have you had any luck with that?

---

### Post by uteck on 2008-07-23
> **NickGray said:**
> When I play any video file within MythVideo (using VLC as the default player), VLC opens as a small window. Using VLC in MythTV 0.20.2 (Ubuntu 7.10) as my internal player:
```
vlc file://%s vlc:quit
```
** How can I make the video files play full-screen using VLC as my internal player in MythTV?**
Try ```
vlc -f file://%s vlc:quit
```
or use the link from the previous post to edit the vlc config file.

Just realized after posting that you have to edit the config anyway to enable a remote to control VLC.

---

### Post by alizia on 2008-07-23
VLC stands for video LAN player. This is really a very nice player. I like to use it.
_______________________________
alizia
[Wide Circles]("http://www.widecircles.ca")

---

### Post by bobpaul on 2008-09-22
> **uteck said:**
> Try ```
vlc -f file://%s vlc:quit
```
or use the link from the previous post to edit the vlc config file.

Just realized after posting that you have to edit the config anyway to enable a remote to control VLC.

I actually don't have a vlcrc file anywhere to be found on my system (even after running VLC once). So, before I went about creating one, I ran 'vlc --help' and found there is a --control directive. Thus, one can simply use:

```
vlc -f --control lirc file://%s vlc:quit
```

---

### Post by jetpeach on 2008-10-21
could you tell me where exactly this vlc command should be entered in mythtv? the page
[http://mythtvbox.blogspot.com/2006/10/switching-from-mplayer-to-vlc.html](http://mythtvbox.blogspot.com/2006/10/switching-from-mplayer-to-vlc.html)
says to put it in "video settings" but my list of available preferences to choose from is only "general   appearance   screen setup wizards    tv settings"
inside tv settings i can pick a "decoder" for video files, but no place to add a command line,
thanks for any help!
jetpeach

---

