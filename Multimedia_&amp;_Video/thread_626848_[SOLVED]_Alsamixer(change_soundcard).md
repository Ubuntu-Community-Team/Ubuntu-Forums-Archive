---
title: "[SOLVED] Alsamixer(change soundcard)"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by Dave Otter on 2007-11-29
How do I set the souncard I want to use in alsamixer?
          Have done asoundconf  and been to applications-system-preferences sound and the card I use is set as default
    BUT NOT IN ALSAMIXER
               What have I missed?

---

### Post by kyphi on 2007-11-29
Many people start with on-board sound (sound chip) and then install a proper sound card.

Since the inbuilt chip is no longer required, you need to go into the BIOS to disable on-board sound.

After you have done that, only your sound card will register on your system.

---

### Post by warrior24 on 2007-11-29
I also just did the same thing just disable it in bios and  the sound works. But my sound level icon no longer works(the one you control, the sound level from) . I don't mean to hijack this thread but I feel that it may be a similar problem Dave Otter  may run into.

---

### Post by kyphi on 2007-11-29
> my sound level icon no longer works

The speaker icon on the top panel is linked to the alsamixer sound control and should not be affected by a change of sound output devices in the BIOS.

Check your controls by right clicking on the speaker icon in 'Open Volume Control' as well as 'Preferences' or restart X or reboot.

---

### Post by Dave Otter on 2007-11-29
kyphi  
      Thanks did as you suggested - problem appears to have corrected tho to early to say whether it will be permanent.

     Anyhow it certainly better

    Thanks

---

### Post by kyphi on 2007-11-29
Thank you for the feedback, Dave Otter.

---

