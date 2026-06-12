---
title: "Installing a USB Microphone in 7.04"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by dthomasdigital on 2007-05-05
Installing a Logitech USB Microphone

This is a step by step guide on how to use a Logitech USB microphone  in Ubuntu 7.04 and the application Audacity.

The first step is to plug the microphone into an open USB port and turn your computer on.

The next thing you need to do is click on [IMG]http://www.mediamax.com/dthomasdigital/Hosted/mic1.png[/IMG]       that is located on the panel bar.

You should now see this window.
[IMG]http://www.mediamax.com/dthomasdigital/Hosted/mic2.png[/IMG]

You will need to click on FILE – CHANGE DEVICE – AK5370 (as shown in the following window)
[IMG]http://www.mediamax.com/dthomasdigital/Hosted/mic3.png[/IMG]

It will then go to the next window make sure that there is no red x on the microphone icon and move the slider so it is at about 80%
[IMG]http://www.mediamax.com/dthomasdigital/Hosted/mic3.png[/IMG]

Next lets open Audacity
[IMG]http://www.mediamax.com/dthomasdigital/Hosted/mic5.png[/IMG]

You will now need to got to EDIT – PREFERENCES  as seen in the next window
[IMG]http://www.mediamax.com/dthomasdigital/Hosted/mic6.png[/IMG]

You will see the next Window
[IMG]http://www.mediamax.com/dthomasdigital/Hosted/mic7.png[/IMG]

Where you see the section on recording change it to ALSA: AK5370 :USB Audio

Click OK and your ready to record using your new Logitech microphone. This Howto should work on most USB microphones.

---

### Post by gobuntu on 2008-01-18
Thanks for this post, dthomasdigital.

However, going into Volume Control all that's being done is tell that applet to control the usb mic, which Audacity can do by itself, once one tells Audacity to use the USB mic as recording input.

What I would like to know, though, is HOW TO setup the USB mic so that it replaces the conventional analog mic, because the X in Microphone is for the analog mic, not for the usb-mic.

What is described above is how to record using the usb-mic in Audacity, but what I would like to know is how to record in Audacity THE MIXER output WHEN using the USB-mic as one of the mixed sounds, along with another sound source controlled by the mixer (Gnome Volume Control).

For instance, in order to record one's voice via the USB-mic SIMULTANEOUSLY with the sound of a Karaoke file being played by the Totem Movie Player.

I can do that using a regular mic plugged in the mic jack, but can't yet do it using the USB-mic.

I feel I need to know HOW TO replace the analog mic IN THE MIXER (Open Volume Control = Gnome Volume Control 2.20.1) with the USB-mic.

The way I do it , to record simultaneous analog mic and a player, I set Audacity's Recording Device: ALSA default. 

So, can any one please help me on how to do this with the USB-mic?

(In Windows I replace the mic analog standard device with the USB mic, and Audacity takes it from there, and I believe this is what I would need to do in Ubuntu).

In Ubuntu, at the Gnome Volume Control, File-Change Device DOES NOT replace the analog mic. 

"Change Device" only sets the slider to control the USB-mic, with the action described in the original post.

I'd really appreciate help on this issue.

Thanks.

---

### Post by gobuntu on 2008-02-22
Well, dear friends,

Just to report that I gave-up on using the USB mic I had, and am back to using an analog mic.

It should have been obvious to me earlier that a USB mic, being digital, does have unavoidable latency due to processing required, at least for the USB mic I was using, and probably for most.

That's why, I gather, it comes with it's own "mixer" and can not be used to "sing-along and record-along" in synch  in real-time with another sound source.

There may be more costly digital USB phones with their special drivers, but I can't find such.

If anyone knows, or can correct/expand on what I gather, please do so.

Thanks!

---

### Post by SMA11784 on 2008-03-25
> **gobuntu said:**
> It should have been obvious to me earlier that a USB mic, being digital, does have unavoidable latency due to processing required ... and can not be used to "sing-along and record-along" in synch  in real-time with another sound source.

This is something I wish I knew a hundred dollars ago.

You can actually record one track, export it to MP3 or WAV or whatever, and play it back in another program like rhythm box while recording another track.  Of course then you have to be very careful lining the tracks up when you mix them; it's not automatic like it would be with an analog mic.

The thing is, if playing back the other track lets you play and record at the same time, shouldn't it be possible to fit that functionality into a single interface like Audacity?  I mean, I'm not that skilled, but surely somebody out there is.

---

### Post by Blessed_Coffee on 2008-04-06
Wow, thanks!  That was easy, and it worked.  I've been trying to get one of two mics to work.  One of them is a usb mic, and the other is a jack.  When I would go to test them I would hear myself in the speakers, but then I would get an error message saying that it failed to create a pipeline, and I would then be unable to record myself.  Thanks again.

---

### Post by zidkenu on 2008-07-07
Google search for
Logitech USB Microphone Ubuntu 7.04
you will find it

---

### Post by alanlevin on 2008-07-10
[http://ubuntuforums.org/showthread.php?t=225019](http://ubuntuforums.org/showthread.php?t=225019) gave the right answer. 

Fix: Double click on the volume applet, File > Change Devices > AK5370, and raise the volume (as high as it goes works).

For Skype: Go to Options > Sound devices > Sound in >  AK5370 (plughw:default,0). Seems v.good.

---

