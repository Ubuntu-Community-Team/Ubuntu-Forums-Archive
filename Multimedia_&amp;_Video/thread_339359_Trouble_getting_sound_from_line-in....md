---
title: "Trouble getting sound from line-in..."
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by Bidimus on 2007-01-15
I'm having trouble getting any sound from my line-in port and I'm not sure where to start or even if this is the right place to post.  I know the physical connections are working because without changing them I can get audio from my external mixer in windows.

I'm not really sure where to start or what information would help here.  I've tried a ton of configurations and various combinations of adding "capture" devices through the gnome mixer such as "aux" or "line".

---

### Post by Bidimus on 2007-01-15
Here is an update... I discovered I actually am getting sound through my aux channel but the levels are so low their beyond usable...  The aux channel doesn't have a mic boost and I can't get it to push the capture level beyond 100%...

Is there some place where the levels are scaled?  I noticed a limit value in amixers output...

Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [on]
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 54 [100%] [on]
  Front Right: Capture 54 [100%] [on]


Thanks in advance...

---

### Post by sgx on 2007-01-16
try installing alsamixer and alsamixergui and alsaoss (for luck in the future)...alsamixergui should reveal your line-ins, and allow adjustments. 
And make sure the same user is starting all your sound apps. Hope this helps...

---

### Post by Bidimus on 2007-01-18
Thanks for the response...  I actually have installed all those utilities and more...  All my volume levels are pushed to 100% and the capture channel is still coming in weak...  Mic boost appears to has no affect on non microphone channels...  What I have is an external hardware mixer plugged into the line-in port on the sound card...

I am getting sound so I know it is hooked up right and when I try it from windows I have to turn down the line-in gain to reach 0db...  Under linux though with the line-in gain (capture aux) at 100% I can't get above -20db...  Still not understanding ALSA well, I suspect the ttable parameter in the config file might be the answer but I just can't find enough information on how to do this...

Looking at the amixer output the "limits" line catches my eye...  This appears to be a valid range restrictor but I can't find any information to properly explain it...  If it is, one would assume it is configurable...

I really don't want to have to boot into that other OS to do my podcasts...  ;)

Thanks,

- Jim

---

### Post by sgx on 2007-01-19
[QUOTE=Bidimus;2031990]Thanks for the response...  I actually have installed all those utilities and more...  All my volume levels are pushed to 100% and the capture channel is still coming in weak...

snip...

I would try a Knoppix, Mepis, Mandriva, and Suse live cd/dvd, and if one of those is working, compare config files, or just switch...if you bought a mixer, that means you're serious enough to be distro agnostic...a good thing! Consider an mAudio 24/96 card, or it's usb version if laptop bound...excellent i/o in linuxes

---

### Post by Bidimus on 2007-01-19
Thanks... I did more work with it today and verified it is using the right driver and identifying the chip set properly...  I then tried upgrading ALSA to the latest version to no avail...  With a regular mic attached I found I was getting the same results on the mic channel as I was on the aux channel even with the mic boost at max...  I get sound but not high enough to record...

I'm all for trying out the other distros, do any of them use repository style software installation like Ubuntu does?  That's my favorite feature...  With the exception of this sound issue I'd prefer to stick with Ubuntu though...  :)

---

### Post by sgx on 2007-01-21
> **Bidimus said:**
> Thanks... I did more work with it today and verified it is using the right driver and identifying the chip set properly...  I then tried upgrading ALSA to the latest version to no avail...  With a regular mic attached I found I was getting the same results on the mic channel as I was on the aux channel even with the mic boost at max...  I get sound but not high enough to record...

I'm all for trying out the other distros, do any of them use repository style software installation like Ubuntu does?  That's my favorite feature...  With the exception of this sound issue I'd prefer to stick with Ubuntu though...  :)
Mepis and Knoppix are Debian based, just like Ubuntu, I use Ubuntu repositories with Mepis on a second setup for vst instruments, same apt-get install, same config files for
repositories...easy money!

---

### Post by Bidimus on 2007-01-22
Thanks for all the help everyone...  I tried other distributions but came to the conclusion that it was an ASLA driver issue...  I'm not clear how to get word to the developers of the driver that they have what appears to be a bug in their driver and if anyone has any pointers in this direction I'd very much appreciate it...

My solution was a new sound card...  I decided I wanted something portable for future use and ended up with the USB Turtle Beach Roadie...  It's a great card with some great features and handles line in very well...  Turns out there are a few advantages to having a second card for recording with in Linux since you have allot of control over what applications use for sound I/O...  This is amplified when you start using Jack to route sound between applications...  I'm still using my on board card for my system sounds and games as it still fine for output and I use headphones on my Roadie when I'm recording...

Skype is setup to use the Roadie for the Mic and the on board card for output...

For anyone looking to do some recording under Linux I'd easily recommend a similar setup...  In particular I had zero issues getting the Roadie up and running, plug and play...  The product is reaching end of life but is being replaced by the Audio Advantage SRM which  appears to be nearly the same product...  I would hope it would work equally well and in the future...  If I were in the market for another sound card, I'd love to try the SRM...

Anyway, just wanted to report back in and say thanks...

- Jim

---

