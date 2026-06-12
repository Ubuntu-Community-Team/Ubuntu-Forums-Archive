---
title: "Amarok &quot;xine was unable ... &quot; &quot;could not launch mail client&quot;"
date: 2007-03-15
forum: Multimedia &amp; Video
---

### Post by pixelstuff on 2007-03-15
(edit: first post sold ;))

hi 
I've been using Amarok for maybe two weeks a lot with no problems. Then I installed timidy and had all sorts of sound problems in games mainly. I hoped to get rid of it with removing the autostart entries  
this is what I followed:

   * Uncomment the following line (remove the "#" sign) 

#TIM_ALSASEQ=true

    * Set the required modules to load as well 

sudo gedit /etc/modules

    * Add the following modules to the end of the file 

snd-seq-device
snd-seq-midi
snd-seq-oss
snd-seq-midi-event
snd-seq

But, after a restart, the problem is still present in  Amarok: In the middle of playback it suddenly says: "xine was unable to initialize any audiodrives".  Right now I count 11 such message windows. When I click ok on one of them I get "Could not launch mail client" and everything crashes. :(  I loved Amarok and want it back! Please help! Thank you

edit: I followed this guide 
[How to configure sound to work properly in GNOME]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME") without the slightest clue what I was doing but everything is fine again! I wonder if I can put timidity on autostart again.

---

### Post by catdriver on 2007-05-28
> **pixelstuff said:**
> hi When I click ok on one of them I get "Could not launch mail client" and everything crashes. :.
I'm getting this error too, and really want it to go away..... having amarok crash randomly because something want to call up a non existant email client is a pain in the butt.  Not to mention it really screws with my Zen V.  It will sometimes take a warm restart to get it recognized again.....

---

### Post by pixelstuff on 2007-06-01
Have you tried that guide that had solved my sound problems?

---

### Post by catdriver on 2007-06-16
> **pixelstuff said:**
> Have you tried that guide that had solved my sound problems?
I didn't need that, since my sound and lay back all work fine.  My errors occur during file transport.  I have learned, in the interim, that the mail launch is integral to bug reporting.  I have a post in on the Amarok forums, but no one has an answer.  The Amarok forums seem to have a very slow churn rate.  [http://amarok.kde.org/forum/]("http://amarok.kde.org/forum/")

---

