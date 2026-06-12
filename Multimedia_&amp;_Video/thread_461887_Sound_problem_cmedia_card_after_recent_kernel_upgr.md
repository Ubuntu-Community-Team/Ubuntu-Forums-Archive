---
title: "Sound problem: cmedia card after recent kernel upgrade on feisty"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by Mark F on 2007-06-02
Upgraded kernel a few days ago via update manager. Sound worked intermittently then stopped. I have on-board sound card and a CMedia 5.1 card. I followed the instructions on the [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide) page aplay and lspci as expected. Tried reinstalling drivers from source and from ALSA site - same errors. Tail of output is attached.

Thanks in advance

Mark

---

### Post by jamespetts on 2007-06-04
My sound has also totally failed after installing the kernel upgrade. I have the latest ALSA RC installed (1.14 RC4), and a VIA HDA VT82xx. It worked fine (after manual installation of the latest ALSA version) before the kernel upgrade.

**Edit**: Booting using the old kernel image is an effective workaround to the problem.

---

