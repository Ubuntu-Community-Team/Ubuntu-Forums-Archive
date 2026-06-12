---
title: "problem with microphone es1968 sound card"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by tiepolo on 2007-02-15
Hello everybody!

I have a big problem with a old card ESS ES1968 maestro 2, correctly recognized as pci extension, with a old laptop under xubuntu dapper; card is listed by lshw with his driver and module snd-es1968 is charged, as per lsmod.

i can hear ok, but no microphone, which run under W$. i can get an external usb sound card run ok, but i'd prefer to use internal soundcard to let usb for the net card.

a bug in capture was known in alsa, and should have been solved after version 1.0.11; i successfully installed from alsa-project source in my pc alsa 1.0.13 in order to be sure to get last driver - checking alsamixer -V capture capture has been set as per indications above, but no way to move or select microphone, which is set to 0, neither for $ nor for #.

I think this the same bug noted by alsa (capture doesn't work) but not sufficiently expert.
([www.alsa-project.org/alsa-doc/doc-php/template.php?company=ESS+Technology&card=.&chip=ES1968+%28Canyon3d%29%2C+ES1968+%28Maestro-1%29%2C+ES1968+%28Maestro-2%29%2C+ES1968+%28Maestro-2E%29%2C+ES1968+%28Maestro-2EM%29&module=es1968](www.alsa-project.org/alsa-doc/doc-php/template.php?company=ESS+Technology&card=.&chip=ES1968+%28Canyon3d%29%2C+ES1968+%28Maestro-1%29%2C+ES1968+%28Maestro-2%29%2C+ES1968+%28Maestro-2E%29%2C+ES1968+%28Maestro-2EM%29&module=es1968))

i also saw people making patches for this card, but i didn't understand if it was the right way, that's above what i know. ([http://www.linuxhq.com/kernel/v2.6/15-git12/sound/pci/es1968.c](http://www.linuxhq.com/kernel/v2.6/15-git12/sound/pci/es1968.c))

I wasn't also able to find maestro module in my distribution in order to run oss driver instead, to check the oss way.

Do you have suggestion?

I really didn't get any idea googling......

Thanks !

---

