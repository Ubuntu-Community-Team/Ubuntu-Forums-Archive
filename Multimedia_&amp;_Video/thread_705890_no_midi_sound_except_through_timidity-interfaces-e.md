---
title: "no midi sound except through timidity-interfaces-extra gui"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by raydar on 2008-02-23
I'm unable to get any MIDI output except by playing a file through the GTK2 interface in the timidity-interfaces-extra package. Trying to play the same file by typing "timidity -Oj [filename]" results in these 3 lines:
      JACK tmpdir identified as [/dev/shm]
      cannot read response from jack server (No such file or directory)
      Couldn't open JACK device (`j')
But I have Jack running stably, Timidity is listed in the connections lists and appears to be (automatically) connected, and other system audio and Jack audio work fine.  Rosegarden won't make any sound, and neither will the little MIDI keyboard app. I've tried playing with the connections in Jack and Patchage to no avail, and haven't found any Ubuntu settings that specify MIDI volume level or device selection.  Also, if I open the MIDI file from Audacious, it won't play, but if I open it in Audacious by right-clicking on the MIDI file's icon, Audacious starts and then goes dark & hangs.

Hardware-wise, I have a PCI sound card installed as well as on-motherboard audio, but the problem existed before I installed that sound card and didn't change at all when I installed the card. I've attached a text file of what Rosegarden's detailed sequencer status reports, in case that could help; the regular status says "MIDI OK" as well as "audio OK."

I'm glad I downloaded the GUI for Timidity, 'cause after a month playing with a fresh Ubuntu Studio installation, finally I can hear a MIDI file.  I've searched this forum & elsewhere, but I haven't found how to track down why there's no other Jack- or non-Jack MIDI output.  Can anyone help?

---

