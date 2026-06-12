---
title: "iPod Touch Working in GtkPod but not Amarok"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by bthoward on 2007-11-29
Having strange luck here...

I've followed the directions here closely:
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

I'm running the 1.1.2 firmware on the phone jailbroken and all.

I'm able to SSH into the phone with no password.  I'm able to run iphone-mount and iphone-umount and all works as it should it mounts the device over WiFi like a dream.

GtkPod can write files to it without problem album art and everything works perfectly.  But Amarok says Media Device: No mounted ipod found whenever I try to connect.  I have added the device into the settings and I have added iphone-mount and iphone-umount to the preconnect and postdisconnect sections respectively.  Yet no matter what I do I seem to get this error.  One thing that concerns me is that when I click connect and its not already mounted it doesn't end up getting mounted...  

If I mount it by hand and try to get it to connect I get the same error even if I remove the pre and post connect scripts.  I've not been able to find where Amarok writes its logs to try and see what is happening either so even being informed as to where that lives may be enough help to get me moving forward.  

Thanks all

~Brett

---

