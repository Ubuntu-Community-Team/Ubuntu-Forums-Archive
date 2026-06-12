---
title: "snd_seq_oss"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by sovereign_soul on 2007-03-22
After a clean install of Ubuntu Edgy eft, I had problems with the mic/headphone. This got resolved once I compiled and installed alsa driver/lib/util from the alsa project website.

However, during insertion of the compiled module, snd_seq_oss gave the following error :

 Error inserting snd_seq_oss (/lib/modules/2.6.17-11-generic/kernel/sound/acore/seq/oss/snd-seq-oss.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Dmesg output is as follows :

[17208366.412000] snd_seq_oss: Unknown symbol snd_seq_kernel_client_enqueue
[17208366.412000] snd_seq_oss: Unknown symbol snd_seq_set_queue_tempo
[17208366.412000] snd_seq_oss: Unknown symbol snd_seq_delete_kernel_client
[17208366.412000] snd_seq_oss: Unknown symbol snd_seq_autoload_lock
[17208366.412000] snd_seq_oss: Unknown symbol snd_seq_kernel_client_dispatch
[17208366.412000] snd_seq_oss: Unknown symbol snd_seq_kernel_client_enqueue_blocking
[17208366.412000] snd_seq_oss: Unknown symbol snd_seq_autoload_unlock
[17208366.412000] snd_seq_oss: Unknown symbol snd_seq_device_register_driver
[17208366.412000] snd_seq_oss: Unknown symbol snd_midi_event_free
[17208366.412000] snd_seq_oss: Unknown symbol snd_midi_event_no_status
[17208366.412000] snd_seq_oss: Unknown symbol snd_use_lock_sync_helper
[17208366.412000] snd_seq_oss: Unknown symbol snd_seq_device_unregister_driver
[17208366.412000] snd_seq_oss: Unknown symbol snd_seq_event_port_detach
[17208366.412000] snd_seq_oss: Unknown symbol snd_midi_event_new
[17208366.412000] snd_seq_oss: Unknown symbol snd_midi_event_decode
[17208366.412000] snd_seq_oss: Unknown symbol snd_seq_create_kernel_client
[17208366.412000] snd_seq_oss: Unknown symbol snd_seq_kernel_client_write_poll
[17208366.412000] snd_seq_oss: Unknown symbol snd_midi_event_encode_byte
[17208366.412000] snd_seq_oss: Unknown symbol snd_seq_kernel_client_ctl

Due to this OSS emulation isn't working.

Any idea how the problem be rectified ..

Thanks in advance.

---

