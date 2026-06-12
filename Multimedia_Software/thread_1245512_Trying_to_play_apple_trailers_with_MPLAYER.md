---
title: "Trying to play apple trailers with MPLAYER"
date: 2009-08-20
forum: Multimedia Software
---

### Post by abartylla on 2009-08-20
Alright I've been trying to play apple.com trailers. Using synaptic I removed the totem--mozilla plugin then installed mplayer. When I click on any of the resolutions or sizes to view the movies the mplayer pop up logo jumps for a split second then firefox closes without explanation. This all occurs in under 1 second. Also trying to view youtube videos on external sites like digg.com is impossible. I get sound but no video the youtube window freezes.

Any help would be greatly appreciated

---

### Post by zshuford on 2009-08-20
Apple did something.  No one seems to know what yet.

[http://ubuntuforums.org/showthread.php?t=1245441](http://ubuntuforums.org/showthread.php?t=1245441)

---

### Post by lovinglinux on 2009-08-20
[Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683)

I follow the tutorial above every time I install Ubuntu and don't have any media problems.

I use gecko-mediaplayer plug-in, which is great.

---

### Post by LoneSt4r on 2009-09-14
> **lovinglinux said:**
> [Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683)

I use gecko-mediaplayer plug-in, which is great.

Gecko solved it for me for a while, but not anymore...  Any idea what to do next?

Right now, using Gecko or the standard mplayer, the media file starts and then restarts a fraction of a second later...

---

### Post by LoneSt4r on 2009-09-14
I found a workaround at [http://www.linuxformat.co.uk/forums/viewtopic.php?p=77131]("http://www.linuxformat.co.uk/forums/viewtopic.php?p=77131")

> OK, a solution of sorts, with many thanks to some clever guys on the ubuntuforum.org, where I also posted this problem.

Install the Firefox add-on User Agent Switcher and in its own setup system make a new user agent and in the top box of the setup, call it Quicktime 7.6.2. In the second box enter
Code:
QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)

and save it.
Now to see quicktime trailers you can simply set the firefox window to the new user agent (I use the toolbar button which you can add), and the trailers will play again, thinking they are using quicktime, rather than a linux movie player, gecko-mediaplayer in my case.

This did it for me!

---

### Post by ajgreeny on 2009-09-18
Yes this is exactly what I did some time ago now.  It simply fools the apple site into believing that you are using a platform which it supports, ie windows or mac.

Here is a screenshot of the config of the new user agent profile.

---

### Post by treris on 2009-12-19
Seems to be working for me as well with Kubuntu Karmic and firefox 3.5.6, very nice, thanks to all!

---

