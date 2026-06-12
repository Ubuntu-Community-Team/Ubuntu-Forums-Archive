---
title: "Recover broken avi file over 4gb"
date: 2012-02-05
forum: Multimedia Software
---

### Post by db579 on 2012-02-05
I was using CamStudio to record but unfortunately the program crashed before I could properly stop and save the video. I have a 4gb avi file it was producing from the temp directory but opening this in VLC or similar does nothing the seek bar just stays at 0 and no video content loads.

Is there any way of recovering the video content saved in that file? Thanks for any suggestions!

---

### Post by SeijiSensei on 2012-02-05
[This posting](http://falcon1986.wordpress.com/2010/09/10/how-to-fix-avi-files-within-ubuntu-quick-command/) shows how to use **mencoder** to accomplish this task.  Positive results are not guaranteed, of course, but it's the best place to start.

---

### Post by db579 on 2012-02-05
Hi thanks for the link. Using the mencoder command gave me this output:

```

mencoder: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
MEncoder SVN-r33713-4.6.1 (C) 2000-2011 MPlayer Team
success: format: 0  data: 0x0 - 0xfa00
Invalid seek to negative position ffffffffffffffff!
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

```

Does that maybe mean the video content hasn't been compressed yet?

---

### Post by db579 on 2012-02-07
Is there anything else I could try? Thanks

---

