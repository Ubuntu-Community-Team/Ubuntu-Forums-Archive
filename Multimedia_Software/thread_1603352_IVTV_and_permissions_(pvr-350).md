---
title: "IVTV and permissions (pvr-350)"
date: 2010-10-22
forum: Multimedia Software
---

### Post by pgcudahy on 2010-10-22
Hey all, I have hauppauge pvr-350 which has an mpeg2 decoder with an RGB and s-video out to let me send video to my tv. I'm using the ivtv drivers which work well. To test the card I ran ```
cat test.mpeg > /dev/video16
-bash: /dev/video16: Permission denied
```
So then I did ```

ls -l /dev/video16
crw-rw---- 1 root video 81, 5 2010-10-22 12:21 /dev/video16
sudo chmod a+rw /dev/video16
[sudo] password for patrick: 
cat test.mpeg > /dev/video16

```
And all is well. However the permissions get reset everytime I reboot. Is there any way to pass an argument to the ivtv driver to change the default permissions?

---

### Post by pgcudahy on 2010-10-22
Solved my own problem.
The output was saying
crw-rw---- 1 root video 81, 5 2010-10-22 12:21 /dev/video16
Which meant that group "video" had access. A quick ```
sudo adduser patrick video
``` and I was in business

---

