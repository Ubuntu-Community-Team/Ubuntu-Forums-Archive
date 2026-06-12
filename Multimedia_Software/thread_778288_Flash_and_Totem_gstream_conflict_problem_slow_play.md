---
title: "Flash and Totem gstream conflict problem: slow playback and no sound"
date: 2008-05-01
forum: Multimedia Software
---

### Post by lennydizzy on 2008-05-01
The nonfree flash has no sound if i open a movie first. The totem is slow and no sound if I open a flash site first. Maybe a sound mixer ALSA kind of problem?

---

### Post by lennydizzy on 2008-05-01
I am using Nvidia 8800gt, realtec on board sound card(ALC888). Default totem gstream with ubuntu-retricted-extra installed for video codecs.

---

### Post by coolen on 2008-05-02
The nonfree flash plugin uses ALSA. The betas had a compatibility package in place to allow Flash to use PulseAudio, but it caused Firefox to crash too often, and so was removed.

I found a workaround [here]("http://markusthielmann.com/blog/defusing_one_most_annoying_bugs_ubuntu_hardy_heron_stop_flash_killing_firefox"). It didn't work for me (perhaps it only worked for beta?) but it may suit your needs. It's pretty simple to undo the changes either way.

---

### Post by quirks on 2008-11-24
Sorry, for opening such an old thread, but I had the same problem and could solve it: the problem seems to be PulseAudio (once again ... :mad:). Go to System -> Preferences -> Sound. Switch to the Devices tab and change all sound playback devices to ALSA. Click the Test buttons => you should hear a sound in each case; when they are set to default, you should not hear anything.

Hope I could help someone.

---

### Post by psyke83 on 2008-11-24
Don't set the Sound playback options to ALSA, it's a poor workaround (and doesn't work for Intrepid, as the ALSA libraries remap ALSA output to PulseAudio anyway).

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

