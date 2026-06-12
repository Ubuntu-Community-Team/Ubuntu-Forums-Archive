---
title: "Transmission doesn't start torrents automatically"
date: 2010-12-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Yahoé on 2010-12-29
Under Natty, using Transmission 2.13, when selecting a torrent under Firefox, Transmission main UI starts but then nothing happens, torrent is not imported.

If the .torrent is downloaded locally to the download folder, then Transmission starts downloading it.

Could find if this is a know problem.

Any assistance welcome

---

### Post by Starks on 2010-12-29
Confirming.

You have to double-click on the torrent in the download manager or file manager in order to load it.

---

### Post by Yahoé on 2010-12-30
Bonjour Starks,

I don't think you understood the problem explained here. Once a .torrent is selected, Firefox calls for Transmission as it should, Transmission main UI does start, but then should it open the "Torrent options" windows, but fails to do so.

I tried that from a USB Live version of Natty as well with the same result, this might be a bug.

Regards,

Alain-Olivier

---

### Post by Starks on 2010-12-30
Umm, I use Transmission and Deluge on a daily basis. I know exactly what the problem is and I've experienced it.

My previous post was the work-around.

---

### Post by macroshaft on 2010-12-30
I reported this here a while back and everyone just ignored it! But yes, I am experiencing this too.

---

### Post by cariboo on 2010-12-30
I use qbittorrent, and I get the same behavior with both Firefox and Chromium

---

### Post by Framli on 2010-12-31
My work-around : I make Transmission watching new torrents in ~/Downloads. 

As it makes a copy in its own folder when it starts using them, you can delete them from ~/Downloads.

---

