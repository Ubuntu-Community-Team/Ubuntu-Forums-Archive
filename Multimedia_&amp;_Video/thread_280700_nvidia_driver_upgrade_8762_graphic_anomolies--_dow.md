---
title: "nvidia driver upgrade 8762 graphic anomolies-- downgrade possible??"
date: 2006-10-19
forum: Multimedia &amp; Video
---

### Post by adverb on 2006-10-19
on my computer i have the nVidia 6600GT, i upgraded to the 8762 driver and everything was peachy.

on my son's computer (GeForce MX440) i just yesterday put the 8762 driver on.

now his Need for Speed Underground (1 and 2) have terrible graphic faults.

is there a way i can undo the driver upgrade?  or go back thru the recently updated packages, and downgrade them to what they were before?

i was trying to be a good dad and get his computer all updated and everything, but i broke his favorite game.  i feel terrible about this.

im pretty sure it had the 8756 driver on there.. and it would run ok (at the lowest graphic detail) but now, its simply unplayable...

any ideas?

---

### Post by tseliot on 2006-10-20
1) Which version of Ubuntu do you use?
2) How did you install the driver?
3) Why don't you try driver 8776?

---

### Post by adverb on 2006-10-20
> **tseliot said:**
> 1) Which version of Ubuntu do you use?
2) How did you install the driver?
3) Why don't you try driver 8776?

1. Ubuntu Dapper 6.06 with Gnome and automatic updates

2. Originally, I had used Easyubuntu to install the nvidia driver, then did an apt-get install nvidia-glx to get the 8756 driver, then updated via 'automatic updates', I had modified the xorg.conf from 'nv' to 'nvidia' (and subsequently removed load=dri) 

3. I guess I could, I didn't really know it was out.  Is that available via *.deb package, or should I run the binary from the nVidia site?

and thank you very much for your response.

---

### Post by tseliot on 2006-10-20
> **adverb said:**
> 1. Ubuntu Dapper 6.06 with Gnome and automatic updates

2. Originally, I had used Easyubuntu to install the nvidia driver, then did an apt-get install nvidia-glx to get the 8756 driver, then updated via 'automatic updates', I had modified the xorg.conf from 'nv' to 'nvidia' (and subsequently removed load=dri) 

3. I guess I could, I didn't really know it was out.  Is that available via *.deb package, or should I run the binary from the nVidia site?

and thank you very much for your response.
I'll make it available tonight on my testing (non-legacy) repositories:
[http://ubuntuforums.org/showthread.php?t=255929](http://ubuntuforums.org/showthread.php?t=255929)

---

### Post by adverb on 2006-10-20
I added your repo, downloaded, updated, rebooted.. and after some (very minor) tweaking in the video settings in the game everything is working marvelously.

Thank you very much for your attention.

you rock.

---

