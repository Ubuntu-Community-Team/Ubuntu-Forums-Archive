---
title: "Webcam black in skype, but works in cheese"
date: 2013-11-02
forum: Multimedia Software
---

### Post by Thee on 2013-11-02
I tried all the other threads with the LD_PRELOAD=.... and none of them work.
I'm using Ubuntu 13.10, in past versions it worked, but now what ever preload command I try it just returns:

```
LD_PRELOAD cannot be preloaded: ignored.
```

Anyone got any idea what I'm doing wrong?

Thanks

---

### Post by warp99 on 2013-11-02
Are you using the Skype version from the Ubuntu partner sources?

---

### Post by Thee on 2013-11-02
I'm using the one I've downloaded from Skype website.

---

### Post by warp99 on 2013-11-02
Remove your version and install the version in the Ubuntu repositories since it includes some bug fixes. Here's how you enable the partner repositories:

[http://askubuntu.com/questions/14629/how-do-i-enable-the-partner-repository](http://askubuntu.com/questions/14629/how-do-i-enable-the-partner-repository)

Of course change "maverick" to "saucy" for 13.10.

---

### Post by Thee on 2013-11-03
I did that now, but the problem remains. Any other suggestions?

Thanks

---

### Post by warp99 on 2013-11-03
Are there any error message when you start Skype from the terminal? When you go to the Options > Video Devices menu does the camera work? There should be a preview window when you select the correct device.

---

### Post by Thee on 2013-11-04
There are no error messages. The camera is detected and selected in the video options but the preview shows only black.

---

### Post by shantiq on 2013-11-05
well Thee i do not know the ins and outs here    but i know a practical "trick"    which has worked most times for me
1. load skype   go to settings  check video   ok black has not kicked in
2. load cheese it is ok    turn it off now
3. back to skype try again   ok now video shows up

if that does not do it   reboot then do 1 to 3 again  ....     i also found after reboot skype video much more likely to kick in straight off

Clearly cheese "knows"   how to start it better than skype    and can help skype "get it right"   like a priming pump

See no knowledge of what it is but pragmatic help of sorts  ...    please  tell me how you get on

---

### Post by Thee on 2013-11-05
Thanks for the tip, but its the same. Cheese has video Skype not, no matter what.

---

### Post by shantiq on 2013-11-05
bummer ::]]   skype and ubuntu never been a smooth dance for me really  ...   not sure it is for any Linux user  ...   hopefullly more help for you on the way    ....

---

### Post by skimo12 on 2013-11-19
Hi @Thee, 
have a look at [http://phoxis.org/2012/02/24/fix-dark-video-in-skype-for-linux/](http://phoxis.org/2012/02/24/fix-dark-video-in-skype-for-linux/)
This was the solution that I used with ubuntu 13.04

---

### Post by wertsmhvonline on 2014-02-25
My system: Ubuntu 12.04 LTS, 64-bit. Logitech C310 HD webcam. Skype 4.2.0.13, downloaded as ".deb" from Skype web-site, and installed using Software Center.

I had a similar problem, the webcam not working in Skype, but functioning normally in Cheese, Camorama.
In Skype, the webcam was not even recognized (the drop-down list was empty).
After having unsuccessfully tried re-installing Skype, and all various  ways of starting Skype with extra options (as suggested in many  messages), the solution that worked for me was actually simple:

- In the home folder, remove the hidden '.Skype' directory. This can be  achieved in Nautilus: open the home folder, press Ctrl+H to show all  hidden directories, and rename the '.Skype' directory to something like  "dotSkype-old" (or delete it altogether)

All Skype settings will be lost, and Skype will ask for your Skype name and pass-word on next start-up.

In my case this procedure led to Skype recognizing my new webcam, and now the webcam works in Skype, in Cheese, in Camorama.

P.S.  My problem was probably related to the fact that I changed  webcams. The previous, an old Philips SPC710NC, broke down and I  replaced it with the Logitech. The .Skype folder perhaps also contains  some specific configuration data on the webcams, which prevented the new  webcam from being recognized.

---

