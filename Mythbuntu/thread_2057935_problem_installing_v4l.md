---
title: "problem installing v4l"
date: 2012-09-14
forum: Mythbuntu
---

### Post by Bong_Master_Darky on 2012-09-14
allrighty i am trying to install v4l to make my usb lme2510c satellite box work but i have a problem 

i install all the requirements like perl patchutil etc 

i got to ./build 

it go quite away through and then displays a error 

[CODE]/home/rob/v4l-dvb/media_build/v4l/dvb_frontend.c: In function 'dvb_frontend_poll':
/home/rob/v4l-dvb/media_build/v4l/dvb_frontend.c:2304:2: error: implicit declaration of function 'dev_dbg_ratelimited' [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[3]: *** [/home/rob/v4l-dvb/media_build/v4l/dvb_frontend.o] Error 1
make[2]: *** [_module_/home/rob/v4l-dvb/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/rob/v4l-dvb/media_build/v4l'
make: *** [all] Error 2
build failed at ./build line 452./CODE]

my dvb usb is a dvb-usb-LME2510c rs2000 

thanks

rob

---

