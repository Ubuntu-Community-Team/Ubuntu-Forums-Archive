---
title: "Ubuntu 14.10 stopped playing videos?!"
date: 2014-10-17
forum: Multimedia Software
---

### Post by emk on 2014-10-17
After I dist-upgraded my 14.10 today (should be the release version now), videos have stopped playing in mpv and the standard totem. The first frame opens, and the player just sits there. We are talking about mkv Videos with a h264 video track. Any ideas?

Starting mpv from the command line with -v doesn't give the slightest hint - everything green.

---

### Post by Rob Sayer on 2014-10-18
It's still in beta ... the official release date for 14.10 is Oct 23.  Unfortunately you're still dealing with a kettle of worms.

Try the +1 developmental forum here, and install or reinstall vlc or smplayer.  Neither need external codecs.

And in the future, NEVER install an alpha/beta release unless you have very good terminal recovery skills.  The probability of something breaking after an update eventually is about 100%.  I know a couple of guys who maintain unix/linux systems for a living and they won't touch pre stable releases unless they absolutely have to.  Not saying people shouldn't use them but they're definitely not for noobs.

Actually, unless you have a hardware support issue that requires a newer kernel, my recommendation would be to reinstall 14.04.  I won't use anything but LTS releases unless I need that newer kernel version.

---

### Post by mc4man on 2014-10-18
This was a matter that the non playing vids were drm'ed, so case closed..

---

