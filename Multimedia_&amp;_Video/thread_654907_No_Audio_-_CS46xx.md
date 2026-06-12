---
title: "No Audio - CS46xx"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by d0c_spratley on 2007-12-31
Hello All,

I'm an Ubuntu noob...recently installed 7.10 on an IBM Thinkpad A22m - it's looks as though it detects the card but I am unable to get any audio at all.  I know it works as I am able to get sound using a Knoppix CD, no problem.  

I read other posts on this subject however the resolutions have not been helpful so far and as the hours pass by I'm getting rather frustrated.  Any suggestions would be really helpful.  Thank you and Happy New Year!!! :)

D0c

---

### Post by d0c_spratley on 2008-01-03
bump

---

### Post by d0c_spratley on 2008-01-03
Resolved my problem.

I had checked the alsamixer before to make sure that the sound was unmuted but it still did not work.  I checked again and simply enabled everything and increased the volume.  I found that when the DAC was muted or turned down there was no audio.

To launch the alsamixer open the termial and type: alsamixer

I also updated the bios but I don't think that helped much but it mever hurts.

Anways I'm sure someonelse has already suggested this on other posts but hopefully this may become useful for somebody else.

---

### Post by Astroham on 2008-01-03
I'm new to Ubuntu and had a similar problen just yesterday.   Finally fixed it by unmuting the PCM in "Volume Control" and turning up to full.

Hope this helps.

Cheers

Nev

---

