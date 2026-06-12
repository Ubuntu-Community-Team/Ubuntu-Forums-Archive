---
title: "offline VLC installation"
date: 2011-09-03
forum: Multimedia Software
---

### Post by LinuxSavedMyComputer on 2011-09-03
I have an offline Installation of 64-bit ubuntu 11.04. Because i can't get Internet on that machine i want a way to download the required packages and dependancies on a seperate ubuntu machine and install them offline on the first. I have a USB key that i can use. to transfer files

---

### Post by dave01945 on 2011-09-03
if you open synaptics package manager select the packages you want to install then you can click on **file > generate package download script** save that to your usb the take that to your other box and run the script it should download the packages onto your usb

then you need to open synaptics again (on the box where you want to install) click on **file > add downloaded packages** and it will install everything you downloaded


hope this helps

---

### Post by LinuxSavedMyComputer on 2011-09-03
> **dave01945 said:**
> if you open synaptics package manager select the packages you want to install then you can click on file > generate package download script save that to your usb the take that to your other box and **run the script it should download the packages onto your usb**

then you need to open synaptics again (on the box where you want to install) click on file > add downloaded packages and it will install everything you downloaded


hope this helps

How can you download the VLC packages on my other box if it does not have internet?

---

### Post by dave01945 on 2011-09-03
i may have misunderstood but i gathered from your post that you have a separate ubuntu machine with internet that is the one you would run the script on to download the packages then take the usb to the machine without internet and click on add downloaded packages

---

### Post by LinuxSavedMyComputer on 2011-09-03
so i make the download script with synaptic on the machine with internet and** on the same machine download it**, then use synaptic  on the machine without internet to add the downloaded packages?

---

### Post by dave01945 on 2011-09-03
you should make the script on the machine without internet using **generate package download script** this will make sure it will download everything that is needed 

then run the script from the usb on the machine with internet

then take the usb back to the machine without internet use the **add downloaded packages** in synaptic and that will install them

---

### Post by LinuxSavedMyComputer on 2011-09-03
Thanks alot!

---

