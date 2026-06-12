---
title: "System crashes because of my soundcard(Creative Soundblaster Live)"
date: 2008-12-08
forum: Multimedia Software
---

### Post by Truckerpunk on 2008-12-08
I close to just plain giving up all hope....

It's been some long days and nights trying to fix my problem, but without any luck yet. Here's the problem. I have a Soundblaster Live card and when I plug it into my machine(witch also has a onboard soundcard) Ubuntu freezes right after booting. Sometime icons appear, sometimes not. But when it get that "far"(with the icon appearing), a loud Biiiiip!!! noise comes from my speakers and everything freezes. I have tried to disable the onboard-card through the BIOS, and that didn't help. I have tried to plug my SBLive card into other PCI-slots, just in case that was the problem... Didn't work. I have tried to boot in Safemode and that didn't help... Still freezes either while booting or as decribed. I have installed ALSA and Pulseaudio. But I can never get as far as to see if my system recognizes my SBLive card because it crashes so fast. But if I remove the SBLive card and just boot with the onboard-card it can boot without problems. But that soundcard is so bad that I can't stand listning to music through it, and for some reason I can only listen to one media at the time... Witch is pretty bad for me, I like listning to music while playing games for example. Have anyone gotten their system to boot with a Soundblaster Live plugged in? If you have or have ANY idea to sort this out, PLEASE help. I'm getting desperate here. I'm running Intrepid Ibex. Any help is greatly appreciated. Please don't make me go back to Windows.....

---

### Post by Truckerpunk on 2008-12-08
I got it working!!! So Sweet!! You encouraged me to give it another try with changing PCI-slots, and it made it not crash!! But then instead there was a loud BIIIP-noise that was even worse that silence. But it turned out the even-though I had disabled the onboard caed in the BIOS it was listed in the volume control(double click volume in the panel) as AC97, and after muting it the BIIIP-sound disappeared, and only the sweet sound of the loud punk-music that was playing it the background came through my speakers!!! Great! So to sum things up, if anyone has a similar problem: Make sure that you disable the onboard-card from the BIOS AND that you mute it in the volume control. (And make sure that your PCI-slots are functional...). Thanks a lot for all the answers, and for finally letting me have the sweet freedom of Ubuntu!! THANKS!! Really appreciate it.

---

