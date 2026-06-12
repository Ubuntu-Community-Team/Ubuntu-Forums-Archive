---
title: "Acer Aspire Revo - XBMC - Ubuntu"
date: 2010-06-10
forum: Multimedia Software
---

### Post by Statecowboy on 2010-06-10
Alright, the lifehacker article about this Acer machine got me interested in revisiting XBMC as a media center. I bought the AR1600-U910H from Newegg and have been struggling for a couple of weeks to get it working correctly. I opted to install a full Ubuntu desktop to utilize the hardware fully with a standalone version of XBMC. I am currently running Lucid with NVIDIA 256.25 (was running 195 series) driver. Switched to 256 because I heard it fixes the no multi-channel output problem. However, sadly I can't get multi-channel out to work. I have the HDMI output going through my Onkyo TX-SR608 receiver for both audio and video. My problem is I can only get stereo sound out while running XBMC (or any application for that matter).
 
I've upgraded Alsa to 1.0.23. I've installed new Beta 256.25 NVIDIA driver. I've configured Alsa about 28 different times. I'm at my wits end.
 
So, my question is - does anybody having a similar setup with the ION chip (or the Acer Aspire Revo in particular) where they can succesfully get HDMI digital audio pass through to a receiver (or at least digital multi channel out)? The best I've gotten is 2 channel audio, which doesn't do a lot of good on a 5.1 setup. If I would have known getting multichannel audio would be so difficult I would have rethought starting this endeavor. 
 
I don't care if I have to do a fresh reinstall of everything - if that means a different version Ubuntu so be it.
 
Any ideas would be appreciated. It's hard to believe getting multichannel out would be this hard.

---

### Post by ilikelinuxtoo on 2010-06-22
i've been able to get 5.1 working over hdmi on 10.04 using the nvidia beta 256 drivers and alsa 1.0.23, but in XBMC and boxee, I couldn't have both DTS and AC3 decoding selected at the same time.  When one was checked, it would work properly (outputting to all speakers via a yamaha receiver) but with both DTS and AC3 checked XBMC and boxee would complain about not being able to use the audio card.  Somewhere along the line, I could check and immediately uncheck the 'output stereo to all speakers' and that would kick something over and it would recognize the 5.1 again (with both DTS and AC3 checked).  Having to go into the options every time was annoying though, so i'm back on 9.10 with the 185 drivers and stereo sound :(

---

### Post by koshari on 2010-11-25
my settings for acer r3700 with 5.1 over optical and analog stereo out of 3.5mm

[http://ubuntuforums.org/showpost.php?p=10163439&postcount=9](http://ubuntuforums.org/showpost.php?p=10163439&postcount=9)

---

