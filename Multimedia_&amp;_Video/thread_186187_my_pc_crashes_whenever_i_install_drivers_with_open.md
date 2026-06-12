---
title: "my pc crashes whenever i install drivers with opengl support"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by mayonesiac on 2006-06-01
Hello,

I'm running Ubuntu Dapper Drake LTS 6.06 and am what you would call a linux newbie. I'm running it on my second PC, and when i installed the system i had a geforce 2 mx4400 but then remembered i had a spare fx5500 so i put that in, reconfigured the xorg thingie, and then as soon as gnome started it froze. i reconfigured the xorg thingie again, this time setting the driver to nv and it's working fine, except now i don't have opengl. i tried numerous ways of installing nvidia drivers but always the same problem occurs. it's driving me mad please can someone help me? ](*,)

---

### Post by david_e on 2006-06-27
deleted

---

### Post by david_e on 2006-06-28
Yesterday I said something wrong so I cleared that post. 

Now I have succesfully removed the nvidia driver and I have a basical OpenGl support from MESA:

First I:

```
sudo apt-get remove --purge nvidia-glx
```

then I have taken the xorg.conf file from the LIVE CD as I have messed it and wasn't able to have mesa opengl....

---

### Post by tseliot on 2006-06-30
Try my guide or my script:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

