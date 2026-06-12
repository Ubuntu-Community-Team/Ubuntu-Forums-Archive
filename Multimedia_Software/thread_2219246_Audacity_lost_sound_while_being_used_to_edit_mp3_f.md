---
title: "Audacity lost sound while being used to edit mp3 file"
date: 2014-04-23
forum: Multimedia Software
---

### Post by mamboze on 2014-04-23
I have a fairly large mp3 file of spoken words and I've been exporting individual words as small mp3 files. I have done this quite a few times (I use the files in an English language class). I've been using an external USB sound card (ASUS Xonar) for most of this work. This setup has worked reliably for a number of months. This morning Audacity lost sound with the Xonar on, but was playing back thru the laptop's built in speakers OK. Then this afternoon, Audacity lost sound even with the laptop speakers. The only recent change in the system was an upgrade to 12.04 from 11.10. Audacity is the only app that is not outputing sound, VLC and internet pages are OK either thru the Xonar or laptop speakers.

Any help would be very much appreciated.

Edit: I forgot to add that I uninstalled (apt-get purge) and reinstalled Audacity from the repository. Still no sound.

---

### Post by mamboze on 2014-04-23
Has nobody any suggestions on this problem?

---

### Post by mamboze on 2014-04-29
WOW, is there no one that has had this problem with audacity. Pretty hard to believe! Surely, I'm not the only one ever to experience this hassle with audacity. 
Any help would be most welcome

---

### Post by kostkon on 2014-04-29
Since you have recently upgraded, you could try resetting your pulseuadio configuration completely, by deleting your .pulse hidden folder in your home, then logging out and back in.

Another option is to install pulseuadio volume control (pavucontrol is the package), start playing an audio file in audacity and then click on Playback in pavucontrol and tell audacity to use your usb card for its output. Before doing that, open audacity's preferences, click on Devices and make sure that the host is set to Alsa, and the devices to Default.

Hope that helps.

---

### Post by mamboze on 2014-04-29
Hi, you got it!!. I deleted the .pulse file, no change. I then went to audio prefs and changed devices to Default.  Voila!! it worked. Many thanks for your help.

---

