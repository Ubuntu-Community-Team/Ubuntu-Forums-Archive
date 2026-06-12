---
title: "annoying video playback problem"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by weird_c00kie on 2007-10-06
Been a while since I posted here, which is probably a good thing, given that I almost only come here when I'm in trouble :mrgreen:

Over the last few weeks I've had a very annoying problem with video playback.

When I first installed Ubuntu on this laptop (Dell Inspiron 1420) I could play just about any video file I wanted. WMV, AVI, FLV, MPG, DVDs, you name it. But then one day, I downloaded some system updates or whatever it was, and it all went to hell.

Now everytime I try to open a video file, the player starts up, loads the clip and then quits straight away. Both Movie Player and VLC do this. I've tried the various flavors of Movie Player as well (totem, gstreamer, etc etc, even though for the life of me as a n00b I can't see the difference) and it still does it. The same thing happens for DVDs too :(

I've tried uninstalling the media codecs with Automatix so I can reinstall them, but it comes up with an error saying that it won't delete them because other applications will be affected. I also tried uninstalling the codecs by reversing the instructions on the ubuntu guide
```
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install w32codecs
sudo apt-get install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
```
After reinstalling them, the problem persisted.

What really annoys me is that I can still watch FLV videos on YouTube, but when I download them and try to view them, I can't!

Can anyone help me with this? It was just an out-of-the-blue working-one-day-broken-the-next thing. My newbie brain can't think of anything else to try :(



PS. Sorry if there's a thread like this already. I couldn't find anything similar when I searched
PPS. In case anyone asks, the mplayer browser plugin never worked for me. If the browser window was in focus, it wouldn't play at all, while if it wasn't in focus, it would play just the audio for a split second and then stop. Go figure...
PPPS. I don't really care about the mplayer browser plug in, but I'd really like to have my video playback capabilities back!
PPPPS. Don't you love post-script insertions? :D

---

### Post by RomeReactor on 2007-10-06
Hi. Try running Totem from the terminal:
```
totem
```
then open a video file; if it crashes, please post the output here so people can take a look at it.

---

### Post by bubill on 2007-10-06
hi .you means: it's problem of  watching  video on firefox ? oh!  you must install the lastest adobe flash player 9 .  i can watch and listen it

---

### Post by Artemis3 on 2007-10-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/135141](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/135141) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/122979](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/122979) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ah this sounds so familiar: Intel video... Do not use Compiz, Beryl or Compiz Fusion (Desktop Effects or whatever its called in gutsy). Bug in driver i810 and intel won't let you have compositing and video playback, so don't bother.

They seem to be fixing this problem on both, but the intel driver is replacing i810.

---

### Post by weird_c00kie on 2007-10-07
THAT IS SO LAME!!!

I disabled the Desktop Effects and now it works!

When I run totem through the terminal and try to open a video clip it says:
> The program 'totem' received an X Window System error.
This probably reflecs a bug in the program.
The error was "BadAlloc (insufficient resources for operation)'.
(Details: serial 72 error)code 11 request_code 141 minor_code 19)

This is bittersweet news to me. I am so in love with the wobbly windows. Having to lose them now would be like denying myself one of the simplest pleasures in life hehe

Hopefully this bug will be fixed. Until then... I will no longer wobble my windows



Thanks heaps for the easy fix :)

---

