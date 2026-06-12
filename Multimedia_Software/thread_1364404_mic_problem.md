---
title: "mic problem"
date: 2009-12-25
forum: Multimedia Software
---

### Post by u_kapaley256 on 2009-12-25
Hi all,

I can get output from my audio but no input.
I am using kubuntu on my hp pavilion dv4-2088dx which has 2.2 Ghz AMD processor.I am using 32 bit version of the OS.
The sound device as reported my windows is 'ATI high definition audio codec' as well as 'IDT high definition audio codec'.The driver used by kubuntu is HDA ATI SB (STAC92xx Analog) (which screwed up in the kernel 2.6.31-16 so i switched back to 2.6.31-14)

I used to get very low volume from earphones and none from the earphones until i added the line in alsa-base.conf regarding the model=hp-dv5 or something similar but i still cant get the mic(both the inbuilt as well as the plugged in) to work.The plugged in mic shows 'hdmi(unknown)' in skype whereas the inbuilt shows 'default'

I dont like switching to win for skype 

Pls help
Thanks.

---

### Post by DSGamer on 2010-01-29
Has anyone gotten this to work yet? I have a new Pavilion dv4. I can get audio to work if I turn the device from Digital Audio + Analog Input to Analog Output. However, that means Skype, etc. don't work. Has anyone figured out the correct alchemy for this.

---

