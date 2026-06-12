---
title: "Strange Banshee Lyrics Error"
date: 2010-01-07
forum: Multimedia Software
---

### Post by Kozar on 2010-01-07
I'm using the Banshee music player and am having an odd error with the lyrics plugin. It'll bring up the lyrics for most songs but when it does they are composed into just one continuous sentence like this:

lyric lyric lyric lyric lyric lyric lyric lyric
lyric lyric lyric lyric lyric lyric lyric lyric
lyric lyric lyric lyric lyric lyric lyric lyric
lyric lyric lyric lyric lyric lyric lyric lyric

See. All just in one block. 

Other times when Banshee can't find the lyrics and brings up a list of suggestions or offers the option to fill them in manually, clicking on any of the options causes Banshee to shut down immediately.

Is there any way to fix this?

---

### Post by boombox1387 on 2010-01-09
Which version of Banshee are you using?  And, probably more importantly, which lyric plugin are you using? what version of the plugin are you using? where did you download the plugin from?

Banshee doesn't have a built in lyric plugin, so you must have gotten yours from a third party.  Depending on when they last updated the plugin, it may or may not even be compatible with recent versions of Banshee.

Still, a third-party plugin shouldn't be able to crash the whole application, and if that's the case, the issue should be reported to the Banshee team.

---

### Post by Kozar on 2010-01-15
I have banshee 1.5.0.0 and the lyrics plugin reads as 0.0.0.0.

Could you tell me how to remove it so I can install a better one?

---

### Post by boombox1387 on 2010-01-19
I'm still not exactly sure which lyrics extension you're using, but the "most official" option just got a much-needed update.  You can [read about it here]("http://www.mentby.com/Group/banshee-list/new-year-and-new-lyrics-plugin.html").

If you want to add (or update to) this extension, you'll need to add [the Banshee Team PPA]("https://launchpad.net/~banshee-team/+archive/ppa") to your software sources.  When you get your updates, you'll be updated to Banshee 1.5.2, and you'll be able to install the package bansheelyricsplugin, which will give you the newest version (0.8.1) of the best lyric plugin that I know of.

Also, it should be pretty easy to disable the plugin you're using now.  Go to Edit > Preferences > Extensions [tab] in Banshee, find the lyric plugin, uncheck it.

Good luck, and let me know if you run into problems along the way.  I haven't actually updated to the lyric plugin that I'm recommending, so let me know if it's any good.

---

