---
title: "getting crazy with module 1394 + kino"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by smoking81 on 2008-02-06
hello everybody!
I open this post since I didn't succeed in letting the module 1394 work and Kino is still showing the message: "Warning: raw1394 kernel module not loaded or failure to read/write /dev/raw1394." Of course, my aim is to acquire video from my Sony DCR HC27 via firewire.

I began with reading this post: [http://ubuntuforums.org/showthread.php?t=454698](http://ubuntuforums.org/showthread.php?t=454698) and then followed this guide: [http://www.bxlug.be/en/articles/220](http://www.bxlug.be/en/articles/220) step by step without success. So I tried to follow what is advised here: [http://ubuntuforums.org/showthread.php?t=56468#8](http://ubuntuforums.org/showthread.php?t=56468#8) but got a lot of errors. 
Here is what I get in answer to several commands:
```

federico@federico-laptop:~$ sudo lsmod | grep 1394
video1394              19800  0
raw1394                31096  0
ohci1394               36528  1 video1394
ieee1394               96312  4 video1394,raw1394,sbp2,ohci1394

federico@federico-laptop:~$ gscanbus
couldn't get handle: Permission denied
This probably means that you don't have raw1394 support in the kernel or that
you haven't loaded the raw1394 module.

federico@federico-laptop:~$ testlibraw
couldn't get handle: Permission denied
This probably means that you don't have raw1394 support in the kernel or that
you haven't loaded the raw1394 module.

```

and of course kino still shows its warning (after 2 reboots).
can you help me please? Thanks a lot!

---

### Post by soro2005 on 2008-02-11
For the quick fix:
```
sudo chmod 666 /dev/raw1394
```
This will most likely revert at next reboot, but if you want to quickly find out whether it works in theory on your setup, you should be done with the above.

For a permanent fix, you can follow point #2 in [this post here]("http://nexthing.wordpress.com/2007/10/31/dlink-dfw-500-firewire-controller-on-ubuntu-710-kino/"). It is my understanding that you are essentially taking down some important security restrictions on your firewire port by following these steps. But if you only ever use your firewire with your video camera, it's probably okay. Also, it doesn't look to me like there's a different option...

---

### Post by linuxfan3 on 2008-04-01
since its risky to give user access to this bus device you should try to install "dvgrab" and restart your system. now it should work
that worked with me at least

---

### Post by granny6989 on 2008-04-03
Try this:

[http://ubuntuforums.org/showthread.php?t=645826](http://ubuntuforums.org/showthread.php?t=645826)

Get into terminal and type in the modprobe codes.

I had a running Kino, and Dvgrab worked from command line for me, but I wanted it all, GUI in Kino and full camera support. I have a Sony DCR-TRV30, and none of the 'fixes' would work. I did the full permissions for raw DV, all those little interior changes, but never got my camera to work inside of Kino. I read the above article, typed in the 4 lines of code, and exited. Fired up Kino and my camera and all capture buttons were alive and functional. As I stated in that post, make sure your camera is plugged in and in VCR mode before starting Kino, and it will hopefully work out for you.

Maybe start by making sure you have all the dependencies from here installed:

[http://www.kinodv.org/article/static/3](http://www.kinodv.org/article/static/3)

Then, go to command line and try running Dvgrab(assuming you have that installed). You can use Dvgrab --help to get some hints on how to run that. Make a short couple second capture just to make sure you have camera support. Are you using Firewire? I think you need to be. Anyways, if Dvgrab works and all looks good, then get in and try the modprobe codes, then fire up Kino and hopefully you'll be there.

S*

---

