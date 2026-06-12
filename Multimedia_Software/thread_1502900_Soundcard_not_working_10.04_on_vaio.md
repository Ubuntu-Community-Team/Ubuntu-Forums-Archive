---
title: "Soundcard not working 10.04 on vaio"
date: 2010-06-06
forum: Multimedia Software
---

### Post by ubukid on 2010-06-06
Hi 

I have a Sony Vaio VPCEB1E0E and this is the soundcard it came with -

                                 Codec: Realtek ALC269
 Codec: Intel G45 DEVIBX
 

 **** List of PLAYBACK Hardware Devices ****  
 card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]  
   Subdevices: 1/1  
   Subdevice #0: subdevice #0  
 card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]  
   Subdevices: 1/1  
   Subdevice #0: subdevice #0
 
I have referred to this guide - [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
and don't even think my sound card is being detected, but being a novice I am not even sure how to access the system's BIOS and enable the soundcard.

Can anyone help here?

Thanks

---

### Post by frozonecom on 2010-06-06
go to applications>>accessories>>terminal

and type this :
```

lspci | grep audio
```

and post the output here.

---

### Post by ubukid on 2010-06-06
there is no output when I type this in.

---

### Post by lesnoland on 2010-06-09
upgrade to latest alsa, and it will work.

Here is how you can do that:

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

good luck.

---

