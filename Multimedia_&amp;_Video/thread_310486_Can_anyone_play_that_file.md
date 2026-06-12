---
title: "Can anyone play that file?"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by javierfh on 2006-12-01
The file i want to play it is in the following link, in fact the one i wanted to play is the bigger one but the small one doesnt play either.

[http://www.apple.com/quicktime/guide/hd/nasaspaceshuttle.html](http://www.apple.com/quicktime/guide/hd/nasaspaceshuttle.html)

So i assume the problem is the codec right? the support for H.264 and if thats the case, how can this be solved? Any solution?
Are there any plugins, to add support for these formats, to different players,as for example VLC?
And what happens with HD TV can it be watched anyway?


Thanks in advance and sorry if i sound little fuzzy in some of the questions.

Javi

---

### Post by hanzomon4 on 2006-12-01
I can play it, using the mplayerplug-in 3.25

---

### Post by javierfh on 2006-12-01
> **hanzomon4 said:**
> I can play it, using the mplayerplug-in 3.25

How you install that?
or where in fact :)

thanks for all help you can provide me.

Javi

---

### Post by hanzomon4 on 2006-12-01
I used [this guide]("http://ubuntuforums.org/showthread.php?t=179694") to compile from source, but if you're running edgy try  running this first....... ```
 sudo apt-get install mplayerplug-in 
```

---

### Post by javierfh on 2006-12-01
> **hanzomon4 said:**
> I used [this guide]("http://ubuntuforums.org/showthread.php?t=179694") to compile from source, but if you're running edgy try  running this first....... ```
 sudo apt-get install mplayerplug-in 
```

Doesnt work...still crashes..
i have edgy and installed 3.31-1 and still nothing..as soon as i try to open it the bug report tool launches and well..it crash.

Any idea whats going on?


Javi

---

### Post by hanzomon4 on 2006-12-01
If you have an x86(intel) cpu this should work.

[LIST=1]
[*]Ok first download the attachment
[*]Then move the tar.gz file to the firefox plugin dir ```
sudo mv ~/Desktop/plugins.tar.gz  /usr/lib/firefox/plugins
```
[*]Last un pack the tar.gz ```
 sudo tar zxf /usr/lib/firefox/plugins/plugins.tar.gz
[/LIST]

```

Restart firefox and see if it works

---

### Post by javierfh on 2006-12-01
> **hanzomon4 said:**
> If you have an x86(intel) cpu this should work.

[LIST=1]
[*]Ok first download the attachment
[*]Then move the tar.gz file to the firefox plugin dir ```
sudo mv ~/Desktop/plugins.tar.gz  /usr/lib/firefox/plugins
```
[*]Last un pack the tar.gz ```
 sudo tar zxf /usr/lib/firefox/plugins/plugins.tar.gz
[/LIST]

```

Restart firefox and see if it works

I followed your instructions but nothing...same situation..
doesnt work at all..it just sounds some weird sounds...like every two seconds...and it opens inmediately the bug report tool.


Any other suggestion?

Javi

---

### Post by hanzomon4 on 2006-12-01
I can't make heads or tails of it, does it work for other videos? I would file a bug report at this point

---

### Post by christhemonkey on 2006-12-01
Works fine for me, with only usual sort of gstreamer plugins installed!

From about: plugins:
> QuickTime Plug-in 7.0 (compatible; Totem)

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes

---

### Post by itchanddino on 2006-12-01
Try changing your video drivers to X11 or a different set.

---

### Post by javierfh on 2006-12-02
> **hanzomon4 said:**
> I can't make heads or tails of it, does it work for other videos? I would file a bug report at this point

Thanks for your interest.
In fact i filled the bug report and got email saying that there is already report for that.
So i might not be the only one..but i wonder why and annoys me, because i should have powerfull enough computer, video card and good monitor..grr :D

Thanks,

Javi

---

### Post by javierfh on 2006-12-02
> **christhemonkey said:**
> Works fine for me, with only usual sort of gstreamer plugins installed!

From about: plugins:

Hi,
i guess i have gstreamer plugins also installed.
I have these:

gstreamer0.10-pitfdll
gstreamer0.8-pitfdll (which i dont even know whats the difference with previous but description looks different)
gxine
libquicktime0
libvlc0
libxine1
libxine-extracodecs
quicktime-utils
quicktime-x11utils
vlc

so is the one you are referring different one?

Javi

---

### Post by javierfh on 2006-12-02
> **itchanddino said:**
> Try changing your video drivers to X11 or a different set.

What do you mean? do you mean replacing the nvidia drivers for the generic vesa video in Xorg.conf? or how to do that??

Thanks in advance for all the help and suggestions.

Javi

---

