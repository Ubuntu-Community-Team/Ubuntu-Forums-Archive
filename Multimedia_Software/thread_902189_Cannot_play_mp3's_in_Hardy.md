---
title: "Cannot play mp3's in Hardy"
date: 2008-08-27
forum: Multimedia Software
---

### Post by theravenproject on 2008-08-27
Having just gotten some fresh tunes through transmission I naturally want to play them but none of my media players will play back?  Is it because these came from torres?  Or are there updates/patches for a known bug?  Please advise..oh this is the specific behavior:  I load the songs into my player (Rythbox or elisa) amd it loads my song and says it is playing it but it isn't-there is no progress on the progress bar as well as no sound (Which my God I finally fixed!

---

### Post by mcduck on 2008-08-27
No, it's not because the files are from "questionable sources",and it's not a bug: many commonly used media formats (like mp3) are patented and can not be freely distributed (at least in USA an some other countries). Because of that they are not included with the default Ubuntu install. You need to install them yourself, either by installing all the codecs you need, like Gstreamer0.10 packages, from the repositories, or by installing the ubuntu-restricted-extras package (which will give you most commonly used codecs and programs that are excluded from the default install).

"sudo apt-get install ubuntu-restricted-extras"

Edit: read this for more information & detailed instructions: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

