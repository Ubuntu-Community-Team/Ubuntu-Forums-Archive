---
title: "&quot;Bookmark&quot; in MythTV"
date: 2008-11-13
forum: Mythbuntu
---

### Post by ajut on 2008-11-13
Hello,

Is it possible to set "bookmark" when watching recording, so I can resume from bookmarked position later?

I looked into: http -> "http//www.mythtv.org/wiki/index.php/User_Manual:Watch_Recordings" and can't find feature like that.

For a sample XBMC have such feature.

BR,
Ajut

---

### Post by SiHa on 2008-11-13
Pressing Enter or 'OK' on the remote will mark a position. Playback will then start from that position next time.

Even simpler though, is to go into the playback options menu (Setup - TV Settings - Playback, I think). There is an option called 'Action on ESC' or something similar. In the submenu there, you have different options which you can select to appear in a menu whan you exit a recording. One of these is 'Save Position and Exit'.

I have mine configured to prompt to Just Exit, Save Position & Exit or Delete, and it works nicely.

Be aware, though, that if you have saved a position like this, it seems to be automatically cleared when you next watch, so if you then exit without saving the position, it will start from the beginning of the recording. Not sure if this applies if you have manually marked a position via OK/Enter.

Sorry the location in the setups is a bit vague, but I'm at work at the moment. There are too many setup menu's to remember them all...

HTH

Simon

---

### Post by ajut on 2008-11-13
> **SiHa said:**
> Pressing Enter or 'OK' on the remote will mark a position. Playback will then start from that position next time.

Even simpler though, is to go into the playback options menu (Setup - TV Settings - Playback, I think). There is an option called 'Action on ESC' or something similar. In the submenu there, you have different options which you can select to appear in a menu whan you exit a recording. One of these is 'Save Position and Exit'.

I have mine configured to prompt to Just Exit, Save Position & Exit or Delete, and it works nicely.

Be aware, though, that if you have saved a position like this, it seems to be automatically cleared when you next watch, so if you then exit without saving the position, it will start from the beginning of the recording. Not sure if this applies if you have manually marked a position via OK/Enter.

Sorry the location in the setups is a bit vague, but I'm at work at the moment. There are too many setup menu's to remember them all...

HTH

Simon

Thanks Y for your answer :)

It's still little bit confusing to operate blindly. I mean in XBMC you can mark multiple positions and get overview of them in a personal window with starting times and screenshots and delete them separately. It's good feature, when different people (like me and my wife) happens to watch same recording in different time and with breaks.

---

### Post by SiHa on 2008-11-13
Ah, I see.

Not sure about that to be honest.

I really must grab XMBC and have a look, it sounds interesting. It's just that after investing so much time getting Myth up and running, I'd feel a little like a traitor.

---

### Post by ajut on 2008-11-13
> **SiHa said:**
> Ah, I see.

Not sure about that to be honest.

I really must grab XMBC and have a look, it sounds interesting. It's just that after investing so much time getting Myth up and running, I'd feel a little like a traitor.

I have long experience with system, where mythtv was backend (recording server) and XBMC was frontend. First there was phyton script for that and now You can use built in mythtv support. In Videos section add myth://mythtv:<password>@<IP>. It's working quite well but, because of XBMC can't handle my DVB-T TS (MPEG4-AVC), I can't use it for that, until ffmpeg in XBMC source is not updated. It (maybe) will happen after next stable release of XBMC. If You have mpeg2 (from DVB-T or analogue - compressed to mpeg2 by PVR150 for example), then it should work (worked for me with PVR150).

BR,
Ajut

---

### Post by SiHa on 2008-11-13
> myth://mythtv:<password>@<IP>
Thanks for that, I'll give it a try when I have a moment.

---

### Post by ajut on 2008-11-14
.

---

