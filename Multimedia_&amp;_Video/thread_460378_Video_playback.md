---
title: "Video playback"
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by tdwester on 2007-05-31
For some reason I can not get video playback to work. It will not come up in M-player or totem. I have all the codecs installed. The driver for the video seem to be ok also, I have been trying to get this to work for 5 days now.

---

### Post by benanzo on 2007-05-31
what kind of video is it?  do you know the codec or the extension?

---

### Post by tdwester on 2007-05-31
It is just a dvd.

---

### Post by benanzo on 2007-06-01
Does the disc mount in Nautilus?  If you click the **Places** menu after the DVD has been inserted does the disc show as a menu option?

If not, I would recommend checking your media mounting settings.

Go to **System -> Preferences -> Removable Drives and Media** and make sure that the top three check boxes are checked under **Removable Storage**.

---

### Post by david_2001 on 2007-06-01
> **tdwester said:**
> For some reason I can not get video playback to work. It will not come up in M-player or totem. I have all the codecs installed. The driver for the video seem to be ok also, I have been trying to get this to work for 5 days now.
Do you do have libdvdcss installed?

---

### Post by ronocdh on 2007-06-01
> **david_2001 said:**
> Do you do have libdvdcss installed?
Definitely the answer, tdwester. This is necessary because most commercial DVDs come encrypted in such a way that your computer cannot read them; the other major operating systems are licensed to have the necessary decrypting codec in their component software suites. 

I am not certain, but perhaps the application VLC comes prepared to play DVDs. (**sudo apt-get install vlc** to try it out.)

---

### Post by tdwester on 2007-06-03
Yes it mounts and I have the liddvdcss installed. I first thought it may be a hardware problem but swaping out the dvd burner did not help.

---

