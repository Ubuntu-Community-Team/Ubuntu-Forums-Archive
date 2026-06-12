---
title: "Sound Issues 14.04 S/PDIF"
date: 2014-10-25
forum: Multimedia Software
---

### Post by aimless2 on 2014-10-25
Hooking up an HTPC.  I transmit video to a big screen via HDMI (muted sound).  And audio to my reciever via S/PDIF optical.

Something strange is happening with volume control.  When I first log in, and until I change the volume setting within Ubuntu, the sound is normal.  

But as soon as I change the volume (up or down, doesn't matter) it's as if the OS switches to another driver and throttles the volume way down to a point I have to turn it all the way up to hear anything.

Here's the kicker.  And I found this out the hard way.  If I switch to the HDMI audio output (or any other audio output) and then BACK to S/PDIF it'll be unthrottled again (meaning my house will shake if still turned way up).   But once I change the volume it throttles way back.

What's happening here and how do I control it?  I'm trying to get a consistent audio setting.  My receiver doesn't take HDMI, it's a little older but still strong so optical is what I'll be stuck with.

---

### Post by aimless2 on 2014-10-26
Update:

Experimenting a little more it seems that when the S/PDIF option is first selected (whether by default on boot or just toggling between output devices) the sound will be received from my receiver via optical audio at the correct level but as soon as the volume is adjusted in Ubuntu the volume drops by like 90%.  Meaning, even if i turn the volume UP it goes way down.  

Any change in volume AFTER selecting S/PDIF as output seems to cause Ubuntu to do something in the background that muffles the sound to a point where I have to turn the volume almost all the way up (in Ubuntu) to hear anything.  If I toggle off S/PDIF and then back on the sound level will be correct but only until you make a volume adjustment at which point sound cuts almost all the way out.

---

### Post by aimless2 on 2014-10-26
Update again, I don't get this behavior in Windows at all.  It's definitely something within Ubuntu.  I'd like to know what is taking place behind the scenes when I engage the audio controls that results in throughput being robbed off S/PDIF.  Fortunately the behavior is repeatable and consistent so testing any changes should be straightforward.

---

