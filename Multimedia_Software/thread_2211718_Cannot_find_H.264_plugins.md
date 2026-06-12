---
title: "Cannot find H.264 plugins"
date: 2014-03-17
forum: Multimedia Software
---

### Post by SeijiSensei on 2014-03-17
Kubuntu 14.04, but I think it applied to earlier versions I've run.

Programs like Dragon Player and the video previewer in Dolphin routinely pop up a dialog box that says there is no H.264 decoder plugin available.  Then the app searches the machine for a matching plugin and finds none.  I've tried having all the gstreamer plugins known to mankind installed, but I still get the same error.  I've had both 0.10 and 1.0 gstreamer versions as well.  Some discussions about the problem online suggest using the 0.10 plugins, but even when I limit the machine to just that version, the problem remains.

Since nearly every video file distributed these days is H.264-encoded this is a very annoying error.  Luckily you can use mplayer-based solutions since it has its own set of codecs.  I presume this problem has something to do with patent issues surrounding the H.264 codec, but I always check the box during installation to install restricted-extras.  I just forced the installation of both ubuntu-restricted-extras and kubuntu-restricted-extras, and Dragon Player still cannot find an H.264 decoder to use.

---

### Post by mc4man on 2014-03-17
> **SeijiSensei said:**
> Kubuntu 14.04, but I think it applied to earlier versions I've run.

Programs like Dragon Player and the video previewer in Dolphin routinely pop up a dialog box that says there is no H.264 decoder plugin available.  Then the app searches the machine for a matching plugin and finds none.  I've tried having all the gstreamer plugins ....
  I presume this problem has something to do with patent issues surrounding the H.264 codec, but I always check the box during installation to install restricted-extras.  I just forced the installation of both ubuntu-restricted-extras and kubuntu-restricted-extras, and Dragon Player still cannot find an H.264 decoder to use.

Nothing to do with that at all. It's just a case of poor codec detection/installer combined with probably a crappy player.
In gnome sessions sessioninstaller is used & currently seems quite broken on several common codecs, maybe the same for whatever Kubuntu uses if not sessioninstaller
[https://bugs.launchpad.net/ubuntu/+source/sessioninstaller/+bug/1281363](https://bugs.launchpad.net/ubuntu/+source/sessioninstaller/+bug/1281363)

As far as dragon player - it is still using gstreamer0.10 so for h.264 it needs gstreamer0.10-ffmpeg which is not available in 14.04 & likely will not be. So dragon player needs to get current or you'll need to provide the plugin yourself.

---

### Post by Yellow Pasque on 2014-03-17
KDE programs like Dragon and Dolphin use Phonon (which can use different backends, the default being gstreamer0.10). Try installing phonon-backend-vlc and switching the Phonon backend to VLC...

---

### Post by SeijiSensei on 2014-03-17
> **mc4man said:**
> As far as dragon player - it is still using gstreamer0.10 so for h.264 it needs gstreamer0.10-ffmpeg which is not available in 14.04 & likely will not be. So dragon player needs to get current or you'll need to provide the plugin yourself.

Any idea why that package will no longer be supported?  The [page for gstreamer0.10-ffmpeg]("http://packages.ubuntu.com/search?keywords=gstreamer0.10-ffmpeg") provides no information about Trusty other than a link that goes nowhere.  I expect we'll be seeing some support requests here if an LTS version doesn't support H.264 playback without considerable fiddling.

Personally I avoid gstreamer-based video apps because of the morass that gstreamer seems to have become.  For some reason, probably because of Canonical's relationship with Fluendo, gstreamer seems to be the dominant codec library on Ubuntu rather than the mplayer/ffmpeg code.  If I were packaging a distribution for widespread use, I'd include SMPlayer+mplayer2 as the default for video playback.

> **Temüjin said:**
> KDE programs like Dragon and Dolphin use Phonon (which can use different backends, the default being gstreamer0.10). Try installing phonon-backend-vlc and switching the Phonon backend to VLC...

I tried that.  Dolphin no longer complains about an H.264 plugin, but it also doesn't play the video in the information panel either.

There also seems to be a really serious bug in the updates released for 14.04 over the weekend.  Both mplayer and Dragon crash the X server.  I even built a new version of mplayer2 from the git repository this morning, and it doesn't work either using the default xv output driver.  The version in the Ubuntu repositories works if I select the OpenGL driver, but with xv it crashes the X server as well.  None of this was the case on Friday.

---

### Post by Yellow Pasque on 2014-03-17
> Any idea why that package will no longer be supported?
It's not compatible with newer versions of libav, and programs still using gstreamer0.10 should update to gstreamer1.0 There are threads with much more detail but searching for them is left as an exercise for the reader ;)

---

### Post by mc4man on 2014-03-17
Can't say I see that here (Ubuntu install), xv works fine in mplayer, mplayer2, mpv though here generally default to va_gl (libvdpau-va-gl1

There was a bug fix last week to xorg-xserver to fix some crash when using nvidia-prime, maybe worth your time to see if that's affecting you by downgrading to previous version.
Myself only have one laptop now with nvidia gtk775m so only use the onboard Intel for linux (4600), last time I tried nvidia-prime found it to be worthless for general purpose use & video playback as there is no shred of vsync

Anyway bug that caused change - 
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1280743](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1280743)
(generally speaking you only need to downgrade 2 packages + 1 -dev if installed, though should be checked before doing so..

---

### Post by monkeybrain20122 on 2014-03-17
So what happens to html5 video playback for Firefox? It relies on gstreamer0.10-ffmpeg to decode h264 and works beautifully in 13.10.  It would be quite unacceptable if FF cannot play html5 videos in 14.04. What is the reason to remove the package?

Edited bug report [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/1275556](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/1275556)

---

### Post by mc4man on 2014-03-17
> **monkeybrain20122 said:**
> So what happens to html5 video playback for Firefox? It relies on gstreamer0.10-ffmpeg to decode h264 and works beautifully in 13.10.  It would be quite unacceptable if FF cannot play html5 videos in 14.04. What is the reason to remove the package?

Edited bug report [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/1275556](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/1275556)
Officially I gather wait until FF supports gst1.x

The main reason removed is that it won't build off of current libav source & Debian/Ubuntu will not be inclined to statically link (ie., use the included libav in plugin source.
You can - 
try the Deb Multimedia package
build yourself (disable use system libs, patch as needed
I had a build in a test ppa but have recently removed, placed [here]("https://launchpad.net/~mc3man/+archive/trusty-media") instead (atm not properly described, more for personal use...

---

### Post by monkeybrain20122 on 2014-03-17
Hi,
Your link is not working. Took me to lauchpad 'lost something'

When do you think FF will support gst1.0?

---

### Post by Yellow Pasque on 2014-03-17
^That's already been answered in [http://ubuntuforums.org/showthread.php?t=2208040](http://ubuntuforums.org/showthread.php?t=2208040)

[QUOTE=mc4man]
choices -
Wait till FF supports gst1.x
Try deb multimedia package
Build your own package, configure not to use system libs
Use the test ppa [https://launchpad.net/~mc3man/+archive/trusty-media](https://launchpad.net/~mc3man/+archive/trusty-media)[/QUOTE]

> What is the reason to remove the package?
Probably because it will not build with newer versions of libav...

---

### Post by mc4man on 2014-03-17
poor c&p on my part, fixed

---

### Post by monkeybrain20122 on 2014-03-17
Thanks.

---

### Post by Yellow Pasque on 2014-03-17
> **SeijiSensei said:**
> Personally I avoid gstreamer-based video apps because of the morass that gstreamer seems to have become.
Well, if you're using Dragon and other KDE apps and have Phonon backend set to gstreamer, then you're really just using a gstreamer-based player with a thin abstraction layer.

> For some reason, probably because of Canonical's relationship with Fluendo, gstreamer seems to be the dominant codec library on Ubuntu rather than the mplayer/ffmpeg code.
Yeah, I'm sure that's part of it. From Kubuntu's viewpoint, it just comes down to choosing a Phonon backend. I'm not a big KDE user, so I have no idea whether they're moving to VLC backend (which is based on ffmpeg) for default.

> Dolphin no longer complains about an H.264 plugin, but it also doesn't play the video in the information panel either..
That's part of the double-edged sword that is Phonon. It makes it easier on devs and for users to choose which media framework they want, but then you get silly bugs that occur in one of the backends. Phonon's detractors think along the lines of, "Instead of 50 backends that work fairly well, we should just have one that works really well." (You could put me in that camp ;) )

---

### Post by monkeybrain20122 on 2014-03-17
if I want to compile gstreamer0.10-ffmpeg against a static ffmpeg which version of ffmpeg should I use?

Edited: looked at the build dependencies it seems rather painful to compile, best to be able to avoid it.

---

### Post by mc4man on 2014-03-17
> **monkeybrain20122 said:**
> if I want to compile gstreamer0.10-ffmpeg against a static ffmpeg which version of ffmpeg should I use?

Edited: looked at the build dependencies it seems rather painful to compile, best to be able to avoid it.

There would be no real advantage to replacing the libav source that's in the gstreamer0.10-ffmpeg source. Gstreamer  moved to libav a while ago so that's what should be used.
I guess if one wanted to 'slightly' improve upon whatever version is in the plugin source they could to some extent, hardly worth the effort, particularly at this point where it's only needed for a few apps or app uses.

---

### Post by monkeybrain20122 on 2014-03-17
> **mc4man said:**
> There would be no real advantage to replacing the libav source that's in the gstreamer0.10-ffmpeg source. Gstreamer  moved to libav a while ago so that's what should be used.
I guess if one wanted to 'slightly' improve upon whatever version is in the plugin source they could to some extent, hardly worth the effort, particularly at this point where it's only needed for a few apps or app uses.

But I think the reason why it is removed is that it doesn't compile with Trusty's libav source so whatever you use (ffmpeg or libav) you still need to make a static library of an older version. Am I missing something?

---

### Post by mc4man on 2014-03-17
> **monkeybrain20122 said:**
> But I think the reason why it is removed is that it doesn't compile with Trusty's libav source so whatever you use (ffmpeg or libav) you still need to make a static library of an older version. Am I missing something?
I believe we're drifting off-topic here but yes to Am I ...
The libav source is already in the plugin's source, basically it's just a matter of Not using the configure option "--with-system-ffmpeg " that Debian/Ubuntu use in their rules file
(Deb-multimedia also removes that option
Actually from gstreamer's perspective the preferred build method is to use the supplied libav source, not system shared, at least it's stated as such in their configure script.

---

### Post by monkeybrain20122 on 2014-03-18
> **mc4man said:**
> 
The libav source is already in the plugin's source, basically it's just a matter of Not using the configure option "--with-system-ffmpeg " that Debian/Ubuntu use in their rules file
(Deb-multimedia also removes that option
Actually from gstreamer's perspective the preferred build method is to use the supplied libav source, not system shared, at least it's stated as such in their configure script.

That makes sense. Not sure why Ubuntu insists on using system shared, it is a major usability bug for not being able to play html5 on Firefox while the fix sounds simple enough.

Thanks for the ppa. Please keep it available. 

Just installed gst0.10-ffmpeg and tested it on Vimeo. Worked great and installed cleanly (no messy dependencies which I was half worrying about as I get ffmpeg 2.1.4 from [https://launchpad.net/~samrog131/+archive/ppa?field.series_filter=trusty](https://launchpad.net/~samrog131/+archive/ppa?field.series_filter=trusty) and use all its dev files to compile things like mpv and vlc)  Need to install allso gst0.10-fluendo-mp3 to play soundcloud in html5 on FF (maybe just have to install gst0.10-plugins-ugly?)

---

### Post by Yellow Pasque on 2014-05-19
Sorry, nvm

---

