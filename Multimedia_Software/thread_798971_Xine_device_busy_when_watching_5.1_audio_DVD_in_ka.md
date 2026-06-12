---
title: "Xine device busy when watching 5.1 audio DVD in kaffeine"
date: 2008-05-18
forum: Multimedia Software
---

### Post by Metallion on 2008-05-18
When I first began using Linux I couldn't get the normal stereo sound to output to all my 5.1 speakers. Eventually I solved that by adding this .asoundrc to my home directory.

```

pcm.!dmix {
   type dmix
   ipc_key 1024
   slave {
       pcm "hw:0,0"
       channels 6
       period_size 1024
       buffer_size 5120
   }
}
pcm.!default {
   type plug
   slave.pcm "dmix"
   slave.channels 6
   route_policy duplicate
}

```

Since then I thought everything worked fine but I recently noticed that whenever I watch a DVD in Kaffeine using the 5.1 audio, it says **xine "Audio output unavailable. Device is busy."** and refuses to play it. However, if I play the same DVD with stereo audio it works just fine.

I have a feeling something in the .asoundrc file might be the cause here but I just compiled the file from a few wikis and forums so I have virtually no knowledge of .asoundrc hacking.

Is there anyone who knows what could be the cause here?

---

### Post by xc3RnbFO8P on 2008-05-18
Try this:
[http://ubuntuforums.org/showthread.php?t=387058]("http://ubuntuforums.org/showthread.php?t=387058")

---

### Post by Metallion on 2008-05-20
Thanks for the reply but unfortunately this didn't help. :( Does anyone else have any ideas?

---

