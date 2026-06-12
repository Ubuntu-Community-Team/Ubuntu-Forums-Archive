---
title: "Changing to nVidia card"
date: 2011-03-25
forum: Mythbuntu
---

### Post by katumba1 on 2011-03-25
Hello, I have a working Mythbuntu (latest stable ver) up and working w/ the onboard ATI video through VGA to my TV. Not the best resolution or video quality. So, I'm going to get a nice quiet nVidia card and use that.

Question is, can I install it and will it work ok or do I (should I) just do a complete reinstall and let it install all the nVidia stuff that way?

It's only been up for a couple of weeks, so I do have some recordings and settings that would be nice not to lose. Yes, I can just copy the recorded stuff to another pc before format.

Thanks
Kat

---

### Post by emunson on 2011-03-25
I would copy the stuff off you want to save, then try and install the card without re-installing the machine.  You _should_ be able to but it may take some messing with commandline apt tools to install the nvidia driver.  I just changed from an HD 5450 to a G 210 and IIRC the GUI worked, I just had to enable the proprietary nVidia driver once the GUI came up (it used nouveau out of the box).

---

