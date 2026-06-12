---
title: "Nvidia Geforce FX 5700LE drivers"
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by wildteen88 on 2006-08-04
Where do I go to get the nvidia geforce FX drivers? I read the manual about installing nvidia-glx from the restricted resporitory. Where is this? Also I did a quick search on google and found [this](http://packages.ubuntulinux.org/dapper/x11/nvidia-glx) Is this what I need? Where do I download the driver from that page, also how do you install the driver too. I am a lixun n00b however I am learning fast.

NOTE: I cannot access the net from my linux box so I have to download the driver first to Windows and then burn it to CD-RW and copy onto linux.

Thank you for any help that is provided.

---

### Post by tseliot on 2006-08-04
Read my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by wildteen88 on 2006-08-04
Hi thank you. I went thorugh method1-offline in the guide provided. But when I restart X i get a blue screen and text in a grey box saing the X isnt configured correctly, at the end of the long message it says no screens found

After clicking the OK buttons it returns to command promt, no gui is present. So I reverted my xorg.conf file back. Restart and its back to nromal. 

Do you have any idea why this si happening?

---

### Post by tseliot on 2006-08-04
> **wildteen88 said:**
> Hi thank you. I went thorugh method1-offline in the guide provided. But when I restart X i get a blue screen and text in a grey box saing the X isnt configured correctly, at the end of the long message it says no screens found

After clicking the OK buttons it returns to command promt, no gui is present. So I reverted my xorg.conf file back. Restart and its back to nromal. 

Do you have any idea why this si happening?

Try point 13 of the Problems Section then try the driver again:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

### Post by wildteen88 on 2006-08-04
That didnt work either. Same result

---

### Post by wildteen88 on 2006-08-05
Does anyone have any more suggestions? Bump

---

### Post by tseliot on 2006-08-05
Try point 4 of the problems section

---

### Post by wildteen88 on 2006-08-07
Okay I think I know why its not working, becuase when I installed the driver i didnt go through steps 1 and 2 of method1-offline installation. Are these steps important?

Today I went through them, but when I go to step 2 it tries to acccess the internet to download some gpg files. How can I run step 2 without being connected to the net?

---

### Post by tseliot on 2006-08-07
> **wildteen88 said:**
> Okay I think I know why its not working, becuase when I installed the driver i didnt go through steps 1 and 2 of method1-offline installation. Are these steps important?

Yes, they are

> **wildteen88 said:**
> Today I went through them, but when I go to step 2 it tries to acccess the internet to download some gpg files. How can I run step 2 without being connected to the net?

Step 2 says:
> 2) Download this package **from another computer (in which you have an internet connection)**:

---

### Post by wildteen88 on 2006-08-07
Sorry I ment step 1 and the 2nd step within step 1 where you run
> sudo apt-get update
I cannot run that as it accesses the web to download some gpg files.

---

### Post by tseliot on 2006-08-07
> **wildteen88 said:**
> Sorry I ment step 1 and the 2nd step within step 1 where you run

I cannot run that as it accesses the web to download some gpg files.

try skipping that step

---

