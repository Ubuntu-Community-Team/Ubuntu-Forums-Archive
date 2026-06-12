---
title: "Jerky video and no myspace sound"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by kousen on 2008-01-05
I recently installed 7.10 on a Dell Inspiron 6000.  My son's band has some music files on their MySpace page ([http://myspace.com/averagescorerocks](http://myspace.com/averagescorerocks)), but when I went there, FireFox told me I needed plugins to make it work.

I followed the instructions in the sticky notes here, which means I installed the "flashplugin-nonfree" and the various GStreamer options.  After that, I could see YouTube videos, but the MySpace audio player just flashed (no pun intended) at me and never worked.  I have a feeling it's connecting and disconnecting over and over again, which is why I don't get any sound.

Digging around in the forums, I found a post on installing the various multiverse packages.  I did that, and now YouTube videos are very jerky (though the sound comes through okay), but the MySpace problem hasn't changed at all.

I don't know what else to try.  I was a Linux user many years ago (about 10 to 15), but I don't have much experience with Ubuntu.  I'm comfortable using the terminal, however.

Are there any diagnostics I can run?  Do I need to uninstall any of the plug-ins I already installed?  I tried doing an update, but it said everything was up to date.

Thanks,

Ken Kousen

---

### Post by kousen on 2008-01-06
I managed to solve this.  I just went to the URL for the FireFox flash plugin ([https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7)) and installed it from there, and now everything works.

I have no idea why installing from the plugin directory rather than just letting it do the install itself worked, but it did.

Hopefully that will help somebody, though.

Ken

---

