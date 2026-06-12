---
title: "How to revert back to old graphics card from nvidia card"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by enlightening on 2007-07-13
After I installed my nvidia 6200 OC in Ubuntu feisty I began to have problems playing video, now I am not 100% sure this is what has been causing my video problems but I think I want to go back to my integrated video card, just to make sure my nvidia card is not the problem, but how would I go about doing this?

To install my nvidia card I used these instructions:  [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)   
                                                                                   [http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)
                                                               

Thanks

---

### Post by benjaminwr on 2007-07-13
Hi,

I think you coul try disconnencting the card, and once you boot up, from the command line (I imagine X won't be working) type the following:

```
sudo dpkg-reconfigure -phigh xserver-xorg

```

that should take you through the process of autodetecting your intel card and reconfiguring the X system. once that is done you can use X normally. remove anything you installed for the nvidia driver.

hope it helps.

---

