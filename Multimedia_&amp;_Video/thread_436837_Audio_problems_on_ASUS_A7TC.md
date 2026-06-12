---
title: "Audio problems on ASUS A7TC"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by jackfigus on 2007-05-08
Hi all, I'm new to Ubuntu and I have a problem with my ASUS A7TC. After installed Ubuntu 7.04 on my notebook I Tried to get out some music but it wasn't possible.
lspci reports

***00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)***

but a dmesg | grep alsa gives back

[B][I][   19.988000] saa7134_alsa: Unknown symbol snd_ctl_add
[   19.988000] saa7134_alsa: Unknown symbol snd_pcm_new
[   19.988000] saa7134_alsa: Unknown symbol snd_card_register
[   19.988000] saa7134_alsa: Unknown symbol snd_card_free
[   19.988000] saa7134_alsa: Unknown symbol snd_pcm_stop
[   19.988000] saa7134_alsa: Unknown symbol snd_pcm_format_physical_width
[   19.988000] saa7134_alsa: Unknown symbol snd_ctl_new1
[   19.988000] saa7134_alsa: Unknown symbol snd_card_new
[   19.988000] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[   19.988000] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[   19.988000] saa7134_alsa: Unknown symbol snd_pcm_format_signed
[   19.988000] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[   19.988000] saa7134_alsa: Unknown symbol snd_pcm_format_big_endian
[   19.988000] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[   19.988000] saa7134_alsa: Unknown symbol snd_pcm_format_width
[/I][/B]

Can anyone try to help me? I'm not a long time Linux user so I'm not so expert but I can believe I have to boot WinXP to hear music and see videos

:)

---

