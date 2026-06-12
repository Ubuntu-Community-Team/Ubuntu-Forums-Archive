---
title: "A good fix for Nautilus?"
date: 2009-10-09
forum: Multimedia Software
---

### Post by onespeedbiker on 2009-10-09
Recently I posted a problem I had with Nautilus cd burner, where the CD/DVD Creator window would open when I inserted a blank CD or DVD, but I could not burn a CD or DVD; Nautilus would ask for a blank DVD with enough room to burn whatever size the file I dropped into the window  was. but Nautilus continued not to recognise the blank disc. The problem cropped up when I switched my IDE DVD players, making the burner primary and the player a slave. I did a lot of goggling and founjd this has been a common problem with ubuntu. One solution was to change some settings in apps/nautilus-cd-burner. That did not solve my problem. I then checked apps/nautilus/{name}desktop/last_device; with a value of "/dev/scd1". Knowing I had switched /dev/scd0 and scd1, I changed the value to "/dev/scd0" and whatdoyaknow; it worked. Natulus and CD/DVD Creator works like a charm. Did I do good?

---

