---
title: "Troubleshooting Webcam"
date: 2010-10-30
forum: Multimedia Software
---

### Post by shanksy75 on 2010-10-30
Hi all,

I've had a problem with the webcam on my Acer Aspire One for some time now. I ditched the original linpus lite and have run both Linux4one light and various versions of Ubuntu Netbook Remix. The webcam stopped working when I installed Linux4one so I just assumed it was a limitation of the OS. Never really used it so just left as is.

Now I have a need to use the webcam but cannot get it working. I tried a fress install of UNR, currently have reverted to a fresh install of Linpus and neither has worked so I had ruled out the OS as the issue.
Next I purchased a replacement webcam as I've heard they can frequently fail on the hardware side. Still nothing.

Where would I go from here ? Is it worth re-flashing the BIOS ? Is there anyway of testing if the Onboard USB controller is recognised in Linux ? 

If anyone could offer any advice on what my next step should be I would be very grateful.

Thanks
Lee

---

### Post by no2498 on 2010-10-31
open a terminal type lsusb click enter
with the cam plugged in and not plugged in
note the diff
did the list change
if yes try the cam in cheese
or im not sure you can use this

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

