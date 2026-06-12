---
title: "HDA Intel (IRQ conflict?) problems"
date: 2010-09-11
forum: Multimedia Software
---

### Post by MrBordello on 2010-09-11
Hi!
I've just installed Maverick on an Acer Aspire L5100 desktop PC. Everything seems to be fine, but the soundcard seems to be conflicting with my mouse - every time I do something sound-related (e.g. change the volume) my left mouse button gets stuck in a click event and is unusable, till I restart X.

There are some errors when I load the snd_hda_intel module:

[  106.237152] HDA Intel 0000:01:05.2: PCI INT B disabled
[  106.239239] HDA Intel 0000:00:14.2: PCI INT A disabled
[  110.631971] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  110.665214] hda_codec: ALC1200: BIOS auto-probing.
[  110.695011] HDA Intel 0000:01:05.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  110.695133] HDA Intel 0000:01:05.2: irq 43 for MSI/MSI-X
[  113.724511] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[  114.728510] hda-intel: No response from codec, disabling MSI: last cmd=0x000f0000
[  115.732511] hda-intel: Codec #0 probe error; disabling it...
[  116.752508] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x000f0000
[  117.003703] hda-intel: Invalid position buffer, using LPIB read method instead.
[  117.003716] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

I've already googled the errors and tried some parameters with the module, but no luck ...

---

### Post by Yellow Pasque on 2010-09-11
IRQ 19 can be problematic. My BIOS has a special option to enable/disable it.
I'm not sure what to suggest except making sure the latest BIOS is used: [http://www.acer.de/acer/service.do?LanguageISOCtxParam=de&miu10einu24.current.attN2B2F2EEF=440&sp=page15e&ctx2.c2att1=9&miu10ekcond13.attN2B2F2EEF=440&CountryISOCtxParam=DE&ctx1g.c2att92=80&ctx1.att21k=1&CRC=1106555572](http://www.acer.de/acer/service.do?LanguageISOCtxParam=de&miu10einu24.current.attN2B2F2EEF=440&sp=page15e&ctx2.c2att1=9&miu10ekcond13.attN2B2F2EEF=440&CountryISOCtxParam=DE&ctx1g.c2att92=80&ctx1.att21k=1&CRC=1106555572) and seeing if there are any options in it to reserve/disable the problematic IRQ

---

### Post by MrBordello on 2010-09-11
I've upgraded to the latest BIOS - didn't help.
The BIOS-options are pretty limited too, but I can "reserve" IRQs 1-9, I played around with some options, but the error persists.

---

