---
title: "MS VX-7000 Webcam work with Cheese, but not Skype?"
date: 2009-01-19
forum: Multimedia Software
---

### Post by dstubb on 2009-01-19
Bought my mother a MS Lifecam VX-7000 and installed 8.10 on her EEEPC.  The camera works fine in Cheese (once I resize the image) but not in Skype.  The receiving computer believes that Skype is sending video but it's just black.

I have scoured the internet trying to find a solution - but no joy.

Any ideas?

---

### Post by stylishkoala on 2009-12-23
I'm having same problem with Kubuntu 9.10. Camera works on luvcview, but not with another program...

If anyone have any glue about how to solve this problem spread around the community.

Thanks in advance!!!

---

### Post by DaveBG on 2010-05-08
Mine is also not working in the options at least during the test. The led on the cam flashes but no picture.

I used the tip from here:
[http://ubuntuforums.org/showthread.php?t=866695&highlight=lifecam+7000](http://ubuntuforums.org/showthread.php?t=866695&highlight=lifecam+7000)

> Go to main menu, System, Preferences, Menus: Applications, Internet, Items: Skype, Properties, and replace the Command with

bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

But still no go?

Any advice?

---

### Post by blanchg on 2010-05-11
I just had the same problem and fixed it by using the following to start Skype instead. 

```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype'
```

---

