---
title: "[SOLVED] I want to create Korean subtitles!"
date: 2008-11-27
forum: Multimedia Software
---

### Post by poebae on 2008-11-27
(Ubuntu 8.10)

I'm captioning some English language videos with Korean subtitles using subtitleeditor, and I can input the text with no problems, but when I go to save, the text either disappears or gets replaced by a garbled mess.

I've installed Korean support and checked the "enable complex character input" box, and I've tried to find a way to be able to save the file as euc-kr in subtitleeditor, but no dice.

Can anyone help with this?

---

### Post by Keyper7 on 2008-11-27
Are you sure the encoding in subtitleeditor is the correct one?

If I remember correctly, the default is ISO-8859-15.

PS: it might take an entire day to check your reply to this, but I will

---

### Post by poebae on 2008-11-27
Yeah the default is ISO-8859-15, but that doesn't seem to work (the characters don't save), so I'm thinking I might have to use a different encoding.

---

### Post by poebae on 2008-11-27
Hmm... I just went to preferences -> encoding, and added all of the different korean encoding options, but all of them save the text as weird broken characters.

---

### Post by Keyper7 on 2008-11-28
> **poebae said:**
> Yeah the default is ISO-8859-15, but that doesn't seem to work (the characters don't save), so I'm thinking I might have to use a different encoding.

Sorry, I should have expressed myself better.

The default of ISO-8859-15 is in fact wrong as far as I know. You should use UTF-8.

---

### Post by poebae on 2008-11-28
> **Keyper7 said:**
> Sorry, I should have expressed myself better.

The default of ISO-8859-15 is in fact wrong as far as I know. You should use UTF-8.
I tried using UTF-8 just then, but when I save the file, close it and reopen, the text that's supposed to be Korean just appears as garble.

Hmmm I need to make this video by Saturday night, can anyone help?

---

### Post by poebae on 2008-11-29
Just to update, saving the subtitles in UTF-8 format and adding the subtitles in AviDemux with the UTF-8 specification worked a treat.

Thanks for your help :D

---

### Post by Keyper7 on 2008-11-30
Ah, yes, I forgot to mention that whatever you use to play/edit the video should use UTF-8 too.

Anyway, glad the problem is solved. :)

---

