---
title: "vlc hardware decoding ubuntu 24..04"
date: 2024-05-30
forum: Multimedia Software
---

### Post by marcopc on 2024-05-30
Hi, vlc used hardware decoding on my pc with intel cpu on ubuntu 22.04, but after updating to ubuntu 24.04 it doesn't work anymore. As you can see from the intel_gpu_top screenshot, vlc now uses render/3d instead of video decoding.

[IMG]https://www.dropbox.com/scl/fi/41q9a35qx34lbhosv2bnt/Schermata-del-2024-05-08-09-42-03.png?rlkey=1qekfxgkly8h4zhm7hylyiuau&dl=0[/IMG][IMG]https://www.dropbox.com/scl/fi/41q9a35qx34lbhosv2bnt/Schermata-del-2024-05-08-09-42-03.png?rlkey=1qekfxgkly8h4zhm7hylyiuau&dl=0[/IMG]
[IMG]https://www.dropbox.com/scl/fi/41q9a35qx34lbhosv2bnt/Schermata-del-2024-05-08-09-42-03.png?rlkey=1qekfxgkly8h4zhm7hylyiuau&dl=0[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293824&stc=1[/IMG]
Do you have the same problem? How could I solve it?

Useful information:
The file is the same one I used with ubuntu 24.04 with h264 encoding, but the same happens with h265 files.

The problem is the same whether installing vlc from apt or from snap.

Hardware decoding works fine in firefox when watching youtube.

---

### Post by currentshaft on 2024-05-30
In VLC preferences, under Input/Codecs, what option is selected for "Hardware-accelerated decoding"?

---

### Post by marcopc on 2024-05-31
The setting is "automatic", same as with ubuntu 22.04.

---

