---
title: "How to check the webcam?"
date: 2023-10-26
forum: Multimedia Software
---

### Post by laxmidhar on 2023-10-26
Hi,

I am new to Linux. I did the minimal installation of Ubuntu 22.04 LTS. So there is no camera app.
Can someone please guide me how can i check my webcam or is there any way to install the camera app.
Please guide me.

Thanking you in advance.

---

### Post by Holger_Gehrke on 2023-10-26
To check if the drivers are loaded you can use 'lsmod' in a terminal and check whether 'uvcvideo' and its dependencies are loaded ('lsmod|grep uvc'). If the drivers are ok, then 'ls /dev/video? /dev/v4l/by-id' should show you device files for the camera.

There's multiple camera apps, the best-known ones are 'cheese' and 'guvcview'. 'cheese' is better integrated with Gnome, but 'guvcview' seems to work better in some problematic cases. Either (or both) can be installed using either the command line ('sudo apt install ' with the package name) or from the Software application.

Holger

---

### Post by laxmidhar on 2023-10-26
Thanks for the response.
By executing the the command 'lsmod' i checked 'uvcvideo' this is available and executed 'ls /dev/video? /dev/v4l/by-id' this command also and saw the device files for the camera.
Installed the 'cheese' app from Ubuntu software.

Thanks for the guidance.

---

