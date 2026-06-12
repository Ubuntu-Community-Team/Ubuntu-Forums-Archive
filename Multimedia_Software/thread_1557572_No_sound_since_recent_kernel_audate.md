---
title: "No sound since recent kernel audate"
date: 2010-08-20
forum: Multimedia Software
---

### Post by mpc_mythtv on 2010-08-20
Hi,

Today, I installed the recent kernel security update (i.e. 2.6.32-24-generic #41-Ubuntu SMP). After a reboot, the sound is gone.

From my user account:
mpc@awd:~$ alsamixer
cannot open mixer: No such file or directory

Same problem with "aumix".

However, the commands "sudo alsamixer" and "sudo aumix" seem to work (but still no sound).

"lsmod | grep snd" will give
snd_hda_codec_atihdmi     2367  1 
snd_hda_codec_realtek   203310  1 
snd_hda_intel          21941  0 
snd_seq_dummy           1338  0 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_pcm                70662  4 snd_hda_intel,snd_hda_codec,cx88_alsa,snd_pcm_oss
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq_oss,cx88_alsa,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm

Any idea?

Thanks in advance.

---

### Post by mpc_mythtv on 2010-08-21
Found a solution:

sudo users-admin

Then, "Manage groups". I select "audio", then click "Properties", and check the box associated to my login name (it was unchecked). Sound in userspace now working.

I also had to restart mythbackend; the mysql database was unaccessible for some reason (might be unrelated, I don't know).

After the kernel update, whether the sound was not working or the mysql database was unreachable (only one or the other of these two was broken, at random). Go figure...

---

### Post by urbinbliss on 2010-08-23
Thanks for the fix. I had the same problem. I also run MythTv, coincidence??

---

### Post by bbb125 on 2010-08-23
I am also having sound problems (see my other post). When I check the "audio" properties using this method, I see that my username is also unchecked. When I check my name and press OK, I see:

[B]
(users-admin:1833): Gtk-CRITICAL **: gtk_list_store_set_valist: assertion `VALID_ITER (iter, list_store)' failed
[/B]
Could this be part of my problem?

---

### Post by urbinbliss on 2010-08-23
Try not using sudo just ```
users-admin
```

---

### Post by bbb125 on 2010-08-23
Still getting the same error. The box is checked now, but still no sound. Ahh, I am so frustrated with this sound problem that I will problem give up soon or have to try something else.

---

### Post by bbb125 on 2010-08-23
But I am seeing a flurry of "no sound" posts lately, so it would be nice for a professional to address the problem since it is affecting many users. As a new user, this is very discouraging as I do not have the technical background to troubleshoot this problem on my own.

---

