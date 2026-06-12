---
title: "PVR150 select input feisty mythtv"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by ptipton on 2007-06-07
Have set up mythtv in feisty but need to change the video input to s-video on the pvr150 tv card. On edgy I did this with ivtvctl -p command but this command doesnt seem to be supported in ivtvctl in feisty. The IVTV documentation seems to suggest that v412-ctl should now be used instead but this doesnt exist on my system and cannot find a package to install it. Thanks.

---

### Post by fenian on 2007-06-07
Install the ivtv-utils package from synaptic and you will be able to use ivtvctl commands to configure ivtv.

---

### Post by ptipton on 2007-06-07
I have the ivtv-utils package installed but if I try ivtvctl  -p 1 option to change the input I get an invalid option message and a list of possible options non of which seem to relate to the video input.  Could you tell me the commands required to list the video input options and then to select the required one? Thanks for your help.

---

### Post by ptipton on 2007-06-07
The s-video input has started working. No idea why but alls well that end well.

---

