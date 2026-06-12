---
title: "load card-specific configuration files"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by pille on 2006-08-21
hi,
i´m using 2 soundcards. both are recognized by the system.
here the output of
# cat /proc/asound/cards
0 [EMU1212m       ]: Audigy2 - E-mu 1212m [4001]
                     E-mu 1212m [4001] (rev.3, serial:0x40011102) at 0xec00, irq 201
1 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                     Ensoniq AudioPCI ENS1371 at 0xe000, irq 185

the second card is doing fine. but of the first one, the emu, i can´t get any output.
now i want to load a card-specific configuration file for the first soundcard. i saw them located under /usr/share/alsa/cards and i want to load EMU10K1.conf as card-specific configuration. how can i do this?

i´m not sure, but i think that the cause why i can´t hear any sound is because of the multiple i/o channels the card has and in the card-specific conf file i saw those channels configured.
in the preferences dialog of xmms in the alsa output plugin config i can select 3 devices for my emu card and 2 for the ensoniq card. playback works for the first device of the emu card and the other two dont work.
for the ensoniq card both devices work properly and i can hear sound.

the emu card i am using is called e-mu 1820.

can anybody help please?

greetz
pille

---

### Post by pille on 2006-08-22
can anybody tell me what the aliases.conf file located in /usr/share/alsa/cards means and how it works?
i searched on the alsa project site but haven´t found any information.

---

### Post by pille on 2006-08-22
*push*
i was looking on alsa-project.org and havn´t found anything helpful.
i dont get any sound of the emu card, nothing worked!
please help!

---

