---
title: "Gwenview video have a blue tone in all video"
date: 2014-04-30
forum: Multimedia Software
---

### Post by Miguel_Antonio_Sit on 2014-04-30
I updated my kubuntu 13.10 to 14.04. Gwenview can shhow videos and images. Since update the videos have a blue screen, all is in a blue tone. In other video player all is normal, just in gwenview. Is very useful for me on my school presentations, but now i can show a video. How can i fix it? By the way, the images in gwenview is fine, just in video is the problem.

---

### Post by Miguel_Antonio_Sit on 2014-05-02
I was trying some configurations, but nothing.
Any clue?

---

### Post by Yellow Pasque on 2014-05-02
Well, Gwenview uses Phonon to play video. You could try the Phonon vlc backend (or the gstreamer backend if you're currently using the vlc one).

---

### Post by mahen2 on 2014-06-04
Hi ! I have the very same issue since upgrading, too ! Did you figure out the solution / the root cause meanwhile ? More importantly, did you take the time to file a bugreport or should I do it ? It's important to get it fixed for the LTS release :)

Thanks !

---

### Post by Yellow Pasque on 2014-06-04
@mahen2, please try vlc backend (you can install phonon-backend-vlc package and chooce VLC backend in Phonon section of systemsettings).

---

### Post by supersasho on 2014-06-29
Hi, I had the same problem and installing phonon-backend-vlc did the trick. Thanks. :)

---

### Post by bagrnator on 2015-04-16
Thanks a lot. This helps.

---

### Post by RogerDavis on 2015-10-30
I have the same problem.  How do I install phonon-backend-vlc ?

I see it in Synaptic.  Maybe just select it and go?

Also, I don't see  "VLC backend in Phonon section of systemsettings", so I guess this will appear after Phonon-backend-vic is installed?

Thanks!

---

### Post by nrbierb on 2015-11-11
> **RogerDavis said:**
> I have the same problem.  How do I install phonon-backend-vlc ?

I see it in Synaptic.  Maybe just select it and go?

Also, I don't see  "VLC backend in Phonon section of systemsettings", so I guess this will appear after Phonon-backend-vic is installed?

Thanks!
For 14.04:
Select and load from synaptic.
Choose System Settings
In "Hardware" line choose "Multimedia"
In "Multimedia" choose "Audio and Video Settings"
Now choose the "Backend" tab.
You should see GStreamer and VLC as choices. Click on VLC and then click the "Prefer" button. It will move it to the top.
Start Gwenview and enjoy the good videos with the right colors.

---

### Post by RogerDavis on 2015-11-13
I installed phonon-backend-vlc.

I have no "Multimedia" anywhere in System Settings, and no "Audio and Video Settings".

---

