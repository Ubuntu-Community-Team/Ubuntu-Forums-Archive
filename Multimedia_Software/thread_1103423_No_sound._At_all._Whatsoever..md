---
title: "No sound. At all. Whatsoever."
date: 2009-03-22
forum: Multimedia Software
---

### Post by penguinguy on 2009-03-22
So today Ubuntu Intrepid decided that I don't have a sound device any more. No login sounds, no music, nothing. My on-board sound works in Windows, but opening volume control in Ubuntu gives the error:

"No volume control GStreamer plugins and/or devices found."

I've been on Google and these forums for a few hours and nothing has worked. One solution gave me a System>Preferences>Default Sound Card option that doesn't do anything. I also have a huge list of ALSA things in my Applications>Sound & Video that didn't use to be there.

I haven't done any kernel upgrades, just installed VirtualBox.

Some commands that were suggested on other threads:
lspci | grep audio : No output
lsmod | grep snd : No output
Everything in Sound Preferences is set to PulseAudio (except default mixer tracks, which cannot be changed). When I click "Test" the window crashes.

This is driving me mad! Please help.

---

