---
title: "No simple control &quot;Capture&quot; in alsa mixer"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by AxAeo on 2007-12-06
I've been trying to get my microphone to work, and if I turn up some controls on alsamixer I any input in the mic is output through the speakers without recording, which means it's working partly at least. So I tried to find a solution via Google and found most people talking about turning "Capture" on. So after enough looking I found this command...

amixer set 'Capture' cap

Which SHOULD turn capture on... What is returned is...

amixer: Unable to find simple control 'Capture',0

Which makes sense seeing as I couldn't even find the Capture control while using alsamixer. Any idea how to get this control back?

---

