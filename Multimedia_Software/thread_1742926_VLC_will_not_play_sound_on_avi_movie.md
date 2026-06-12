---
title: "VLC will not play sound on avi movie"
date: 2011-04-29
forum: Multimedia Software
---

### Post by angmoth on 2011-04-29
I'm running to 11.04 and I can't seem to get the file to play sound. I've tried others and none seem to work. I've tried downloading all sorts of codecs but either not the right ones or just not doing something right...:confused::confused::confused:

---

### Post by el_koraco on 2011-04-29
sudo apt-get install phonon-vlc

Got to System Settings, Multimedia, Phonon. Choose vlc as the backend instead of Gstreamer.

---

### Post by angmoth on 2011-04-30
sudo apt-get install phonon-vlc

That doesn't work so I just did 
sudo apt-get install phonon
and then I went to system settings and founds nothing that said multimedia

---

### Post by angmoth on 2011-04-30
I apologize, turns out the codec isn't the issue it's my headphones I use. So, how do I make it so that I can use my headphones with Ubuntu? No sound goes through them. They are the Razer Megalodon headphones.

---

