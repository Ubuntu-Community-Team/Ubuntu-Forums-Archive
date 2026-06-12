---
title: "Online sound problems after Pulse uninstall"
date: 2009-03-19
forum: Multimedia Software
---

### Post by Mattttttt on 2009-03-19
After having problems with Skype I followed the instructions on a thread to uninstall Pulse audio and ubuntu-desktop.
That has fixed my problem with Skype but has presented me with a new one...
The sound on some websites now sounds like a stuck CD.  Can anyone help?
I'm using Intrepid by the way...

---

### Post by acimmarusti on 2009-03-19
skype works when pulseaudio is not running (if you choose other than default for your input/output audio devices in the sound settings in skype). I don't like pulseaudio, it's very buggy, but I recommend you get pulse back so you get proper audio mixing (that's why you are getting horrible sounds) and run skype alone!! (quit any other sound apps you may have running like your browser, instant messenger, media player, etc)

---

### Post by markbuntu on 2009-03-20
The vast majority of problems with Skype are due to two reasons, one is an improperly set up sound system and the other is using the wrong version of Skype.

If your sound is set up correctly and working properly, including your microphone, you should have no problem setting up Skype to work with either alsa or pulseaudio.

[http://ubuntuforums.org/showthread.php?t=937323](http://ubuntuforums.org/showthread.php?t=937323)

It has been reported by that Skype works out of the box with Intrepid but many also report problems ,mostly with getting their mic to work. If your mic is not working in skype, try to get it working in any other application first. There are also some notes on configuring Skype for Intrepid here

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

If your sound is sort of working, you need to get your sound system set up properly

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If you are having trouble getting your mic to work or other hardware issues go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Mattttttt on 2009-03-20
Maybe I should have been a bit more clear.
There was nothing wrong with my sound system whatsoever until I uninstalled Pulse in order to get Skype to behave properly.
Ok - I understand that maybe you can still have Skype and Pulse working together without a problem as long as you dont want to do anything else during a conversation but I do!  I want to be able to talk to people about eBay items and check them out etc...  while I'm talking to them.  So putting up with Pulse and not using any program during the conversation is not an option.

My mic IS working in Skype.  The problem I have is that if Pulse is installed then that is the only option I have available to Skype.  If it isn't then Skype works perfectly but sound streaming on certain websites does not.  My Skype and mic ARE set up correctly but still I cannot resolve the problem with ALSA or Pulse.

Skype blatantly does NOT work out of the box...

I was happy with Ubuntu until this happened.  Why did the developers insist on using poxy Pulse when they hadn't made the necessary provisions for accommodating it?  It has only served to cause people like me endless problems.  You want people to use Ubuntu?  Get this **** sorted.  End of.

---

### Post by markbuntu on 2009-03-22
First of all, the problem is with skype. While it is certain that ubuntu did not do a stellar job in implementing pulseaudio, by adopting pulseaudio ubuntu has also laid bare many faulty alsa implementations by application developers.

There have been some recent changes that you may not be aware of that are very important to understanding what is going on. The most critical is that low level ALSA sound drivers have moved into the kernel. Important security and kernel integrity protocols must now be followed for applications using sound drivers. 

Pulseaudio strictly implements these new protocols. Applications that fail with pulseaudio are applications that do not implement these protocols and compromise kernel security and stability.

Skype and Wine are two among many that have been exposed in this. The Wine developers have even admitted their own fault in this, they made assumptions about hardware that, while valid in the past, are no longer reasonable now that the drivers are in the kernel. Many other application developers are or already have implemented pulseaudio plugins or are fixing their alsa plugins to conform with these new requirements.

Linux kernel development is a gradient. Changes come a step at a time and adaptation to these changes follow apace as applications adopt them. This is very reasonable since you can always stay with what works for you and move forward incrementally as the applications you want to use also move incrementally forward.

That said, if you want to complain about applications that have not made the incremental impovements necessary to accomodate the incremental improvements in the system, or blame these improvements for the inability to use applications that have not moved to incorporate these improvements then you are barking up the wrong tree.

The system is moving forward. It is not the system developers responsibility to accomodate applications to changes in the basic operating system, that is up to the application developers. It is also unreasonable to expect distributions to suppport applications that do not accomodate themselves to these changes.

Anyway, there is a not so difficult way to configure your sound scheme to accomodate both Skype and streaming audio at the same time. but not with ALL websites since some use proprietary streaming protocols that are only avialable to those using licenses from Microsoft and this is not in any way the fault of Ubuntu, Linux, or Pulseaudio.

---

