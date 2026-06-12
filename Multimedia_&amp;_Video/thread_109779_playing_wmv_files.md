---
title: "playing wmv files"
date: 2005-12-29
forum: Multimedia &amp; Video
---

### Post by robertobaggio2k on 2005-12-29
i try to play wmv files on ubuntu 5.10 but directly from sites n when i click on the video it asks me to launch totem, the video starts but with no sound, how can i fix it? Also wat is the exact code in order for me to see wat driver is being used for my video card? thanks alot

---

### Post by mcduck on 2005-12-29
Have you got all codecs installed? Here's a nice guide to installing those: [http://makuchaku.info/amnesty/#codecs]("http://makuchaku.info/amnesty/#codecs")

You could try installing mplayer and plugin for firefox, do 'sudo apt-get install mplayer-386 mplayer-fonts mozilla-mplayer' (you can replace mplayer-386 with mplayer-586 if you have a Pentium or later, mplayer-K5 if you got Athlon)

For video card, I can't remember the nice command that gives you only the driver used, but if you run 'glxgears -info' it is shown in the first lines of the output. like this:
GL_RENDERER   = RADEON 9600 XT Generic
GL_VERSION    = 1.3.5272 (X4.3.0-8.16.20)
GL_VENDOR     = ATI Technologies Inc.

---

### Post by robertobaggio2k on 2005-12-29
yeah i have codecs installed n samething with the mplayer for firefox it says already installed...the problem is that firefox automatically launches totem...is tehre a way to change that?

---

### Post by shin on 2005-12-29
Uninstall totem :P
But if you want to keep it - make sure that you got mplayer plugins in your firefox plugins directory. To find where are your plugins for firefox, type
ls -l /usr/bin/firefox

Then go to that directory and to plugins. For wmv there should be mplayer-in-wmp.so and mplayer-in-wmp.xpt. If they're not here - installing mozilla-mplayer should do the thing.

If there are any totem plugins (dunno about it) - delete them.

---

### Post by robertobaggio2k on 2005-12-29
i found the mozilla plugin should i download the rpm file our source...and wat command do i use to install?

---

### Post by robertobaggio2k on 2005-12-29
nevermind i just checked the directory i ahve both of those files isntalled...i dunno y totem gets launched is tehre an option to disable that?

---

### Post by shin on 2005-12-29
mozilla-mplayer is in repo archive.ubuntu.com. In multiverse.
It's 3.05 but works fine. Still you can use search function because I saw someone posting mozilla mplayer plugin 3.11.

Don't experiment with rpms. You can convert them to .deb with alien but it is not recommended if there are debs. Of course you can always compile it. But as I mentioned before - there is no real need to do it.

---

