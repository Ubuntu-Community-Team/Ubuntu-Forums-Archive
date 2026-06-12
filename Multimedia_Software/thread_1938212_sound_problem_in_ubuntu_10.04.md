---
title: "sound problem in ubuntu 10.04"
date: 2012-03-09
forum: Multimedia Software
---

### Post by kpdutta on 2012-03-09
Hi all,
      I am using ubuntu 10.04 in my Dell Vostro 1014 laptop. whenever I plugged 3.5 mm jack headphone to the audio port sound comes from both headphone and laptop speaker simultaneously.  Can any one help me...?

---

### Post by Jon Monreal on 2012-03-09
Hello,

Can you type into a terminal: sudo gedit /etc/modprobe.d/alsa-base.conf
And add (copy+paste) this line at the end: options snd-hda-intel model=dell-vostro position_fix=0 enable=yes

If that doesn't work, there are other things we can try.

---

### Post by kpdutta on 2012-03-09
thanks for reply..But this does not work..Problem remaining same..If there other option, please let me know.

---

### Post by Jon Monreal on 2012-03-09
Sorry, I forgot to mention you should restart for it to take effect. If you have or that still doesn't work, there are some other ideas I have.

---

### Post by kpdutta on 2012-03-09
yes, I restarted the machine after doing that, but still the problem is. If there is other way to fix this problem please let me know...

---

