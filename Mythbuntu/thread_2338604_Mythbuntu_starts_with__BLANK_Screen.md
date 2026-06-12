---
title: "Mythbuntu starts with  BLANK Screen"
date: 2016-09-29
forum: Mythbuntu
---

### Post by gga96 on 2016-09-29
My system is a clean install of iso 0.28/16.04 achieved several days ago.

Startup today seemed [FONT=arial]normal [/FONT]but it finished at a blank screen.

On searching I found a ref to [http://lists.mythtv.org/pipermail/mythtv-users/2016-May/387196.html](http://lists.mythtv.org/pipermail/mythtv-users/2016-May/387196.html) which lead to [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105/comments/22](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105/comments/22) whch says:
>                         This  also affects me on Mythbuntu 14.04 x86 64bit with the open radeon  driver and ATI RS880 [Radeon HD 4250] graphics controller.
The workaround for me was to disable xfsettingsd in the GUI Settings under "Session and Startup":
1) In the "Application Autostart" tab I unticked xfsettingsd.
2) In the "Session" tab I selected xfsettingsd and clicked "Quit Program".

              


I used Ctl-Alt-F1 to get a logon prompt and terminal. I signed on and the simple ls command echoed my home directory, so I do have some access.

I cannot figure out how to achieve the above quoted workaround from the terminal access I have.

Any thoughts?

Explicit instructions would be appreciated.

Thanks
Glen

---

