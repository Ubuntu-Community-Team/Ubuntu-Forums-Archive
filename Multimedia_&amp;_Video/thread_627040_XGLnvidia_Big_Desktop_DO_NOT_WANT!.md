---
title: "XGL/nvidia Big Desktop: DO NOT WANT!"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by hotani on 2007-11-29
Because of a [bug in the nvidia driver](http://ubuntuforums.org/showthread.php?t=579761), I am forced to use XGL. Which means I don't have access to nvidia-settings as it throws up a nasty error when I try to open it. 

This is ok, as running XGL fixes the hangs I and many others were having while using the default nvidia setup.

However. XGL seems to always want to run in "Big Desktop" mode. I hate this. It is awful and making me want to claw my eyes out. Dialog boxes pop up right "in the crack" and I have to move them to read. The panel spans 2560px and I really just want it on one of the screens. I cannot maximize windows because they cover both screens. 

Here's where it really gets me: sometimes, maybe once every two weeks, things start to hang up like before (the pre-XGL days, those were the dark times... the times of the black flashes!), and I do a ctrl+alt+backspace. When I log back in, IT IS WORKING CORRECTLY! But I can't figure out how to keep this! Once I log out and back in again I'm back to Big Stupid Desktop.

Compiz/Metacity makes no difference.

PLEASE tell me there is a setting somewhere to make XGL use dual screens in a sane manner. I checked the xorg.conf file during big desktop mode and while it was working correctly: there was NO DIFFERENCE. Nor was there a difference in the '/etc/X11/Xsession.d/98xserver-xgl_start-server' file. OR in the running process. W.T.F.??

---

