---
title: "big sound issues"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by BradNeuman on 2007-06-28
Ok so I have had sound issues since i switched to ubuntu (from xp) 6 or 7 months ago and I have found various quick fixes on forums but they only seem to break other things and I am looking for more of an explanation and permanent solution so i figured I'd ask here, feel free to scream at me to search google or something.

Here is my setup:

I run kubuntu feisty on an amd64 system on my Acer aspire laptop. Sometimes I use the built-in speakers or headphones (realtech speakers) but I also have an external sound card connected to better speakers set up in my room which I use when my laptop is there. Whenever I switch from the external card to the speakers I get weird issues (no sound or some sound coming from some places and no sound from others) so I made a shortcut to do
```
sudo /etc/init.d/udev restart
```
which helps if my external card isn't recognized (this is a hardware issue i think because it would happen sometimes on windows also).

Also, I have no sound (usually) in firefox flash and I have followed the tutorial [here]("http://ubuntuforums.org/showthread.php?t=202537") and flash and java work, there is just no sound. I'm not actually sure if embedded java has sound, but flash usually works with my external card (when it is working) but never works on the built-in speakers.


So I know there are various sound system (alsa, osd, etc.) and I am wondering which of these I should use, and is there any kind of easy way to switch between systems when i change devices. I would appreciate any suggestions or even links on where I can read about this.

Thanks!

---

