---
title: "3D acceleration problem with VIA drivers"
date: 2011-05-19
forum: Multimedia Software
---

### Post by musshan on 2011-05-19
Hello,

I have Asus A8V-MX motherboard with Athlon 64 3000+ processor.
I have 3D accelaration problem with display. whenever i play a video or audio the OS crashes and while browsing internet too....the scrolling is not smooth and gets stuck.

I found another user's post with similar problem and he having solved it. But when i try the solution I am not able to implement his solution (or I dont know how to I am beginner to linux) .

[COLOR="black"]_Below is his post._[/COLOR]
"[B]Hi Guys,
I have been comprehensively searching this forum for a solution to the 3D acceleration problem with VIA drivers.I have a K8M800 graphics card (integrated) with my A8V-MX mobo for AMD 3000+.

I am glad to inform you that this problem is SOLVED ! If anyone has a similar problem with streaming/playing high res videos ,esp with flickering ,and low graphics performance, i reccommend u try this out. 

1.Check if openchrome is installed in your system by using synaptic packet manager
2.Check the xorg.conf file
a) Most Ubuntus set your graphics driver to vesa.Change this to openchrome
b)Load teh dri module.DRI is for direct hardware acceleration 
c) configure the frequency of your monitor ( if it goes blank,while loading this xorg.conf - this happens after you log out and log in to your account) 

It looks like this :

sreek@ubuntu:~$ cat /etc/X11/xorg.conf

Code:
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
3. Restart/Log out and log in . If there is any problem while loading,check if you have made the right changes in xorg.conf file.Just in case you think your changes are not right , always take a backup of the xorg.conf file, and restore it in command mode , during start up ( by choosing safe mode/somthing like that )

4. It should work fine now 

PS : If dri doesnt load, there are some MESA drivers available in the synaptic packet manger.Try using them too.

HOW TO CHECK --> In VLC , if the videos are still flickering after this , change the video output in Tools->Preferences->Video->Output and experiment. It should do alright.


Many thanks to Ubuntu forums for all valuable info.

Warning : The enabling of DRI has been highly discouraged by UBUNTU , due to known issues of system crashes etc with VIA drivers.So, please do this if you are only willing to forego such problems in return for performance.
__________________[/B]"
-------------------------------------------------------------------------------------------------------------------------------


I am running Ubuntu 11.04. I am not even able to execute the fist line in the code (ie cat /etc/X11/xorg.conf) because terminal says an error.

Experienced Ubuntu users please help. your help greatly appreciated. Thanking you.

---

### Post by musshan on 2011-05-20
I was and do hope that some of the experienced users here could help me.:confused:

---

### Post by coffeecat on 2011-05-20
> **musshan said:**
> I was and do hope that some of the experienced users here could help me.:confused:

I'm not sure I can help you much because I haven't used VIA graphics for a long time. That's probably why you haven't had any replies yet - not many people use VIA graphics. But I do have a few comments for you.

The reason that 'cat /etc/X11/xorg.conf' gives an error is because there is no /etc/X11/xorg.conf in a default installation of Ubuntu - there hasn't been for at least a couple of years. In most cases the xserver is able to autoconfigure all the hardware that you previously needed to configure in the xorg.conf file. However, if you create an xorg.conf file, those settings will over-ride any autoconfiguration.

As far as the post you quote is concerned, it would be better if you posted a link to the actual thread so that we can see it in context. I have a couple of criticisms of that post, so it would be useful to see it in context. My criticisms are:

1 - Telling you to 'cat /etc/X11/xorg.conf' won't work, as you have found, if you don't have a xorg.conf. The poster should have anticipated this and suggested creating an xorg.conf.

2 - More seriously, including this in a posted xorg,conf with no caveat is bad:

```
HorizSync        30.0 - 53.0
VertRefresh      50.0 - 60.0
```The HorizSync and VertRefresh values should be adjusted for the particular monitor in use. Those values are probably valid for the poster but could possibly damage another monitor.

So - you may achieve what you want by creating an xorg.conf file, but don't copy all of what was posted for the reasons I've just explained. Post a link to that thread and we can take it from there.

Last comment: according to a quick google search, your motherboard has an AGP slot. Does your budget stretch to buying an AGP graphics card? Even a modest ATI or nvidia chipset is going to give you better performance than the VIA and will be much easier to set up. And by using a dedicated GPU you'll take some of the work off your CPU which should lead to somewhat better overall performance anyway.

**EDIT**: I forgot something. Another reason for posting a link to that thread is that it could have been for an earlier release of Ubuntu. Ubuntu 11.04 uses a later version of the xserver than earlier versions and there have been changes in video drivers as well. What works for an earlier version of Ubuntu may not work for Natty.

---

### Post by musshan on 2011-05-26
Dear Coffee Cat,

                       Thank you so much for taking time to help me out. I actually put a PCI nVidia graphics card and everything works automatically and it is superb. Ubuntu is wonderful and so far I am very much enjoying switching from Windows XP. 

I apologize for not being able to reply earlier but my computer had a  few hardware issues that sent around in roundabouts before i could solve  them and have a trouble free computing. Turns out it was a faulty SATA cable.

Thanking you

---

### Post by coffeecat on 2011-05-26
That's good news. Good luck with using Ubuntu. :)

---

