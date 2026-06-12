---
title: "Totem's sound settings (AC3 passthrough and Stereo)"
date: 2006-03-02
forum: Multimedia &amp; Video
---

### Post by DonQuixote on 2006-03-02
In playing with some Totem settings I tried out "AC3 passthough" in the "Edit -> Preferences -> Audio" tab.  I lost the sound in the .avi's I was testing with.  So, I went back to the "Audio" tab and changed the selection to "Stereo" (Where is was at first).  I restarted Totem... still no sound.

I went back to the audio tab and saw that it was still set to "AC3 passthrough" even though I had changed it to "Stereo" the last time I ran the program.

I have tried changing it back many times, but it has always remained on "AC3 passthrough" when ever I have restarted and gone to look at the "Audio" setting.

Is there a solution to this problem?

Thanks!

---

### Post by noomz on 2006-03-02
Try to comment out the line specify in audio device u want to use in '~/.gnome2/totem_config' 

and start totem then select audio device again :)

---

### Post by MrFSL on 2006-04-10
Here's an oddity. I did the same thing and had the same problem. So instead of setting it back to stereo I set it to the next one up from AC3 in the list. This change worked. I continued to move up the list with the settings applying all the way up to stereo which I was never able to set again.

:???:

---

