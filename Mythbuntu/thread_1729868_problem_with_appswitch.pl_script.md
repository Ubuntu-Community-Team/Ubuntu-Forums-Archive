---
title: "problem with appswitch.pl script"
date: 2011-04-15
forum: Mythbuntu
---

### Post by wrectum on 2011-04-15
Hi All, 

I Was hoping for some help  with a niggling issue I have, but first some background in case any of it is useful:

I'm running mythbuntu 10.10 ( frontend + backend ) on my acer revo 3610, with all recommended updates installed + 3rd party drivers for the nvidia ION gpu and my DVB-T usb tuners. I've also used Mythbuntu Control Center to upgrade xfce to a more fully fledged desktop, and add lirc support for my mceusb remote.

I've added xbmc dharma to end up with a rather wonderful media center. Because I'm using hdmi to output video + audio to my tv, i've used the sound preferences dialogue (PulseAudio?) and changed my audio profile to:

"Digital Stereo (HDMI) Output + Analog Stereo Input"

This was the most reliable way of getting HDMI audio working in myth frontend, xbmc and desktop apps, that I've found. (one minor niggle is that volume control in mythfrontend has no effect, but I can live with that) Some messing about in ALSA was also undertaken.

I then used the appswitch.pl script taken from here  [http://code.google.com/p/yatvgrabber/wiki/XbmcMythtvRemote](http://code.google.com/p/yatvgrabber/wiki/XbmcMythtvRemote) which is where all the problems begin.

The idea is that the script will allow me to map a button on my mceusb remote, to switch between xbmc and mythfrontend, which it does, BUT, after using the script to switch a few times, any video playback in xbmc becomes awfully slow (perhaps 5 frames per second), and no audio is output at all. Interestingly I can see that gpu and cpu usage is still very low, yet the playback is unwatchable.

Its worth noting that if i reboot, and launch xbmc without using the appswitch.pl script, everything works beautifully.

I suspect that the problem is really caused by some kind of conflict for audio hardware.

Looking at the perl code of the script, I can see some pretty dirty stuff going on, particularly in respect to audio hacks. (the author himself has comments in the script alluding to this...).

My perl skills leave a lot to be desired, but I tried a couple of tweaks (removing the --standalone switch in the $XBMC launch string, and setting $AUDIOHACK to be an empty string , but no joy..)

I realise that this script is probably not "supported" as such, in this forum, and neither is xbmc, but I'd imagine im not the first person to try this, and would really appreciate any suggestions or advice. At the moment I'm having to use the mouse / keyboard to switch between the apps which is a bit of an irritation, and a shame considering all the awesome work that has been put into these various bits of software.

Thanks for all the hard work guys.

---

### Post by wrectum on 2011-04-16
I've decided to not use this script. Instead, I've used irexec to map 2 buttons, one starts xbmc, one starts mythfrontend. The only downside is you have to exit one app before starting the other, but at least it can all be done from the remote. Its not ideal, but will do for now. 

xbmc eden is due in 9 months or so, and should have pvr support, including a much more usable mythtv client. If its usable enough I will probably not need to switch between the 2 anymore anyway.

I guess we should mark the post as solved =]

---

