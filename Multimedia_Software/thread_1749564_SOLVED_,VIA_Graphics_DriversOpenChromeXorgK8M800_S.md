---
title: "SOLVED ,VIA Graphics Drivers/OpenChrome/Xorg/K8M800 Solution"
date: 2011-05-04
forum: Multimedia Software
---

### Post by shrecks_ on 2011-05-04
Hi Guys,
I have been comprehensively searching this forum for  a solution to the 3D acceleration problem with VIA drivers.I have a K8M800 graphics card (integrated) with my A8V-MX mobo for AMD 3000+.

I am glad to inform you that this problem is SOLVED ! If anyone has a similar problem with streaming/playing high res videos ,esp with flickering ,and low graphics performance, i reccommend u try this out. 

1.Check if openchrome is installed in your system by using synaptic packet manager
2.Check the xorg.conf file
          a) Most Ubuntus set  your graphics driver to vesa.Change this to openchrome
          b)Load teh dri module.DRI is for direct hardware acceleration 
          c) configure the frequency of your monitor ( if it goes blank,while loading this xorg.conf - this happens after you log out and log in to your account) 

It looks like this :

sreek@ubuntu:~$ cat /etc/X11/xorg.conf

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "openchrome"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    VendorName       "Monitor Vendor"
    ModelName        "Monitor Model"
    HorizSync        30.0 - 53.0
    VertRefresh      50.0 - 60.0

EndSection

Section "Module"
    Load    "dri"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```3. Restart/Log out and log in . If there is any problem while loading,check if you have made the right changes in xorg.conf file.Just in case you think your changes are not right , always take a backup of the xorg.conf file, and restore it in command mode , during start up ( by choosing safe mode/somthing like that )

4. It  should work fine now 

PS : If dri doesnt load, there are some MESA drivers available in the synaptic packet manger.Try using them too.

HOW TO CHECK --> In VLC , if the videos are still flickering after this , change the video output in Tools->Preferences->Video->Output and experiment. It should do alright.


Many thanks to Ubuntu forums for all valuable info.

Warning : The enabling of DRI has been highly discouraged by UBUNTU , due to known issues of system crashes etc with VIA drivers.So, please do this if you are only willing to forego such problems in return for performance.

---

### Post by musshan on 2011-05-19
Hi shreck,

I am a new user of ubuntu (linux). i am using ubuntu 11.04 (64 bit) and having the same problem as yours. my mother board is A8V-MX and processor is Athlon 3000+ 64. i tried your command in terminal but unable to find the xorg.conf file. 

detailed step by step guidance is highly appreciated. thank you

regards
musshan

---

### Post by sshaitan on 2012-04-24
**cat /etc/X11/xorg.conf - file not found :popcorn:**

---

### Post by shrecks_ on 2012-05-17
@sshaitan . in your case , you would need to create and xorg file in the location and fill in the details i presume.  And it could be tricky since the system could choose to black out on the next boot .But u can resolve this by logging into terminal mode (ctrl + alt + f1) , and then go to the location and delete the file , or move it to another location . Hope that helps. 

From my experience , i can tell that there is no real guarantee to whether one method always works on different systems . So its always experimenting :-/

---

