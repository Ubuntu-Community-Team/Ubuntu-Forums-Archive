---
title: "1440x900 resolution with ATI card"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by jonberling on 2007-05-26
Hello everyone, I'm trying to get 1440x900 resolution with my ATI X700 card. 

I was running 6.10 and the resolution worked fine, but I just did a clean install of 7.04 and now I cant get 1440x900. I followed the guide on [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI).  

fglrxinfo gives me:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 PRO
OpenGL version string: 2.0.6334 (8.34.8)

and fgl_glxgears seems to be working properly.

I edited /etc/X11/xorg.conf and added "1440x900" to the correct spots, but that resolution is not an option when I use "System | Preferences | Screen Resolution".

Does anyone have any pointers? My screen native resolution is 1440x900, and I don't like my screen to be stretched out.

Thanks in advance,
Jonathan - wishing I had a NVidia right about now...

---

### Post by Lemony Fresh on 2007-05-27
I am having the same problem.  Mine will not display 1280x1024.  I worked after the most recent update but I just shutdown due to a lockup and now I am back to limited display options.  It was wirking so well too.  Good luck Bro!

---

### Post by jonberling on 2007-05-27
Thanks for the reply. I think I'm just going to roll back to 6.10.

- Jonathan, who's still wishing he had a NVidia....

---

