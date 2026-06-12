---
title: "canon 20 seems dont like linux !"
date: 2010-09-21
forum: Multimedia Software
---

### Post by TMMXONE on 2010-09-21
Hello people.

i cant connect my canon 20d ( that works great in windows)

i tried f-spot - digikam - picassa
no way

i did many searchs but no chance with google !

i do that :

 ```

mehdi@mehdi-laptop:~$ gphoto2 --auto-detect
Modèle                        Port                                             
----------------------------------------------------------
Canon EOS 20D (normal mode)    usb:            
Canon EOS 20D (normal mode)    usb:002,007     
mehdi@mehdi-laptop:~$ gphoto2 --auto-detect
Modèle                        Port                                             
----------------------------------------------------------

```

the device seems recognized but no apps cant find it.

whats wrong ?

thanks for any help.

---

### Post by gaga666 on 2010-09-21
Try to mount it with gphotofs. It won't make it visible to camera-apps as camera, but at least you'll be able to download photos.

---

