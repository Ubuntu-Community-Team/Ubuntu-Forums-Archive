---
title: "No webcam support in Ubuntu 10.04 LTS for skype users"
date: 2010-05-02
forum: Multimedia Software
---

### Post by beaxe on 2010-05-02
In skype 2.1 beta for ubuntu 10.04 LTS desktop amd64, the webcam is not getting configured at all. The test button in <options> for video shows no results or response. The same problem was faced in Karmic Koala also and now in Lucid Lynx. Kindly provide some concrete solutions to this very problem of configuring webcam in skype for ubuntu.

---

### Post by Claus7 on 2010-05-02
Hello,

since you face this from karmic this might help:
1)open terminal
2)vim .bashrc
3)insert there:
alias skype='LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

restart.

Regards!

---

### Post by pashlit on 2010-05-03
> **Claus7 said:**
> Hello,

since you face this from karmic this might help:
1)open terminal
2)vim .bashrc
3)insert there:
alias skype='LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

restart.

Regards!

That didnt work for me. Ubuntu 9.10 worked like a charm. But 10.04 has tons of bugs as I see. Kopete recognized camera and it works fine. Skype lists my camera but pressing TEST button gets no results. Any help before I downgrade to 9.04? Thanks.

---

### Post by Claus7 on 2010-05-04
Hello,

have you tried the newest beta version instead (at least I think it was new)? I had some problems with skype too, since I updated, yet in the end downloading the latest deb file from their web site, installing it, pressing the test button in camera, and finally restarting skype, things were working as normal. This on 32 bit machine though. At least you can try that since it's pretty easy.

I said new, because even though I had installed skype beta 2.1, when I downloaded the deb file and tried to install it, it did not recognised my previous installation (it did not prompt me for re-installation). So, before installing, I removed the "old" one.

Good luck,
Regards!

---

### Post by pashlit on 2010-05-04
> **Claus7 said:**
> Hello,

have you tried the newest beta version instead (at least I think it was new)? I had some problems with skype too, since I updated, yet in the end downloading the latest deb file from their web site, installing it, pressing the test button in camera, and finally restarting skype, things were working as normal. This on 32 bit machine though. At least you can try that since it's pretty easy.

I said new, because even though I had installed skype beta 2.1, when I downloaded the deb file and tried to install it, it did not recognised my previous installation (it did not prompt me for re-installation). So, before installing, I removed the "old" one.

Good luck,
Regards!

I downloaded the latest .deb from Skype web site. Then I removed it and downloaded via wget. Same thing I guess. The camera does not work. It is actually the first time my Chicony camera is not working on Skype. I ve been using Ubuntu for quite a while and have never had any problems with Skype. I switched to x64 version when 9.10 came out and it worked just unbelievably perfect. The only reason I installed 10.04 is that they finally created descent iTouch support. But I guess It wasnt really worth it. 9.10 performed way better. Hopefully they will release updates before I downgrade to the previous version.

---

### Post by GerryGG on 2010-05-04
I was in the same boat. Just upgraded to 10.04 and no video in Skype. I found this advice on another page; tried it and it worked:

Create file:

$ sudo gedit /usr/local/bin/skype

add this:
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so /usr/bin/skype

Save file.

then:

$ sudo chmod a+x /usr/local/bin/skype

---

### Post by Icarus315 on 2010-05-04
In the menu editor for my skype shortcut I have:

bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'

in the command field in the menu items properties.  This is also the exact same command I use in the startup programs menu.  Notice the 32, I don't believe it will work without it.  I am also 64-bit Ubuntu 10.04.

---

### Post by pashlit on 2010-05-04
> **GerryGG said:**
> I was in the same boat. Just upgraded to 10.04 and no video in Skype. I found this advice on another page; tried it and it worked:

Create file:

$ sudo gedit /usr/local/bin/skype

add this:
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so /usr/bin/skype

Save file.

then:

$ sudo chmod a+x /usr/local/bin/skype

No luck. Same thing. I press TEST button. I see camera turns on but no video :((

---

### Post by pashlit on 2010-05-04
> **Icarus315 said:**
> In the menu editor for my skype shortcut I have:

bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'

in the command field in the menu items properties.  This is also the exact same command I use in the startup programs menu.  Notice the 32, I don't believe it will work without it.  I am also 64-bit Ubuntu 10.04.

Tried to run Skype using above command. Same results. Its getting annoying. Everything worked before 10.04 came out. What the h..l developers changed. Just leave it alone and make it work. My other PC stopped powering off after another update. I love Ubuntu and will continue using it but some things just get on my nerves.

---

### Post by zaphod777 on 2010-05-04
Mine works fine for me but I am running Beta2 updated to now.

---

### Post by mve-lamb on 2010-05-05
> **zaphod777 said:**
> Mine works fine for me but I am running Beta2 updated to now.

Ye, but mine WebCam (Bus 001 Device 004: ID 0ac8:3420 Z-Star Microelectronics Corp.) also do not work with Skype, but work in Cheese.
I'm runing Ubuntu 10.04 LTS 32bit Desktop Edition.
It was working fine in Debian 5 (Lenny) with gspca-modules installed and Skype Beta 2.1.0.47, do not lose your time to switch back to the old version of Skype in Ubuntu 10.04 the result is  the same.
 
Can you post the output of the fallowing commands in terminal?
> mve@mven:~$ lsusb
mve@mven:~$ lsmod | grep videodev
mve@mven:~$ uname -a
Your exact Skype Beta version like mine is v. 2.1.0.81 what?
Try your camera with Cheese?(Install it from Synaptic first)
and > mve@mven:~$ sudo gstreamer-properties Open VIDEO TAB, and Default device: V4L2 , hit TEST button, and report back, also you can try to cahnege V4L2 with V4L, and see what is going on.

I think the problem might be that Skype Beta 2.1.0.81 do not support V4L2 devices according to one of the postings here[Skype developers page]("http://blogs.skype.com/garage/2010/01/skype_21_beta_2_aka_talking_sc.html"), and Ubuntu works only with [V4L2 device driver]("http://www.ideasonboard.org/uvc/#footnote-8") natively. But I may be wrong!

If someone knew a way of enable V4L v.1 in Ubuntu 10.04 that may resolve the problem if your camera work in Cheese but not in Skype.

Hope to resolve our problem soon, I do not think that you want to go back on U 9.10? 

Also for me neither of the mentioned above post did not do the trik, and also a many others that I found on the www.

mve

---

### Post by pashlit on 2010-05-05
> **mve-lamb said:**
> Ye, but mine WebCam (Bus 001 Device 004: ID 0ac8:3420 Z-Star Microelectronics Corp.) also do not work with Skype, but work in Cheese.
I'm runing Ubuntu 10.04 LTS 32bit Desktop Edition.
oblem soon, I do not think that you want to go back on U 9.10? 

Also for me neither of the mentioned above post did not do the trik, and also a many others that I found on the www.

mve

So is there a solution for that bug? As I said my camera works fine in Kopete and has always worked perfect before 10.04. I use the .deb downloaded from official Skype web site. Is there another version of Skype I could try?

---

### Post by bjennworld on 2010-05-05
Had many problems with my Logitech SPCA based webcam not working with Skype. Tried many of the 'Fixes' all of which failed to work.

Just upgraded to 10.04 64bit, installed Skype 2.1.0.81 and based on Logitech info at [http://www.quickcamteam.net/devices/logitech_uvc_device_feature_list_by_device.pdf](http://www.quickcamteam.net/devices/logitech_uvc_device_feature_list_by_device.pdf) which claims Linux support for UVC webcams I bought a cheap Logitech C120 which worked with Skype 'Out of the Box'

Hope this is of interest/helps others having Skype webcam issues.

---

### Post by GerryGG on 2010-05-05
I should point out that I am running 32 bit. So, perhaps the solution that I used successfully and posted above, is 32-bit specific.

---

### Post by pashlit on 2010-05-05
Here is the error I get trying to preload v4l. Tried to reinstall v4l packages. Didnt help.


ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

Then after pressing test button terminal shows some kind of another error. So there is definitely smth wrong (((

---

### Post by castironpants on 2010-05-05
It worked!

---

### Post by castironpants on 2010-05-05
> **GerryGG said:**
> I was in the same boat. Just upgraded to 10.04 and no video in Skype. I found this advice on another page; tried it and it worked:

Create file:

$ sudo gedit /usr/local/bin/skype

add this:
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so /usr/bin/skype

Save file.

then:

$ sudo chmod a+x /usr/local/bin/skype

No idea why (I've been using a line of code just like this) but it worked! Thank you!

---

### Post by pashlit on 2010-05-05
> **castironpants said:**
> It worked!

Are you using 32 or 64 bit system?

---

### Post by zaphod777 on 2010-05-05
> **castironpants said:**
> No idea why (I've been using a line of code just like this) but it worked! Thank you!

you should file a bug report so we can get  a fix pushed out.

---

### Post by xc3RnbFO8P on 2010-05-06
Read this:
[https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

---

### Post by pashlit on 2010-05-06
> **Ringi said:**
> Read this:
[https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

There is no use for that right now. First of all its old and does not list latest Ubuntu release. Secondly the problem is that the camera worked in previous releases just fine right out of the box. Thirdly camera works fine with other programs like Ekiga, Kopete etc. There is a conflict between Skype and current Ubuntu release we are trying to solve.

---

### Post by ementos on 2010-05-06
the best is make icon with program:
```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
It works, but for me it's too dark :/
Greet,
Józef M.

---

### Post by Im_Original on 2010-05-06
> **castironpants said:**
> No idea why (I've been using a line of code just like this) but it worked! Thank you!

Responding to castironpants, post #17: 

This worked for me too. 

Running 10.04 on a Thinkpad T40 with Logitech QuickCam Connect. 

And I don't know why it worked either. But it did! Thanks!

---

### Post by mve-lamb on 2010-05-09
> **pashlit said:**
> So is there a solution for that bug? As I said my camera works fine in Kopete and has always worked perfect before 10.04. I use the .deb downloaded from official Skype web site. Is there another version of Skype I could try?

Hi guys, I have some success with my not working webcam :guitar:

> vovo@mven:~$ uname -a
Linux mven 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
vovo@mven:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0ac8:3420 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
vovo@mven:~$ 

Now I have WORKING WEBCAM with SKYPE Beta 2.1.0.81 , as I said before on my earlier post neither of the "LD_PRELOAD.......", and "export...." did work for me! 
So I have my WebCam working out of the box with Cheese, but not working in Skype. I tried all things mentioned here [http://forum.skype.com/index.php?act=Print&client=printer&f=18&t=411441]("http://forum.skype.com/index.php?act=Print&client=printer&f=18&t=411441"), all credit goes there - Thank you guys! 
So here is the solution for me (and I hope for others too :):
In your home directory you should have hidden folder .Skype/skypeusername/config.xml open that file with nano or whatever and find <video> section.
Should look like this:> </StatsSender>
    <Video>
      <AdvertPolicy>contacts</AdvertPolicy>
      <RecvPolicy>contacts</RecvPolicy>
    </Video>
    <table_insert_history>
add the fallowing lines inside:
> </StatsSender>
    <Video>
      <AdvertPolicy>contacts</AdvertPolicy>
      <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
      <RecvPolicy>contacts</RecvPolicy>
    </Video>
    <table_insert_history>
Save and close it, my skype was not running during editing this lines, start skype and test in options! TEST button works and also video calls Works!
If it's working for you - then cheers! Happy Video Skypping!

mve:popcorn:

---

### Post by pashlit on 2010-05-09
> **mve-lamb said:**
> Hi guys, I have some success with my not working webcam :guitar:

st in options! TEST button works and also video calls Works!
If it's working for you - then cheers! Happy Video Skypping!

mve:popcorn:

NO, no luck here. Still the same.:confused:

---

### Post by pashlit on 2010-05-09
OK, guys. I just made a complete fresh install of Ubuntu 10.04. Ran update, installed Skype. And video worked right out of the box. Then I tried it again....and same result...no video in Skype. Thats just strange.

---

### Post by mve-lamb on 2010-05-09
> **pashlit said:**
> OK, guys. I just made a complete fresh install of Ubuntu 10.04. Ran update, installed Skype. And video worked right out of the box. Then I tried it again....and same result...no video in Skype. Thats just strange.
Hi, can you post the output of all commands that i wrote in my first [post?]("http://ubuntuforums.org/showthread.php?t=1469720&page=2")#11

and also can you try this, open new empty file in your home directory just for testing with $ nano startskype and paste these inside:
> #!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
/usr/bin/skype

make it executable$ sudo chmod a+x startskype
and test it$ ./startskype

before that also make sure that you put > <CaptureHeight>480</CaptureHeight>
<CaptureWidth>640</CaptureWidth> in your $/home/user/.Skype/skypeuser/config.xml <video> section. 



mve

---

### Post by pashlit on 2010-05-10
> **mve-lamb said:**
> Hi, can you post the output of all commands that i wrote in my first [post?]("http://ubuntuforums.org/showthread.php?t=1469720&page=2")#11


pasha@pasha-laptop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

pasha@pasha-laptop:~$  lsmod | grep videodev
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev

pasha@pasha-laptop:~$ uname -a
Linux pasha-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux


> 
and also can you try this, open new empty file in your home directory just for testing with $ nano startskype and paste these inside:

make it executable$ sudo chmod a+x startskype
and test it$ ./startskype

That actually did the trick!!! The video worked. I didnt try to call anybody, but at least camera stared working in test mode.

> 
before that also make sure that you put  in your $/home/user/.Skype/skypeuser/config.xml <video> section. 


I dont have VIDEO section at all in my config file. I tried adding it manually before but it didnt help.
Thanks for tht info. So what seems to be the problem? I am not a pro and dont know what exactly your test file did, but it made my Skype show video. When I run your file I get the following error in terminal, but video works:

pasha@pasha-laptop:~$ ./startskype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

So should I just start Skype using your file now? I ll post more results, if I run into other problems.

---

### Post by pashlit on 2010-05-10
Some updates.

In my skype shortcut command line i just put:

bash -c 'XLIB_SKIP_ARGB_VISUALS=1 skype'

I have no idea what that command does. I just combined the ideas what guys put here and created that line. I guess other guys might explain it better. 
Now video works!!! Hope it will help others. For some reason Skype icon looks different on my panel now. It has white background and my panel is black. ))) I d like to fix that also but it s a minor problem to compare to not having video. LOL

---

### Post by Manyette on 2010-05-10
I am using the released version of 10.04 on an HP G71 machine, and Skype came right up without problems.  Sort of surprising that it worked before and doesn't now.  I think I'd look elsewhere than 10.04, and search for some other problem, although I can't imagine what that might be at this point.  (Mine is also the X64 on a core 2 Duo.)

---

### Post by noisemonkey on 2010-05-18
I'm not sure if it was already mentioned, but i haven't found it in the forums or elsewhere probably because it's a dirty workaround, but since i'm only interested in the result here is it:

if your webcam is supported by cheese photo booth or some other application that displays the video, you can use the "share part of the screen"-feature in the newest version (beta 2 for linux) of skype and just drag the selection over your webcam videostream. 

hope i helped some of you until there's a real fix from the development team.

---

### Post by pashlit on 2010-05-18
> **noisemonkey said:**
> I'm not sure if it was already mentioned, but i haven't found it in the forums or elsewhere probably because it's a dirty workaround, but since i'm only interested in the result here is it:

if your webcam is supported by cheese photo booth or some other application that displays the video, you can use the "share part of the screen"-feature in the newest version (beta 2 for linux) of skype and just drag the selection over your webcam videostream. 

hope i helped some of you until there's a real fix from the development team.

I found better workaround and it works like a charm - i eventually downgraded to Ubuntu 9.10. I hate saying that...but 10.04 sucks real bad. I managed to make my Skype work but tons of other bugs made me switch back to earlier version...

---

### Post by Hoppermania on 2010-05-24
> **pashlit said:**
> I found better workaround and it works like a charm - i eventually downgraded to Ubuntu 9.10. I hate saying that...but 10.04 sucks real bad. I managed to make my Skype work but tons of other bugs made me switch back to earlier version...

I run Ubuntu 10.04 64bit and am quite satisfied so far. My Skype worked just fine with the webcam right from the start, however it seemed to not load the webcam at every session. After playing around I found that starting skype from the terminal loaded the camera and everything. Starting skype from the applications toolbar button did not do as good of a job. So try to start it from the terminal, that worked for me.

---

### Post by pashlit on 2010-05-24
> **Hoppermania said:**
> I run Ubuntu 10.04 64bit and am quite satisfied so far. My Skype worked just fine with the webcam right from the start, however it seemed to not load the webcam at every session. After playing around I found that starting skype from the terminal loaded the camera and everything. Starting skype from the applications toolbar button did not do as good of a job. So try to start it from the terminal, that worked for me.

As I had mentioned, I managed to get video in Skype to work in 10.04. But Latest version of Ubuntu has tons of other bugs, like loosing wireless connection after resuming from suspend mode; not seeing other drives, not seeing USB ports, freezing, printer problems, audio problems... I can go on. I tried it on both of my Desktop and Laptop machines and on both of them 10.04 SUCKED big time! After I downgraded I got my peace of mind back. Everything works perfect and I dont have to dig for hours searching for solution for d..n Skype video or other stuff. I have lots of stuff to do besides troubleshooting Ubuntu. Of course every case is different. I still love Ubuntu and I use Ubuntu.
Good luck to all of us.

---

### Post by NonMSman on 2010-06-21
I gave 10.04 a try and found it to be a great departure from other Ubuntu distributions.  Its more like a MacBuntu.  Since I do not like the Apple flavor much I tried to accept it and found that it was simply wrong.  I hated it.  Looking past that it was also several orders of magnitude slower then 9.10.

After careful consideration I switched back and advised my clients to never click the UPGRADE button ever.  10.04 is clearly a mistake of some sort.  To say theat UBUNTU sucks is wrong.

Ubuntu 10.04 might suck, and certainly in my case I would agree on many fronts with that.  I think you should try Ubuntu 9.10.  Its an almost perfect Linux in every way.

How hard it must be for first time Ubuntu clients to fully grasp that a once perfect linux would become so currupt.  Most new clients that I have met up with hated the new look and feel.  This is not even to mention the new slow response.

I suppose change is allways going to happen no matter what.  What we hope for is that such changes are positive ones.  Every company makes mistakes.  Coke made on when they changed an already established product.

Microsoft made Vista and NT and we all know the problems that brought them. XP seems to have been a far better version of Windows then any of their prior software.  So when Vista showed up with all its crazy permission screens people ran back to XP, and even Dell refused to load Vista at one point.  Remember they support these machines.

So Canonical like any other company tried somethng new and got it wrong !
Sure 10.04 is the worst Ubuntu version.  But hey..  We still have Karmic Koala Ubuntu 9.10, and that version will convert even the most seasoned Windows user back to Ubuntu.

Ubuntu 9.10 is perhaps the best Linux distro out.  Fast as lightning !  Great in almost every way.  Skype works well in 9.10.   In fact all my clients love Karmic.  If Ubuntu continues to loose touch with their core users, then they have lost sight of what made Ubuntu so good.

While Machintosh users might like the feel of 10.04.  Its clearly a serious blow to the Ubuntu community, and frankly its seem like we are loosing new Ubuntu clients on their very first experience as is the case here.

Its a sad state we are in.  The loss of the finest OS to outside forces like Apple and MS is tragic enough.  The loss of new potential Ubuntu clients, as well as a departing Ubuntu core is beyond anything I ever thought would happen.

Ubuntu will need to fall flat on its face before the key players in its development team realize what hit them.  Before they realize that it was themselves that hit them might take a bit longer.

:confused:

Don't quit Ubuntu yet.  In time these people will loose their job there and Ubuntu will go back to its roots.  Try 9.10 and wait Canonical out.  They are down but maybe not out yet !

---

### Post by ndstate on 2010-06-26
[http://ubuntuforums.org/showpost.php?p=9270395&postcount=27](http://ubuntuforums.org/showpost.php?p=9270395&postcount=27) works for me on 10.04 64bit with a Chicony USB webcam.

Thanks!

---

### Post by geudrik on 2010-07-19
> **pashlit said:**
> Some updates.

In my skype shortcut command line i just put:

bash -c 'XLIB_SKIP_ARGB_VISUALS=1 skype'

I have no idea what that command does. I just combined the ideas what guys put here and created that line. I guess other guys might explain it better. 
Now video works!!! Hope it will help others. For some reason Skype icon looks different on my panel now. It has white background and my panel is black. ))) I d like to fix that also but it s a minor problem to compare to not having video. LOL

I have no idea what that does either, but it seems to have worked for me :D

Installed Skype Beta, tried all the other BS and fail... Ran your command
```
$ bash -c 'XLIB_SKIP_ARGB_VISUALS=1 skype'
```
Terminal gives me lots of errors with my theme though, but who cares. It seems to be working :)

---

### Post by tushar.pereira on 2010-10-04
Thanks the above solution worked for me. I had exactly the same problem. The webcam (logitech quickcam series) worked in cheese, but for some reason dint show the video in skype, though it switched on. Using ubuntu 10.04.
Thanks again.

---

### Post by hanslinux on 2010-10-12
> **mve-lamb said:**
> Hi, can you post the output of all commands that i wrote in my first [post?]("http://ubuntuforums.org/showthread.php?t=1469720&page=2")#11

and also can you try this, open new empty file in your home directory just for testing with $ nano startskype and paste these inside:


make it executable$ sudo chmod a+x startskype
and test it$ ./startskype

before that also make sure that you put  in your $/home/user/.Skype/skypeuser/config.xml <video> section. 



mve

For me it only works when I start another webcam app (e.g. cheese) for a short while before starting the above xkype solution.

My startskype is:
#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
export LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so
#
cheese &
sleep 10s
killall cheese
#
/usr/bin/skype 

But that does not work when autostarted when logging into kde. Somebody a solution for that?

---

### Post by lem79 on 2010-11-04
Not quite the right thread, but I should mention that I got Skype working with a Logitech Quickcam on **Ubuntu 10.10 AMD64 (x86_64)**. The trick was to preload the 32bit v4l2convert library. The same solution *may* work on Ubuntu 10.04 LTS. **EDIT:** This is only for the .deb available from skype.com at the moment. The version of Skype offered by Canonical (Ubuntu Softwre Center -> Get Software -> Canonical Partners -> Skype) works fine here out of the box, no tweaks required.

USB webcam:
# lsusb
Bus 002 Device 004: ID 046d:08d9 Logitech, Inc. QuickCam IM/Connect

Ubuntu 10.10 default kernel at this time:
# uname -a
Linux desktop 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

Skype version 2.1.0.81-1  (installed from Skype's website, 64bit Ubuntu 8.10+ deb package).


**HOW TO**

Created a launcher script in /usr/local/bin/skype  ( sudo gedit /usr/local/bin/skype )
```

#!/bin/bash
export LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so
/usr/bin/skype

```

Make the script executable:
```

sudo chmod a+x /usr/local/bin/skype

```

Change any Skype launchers on the panels and in System -> Preferences -> Startup Applications to execute /usr/local/bin/skype rather than /usr/bin/skype

Webcam now works in Skype video test options page. Verified that the solution works by explicitly starting Skype in a terminal as /usr/bin/skype .. video test page fails. /usr/local/bin/skype (executing the above script with the LD_PRELOAD), webcam works again.

---

### Post by Claus7 on 2010-11-14
Hello,

> **pashlit said:**
> Some updates.

In my skype shortcut command line i just put:

bash -c 'XLIB_SKIP_ARGB_VISUALS=1 skype'

I have no idea what that command does. I just combined the ideas what guys put here and created that line. I guess other guys might explain it better. 
Now video works!!! Hope it will help others. For some reason Skype icon looks different on my panel now. It has white background and my panel is black. ))) I d like to fix that also but it s a minor problem to compare to not having video. LOL

thanks a lot! At least I'm having the preview test working now using ubuntu maverick 64 bit. I faced all the problems mentioned in this thread without any luck. With this it remains to test it on a real call.

Just to mention that skype opens normally without black background e.t.c..

Regards!

---

### Post by forliberty on 2012-12-09
An important tip here for those googling this: if you are running Ubuntu 10.04-64, you need to point to the v4l1compat.so found at /usr/lib32/libv4l. The solution posted by mve-lamb (post #27) works, but only if you change the path for v4l1compat.so as indicated above. Although you are running a 64-bit OS, Skype is compiled for 32-bit, so the 64-bit v4l1compat.so doesn't work. It took me hours to figure this out; this was the only missing piece, which I found here: 
[http://askubuntu.com/questions/176066/why-doesnt-ld-preload-v4l1compat-so-work-with-64-bit-skype]("http://askubuntu.com/questions/176066/why-doesnt-ld-preload-v4l1compat-so-work-with-64-bit-skype")

David

---

