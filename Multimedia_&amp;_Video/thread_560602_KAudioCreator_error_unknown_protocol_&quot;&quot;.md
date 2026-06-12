---
title: "KAudioCreator error: unknown protocol &quot;&quot;"
date: 2007-09-26
forum: Multimedia &amp; Video
---

### Post by MacMan on 2007-09-26
Ciao,
I have an up-to-date Kubuntu 7.04 system, and my KAudioCreator doesn't work anymore.

My audio cd is read and accepted, the cddb entry is correctly retrieved, but if I select a track and then an encoder (Ogg, Lame, Wav, it doesn't make any difference) I get this error message:

[indent]Impossibile avviare il processo Impossibile creare un io-slave:
klauncher ha detto: Protocollo "" sconosciuto.
.[/indent]

Which, roughly translated, means something like: 

[indent]Impossible to start the process Impossible to create an io-slave:
klauncher said: Unknown protocol ""[/indent]

The encoders are correctly installed and work. I can extract the .ogg tracks browsing the audio cd in Konqueror.

Any ideas about what can I do to fix this?

Thanks in advance for any help.
Ciao.

---

### Post by MacMan on 2007-09-27
OK, I haven't fixed the issue, but I've found a good workaround: using K3B instead of KAudioCreator.

When I start the ripping process, K3B warns me there are other apps using the CD drive, but it can shut down them for me automatically; then, it works just fine. I guess this was the same problem KAudioCreator was having. Anyway, K3B seems to work better for me, so I'm sticking with it.

I hope this helps.

Ciao.

---

