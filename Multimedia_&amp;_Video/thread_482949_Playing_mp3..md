---
title: "Playing mp3."
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by Rabindranath on 2007-06-24
I am unable to connect to the internet in kubuntu and ia there a mp3 player so that it can play those files in kubuntu. I tried vlc but it says "dependencies not satisfied" and says to install "liba" . Can someone please tell me where i can download those dependency packages in .deb or is there a vlc installation with all those dependency packages in .deb. I have to download it using XP. If there is any .tar packages please tell me how to install it.Help me please.

Thanks in advance.

---

### Post by Ziox on 2007-06-24
one way of doing so is manually accessing ubuntu's repository, which is located here:

archive.ubuntu.com < this is where apt draws all of its .deb files.

You must have all the dependencies in order to have a functioning application.

If you can, attempt to get internet first because by manuallly install .deb files, you increase the system's instability and the likeliness of a crash.

If the internet problem is software based do a thorough search of the forum.
to fine info about your internet card, use this command:


lspci -v

---

