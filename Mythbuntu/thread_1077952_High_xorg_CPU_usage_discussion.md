---
title: "High xorg CPU usage discussion"
date: 2009-02-22
forum: Mythbuntu
---

### Post by pjbgravely on 2009-02-22
myth .23 fixes this problem for me, thanks for all your help.


I know the official solution for this is to add 

Option "UseEvents" "True" To the xorg.conf device section. 

   This did not work for me so I am hoping that this post will attract others that this fix has not helped.

   I have a Mythbuntu 8.04 64 setup with both back and front end on the same machine. It is using a Nvidia GeForce 8500 GT card running component video out to a 4x3 TV running at 1024x768 resolution. I have a HD Homerun tuner.

   I discovered the high xorg CPU usage when my remote became unresponsive. It only happened with certain stations ( both HD and SD) and with certain recordings. Strangely if the problem is gone on a station it will be there on the recording of the station and vise versa. 

   I tried the fix but it did nothing to help. I have a Ubuntu 8.04 64 desktop with 2 video cards so I decided to install the mythfrontend on it to help test. The desktop has a Nvidia GeForce 8500 GT card running 2 VGA monitors at 1080x1024 and a Nvidia GeForce 9500 GT card with 1 monitor on DVI running at 1680x1050. Both boxs are running the 173.14.12 Nvidia driver installed with Envy.

   The fix worked for both monitors running the 8500, but not for the 9500. Now I can't just change the video card in the Mythbuntu box. It either has something to do with using the component video out or it is a software problem with something in the backend.

   I next tried working with the Sync to Vblank setting in nvidia-settings. It stopped the problem with both the 9500 and the 8500 but in both cases it caused tearing in SD and HD broadcasts of SD programs and some HD programs. I also just found a problem on the desktop with the 9500. It had high xorg CPU until I turned Sync to Vblank on and off again, when it was set to off when starting Myth frontend. 

    For some reason I cannot find a bug submission for this problem that is not titled a remote problem. I think Myth believes this bug has been fixed with the work around. 

   My next try will be to hook a TV up to my 9500 to see if it works with that, and to hook one up to the 8500 to try and replicate the bug on my desktop for that card.

   I would also appreciate anyone letting me know if weekly builds or weekly trunk updates have helped them. Since I have read a few people saying that this is also a problem with 8.10 I doubt that will help me, but I am going to upgrade my desktop soon. I just wish I had the same problem with the 8500 in both places.

---

