---
title: "Cannot capture audio from line input, SB0100 soundcard"
date: 2014-05-19
forum: Multimedia Software
---

### Post by mattmoose1969 on 2014-05-19
Hello. I can monitor the line input at the card's output via a software mixer fader, but I cannot capture/record this audio source into the Jack sound system. It is as if all the mixer apps I can find cannot correctly operate the card.

Audacity can record this audio input, stutteringly, but it seems that Jack cannot pick it up at all as a capture stream. But ultimately, I need Ardour to record the line input, via Jack.

Please can anyone suggest some logical steps to troubleshoot this? It all worked fine in a previous version of Ubuntu Studio.

---

### Post by mattmoose1969 on 2014-06-02
SOLVED: I used alsamixer to inspect and control the capture sources/levels. The space bar selects and deselects the capture switches for capturable channels. I just turned every record source up and set it to capture, until Line Input audio could be seen reaching Ardour via Jack. Then I turned the sources down one by one until the necessary switches/channels remained obvious. Not so obviously, the AC97 source needed turning up, and a generic faderless capture switch needed selecting.

kmix used to be my mixer of choice, but in this distro it did not appear to show all the controls available on my SB0100. I wasn't as familiar with alsamixer!!!!

thanks to zequence on the IRC channel for encouragement :)

---

### Post by Yellow Pasque on 2014-06-02
Please mark thread solved (thread tools menu towards top).

---

