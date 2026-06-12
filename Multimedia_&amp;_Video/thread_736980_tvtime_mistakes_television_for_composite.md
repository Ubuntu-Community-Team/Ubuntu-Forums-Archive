---
title: "tvtime mistakes television for composite"
date: 2008-03-27
forum: Multimedia &amp; Video
---

### Post by cbo_x on 2008-03-27
Hi

I installed TV time today, and in lspci my card is listed as
Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)

However when I ran the program and tried to scan for channels it didn't work. My Card has two inputs, one for antenna and the other for composite/SVideo. I accidentally turned on my xbox (composite) and the image came up on tvtime, even though it was on 'television.' If anybody knows how to fix this it would be greatly appreciated. Also there was no sound from plugging in the xbox.

---

### Post by xzero1 on 2008-03-28
In your .tvtime folder in your home diectory edit your tvtime.xml file. The video source will be the line <option name="V4LInput" value="2"/>. In my case the value "2" indicates use svideo as input. Check the tvtime documentation. I think the tuner will source would have a value of '0".

---

### Post by cbo_x on 2008-03-29
Hi thanks for your reply, but the .tvtime folder is empty. Would it work if I just made an xml file with that line?

---

### Post by xzero1 on 2008-03-30
It should be auto-created at some point. Try this: Start tvtime, right click on the tvtime window then select "input configuration" then click "change video source" for your desired source. When tvtime exits, the settings should be saved in the tvtime.xml file. If you want sound from the xbox connect the xbox audio out cables to the soundcard's aux input if available.

---

