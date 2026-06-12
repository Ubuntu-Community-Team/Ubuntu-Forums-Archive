---
title: "no HDMI audio out when viewing multimedia files"
date: 2011-07-20
forum: Multimedia Software
---

### Post by Cincinnatux on 2011-07-20
For starters, although I've been relying on Ubuntu for home computing since 2007, I remain largely clueless when it comes to troubleshooting problems within the OS.  My intentions are good, but my comprehension is weak.

A few days ago, after a routine update that looked like it included a new kernel, I lost HDMI audio.  I do not have any other way of getting audio from my desktop computer to my monitor (which is actually an HD TV), so I do not know if the audio problem extends beyond the HDMI output.

In my troubleshooting, one suggestion I read was that Pulseaudio might be locking up audio resources and that removing Pulseaudio might solve the problem.  I removed Pulseaudio and that did not, in fact, solve the problem.  No surprise.  I then went to:
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
to reinstall Pulseaudio on the computer.  Unfortunately, following the instructions in the wiki for installing Pulseaudio resulted in removal of XBMC from my machine.  This computer's purpose is to act as a Home Theater PC, and XBMC is the primary interface for doing so.  Thus, deleting XBMC in the interests of getting the HDMI audio to work is counter to my purpose.

[HTML]aplay -D plughw:1,3[/HTML]
produces sound through HDMI, but running VLC to view media files results in video without audio.

Because it does me little good to solve the audio issue without XBMC, I then went to
[http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide](http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide)
to reinstall XBMC.  In addition to doing the XBMC install, I also followed the instructions for adding the VDPAU software for nVidia (since I'm using a GT-240).

Now I get HDMI audio when using XBMC.  No clue how what I did made any difference, but clearly it did.  If I can get audio working via VLC I'll post here as well, but for the time being I cannot.

---

### Post by Cincinnatux on 2011-07-20
If anyone happens to know, I'd love to know why it is that regular updates often bork my audio settings.  This is the third time this year I've had to troubleshoot audio after a regular update.  I thought that sticking with 10.04 LTS would be the most stable option I could have, but it would seem that destabilizing elements are included in routine updates, even for the LTS release.  Am I somehow misconfiguring my system so as to invite these headaches?  I thought people said Linux was more stable and dependable than Windows.  I've been using Ubuntu since 2007 and I have not found it to be either stable or dependable.  I'm willing to accept that the problem is at the user end (i.e., me) but that doesn't make the experience any more pleasant, nor does it impress my wife when I have to spend an evening every week or three troubleshooting the latest lost function in our home media server.

---

### Post by wkulecz on 2011-07-20
You are correct, I believe Ubuntu is trying too hard to be like windows.  I have the same issues with CD/DVD burning, never knowing if it will work or not after updates.

I don't think LTS means anything other than you are not forced to upgrade every year to stay reasonably secure.  Pulse Audio initially appeared in 8.04LTS and was a nightmare for the first six months or so.  Fortunately audio is not "mission critical" for me.

This is a shot in the dark but it might help to install dkms package.  Perhaps XBMC has components that need to be recompiled on a kernel update, dkms is supposed to automatically do the rebuild if everything is setup correctly in the XBMC package -- its a lifesaver when using Virtualbox, which is where I learned about it.

---

