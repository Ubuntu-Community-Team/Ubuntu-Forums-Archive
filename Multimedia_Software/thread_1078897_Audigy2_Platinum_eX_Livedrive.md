---
title: "Audigy2 Platinum eX Livedrive"
date: 2009-02-23
forum: Multimedia Software
---

### Post by paimon.soror on 2009-02-23
Hey guys,

Wonderful forum here.  I am a new ubuntu user but I have been using unix at school/work so I am pushing more towards an intermediate user.  I just recently migrated from vista to ubuntu 8.10 and I have been trying to find the answer to one question, but the only answers I have found have been related to the Gentoo platform. 

I have a creative audigy2 platinum eX sound card installed.  All is well and I am using the alsa drivers that came with ubuntu (no modifications at all), however, the only thing that isn't working is the live drive.  I am able to " cat /dev/snd/midiC0D1" and see some garbage on the screen when i press buttons on my remote / turn knobs on the live drive, however nothing happens in the OS.

I have tried following this guide : [http://www.gentoo-wiki.info/Creative_Labs_Sound_Blaster_Audigy_2_Platinum](http://www.gentoo-wiki.info/Creative_Labs_Sound_Blaster_Audigy_2_Platinum) but the place where I got stuck was at the line that tells me to append "post-install....".  As far as i know ubuntu doesn't recognize post-install.  Is there alternatives, or has anyone found a better guide?  Am i just missing something simple?

---

### Post by paimon.soror on 2009-02-23
bumpage please

---

### Post by paimon.soror on 2009-02-23
Mods please label this as solved!  Thanks

For those who also need help with this topic:

[http://translate.google.com/translate?hl=en&sl=fr&u=http://alexandre.touret.free.fr/dotclear/index.php/post/2005/09/20/22-configuration-debian-etch-creative-audigy-2-zs-platinium-pro&ei=pnejSb7UHY3BtgeV-MzLBA&sa=X&oi=translate&resnum=10&ct=result&prev=/search%3Fq%3D/dev/snd/midiC0D1%2Blivedrive%26start%3D10%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:unofficial%26sa%3DN](http://translate.google.com/translate?hl=en&sl=fr&u=http://alexandre.touret.free.fr/dotclear/index.php/post/2005/09/20/22-configuration-debian-etch-creative-audigy-2-zs-platinium-pro&ei=pnejSb7UHY3BtgeV-MzLBA&sa=X&oi=translate&resnum=10&ct=result&prev=/search%3Fq%3D/dev/snd/midiC0D1%2Blivedrive%26start%3D10%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:unofficial%26sa%3DN)

I followed the instructions on that page from start to end and it worked like a charm!

---

