---
title: "Bluetooth a2dp refuses to work"
date: 2010-11-13
forum: Multimedia Software
---

### Post by petrafan007 on 2010-11-13
So I've searched all over the web and followed every bit of instruction that I could. I get bluetooth manager to detect my phone and it pairs up without any problem. Even when I set it up to connect to play streaming music from the phone it links up but I hear nothing from the speakers. Of course, in pulseaudio I do see "Internet Phone", but there's no way I can edit it. And whenever I try to do this step, I get a failure

Now we need to tell PulseAudio that your Bluetooth headset exists:

    *

      pactl load-module module-alsa-sink device=btheadset
      pactl load-module module-alsa-source device=btheadset


Failure: Module initalization failed:confused::confused::confused:

And I can't get past this. I don't know what I'm doing wrong. Any help would be highly appreciated!

Thanks!

---

### Post by loveman on 2010-11-16
If you are running Maverick Meerkat I think you may not need to do that final step as the module may already be loaded.
I had the same problem trying to stream a2dp from ipad to ubuntu and got the same error about the module at the same point. Everything else seemed to be working but no sound output. If I right click on the bluetooth manager icon in the notification area and select <plugins> from the dropdown menu, I see that the Pulseaudio plugin is not selectable so I guess that is part of the problem. Anyway, I can get audio out by running 

gstreamer-properties

from the terminal and choosing <alsa> input and output.

Unfortunately the sound is garbled, stuttering, choppy and speeds up and slows down all the time. But at least I have sound - so that is progress!

(In case anyone else reads this, yes, I have setup hciconfig accept,master, park, sniff etc.)

So far this has been the most difficult thing to get working in Ubuntu and now I have it half working I am stuck. Anyway - that isn't your problem - let us know if you get it working and if the sound is better than mine!

---

