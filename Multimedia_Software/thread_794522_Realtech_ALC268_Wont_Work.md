---
title: "Realtech ALC268 Wont Work"
date: 2008-05-14
forum: Multimedia Software
---

### Post by borisagrees on 2008-05-14
i get an error message like this when trying to use ALSA

audiotestsrc wave=sine freq=512 | audioconvert| audioresample| gconfaudiosink profile=chat: Could not open resource for writing.

Please help but keep it simple

---

### Post by borisagrees on 2008-05-14
i Have tryed Re: Realtek ALC268 Simple Please 

sudo su
<type in passord>
sudo gedit /etc/modprobe.d/alsa-base

Then, at the end of the file that pops up (as in right at the bottom) add:

options snd-hda-intel model=toshiba

Still did not work after restart

i'm not an experienced user and have a fourum about the same thing but have been reccomened to poast here as well.

i have looked all over the net for a simple solution but its either technical jargon witch i dont understand or it has not worked iu have installed the linux drievrs from realtech but they did not work either

---

