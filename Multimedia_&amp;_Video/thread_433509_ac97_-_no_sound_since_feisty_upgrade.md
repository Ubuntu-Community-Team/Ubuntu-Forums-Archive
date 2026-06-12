---
title: "ac97 - no sound since feisty upgrade"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by starsky51 on 2007-05-05
***resolved: see last post***
I recently upgraded from Dapper to Feisty (via Edgy). The sound worked fine in Dapper and Edgy but now I have upgraded to Feisty it's silent. The 'Test Sound' in the system properties doesn't work.
I've checked the volumes in alsamixer. All fine. I've run asoundconf and selected my soundcard. Rebooted. Still no joy.
lsmod | grep ac97 gives me:
snd_ac97_codec         97184  1 snd_intel8x0
ac97_bus                2304  1 snd_ac97_codec
snd_pcm                76680  5 snd_hda_intel,snd_hda_codec,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    51716  14 snd_hda_intel,snd_hda_codec,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

Anyone got any ideas?
Dave.

---

### Post by anirban.sam on 2007-05-05
Type alsamixer in a console and disable all IEC devices. Save alsactl config.
                                                                                                  [URL="http://ubuntuforums.org/editpost.php?do=editpost&p=2596090"]
[/URL]

---

### Post by depele on 2007-05-05
may be stupid question, 
but how to save alsactl?

grtz

---

### Post by depele on 2007-05-05
==> It is all right!
I just rebooted and the sound went on after disabling the IEC an unmuting all the channels!


grtz...


Arne

---

### Post by anirban.sam on 2007-05-05
sudo alsactl store

---

### Post by starsky51 on 2007-05-05
no joy. i've muted all of the input lines, made sure the ouputs were unmuted, done a 'sudo alsactl store' and rebooted but still no sound.
Is there a way i can check the levels to see if they move when i play a sound?

---

### Post by starsky51 on 2007-05-07
Ok, I finally solved this problem. I found an option in the 'Switches' section of the mixer GUI (accessed via the speaker status bar icon) called 'Headphone Jack Sense'. I turned this option off and the sound worked straight away.
I love Ubuntu but it does try my patience, sometimes. [-o<

---

