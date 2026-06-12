---
title: "YouTube videos stop playing"
date: 2010-06-13
forum: Multimedia Software
---

### Post by gobotsoup on 2010-06-13
Hello, I did an update last week which may have caused flash to quit working properly. When I watch youtube videos that are longer than a couple minutes the video will just stop after a couple minutes in even if it is buffered all the way. I have tried clearing my browser cache, I have also tried uninstalling and reinstalling flash, but none of this helped. This is happening in both firefox and chrome. I am using Ubuntu 9.10. Any help would be great, thanks!

---

### Post by lovinglinux on 2010-06-13
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by gobotsoup on 2010-06-13
Thanks, it looks like there are two:
Shockwave Flash

    File name: /usr/lib/adobe-flashplugin/libflashplayer.so
    Shockwave Flash 10.1 r53

Shockwave Flash

    File name: /usr/lib/swfdec-mozilla/libswfdecmozilla.so
    Shockwave Flash 9.0 r999

---

### Post by lovinglinux on 2010-06-13
> **gobotsoup said:**
> Thanks, it looks like there are two:
Shockwave Flash

    File name: /usr/lib/adobe-flashplugin/libflashplayer.so
    Shockwave Flash 10.1 r53

Shockwave Flash

    File name: /usr/lib/swfdec-mozilla/libswfdecmozilla.so
    Shockwave Flash 9.0 r999

You need to remove swfdec. Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by gobotsoup on 2010-06-14
I just ran the Flash-Aid program from firefox and it actually removed both versions of flash I had. When I went to reinstall flash it installed an older version for some reason, so I updated from that one and now just have this one:
    File name: /usr/lib/adobe-flashplugin/libflashplayer.so
    Shockwave Flash 10.1 r53

Unfortunately the problem seems to persist where I can't watch a youtube video for more than a couple minutes before it just freezes on me.

---

### Post by Dilutu on 2010-06-14
Did you try the older version? I had to downgrade from the latest to get back decent video playing...

---

### Post by lovinglinux on 2010-06-14
> **Dilutu said:**
> Did you try the older version? I had to downgrade from the latest to get back decent video playing...

That is not recommended since all previous versions have a critical vulnerability.

---

### Post by lovinglinux on 2010-06-14
> **Dilutu said:**
> Unfortunately the problem seems to persist where I can't watch a youtube video for more than a couple minutes before it just freezes on me.

The video simply stops or the whole browser freezes? How is the CPU usage when it stops?

---

### Post by gobotsoup on 2010-06-14
Thanks, the video simply stops. When the video is running the browser I am using runs at anywhere from 40-50% CPU usage and the CPU is worked pretty hard at about 85-90%. Then when the video stops the CPU usage for the browser drops down to more like 15-20% and the CPU is working more normally.

---

### Post by lovinglinux on 2010-06-14
> **gobotsoup said:**
> Thanks, the video simply stops. When the video is running the browser I am using runs at anywhere from 40-50% CPU usage and the CPU is worked pretty hard at about 85-90%. Then when the video stops the CPU usage for the browser drops down to more like 15-20% and the CPU is working more normally.

Try this test:

Open a video long enough to cause the problem, pause it and make sure it buffers completely. Play a little bit, not the entire video, then pause it. Wait a minute or two and play another section. Repeat this until you reach the end of the video. Let me know if you are able to view it entirely. Don't worry, this is not the solution, is just a test to know if CPU overheating is causing the problem.

---

### Post by gobotsoup on 2010-06-15
That seems to sort of work actually. If I pause a video and wait for a little while then re-start the video I can watch it longer. However, I haven't been able to watch an entire video, I think the longest I have been able to watch was 7 minutes before it froze on me. So, it does seem to me a good possibility that the CPU is overheating, but I am not totally sure.

---

### Post by lovinglinux on 2010-06-15
> **gobotsoup said:**
> That seems to sort of work actually. If I pause a video and wait for a little while then re-start the video I can watch it longer. However, I haven't been able to watch an entire video, I think the longest I have been able to watch was 7 minutes before it froze on me. So, it does seem to me a good possibility that the CPU is overheating, but I am not totally sure.

Most likely. Flash is a very CPU intensive application and once the CPU heats, flash performance drops considerably. In your case I believe the problem goes a little further and stops the display of the content. See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by gobotsoup on 2010-06-20
Thank you for all of your help on this. I found out that it seemed the problem must have been due to my connection actually. The CPU is still being worked, but after resetting my cable modem youtube videos are playing through to the end. I also found this to be helpful: Create a "custom application launcher" in your panel and then in properties paste this in command:
 sh -c 'vlc /tmp/Flash*'

---

### Post by ankitsikka1982 on 2010-08-25
> **lovinglinux said:**
> Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.


File:  /var/lib/flashplugin-installer/npwrapper.libflashplayer.soVersion:   Shockwave Flash 10.1 r82same problem. Whenever I open a video on any website including youtube, it stops after sometime. Not only this if I play a game called Howzatt online, it does the same. 
I have another problem. My internet is very slow. I tried many solutions online. It works for few days but then again it becomes too slow. 

Ankit

---

