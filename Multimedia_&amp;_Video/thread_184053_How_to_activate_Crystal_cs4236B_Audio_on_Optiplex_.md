---
title: "How to activate Crystal cs4236B Audio on Optiplex GX1"
date: 2006-05-29
forum: Multimedia &amp; Video
---

### Post by danrael on 2006-05-29
>  At the Desktop, open Applications> Accessories> Terminal
>  At the flashing cursor, type:  sudo gedit
>  Type your system password
>  In gedit, click on the "Open" icon
>  Double-click "File System" from the lefthand sidebar
>  Double-click the "etc" folder
>  Scroll down past the folders to the "modules" file, and open it
>  On the line after the last entry, type:

     snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5

>  Click the "Save" icon, and Quit the program.  Reboot.
>  Go to System> Preferences> Sound
>  "CS4236B" should appear in the Default sound card field
>  Make sure "Enable sound server startup" is unchecked
>  Go to Applications> Sound and Video> Volume Control
>  Make sure the volume level is up in both Playback and Capture
>  Open CD Player or Sound Juicer and test for audio from a music cd****

---

### Post by Permanent Beginner on 2007-09-03
It would make me exceedingly happy if this worked, but there -is- no "File System" on the left hand sidebar, and nothing that I click will make it appear, nor will the "type in a name" find either "File System" or "etc".

Any ideas?

PB

---

