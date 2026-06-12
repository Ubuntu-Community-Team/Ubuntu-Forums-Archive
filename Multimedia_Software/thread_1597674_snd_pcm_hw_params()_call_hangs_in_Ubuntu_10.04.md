---
title: "snd_pcm_hw_params() call hangs in Ubuntu 10.04"
date: 2010-10-15
forum: Multimedia Software
---

### Post by SaberCat on 2010-10-15
Hi,
I am trying to get a program running on Ubuntu 10.04 that I wrote and ran successfully on Ubuntu 8.04. It uses the ALSA sound interface. As part of the initialization it calls snd_pcm_hw_params() to write parameters to the driver. On 10.04 this call hangs (does not return). Here are the 'snd_' entries displayed by lsmod (actually: lsmod | grep snd):

snd_hda_codec_atihdmi     2367  1 
snd_hda_codec_realtek   203374  1 
snd_hda_intel          22037  2 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm


I have the following modules loaded (via Synaptic Package Manager):
alsa-base, alsa-source, alsa-utils, libasound2-dev.

Obviously the program compiles OK. Any ideas why snd_pcm_hw_params() should hang? Its arguments were fine when running under 8.04...

Thanks...

My machine is a new Dell Inspiron 570.

---

### Post by SaberCat on 2010-10-16
Problem solved:

Here's the code involved:

  /* Set period size to 128 frames */
  frames = 128;
  snd_pcm_hw_params_set_period_size_near(handle,
                              params, &frames, &dir);

  /* Write the parameters to the driver */
  rc = snd_pcm_hw_params(handle, params);
  if (rc < 0) {
    fprintf(stderr,
            "unable to set hw parameters: %s\n",
            snd_strerror(rc));
    exit(1);
  }

As shown the code works. I had frames set to 32 and that caused snd_pcm_hw_params(...) to hang (not return). It seems that frames needs to be at least 128. I tried 127 and got the hang again. With frame set to 32, the program ran fine on Ubuntu 8.04, so I assume 10.04 is using a different version of ALSA that is more "picky".

Thanks anyway...

---

