---
title: "Too many Firefox media plugins?"
date: 2009-05-11
forum: Multimedia Software
---

### Post by joshzam on 2009-05-11
Is it detrimental to have too many Firefox plugins? I'm not talking about extensions - I know they can sometimes slow down performance. But when do plugins start to overlap and possibly start competing with one another?

I can generally play video and audio just fine through my Firefox setup (3.0.10, Jaunty) although Flash video is sometimes a bit choppy (just a bit). But quicktime videos won't play at all on Apple's movie trailer site ([http://www.apple.com/trailers/](http://www.apple.com/trailers/)). So I searched for a solution and [someone recommended]("http://ubuntuforums.org/showpost.php?p=7087280&postcount=2") installing gecko-mediaplayer along with ubuntu-restricted-extras and w32codecs.

Before installing *yet another* plugin, I checked to see what I already had installed in Firefox:
Default Plugin
Demo Print Plugin for unix.linux
DivX Browser Plugin [mplayerplug-in]
DivX Web Player
Java Plug-in 1.6.0_13-b03
mplayerplug-in 3.55
Picasa
QuickTime Plug-in 7.2.0 [Totem]
QuickTime Plug-in 7.4.5 [mplayerplug-in]
RealPlayer 9 [mplayerplug-in]
Shockwave Flash [10.0 r22]
Silverlight Plug-in
VLC Multimedia Plug-in [0.9.9a]
VLC Multimedia Plug-in (compatible Totem 2.26.1) [Totem]
Windows Media Player Plug-in [mplayerplug-in]
Windows Media Player Plug-in 10 (compatible; Totem) [Totem]

I use VLC as my standalone video player and Amarok for audio. Should I uninstall some of these Firefox plugins to improve media playback performance inside the browser? Or is there no real disadvantage from plugin overkill?

---

### Post by lovinglinux on 2009-05-11
Some sites might not work when using multiple plugins for the same type of content.

I would stick with gecko-media player and remove the duplicates (totem, vlc...).

---

### Post by psyke83 on 2009-05-12
> **lovinglinux said:**
> Some sites might not work when using multiple plugins for the same type of content.

I would stick with gecko-media player and remove the duplicates (totem, vlc...).

I agree, however...

Removing the actual packages may be undesirable (e.g. attempting to remove Totem plugins may remove the totem package itself, which is part of the ubuntu-desktop metapackage). Instead, *disable* the unwanted plugins via Tools -> Add-Ons -> Plugins in Firefox.

---

### Post by joshzam on 2009-05-12
Simplify. I like it. But I'm not very familiar with gecko-mediaplayer and its functionalities. Does it handle AVI, MOV, WMV, DivX, or Flash? More specifically, which of my plugins should I disable to avoid conflicts with gecko-mediaplayer?

Default Plugin
Demo Print Plugin for unix.linux
DivX Browser Plugin [mplayerplug-in] [COLOR="Red"]???[/COLOR]
DivX Web Player [COLOR="Red"]???[/COLOR]
Java Plug-in 1.6.0_13-b03
mplayerplug-in 3.55 [COLOR="Red"]???[/COLOR]
Picasa
QuickTime Plug-in 7.2.0 [Totem] [COLOR="Red"]???[/COLOR]
QuickTime Plug-in 7.4.5 [mplayerplug-in] [COLOR="Red"]???[/COLOR]
RealPlayer 9 [mplayerplug-in] [COLOR="Red"]???[/COLOR]
Shockwave Flash [10.0 r22] [COLOR="Red"]???[/COLOR]
Silverlight Plug-in
VLC Multimedia Plug-in [0.9.9a] [COLOR="Red"]???[/COLOR]
VLC Multimedia Plug-in (compatible Totem 2.26.1) [Totem] [COLOR="Red"]???[/COLOR]
Windows Media Player Plug-in [mplayerplug-in] [COLOR="Red"]???[/COLOR]
Windows Media Player Plug-in 10 (compatible; Totem) [Totem] [COLOR="Red"]???[/COLOR]

---

### Post by lovinglinux on 2009-05-12
> **psyke83 said:**
> I agree, however...

Removing the actual packages may be undesirable (e.g. attempting to remove Totem plugins may remove the totem package itself, which is part of the ubuntu-desktop metapackage). Instead, *disable* the unwanted plugins via Tools -> Add-Ons -> Plugins in Firefox.

You just have to remove the plugin packages. They won't remove the player itself. Besides, just disabling the plugin might not solve the problem. It already happened to me on a video site. It only worked after removing the conflicting plugin packages.

> **joshzam said:**
> Simplify. I like it. But I'm not very familiar with gecko-mediaplayer and its functionalities. Does it handle AVI, MOV, WMV, DivX, or Flash? More specifically, which of my plugins should I disable to avoid conflicts with gecko-mediaplayer?

It handles DivX, Quicktime, RealPlayer and Windows Media Player. It will play avi, mkv, wmv, mov, mp3, mp4 and common streams. The standalone player should also play flv, but you still need the flash plugin for web content like YouTube.

You should remove these:

DivX Browser Plugin [mplayerplug-in] [COLOR="Red"]???[/COLOR]
DivX Web Player [COLOR="Red"]???[/COLOR]
mplayerplug-in 3.55 [COLOR="Red"]???[/COLOR]
QuickTime Plug-in 7.2.0 [Totem] [COLOR="Red"]???[/COLOR]
QuickTime Plug-in 7.4.5 [mplayerplug-in] [COLOR="Red"]???[/COLOR]
RealPlayer 9 [mplayerplug-in] [COLOR="Red"]???[/COLOR]
VLC Multimedia Plug-in [0.9.9a] [COLOR="Red"]???[/COLOR]
VLC Multimedia Plug-in (compatible Totem 2.26.1) [Totem] [COLOR="Red"]???[/COLOR]
Windows Media Player Plug-in [mplayerplug-in] [COLOR="Red"]???[/COLOR]
Windows Media Player Plug-in 10 (compatible; Totem) [Totem] [COLOR="Red"]???[/COLOR

Follow this tutorial:  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by joshzam on 2009-05-12
Thank you, lovinglinux! I followed your instructions and the guide you linked to and everything (including Apple trailers) is working great. Happy day :)

---

### Post by lovinglinux on 2009-05-12
> **joshzam said:**
> Thank you, lovinglinux! I followed your instructions and the guide you linked to and everything (including Apple trailers) is working great. Happy day :)

You are welcome. That tutorial is really good.

---

### Post by timandjulz on 2009-07-16
I will chime in...

I have tried totem and vlc plug ins for firefox.  Neither one works well... totem was failing to work for me and vlc provides no on screen controls (ffwd, play, pause, etc.)

gecko-mediaplayer seems to work well.  I am glad I ran across this post!

Tim

---

### Post by bobince on 2009-07-17
> Is it detrimental to have too many Firefox plugins?It's detrimental to security to expose more code to the untrusted internet, certainly. There have been endless security holes in browser plug-ins (WMP, Real, QT, Acrobat, Java, even Flash) which on Windows have been exploited to automatically install malware again and again.

Though Linux is rarely targeted by these attacks today, that doesn't mean it's actually safe.

I've uninstalled all plugins except for Flash (which is pretty much essential to using the web today; however its worst excesses can be tempered using the Flashblock add-on). If I really need to view a QT or Real file, I would rather download it (using an add-on such as Unplug) and watch it in a proper media player.

With any luck, Flash video and HTML5 video should continue to squeeze QT, Real and WMP out of the market for web embedding.

---

