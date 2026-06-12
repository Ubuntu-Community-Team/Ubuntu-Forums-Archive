---
title: "Audio input not working on SB Audigy"
date: 2006-08-03
forum: Multimedia &amp; Video
---

### Post by rogblake on 2006-08-03
I'm running a Ubuntu 6.06 system equipped with a Soundblaster Audigy audio card (model SB0090). There is also an Osprey 200 (bt878-based) video/audio capture card installed.

Audio output works fine for Gnome sound effects, playing CDs, etc., but I'm running into problems trying to get the line input working on the Audigy. I've verified that the line input is unmuted and cranked all the way up in the mixer. Also tried the microphone, but that does not work either. I've checked that the correct device is being selected by the mixer, and also tried unloading the bt878 modules to prevent confusion. The /dev/dsp device file is present with major and minor device numbers of 14 and 3, respectively. (I had also tried to get the audio through the inputs on the Osprey card, but that did not work either.)

This is a dual-boot system, and the Audigy's line input works OK in Windoze, so I know the hardware setup is OK. What else should I be looking at here to get this operational? (The objective is to use Audacity to convert a tape cassette to CD for a friend.)

---

### Post by rogblake on 2006-08-04
Well, doing some more searching within the forum revealed that there are a lot of problems with getting the Audigy sound cards to work properly in Ubuntu. I tried a number of the ideas found here, but met with only partial success -- I got the audio input to work somewhat, but at low volume and with no monitoring to the speakers.

After all this, I decided to install a cheapie Creative Labs Sound Blaster PCI card (actually Ensoniq 1371) that I had in an older computer. This card "just worked" under Mandrake Linux 9.2, so I had high hopes. Booted up with that and, voila! No sound at all, and the mixer applet did not contain any of the usual volume controls, not even available under "Preferences."

So I did some more searching here and found that the Ensoniq 1371 is also a problematical sound card for Ubuntu. (!) Did some more digging and found a suggestion to unload and reload the snd_ens1371 module before logging in. That worked! Audio output worked fine, all the normal mixer controls were available, the "capture" tab appeared in the mixer, and I had full-volume input and monitoring through the speakers. 

Of course having to manually reload the module at every boot is a PITA, so I added the following lines to /etc/rc.local:

  # Unload and reload the sound module for Ensoniq 1371
  modprobe -r snd_ens1371
  modprobe snd_ens1371

Now on reboot I have all of the audio functions available. One minor nit remains -- when first logging in, the mixer applet comes up with the sound muted. I don't see an option there to save defaults, is there a simple way to do this that won't take hours of head-banging?

(I would eventually like to get the Audigy to work, though. It should have better sound than the cheapie 1371, and it has a firewire port. For the moment I just got tired of fighting with it...)

---

### Post by rogblake on 2006-08-04
To answer my own question again, I used "alsactl store" to store the settings, and in /etc/rc.local I placed "alsactl restore" to bring them back at boot time.

Putting all this stuff in rc.local is something of a kludge, there is probably a better way but for the moment this is working...

---

