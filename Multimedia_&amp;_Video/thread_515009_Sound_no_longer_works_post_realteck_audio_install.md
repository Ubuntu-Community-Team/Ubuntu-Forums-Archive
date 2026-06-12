---
title: "Sound no longer works post realteck audio install"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by FreeSoul on 2007-08-01
Hello,

     I was trying to get my microphone working and someone suggested installing the "realtek-linux-audiopack-4.06a" package. I have a Dell XPS M1710 laptop with an Intel sound card (driver hda-intel I believe).
     Well, after installing the package unsuccessfully I lost my sound. There is a cross through my speaker symbol. Also under sound preferences the sound card is gone. I tried following the directions " Comprehensive Sound Problem Solutions Guide" but to no avail. The realtek must have really hosed something.

     Can I uninstall the realtek package somehow? I followed this command line install, very short:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_recording_does_not_work](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_recording_does_not_work)

   I don't want to re-install linux if possible. If I have to I'd like to just install the binaries and leave my home directory, they are under different partitions.

Any ideas would be appreciated. In the mean time i have sound under windows (dual boot).

Thanks,
FreeSoul

---

### Post by wolfen69 on 2007-08-01
try this:  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Sound](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Sound)

---

### Post by FreeSoul on 2007-08-01
> **wolfen69 said:**
> try this:  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Sound](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Sound)


Thanks for the suggestion.
I tried it but it unfortunately doesn't help.
I still get this error message when I double click on the speaker icon:

> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

Any ideas to remove the unsuccessfully installed realtek package?

Thanks again,
FreeSoul

---

