---
title: "USB DAC won't play with browsers, though it plays with Amarok"
date: 2013-11-13
forum: Multimedia Software
---

### Post by c.hennig on 2013-11-13
Hi there, I want to use an Epiphany E-DAC with an Asus laptop running Ubuntu 12.04. 
Switching outputs in System Settings>Sound worked straight away, or so I thought. Sound from software such as Amarok or Softsqueeze goes through the DAC to my stereo, which is fine.
However, for some reasons, this doesn't work with browsers (I tried Firefox and Chromium). As long as the Sound is set to the DAC, there is trouble. No sound, and for example youtube videos will stop after 7 seconds or so.
How can I make the browsers sending their sound to the DAC properly, too?

---

### Post by c.hennig on 2013-11-14
Update: I played around with this a bit more and the problem actually seems to be that all software including browsers can properly use the DAC until I run Softsqueeze. Softsqueeze then uses the DAC (thorugh Java sound), still fine, but afterwards the usage of the DAC is messed up for other software. I can disconnect the DAC and connect it again, and then other software will work with the DAC but Softsqueeze won't.
As much as I'd like this to be resolved in the Ubuntu forum, this may rather be a problem with Softsqueeze than with Ubuntu. Still, if you have any ideas, I'd be grateful.

---

### Post by jamesisin on 2013-11-15
Perhaps Java is trying to own the device.  I would look through your running processes to see if you can kill Java and thus gain audio for other applications.

---

