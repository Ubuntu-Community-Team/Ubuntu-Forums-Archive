---
title: "Webcam works with Cheese, but not with Skype"
date: 2008-11-25
forum: Multimedia Software
---

### Post by tbraun on 2008-11-25
Hello!

I tried the Tchibo webcam (Tchibo is a retailer in Germany) with Ubuntu 8.10 on a Dell Latitude D820. It shows up as follows via [FONT="Courier New"]lsusb[/FONT]:

[INDENT][FONT="Courier New"]Bus 003 Device 005: ID 093a:2600 Pixart Imaging, Inc. Typhoon Easycam USB 330K (newer)/Typhoon Easycam USB 2.0 VGA 1.3M/Sansun SN-508[/FONT][/INDENT]

When I start the "Cheese Webcam Booth" it works without any problem. However, when I then start Skype (version 2.0.0.63) and I 'test' the video image, I only get static. Quite literally: The image is just shown as colourful static, as if a TV receiver was out of tune. See also the attached screenshot.

How come this works under Cheese, but not under Skype? For what it's worth, they both use the /dev/video0 device.

I would love to be able to use this camera with Skype. Any idea what to do?

Thank you very much...

---

### Post by papamat on 2008-11-26
Thanks mate xD That works for me to.

---

### Post by kiiiikooo on 2008-12-25
First sorry for upping this old thread .

I had the same problem and it really drived me crasy these days, so thanks alot for solution Chauncellor !! 

But as i'm still a newbie in linux i have some problems adding this command to the launcher of skype so i don't have to type it every time I use skype :p I would appreciate your help !

Edit : 
Oups sorry i should have done some research before asking the question, I found the solution on the archive of this forum

---

### Post by stz184 on 2009-01-29
> **Chauncellor said:**
> There's something wrong with GStreamer or something. There's a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918)

I haven't checked this out recently as I don't really use Skype all that much, but there's a workaround mentioned in there.

Run this in a terminal.

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

That should fix your problem. I just have my launcher to start up with that code in a terminal, and all is well at the moment. Glancing over the status, it seems that a fix may have been released.

Good luck:)

Thanks :)
Now I can use my cheap China-phone SciPhone as web camera :lolflag:

---

### Post by befana on 2009-02-05
And how to make Skype to run with working webcam without typing in a terminal?
I am asking this because of my parents - they are too old to type in a terminal.

---

### Post by swamytk on 2009-02-09
> **befana said:**
> And how to make Skype to run with working webcam without typing in a terminal?
I am asking this because of my parents - they are too old to type in a terminal.
To create a shortcut for skype with this fix:

1. Create a simple script shown below with the name launchskype in your home folder
> #!/bin/sh
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so 
skype &

2. Set it as executable file. In file browser, right click the file and select "Make Link" option. It will create a link. Cut and paste this link to your desktop.
3. Double click this shortcut to launch skype. If it is prompted to "display or execute", select execute (or make select as default action in nautilus preferences)

---

### Post by gitboxgreg on 2009-04-14
I have been trying to get this to work for weeks, thank you so much!

---

### Post by eldragon on 2009-04-14
EDIT: nothing, just checked OP's date, my bad

---

### Post by Arcadian on 2009-06-21
This has worked for me also!! Plus I have the shell script running skype for me at login now, which means I can forget about it. A big thanks to everyone involved! :)

---

### Post by mosta7eel on 2009-07-19
Am sorry to hit an old thread, but I have the same problem and was perfectly solved byt the LD_Preloaad command.
Now I am facing the same problem with virtualbox version 3.02. I have tried to run it with the command the same as the one mentioned for skype but it doesn't make a difference.
My OS is Kubuntu (Jaunty)
Virtualbox 3.02 running windows XP SP3
Webcam is Microdia Clas Ohlson TWC-30XOP WebCam
thanks in acvance

---

### Post by andrescodas on 2009-08-18
It works with my:

0c45:6005 Microdia Sweex Mini WebCam

Thanks!

---

### Post by cpatton90 on 2009-08-29
This worked for me as well! Ubuntu 9.04, skype 2.1.0.47, with a Logitech Quckcam. lsusb reads "Bus 005 Device 002: ID 046d:08af Logitech, Inc. QuickCam Easy/Cool". 

I bought this camera for $15 and it worked out of the box with Windows, of course. But as I previously only used windows for skyping, windows got riddled with the bugs, spyware, and the general crappiness that usually leads one to reformat. But now that I came across this post everything's working.

Thanks for the script!

-Chris

---

### Post by Sergei Sotnikov on 2009-08-30
Hello to everyone,
I have the same problem, my webcam works with Cheese, but not with Skype. I was using Ubuntu 8.10 before and with this comand: LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype[FONT=monospace] 
everything worked fine. Then after I downloaded updates for the system it stoped working. I updated to Ubuntu 9.04 version, but it did not help. Now my webcam works with Cheese fine but when I try to run Skype with [/FONT] LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype[FONT=monospace] command in terminal it wrights:

sergei@sergei-desktop:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 
ALSA lib pcm.c:2205(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
Skype Video Capture: Cannot open device '/dev/video0': No such file or directory
Starting the process...
Skype Xv: Xv ports available: 64
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 355
Skype Xv: No suitable overlay format found


Does anybody knows what it means and how to fix my Webcam to work again. Thank you! May God bless you in Jesus Christ name!
[/FONT]

---

### Post by paul1080 on 2009-10-28
> **Chauncellor said:**
> There's something wrong with GStreamer or something. There's a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918)

I haven't checked this out recently as I don't really use Skype all that much, but there's a workaround mentioned in there.

Run this in a terminal.

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```That should fix your problem. I just have my launcher to start up with that code in a terminal, and all is well at the moment. Glancing over the status, it seems that a fix may have been released.

Good luck:)

Running Logitech 08af, and jaunty here - wooo hoo hoo! it works it works!!
Many thanks Chauncellor, good luck Sergei hope somebody here can help you.

---

### Post by gugamare on 2009-11-29
It worked on my Labtec Webcam Pro! 

I'm running ubuntu 9.10 and skype 2.1.0.47.

Thanks!!!

---

### Post by Chriske on 2009-11-30
Thanks for a great solution! It worked with my Creative Vista Live! webcam.

And thanks to the poster who provided the automatic script too. 

Much appreciated.

---

### Post by onetwothreecool on 2009-12-08
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
[1] 6239

i get this error?

---

### Post by snake_eyes on 2009-12-23
it didn't work and no wrong messages at the same time :(

any suggestion?

---

### Post by levimaen on 2009-12-24
> **Chauncellor said:**
> There's something wrong with GStreamer or something. There's a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918)

I haven't checked this out recently as I don't really use Skype all that much, but there's a workaround mentioned in there.

Run this in a terminal.

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

That should fix your problem. I just have my launcher to start up with that code in a terminal, and all is well at the moment. Glancing over the status, it seems that a fix may have been released.

Good luck:)
 You are a genius! I have tried for 24 hours in all Ubuntu forums, in vain!thank you!

---

### Post by av8rbri on 2010-01-10
> **onetwothreecool said:**
> ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
[1] 6239

i get this error?
I get this exact same msg. too after it is typed in a terminal window. Anyone, anyone, Bueller, Bueller......?

---

### Post by chandler220 on 2010-01-21
> **swamytk said:**
> To create a shortcut for skype with this fix:

1. Create a simple script shown below with the name launchskype in your home folder

2. Set it as executable file. In file browser, right click the file and select "Make Link" option. It will create a link. Cut and paste this link to your desktop.
3. Double click this shortcut to launch skype. If it is prompted to "display or execute", select execute (or make select as default action in nautilus preferences)
Thank you very much, I am using Sony VAIO VGN-FT50B & Skype 2.1.0.47,
the LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so works prefect for me.
But I am facing the problem to create a shortcut to open the skype without typing this script in terminal each time.
Although I followed swamytk said every step, but I have no luck still cannot open with the link I created, can anyone give me some hints?

---

### Post by Kyle138 on 2010-01-24
If you don't want to make a desktop shortcut you can edit the System->Preferences->MainMenu properties for Skype. Just change the Command: field from 'skype' to '/path/to/your/script/skype.sh'

---

### Post by chandler220 on 2010-01-24
I think I know where I've done wrong, but since I am a rookie of Linux, so I don't know how to solve it.
To create a shortcut for skype with this fix:

1. Create a simple script shown below with the name launchskype in your home folder
[COLOR=Blue]**I created the launchskype by gedit Text Editor and just save like that, did I make mistake at this part?**[/COLOR]

2. Set it as executable file. In file browser, right click the file and select "Make Link" option. It will create a link. Cut and paste this link to your desktop.
**[COLOR=Blue]I surfed some website and have the idea how to make it executable file, but I couldn't copy the file to my home folder[/COLOR]**

3. Double click this shortcut to launch skype. If it is prompted to "display or execute", select execute (or make select as default action in nautilus preferences)
**[COLOR=Blue]Since I couldn't finished the first 2 steps, I didn't get to the 3 step.[/COLOR]**

And Thank you for the tips Kyle138, but I didn't see any skype.sh, what is the file of skype.sh?
I am sorry that may be I asked some stupid question because I don't know Linux at all, but I really want to join this community, since I found Ubuntu is really great and COOL!
I really willing to learn more about Linux. I hope I can get some help in this forum.

---

### Post by Kyle138 on 2010-01-27
Gedit is fine for editing a scipt file. Think of it as a .bat file in windows, just a text file containing a list of commands to run.

There are a couple of ways to make a file executable. From the GUI (nautilus) you just right-click the file, select properties, select the Permissions tab, and check the box []Allow executing file as program. From the command line you would type chmod +x filename

In my example before the file skype.sh is the one that you created. You named yours launchskype ;)

---

### Post by zeroseven0183 on 2010-02-12
It worked perfectly. Thanks!

---

### Post by arnaud_d on 2010-02-16
> **Chauncellor said:**
> There's something wrong with GStreamer or something. There's a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918)

I haven't checked this out recently as I don't really use Skype all that much, but there's a workaround mentioned in there.

Run this in a terminal.

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

That should fix your problem. I just have my launcher to start up with that code in a terminal, and all is well at the moment. Glancing over the status, it seems that a fix may have been released.

Good luck:)

Thank you so much !!! I was having this problem for month and your solution solved it in a flash !

---

### Post by snake_eyes on 2010-02-18
Thank you so much, solved.....

---

### Post by albtross on 2010-02-18
Hello 

I am struggling to get my webcam to work with Skype 2.1.0.81 , it works with Cheese.
I am running karmic 64-bit.

desktop:~$ lsusb
Bus 003 Device 002: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX
I have test the "sudo gstreamer-properties" select Video & it only works with "v4l2"

When I try to run "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype" I get the following error
"ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored."

Then if I try to run "LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype" Skype will load without errors, however when I go to test (button) the video, the program crashes with a segmentation fault.

Would appreciate some help
Cheers

---

### Post by lotv on 2010-06-06
I tried to open skype with the command you suggest and get this

```
lotv@lotv-laptop:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
X Error, request 42, minor 0, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 42, minor 0, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 42, minor 0, error code 8 BadMatch (invalid parameter attributes)
```

Any suggestions? Skype seems to be using the correct device but all I see is a plain black screen instead of my beautiful face, It works exactly the same with or without the launcher you use.

---

### Post by arunstar on 2010-07-02
I am on Ubuntu 10.04, 64 AMD., HP Laptop.
Skype 2.1.0.81

How I solved the Skype video problem.

1. Do this at terminal
arun@machinix:~$ lsmod | grep videodev
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev

2. Test if the webcam video works on your pc

arun@machinix:~$ sudo gstreamer-properties

- This will open a "Multimedia System Selector" for you (see the screeshot, GS.png).
- Go to the Video tab --> Default input, and click the Test button.
- This will open the Webcam for you. This means the webcam is working fine on your pc (see the screenshot, webcam.jpg).
- Close the "Multimedia System Selector" now.

3. Open the file as:
arun@machinix:~$ sudo gedit /usr/local/bin/skype

- Type in the following 

#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype

- Save and close the gedit.

Note: The usage of library is important, remember I on 64 bit Linux, earlier I was typing the above line with "/usr/lib/..." (notice missing 32 here :) ) that did NOT enable the skype video for me. The trick was to use the 32 bit libraries. Why, this may be because Skype Linux client is most probably built for the normal 32bit linux distros. So 64 bit linux users like me need to direct the Skype to use the 32 bit files only.
Actually the output in step 1, that is 
*v4l2_compat_ioctl32    12020  1 videodev*
this should given me idea that my pc is using 32 bit libs with the webcam (silly me).

4. Just launch the Skype now and text the video as 
Skype menu --> Options --> Video Devices 
- Press Test button
-  You should see that the Webcam is now working fine.

:p

---

### Post by calimerox on 2010-07-05
i got a quite similar problem with skype and lucid
when i use video skype, the sound crashes aufter 6 minutes and i dont hear anything anymore.. i have to kill skype and start again for getting a connection again.. i also had cheese installed, there might be a connection? thanks !

---

### Post by arunstar on 2010-07-06
Hi Calimerox

Well I can say that first you check that the Cheese is working fine for you, try recording a video from the webcam using Cheese.
This will ensure that the loaded video libs are working fine for you. If not then you may like to reload the libs (you may need to search how to reload this "/usr/lib32/libv4l/.." libraries from the repository).
Next you may re-install the Skype and try the video chat again. Hope this helps.

Arun

---

### Post by isleshocky77 on 2010-07-09
First, make sure after making the /usr/local/bin/skype file that you set the proper permissions.

```

sudo chmod 755 /usr/local/bin/skype

```

Secondly, as the user stated above, if you're on a 32 bit system your file I believe should look like this:

```

#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

```

However, I'm looking to see if anyone could help with a problem I'm having. I now can click test in options and see the video working fine.  I can then start a call without video and it works as expected; but as soon as I enable video during a call it crashes skype.

When running from the command line the output looks like this:

```
sostrow@sostrow-v2000:~$ skype
<unknown>: Fatal IO error 14 (Bad address) on X server :0.0.
/usr/local/bin/skype: line 2:  1077 Segmentation fault      LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
```

Any help would be greatly appreciated.

---

### Post by mtopro on 2010-10-14
arunstar. great tutorial above.  i have gone through about every solution out there and you point out just what i needed to get my 64bit system's webcam working on Skype.  Thank you for posting!

---

### Post by bigred1 on 2010-11-10
> **swamytk said:**
> To create a shortcut for skype with this fix:

1. Create a simple script shown below with the name launchskype in your home folder...

This worked for me. Thanks. I have a Logitech Quickcam Express which worked in Cheese. It also worked in Skype on the same machine in Windows. But in Ubuntu, the video was simply coming through black. This fixed it.

---

### Post by solnyshok on 2010-12-19
I am on 64 bit Maverick. In my case, video worked so that my opponents could see me, and worked in cheese. But I could not see neither myself, neither opposite end's video. This was solved by editing skype launch shortcut to

bash -c 'XLIB_SKIP_ARGB_VISUALS=1 skype'

---

### Post by malmsteen84 on 2011-01-03
> **arunstar said:**
> I am on Ubuntu 10.04, 64 AMD., HP Laptop.
Skype 2.1.0.81

How I solved the Skype video problem.

1. Do this at terminal
arun@machinix:~$ lsmod | grep videodev
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev

2. Test if the webcam video works on your pc

arun@machinix:~$ sudo gstreamer-properties

- This will open a "Multimedia System Selector" for you (see the screeshot, GS.png).
- Go to the Video tab --> Default input, and click the Test button.
- This will open the Webcam for you. This means the webcam is working fine on your pc (see the screenshot, webcam.jpg).
- Close the "Multimedia System Selector" now.

3. Open the file as:
arun@machinix:~$ sudo gedit /usr/local/bin/skype

- Type in the following 

#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype

- Save and close the gedit.

Note: The usage of library is important, remember I on 64 bit Linux, earlier I was typing the above line with "/usr/lib/..." (notice missing 32 here :) ) that did NOT enable the skype video for me. The trick was to use the 32 bit libraries. Why, this may be because Skype Linux client is most probably built for the normal 32bit linux distros. So 64 bit linux users like me need to direct the Skype to use the 32 bit files only.
Actually the output in step 1, that is 
*v4l2_compat_ioctl32    12020  1 videodev*
this should given me idea that my pc is using 32 bit libs with the webcam (silly me).

4. Just launch the Skype now and text the video as 
Skype menu --> Options --> Video Devices 
- Press Test button
-  You should see that the Webcam is now working fine.

:p

need help here...
i use 10.10 and skype 2.1.0.81
from gstreamer-properties my webcam is running fine. but i got message "segmentation fault" after running skype using your suggestion above and do videotesting.
any idea?

---

### Post by cordoval on 2011-01-05
maverick and skype 2.1.0.81 I am as many that had not been able to have it working until now

I have tried everything but it would just show that it works with gstream-properties for usb webcam  on /dev/video0 although actually my webcam is incorporated to the screen on this laptop, however when on the skype options one is only shown the default usb camera as if there was not any other besides the default. I think this is one of the problems.


videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev


gstream-properties lack also several other plugins

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'


however I don't think that is the problem, and the window for gstream-properties is attached with configuration that works, however on skype it does not work

---

### Post by dulbirakan on 2011-02-04
I am using an Acer TravelMate 3040 that came with a logitech orbicam.

I confirm that this fix works but you might need to restart skype a few times.

---

### Post by pwabrahams on 2011-02-06
I'm running under fully updated Kubuntu 10.10.  I have two different webcams attached now, so the webcam is unlikely to be the problem.  Cheese works perfectly with both.  But here's what I get when I do the skype video test with either of them:
```
pwa@Asus-laptop:~$ LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so /usr/bin/skype
Segmentation fault
pwa@Asus-laptop:~$ LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype
Segmentation fault

```
With all the reports of success with this fix (and I've seen many), why am I so unlucky?

One other thought: am I using the right repository for libv4l?  I'm getting it from 
> [http://ppa.launchpad.net/libv4l/ppa/ubuntu/](http://ppa.launchpad.net/libv4l/ppa/ubuntu/) maverick main


---

### Post by rvchari on 2011-02-06
its an interesting thread related to web cams. 

i am using integrated webcam (chicony) that comes with laptop. it works fine with all the apps but i have a funny problem.
daylight => web cam works perfect.
night => image is darkened to such an extent that screen is almost black !!! i tried to luminate the room to such an extent that my eyes felt uneasy still the same problem !!! wonder if its hardware related or OS driver related...
any help in this regard will be good..

---

### Post by pwabrahams on 2011-02-06
Until a couple of weeks ago, the skype video test worked for me.  I just did a little investigation and discovered that the copy of libv4l in the repository was updated on January 27.  I can't be sure, but I think that date is the dividing line between when my webcam worked in Skype and when it didn't.

Who gets bug reports for libv4l?

---

### Post by crabsody on 2011-02-13
pwabrahams I think you are right. My cam doesn't work with skype after a recent update....

---

### Post by crabsody on 2011-02-13
Sorry. I reinstalled skype and now works fine...

---

### Post by felixq78 on 2011-02-19
> **Chauncellor said:**
> There's something wrong with GStreamer or something. There's a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918)

I haven't checked this out recently as I don't really use Skype all that much, but there's a workaround mentioned in there.

Run this in a terminal.

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

That should fix your problem. I just have my launcher to start up with that code in a terminal, and all is well at the moment. Glancing over the status, it seems that a fix may have been released.

Good luck:)
This works if you want to start Skype off the terminal "every time"which I'm happy to do but many find it a problem, but if you open Skype from the usual way i.e. Apps>Internet>Skype it doesn't work.
There must be a fix to change Skype so the webcam works in the usual way?

---

### Post by felixq78 on 2011-02-19
> **arunstar said:**
> I am on Ubuntu 10.04, 64 AMD., HP Laptop.
Skype 2.1.0.81

How I solved the Skype video problem.

1. Do this at terminal
arun@machinix:~$ lsmod | grep videodev
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev

2. Test if the webcam video works on your pc

arun@machinix:~$ sudo gstreamer-properties

- This will open a "Multimedia System Selector" for you (see the screeshot, GS.png).
- Go to the Video tab --> Default input, and click the Test button.
- This will open the Webcam for you. This means the webcam is working fine on your pc (see the screenshot, webcam.jpg).
- Close the "Multimedia System Selector" now.

3. Open the file as:
arun@machinix:~$ sudo gedit /usr/local/bin/skype

- Type in the following 

#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype

- Save and close the gedit.

Note: The usage of library is important, remember I on 64 bit Linux, earlier I was typing the above line with "/usr/lib/..." (notice missing 32 here :) ) that did NOT enable the skype video for me. The trick was to use the 32 bit libraries. Why, this may be because Skype Linux client is most probably built for the normal 32bit linux distros. So 64 bit linux users like me need to direct the Skype to use the 32 bit files only.
Actually the output in step 1, that is 
*v4l2_compat_ioctl32    12020  1 videodev*
this should given me idea that my pc is using 32 bit libs with the webcam (silly me).

4. Just launch the Skype now and text the video as 
Skype menu --> Options --> Video Devices 
- Press Test button
-  You should see that the Webcam is now working fine.

:p

All I got was "command not found":guitar:

---

### Post by pwabrahams on 2011-02-19
If the file **/usr/local/bin/skype** isn't marked as executable, then it isn't usable as a command.  To fix that: **sudo chmod a+x /usr/local/bin/skype**.  That bit was missing from the recipe.
To check the status: **ls -l /usr/local/bin/skype**.  The attributes should include **x**.

---

### Post by banyai on 2011-03-04
Ubuntu 10.10 (64 bit)
Logitech Webcam C500 (UVC Camera (046d:0807)(7dev/video 0)
Cheese (audio and video - OK)
Skype (beta) 2.1.0.81    (audio - OK, video - crash) (same driver!)


Neither of the proposed solutions worked for me!!!!!

---

### Post by skiwithpete on 2011-03-04
Same here, got an update through today and now skype cam doesn't work though it does work in cheese...

10.10
32bit
Update was completed today march 5th 2011. 
Logitech camera

---

### Post by crabsody on 2011-03-07
&#921; wrote a post before that I reinstalled skype and it was fixed. Well this is partially the truth. Every time I boot the machine the problem remains. So I should reinstall skype every time. That's very bad.

---

### Post by kan3malato on 2011-03-19
> **Chauncellor said:**
> There's something wrong with GStreamer or something. There's a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918)

I haven't checked this out recently as I don't really use Skype all that much, but there's a workaround mentioned in there.

Run this in a terminal.

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```That should fix your problem. I just have my launcher to start up with that code in a terminal, and all is well at the moment. Glancing over the status, it seems that a fix may have been released.

Good luck:)
> **swamytk said:**
> To create a shortcut for skype with this fix:

1. Create a simple script shown below with the name launchskype in your home folder

2. Set it as executable file. In file browser, right click the file and  select "Make Link" option. It will create a link. Cut and paste this  link to your desktop.
3. Double click this shortcut to launch skype. If it is prompted to  "display or execute", select execute (or make select as default action  in nautilus preferences)
Hi all.
It works!! finally,
You both are f   genius guys, really8-)
Thanks thousand.

---

### Post by pwabrahams on 2011-03-20
Even more convenient is to put the fix into /usr/local/bin:
```
sudo echo "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype" > /usr/local/bin/skype
```
Since **/usr/local/bin** is searched for commands before **/usr/bin**, the simple **skype** command now does what is wanted!

---

### Post by Itsikaviram on 2011-03-20
Can you please expand on this method.  I have the same problem with skype and camera.
What does it mean to create a simple script ?  Can you show step by step ? 
Itsik
Thank you

---

### Post by pwabrahams on 2011-03-20
What is the problem with camera?  If it just needs the same preload, then put the line I recommended into /usr/local/bin/camera, with /usr/bin/camera substituted for /usr/bin/skype.

---

### Post by Itsikaviram on 2011-03-20
I have tried the code 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skypeon my terminal and got an error message 
[FONT=monospace]cannot find preload command, no such directory

What am I doing wrong?


I need a step by step beginners instructions.

Thank you
[/FONT]

---

### Post by pwabrahams on 2011-03-20
You typed:```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
What you should have typed:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
```
Essentially, the preload modified the loading of /usr/bin/skype.  Calling **skype** by itself produces a circularity.

---

### Post by bitbomb on 2011-04-08
**A newbies guide...**

Here is how I got this working on my computer....

I went to my home folder and typed Ctrl-H to bring up hidden folders.  When the hidden folders were shown, I went to the folder named .Skype and made a file named "SkypeWithVideo.sh".  You can name this file anything you want and you can put it where ever you want, I chose this name and location because I like everything to be in my home folder.

I opened my SkypeWithVideo.sh file with a text editor and added these lines...

```
#!/bin/sh
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
skype & 
```I closed the file and then made it executable by opening a command prompt and typing....

```

sudo chmod 755 /home/"user"/.Skype/SkypeWithVideo.sh
```Then I fixed the link in the menu by right clicking on the menu, selecting "edit menus" to bring up the Main Menu configuration tool.  Select the skype entry and in the command section replace the word skype with....

 ```
/home/"user"/.Skype/SkypeWithVideo.sh
```I noticed that this messed up my icon.  If you want to restore it open the Main Menu configuration tool again, click on the Skype entry, click on the icon entry and go to /user/share/icons, the skype icon is called skype.png.  If the icon isn't there, search for the correct location by using the find command.  The following command searchs the root directory and all subdirectories for the skype icon.

```
sudo find / -name "skype.png"
```Hope this helps...

---

### Post by Lordofsraam on 2011-04-08
Works for me (Skype 2.2 on Ubuntu 10.10 using a Microsoft Lifecam) THNX A TON

---

### Post by pwabrahams on 2011-04-09
Although the approach recommended by Bitbomb certainly works, it has the disadvantage that the command has to be modified in every context where it might be used.  Better to put the redefinition ahead of **/usr/bin/skype** in the search path by putting a redefinition in **/usr/local/bin** as I suggested earlier, so the redefinition will be seen before the original definition.  If you don't want to do something that requires root privileges, put the redefinition in **/home/*username*/local/bin**.  That way the simple command "skype" does the right thing.

---

### Post by crabsody on 2011-04-09
I use 10.10 with the latest kernel > Linux angus 2.6.35-28-generic. Skype 2.2.0.25.  Some months ago video worked ok. Then suddenly didn't. Every time I boot the computer I should reinstall skype in order to work. Now a week ago suddenly even this solution stopped working. So I tried the LD_PRELOAD method mentioned above. If I > setenv LD_PRELOAD /usr/lib/libv4l/v4l1compat.so before running skype I got the following message > ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.. dmesg outputs > process `skype' is using obsolete setsockopt SO_BSDCOMPAT. Any suggestions?

---

### Post by crabsody on 2011-04-09
Bingo. arunstar ROCKS!!! I should first do the following

> arun@machinix:~$ sudo gstreamer-properties

- This will open a "Multimedia System Selector" for you (see the screeshot, GS.png).
- Go to the Video tab --> Default input, and click the Test button.
- This will open the Webcam for you. This means the webcam is working fine on your pc (see the screenshot, webcam.jpg).
- Close the "Multimedia System Selector" now.

Now it works OK!!!

---

### Post by pwabrahams on 2011-04-10
> **bitbomb said:**
> **A newbies guide...**
 ```
/home/"user"/.Skype/SkypeWithVideo.sh
```I noticed that this messed up my icon.
The messed-up icon and other related problems occur because you're leaving the meaning of the literal commmand **skype** unchanged.  In posts #53 and @60 I showed just how to make the **skype** command work correctly by intercepting its interpretation and putting the corrected command earlier in the command interpretation path.  Go look again!!

---

### Post by mwray on 2011-04-11
Moderator, can we put this at the top. (Couldn't find the link to the deb file if some one knows it maybe we can have this at the top of the list. This should solve all issues related to the 32-bit/64-bit. Others would be gstreamer issues. Newer versions of gstreamer don't have the lib-theora plugin that worked on older versions to fix the same issue. Works on Ubuntu 8.x and up to at least 10.10. 

HOWTO make the webcam work in BOTH skype and cheese, as above fix breaks cheese w/out the fix broken packages option, and w/out specifying lib32 instead of lib:

Step one:
get the 32bit lib4vl-*version#*_i386.deb

(version# should be replaced w/ current 32-bit version 3)
Step 2:
dpkg -i --force-architecture packagename.deb

Packagename should be replaced w/ name of package retrieved above.

Step 3:
Run synaptic, click "fix broken packages".


Step 4:

write a shell script (say /usr/bin/skype.launcher):
#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
export LD_PRELOAD
/usr/bin/skype &

Step 5:
chmod skype.launcher 755

Step 6:
Use settings Main menu, find the skype launcher and edit command line to be skype.launcher instead of skype.


Note: You can use one or the other, as the device is "locked" for exclusive use. But now you can use either one without jumping through hoops.

---

### Post by pwabrahams on 2011-04-11
> **mwray said:**
> 
write a shell script (say /usr/bin/skype.launcher):
#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
export LD_PRELOAD
/usr/bin/skype &


Now if that shell script is placed in **/usr/local/bin/skype** instead of in **/usr/bin/skype.launcher**, everything works more conveniently.  This approach is also more robust when system updates take place.

---

### Post by Babajus on 2011-04-23
simple fix 

Edit launcher right click on Applications and click edit menus.
There navigate to Internet, right click on Skype and click Properties.
Replace the Command with:

    bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

for me fixed webcammy.

---

### Post by rapattack1 on 2011-04-25
Your a gem Babajus.....this is my first 64bit machine with Artistx(ubuntu) and you solved this for me :0)

---

### Post by houseworkshy on 2011-04-30
I've tried the fixes in this post for 10.04 64bit and still can't make the video in skype work, though ist does in cheese.  It is an HP camera which is supposed to be skype compatable.  Tried the entry in the terminal at the beging of the post, the dropping of an .sh file into the appropriate directory and the altering of the command mentioned above.  Stuck, so it there another program which works in Lucid which would enable video chat that is compatable with skype as most of the people I know are using it on windows.

---

### Post by jaspur on 2011-04-30
I just finished my dig for an answer to the age old problem of skype webcam dysfunction.  I recently installed ubuntu 11.04 and lost a few good apps that I rely on. 

I refer to this article for my final success.

[http://bit.ly/9sCpdH](http://bit.ly/9sCpdH)

hope this helps.

---

### Post by rapattack1 on 2011-05-07
Babajus-Well i got the cam working that i can see but the first two people i tried this with can't see me. Has anyone heard of this? i am using a 64bit system and i have artistx which is a ubuntu distro. Don't know what version it is. It is a multimedia distro. Anyway i can see me in skype and cheese now but no one can see me. One person had windows and the other a mac. Today though a friend said he could see shadows and when i moved my hand in front of the camera he could vaguely see my hand.

---

### Post by pierreu1 on 2011-05-07
I have had the same problem: skype working in all, but in Skype.

I noticed that the video test button indicated that Skype is using a usb 20 camera (/dev/video 0)

My camera is a rocketfish video bought about 4 years ago.

I followed "arunstar" fix , as it was a more recent fix (that I could follow), which would probably be more relevant for a more recent system like I have.

[COLOR="Red"]3. Open the file as:
arun@machinix:~$ sudo gedit /usr/local/bin/skype

- Type in the following 

#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype

- Save and close the gedit.[/COLOR]

AND then I did this:


[COLOR="Red"]pierre2@Pierre-Vancouver:~$ ls -l /usr/local/bin/skyp
ls: cannot access /usr/local/bin/skyp: No such file or directory
pierre2@Pierre-Vancouver:~$ sudo chmod a+x /usr/local/bin/skype
[sudo] password for pierre2: 
Sorry, try again.
[sudo] password for pierre2: 
pierre2@Pierre-Vancouver:~$ sudo chmod a+x /usr/local/bin/skype
pierre2@Pierre-Vancouver:~$ ls -l /usr/local/bin/skype
-rwxr-xr-x 1 root root 70 2011-05-07 09:46 /usr/local/bin/skype
pierre2@Pierre-Vancouver:~$ [/COLOR]

Unfortunately, Skype video test is still not working.

I am running Natty and a webcam that used to work no problem in Skype before I upgraded from 10.10.

What should I try now?

Thanks.

---

### Post by nikonicanicanon on 2011-05-13
100% Funcional!!! tanks

---

### Post by Nausser on 2011-05-24
Worked great for me too on 11.04. Put the script in my home folder under a hidden directory and edited the skype launcher in the menu editor to point to that file. I had to re-associate the Skype icon as well. Not a big deal.

Thanks a lot!!

---

### Post by meddyuk on 2011-05-29
> **Babajus said:**
> simple fix 

Edit launcher right click on Applications and click edit menus.
There navigate to Internet, right click on Skype and click Properties.
Replace the Command with:

    bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

for me fixed webcammy.

I've tried that and it doesn't work. I've managed to get the cam working if i open it from the terminal using the same command, but if i put that command in the skype properties it doesn't work. Any ideas?

---

### Post by _arsen_ on 2011-05-30
Seems like I've tried everything, but still no video in Skype...
"LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" says:
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or foulder
Then skype runs but video doesn't work.
dmesg contains a bunch of messages like these:
[10022.275968] stk11xx: Check device return error (0x0201 = 0C) !
[10022.278221] stk11xx: Check device return error (0x0201 = 0C) !
[10022.280488] stk11xx: Check device return error (0x0201 = 0C) !

In Ubuntu 10.10 somehow It worked.

Now I'm using Kubuntu 11.04 (x86), Skype 2.2 beta.
lsusb gives: Bus 001 Device 002: ID 174f:6a33 Syntek Web Cam - Asus F3SA, F9J, F9S

---

### Post by carter-rowe on 2011-07-05
Hi,

I've got an Acer Aspire One with the crystal webcam.
Having just installed 10.04.02 (Lucid?) I couldn't get the webcam to work on skype

It worked fine in Cheese but not in Skype

I tried all sorts of the PRE_LOAD solutions for compatibility.

After blundering round for hours I noticed that on the 10.04 release notes/manual  ( [http://ubuntuguide.org/wiki/Ubuntu:Lucid#Skype](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Skype) ) 

that they said they downgraded their Skype because the mic didn't work, so I tried that & the video now works fine...

This is what they wrote:-


Many users (including me) have noted that they cannot get their microphone inputs to work with any version later than 2.1.0.47. 

Install:

wget -O skype-ubuntu-current_i386.deb [http://download.skype.com/linux/skype-debian_2.1.0.47-1_i386.deb](http://download.skype.com/linux/skype-debian_2.1.0.47-1_i386.deb)
sudo dpkg -i skype-ubuntu-current_i386.deb
sudo rm skype-ubuntu-current_i386.deb
 
[ aaargh the above is not supposed to be a URL as such the last bit should read linux/skype-debian_2.1.0.47-1_i386.deb ]

or

wget -O skype-ubuntu-current_amd64.deb [http://download.skype.com/linux/skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb](http://download.skype.com/linux/skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb)
sudo dpkg -i skype-ubuntu-current_amd64.deb
sudo rm skype-ubuntu-current_amd64.deb

[ aaargh the above is not supposed to be a URL as such the last bit should read linux/skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb ]

So I did the first one from a terminal window...

Dont know if this will also work with other vid cameras.

The key point seems to be that things like the video stream test work & the camera works in Cheese, so it's *just* skype that wasn't going

Good Luck 

Niq

---

### Post by barkhat on 2011-07-06
> **Nausser said:**
> Worked great for me too on 11.04. Put the script in my home folder under a hidden directory and edited the skype launcher in the menu editor to point to that file. I had to re-associate the Skype icon as well. Not a big deal.

Thanks a lot!!

Can you explain how to do this, please???

Thanks.

---

### Post by redreactions on 2011-07-19
> **Babajus said:**
> simple fix 

Edit launcher right click on Applications and click edit menus.
There navigate to Internet, right click on Skype and click Properties.
Replace the Command with:

    bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

for me fixed webcammy.

THANK YOU Babajus!!!
After reading the entire thread with a load of stuff I don't understand how to do, you provided me with the idiots version of webcam fix.  You are a star!

---

### Post by chriswhat21 on 2011-08-20
I know this is getting to be a really old thread, but

```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
```did not work for me.  I edited the Skype shortcut command to:

```
bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'
```"lib32" being the difference, just in case someone else comes across this thread.

---

### Post by FishRCynic on 2011-09-23
> **chriswhat21 said:**
> I know this is getting to be a really old thread, but

```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
```did not work for me.  I edited the Skype shortcut command to:

```
bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'
```"lib32" being the difference, just in case someone else comes across this thread.

The lib32 change worked for me as well. Much Appreciated!

---

### Post by snake_eyes on 2011-09-23
Hello,

I have Toshiba Satellite c660 the mic is not working on ubuntu 10,04 LTS 64-bit, so any help would be appreciated...

thanks

---

### Post by koftis on 2011-10-10
[B]11.04 x86

Re: Skype problem[/B]             
                                                                ubuntu:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:1869): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:1869): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:1869): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Loading IM context type 'ibus' failed





Any suggestions?

i've also tried this

go to terminal and type:[INDENT] *echo -e "\n# libv4l PPA\ndeb [http://ppa.launchpad.net/libv4l/ppa/ubuntu](http://ppa.launchpad.net/libv4l/ppa/ubuntu) `lsb_release -c | awk '{print $2}'` main" | sudo tee -a /etc/apt/sources.list*[/INDENT][INDENT] *sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C3FFB4AA*[/INDENT][INDENT] *sudo apt-get update*[/INDENT][INDENT] *sudo apt-get install libv4l-0*[/INDENT]Now if you want to start Skype just run this in terminal: [I]LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

my camera info 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:00f5 **Microsoft Corp. LifeCam VX-3000**
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

i got an error in the end...

cheese is working ok..

Any help?;)


[COLOR=Red]the only way i found for to get it working (in this forum fo course is...)

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
[COLOR=Black]/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:2001): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:2001): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:2001): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Loading IM context type 'ibus' failed
libv4l2: error allocating conversion buffer
libv4l2: error allocating conversion buffer
[/COLOR]
still errors but i have videocall (according to test..)
[/COLOR] [/I]

---

### Post by FishRCynic on 2011-10-10
> **koftis said:**
> [B]11.04 x86

Re: Skype problem[/B]             
                                                                ubuntu:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:1869): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:1869): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:1869): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Loading IM context type 'ibus' failed





Any suggestions?

i've also tried this

go to terminal and type:[INDENT] *echo -e "\n# libv4l PPA\ndeb [http://ppa.launchpad.net/libv4l/ppa/ubuntu](http://ppa.launchpad.net/libv4l/ppa/ubuntu) `lsb_release -c | awk '{print $2}'` main" | sudo tee -a /etc/apt/sources.list*[/INDENT][INDENT] *sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C3FFB4AA*[/INDENT][INDENT] *sudo apt-get update*[/INDENT][INDENT] *sudo apt-get install libv4l-0*[/INDENT]Now if you want to start Skype just run this in terminal: [I]LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

my camera info 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:00f5 **Microsoft Corp. LifeCam VX-3000**
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

i got an error in the end...

cheese is working ok..

Any help?;)


[COLOR=Red]the only way i found for to get it working (in this forum fo course is...)

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
[COLOR=Black]/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:2001): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:2001): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:2001): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Loading IM context type 'ibus' failed
libv4l2: error allocating conversion buffer
libv4l2: error allocating conversion buffer
[/COLOR]
still errors but i have videocall (according to test..)
[/COLOR] [/I]

did you try post 79?

---

### Post by Irvs on 2011-10-15
Just upgraded (reinstalled) to Ubuntu 11.10 (64-bit) and trying to get the cam back to work. While previously the above commands used to work, I'm now getting the following output as soon as I log in:
```
$ bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype'
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```

Anyone got this working with Ubuntu 11.10?

---

### Post by FishRCynic on 2011-10-15
Did you install Skype from the repository? 

bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'
still works for me

---

### Post by Irvs on 2011-10-16
> **FishRCynic said:**
> Did you install Skype from the repository? 

bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'
still works for me

Installed it from the website at first, now purged the installed skype and reinstalled from the (Canonical) repo. Still getting the same error #-o

---

### Post by FishRCynic on 2011-10-16
Do you have lightdm-gtk-greeter installed?
(I installed it for a reason and I am hoping this was it)
(( completely irrelevant - I also installed lightdm-qt-greeter for a qt app butI can't remember which one. ))

---

### Post by FishRCynic on 2011-10-16
other thoughts

libv4l-0  - do you have that package installed?

Does Skype run without the webcam support? 
(loading from Dash Icon)

---

### Post by Irvs on 2011-10-16
> **FishRCynic said:**
> other thoughts

libv4l-0  - do you have that package installed?

Does Skype run without the webcam support? 
(loading from Dash Icon)

Thanks for the fast replies Fish!
Yes, libv4l-0 is installed. Installing lightdm-gtk-greeter didn't make any difference either.

Skype itself runs fine from the terminal, and also from Dash (or whatever its called). Just no working cam as expected.

---

### Post by FishRCynic on 2011-10-16
try this

bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'

---

### Post by Irvs on 2011-10-16
Same thing:
```
$ bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/bin/python: can't open file '/usr/share/skype-notify-improved/skype-notify.py': [Errno 2] No such file or directory

```

I don't think the bottom error has anything to do with it, but still strange it shows up.

---

### Post by FishRCynic on 2011-10-16
python-skype
pidgin-skype

I have these two packages installed with skype

---

### Post by Irvs on 2011-10-16
E: Unable to locate package python-skype

Installed pidgin-skype, but no difference either :(

---

### Post by FishRCynic on 2011-10-16
amd64

[https://launchpad.net/ubuntu/oneiric/amd64/python-skype/1.0.32.0-0ubuntu1](https://launchpad.net/ubuntu/oneiric/amd64/python-skype/1.0.32.0-0ubuntu1)

[http://launchpadlibrarian.net/62701044/python-skype_1.0.32.0-0ubuntu1_all.deb](http://launchpadlibrarian.net/62701044/python-skype_1.0.32.0-0ubuntu1_all.deb)

i386

[https://launchpad.net/ubuntu/oneiric/i386/python-skype/1.0.32.0-0ubuntu1](https://launchpad.net/ubuntu/oneiric/i386/python-skype/1.0.32.0-0ubuntu1)

[http://launchpadlibrarian.net/62701044/python-skype_1.0.32.0-0ubuntu1_all.deb](http://launchpadlibrarian.net/62701044/python-skype_1.0.32.0-0ubuntu1_all.deb)

for downloadable deb (same for amd64 and i386)

in software sources do you have multiverse enabled?

it says status deleted for 11.10 but you definitely have a python error.

---

### Post by FishRCynic on 2011-10-16
your webcam does work in Cheese?

if so
does v4l1compat.so
exist in any of these directories\folders?

cd /usr/lib/i386-linux-gnu/libv4l/
dir

cd /usr/lib/libv4l/
dir

cd /usr/lib32/libv4l/
dir

---

### Post by Irvs on 2011-10-16
> **FishRCynic said:**
> 
[https://launchpad.net/ubuntu/oneiric/amd64/python-skype/1.0.32.0-0ubuntu1](https://launchpad.net/ubuntu/oneiric/amd64/python-skype/1.0.32.0-0ubuntu1)

Thanks... made no difference though, the python error is still there.

> in software sources do you have multiverse enabled
Yes.

> **FishRCynic said:**
> your webcam does work in Cheese?

if so
does v4l1compat.so
exist in any of these directories\folders?

cd /usr/lib/i386-linux-gnu/libv4l/
dir

cd /usr/lib/libv4l/
dir

cd /usr/lib32/libv4l/
dir

Cheese didn't come installed in this release... but after installing it, it seems to work just fine. Also worked fine during install, when setup wants to take a picture of you.

/usr/lib/i386-linux-gnu/libv4l/: No such file or directory

In fact, all of these don't exist. I thought I checked before... but nonetheless, the libv4l-0 package IS installed.

---

### Post by Irvs on 2011-10-16
Seems it resides in /usr/lib/x86_64-linux-gnu/libv4l/

But it still isn't able to preload it:
```
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```

EDIT:
Seems it needs the i386 libs from the libv4l-0:i386 package. Once I installed that (spotted the package in synaptic) I was able to run skype:
```
$ LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

```

The error is still there, but at least the cam works now. :D

Thanks for the help FishRCynic!

---

### Post by FishRCynic on 2011-10-16
No problem - 
I think i will do some saving and a reinstall here,
I think my install may have too many orphaned packages hangin around
and not necessarily helpful ones either lol.

---

### Post by Irvs on 2011-10-16
I know what you mean: seems the python script was a left-over, somewhere in my /home directory from the previously installed [Ubuntu Messaging Menu integration]("http://www.webupd8.org/2011/05/skype-ubuntu-messaging-menu-notifyosd.html"). Reinstalled the script and the python error is now gone at least :)

---

### Post by FishRCynic on 2011-10-16
i used this deb for that i think

[http://www.omgubuntu.co.uk/2011/04/how-to-add-and-control-skype-via-the-ubuntu-messaging-menu/](http://www.omgubuntu.co.uk/2011/04/how-to-add-and-control-skype-via-the-ubuntu-messaging-menu/)

---

### Post by josslate on 2011-10-18
actually my webcam doesn't work with cheese or skype  after latest skype/ubuntu installs - tried these 2, which bring up skype OK, but still no webcam
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
any help would be great - thanks

---

### Post by FishRCynic on 2011-10-19
> **josslate said:**
> actually my webcam doesn't work with cheese or skype  after latest skype/ubuntu installs - tried these 2, which bring up skype OK, but still no webcam
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
any help would be great - thanks
Hi 
Usb webcam assumed
advise the output of
lsusb

Thanks

advise if you need clearer instructions

---

### Post by rapattack1 on 2011-11-09
Never did get other webcams working right so happy that i got a Logitech cam that does. Would not have gone out and bought it. Luckily scored it for free :0)

---

### Post by ItalOz on 2011-12-15
big time! worked like a charm.
I did as Arunstar suggested [http://ubuntuforums.org/showpost.php?p=9536960&postcount=31]("http://ubuntuforums.org/showpost.php?p=9536960&postcount=31")
I wanted to use skype with an alternative webcam to the integrated laptop one so I plugged a USB logitec in but did not work straight away.
It did with your trick

I am on a DELL inspiron 1525 Ubuntu 10.10 and skype 2.2.0.35

Cheers

---

### Post by uglspil on 2012-01-15
I can't seem to get my webcam to work with skype either.
As several others have posted I get:

steffen-randahl@steffen-randahl:~$  LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

However, I can't see anybody coming up with a solution for this .. ?

I'm on a 1.1 macbook, with built in iSight cam, and Ubuntu 11.10
works great with cheese.

cheers /steffen

---

### Post by ItalOz on 2012-05-15
Hi

I have upgraded to 12.04
the solution proposed works for me in 11.04

now I have tried to apply the same (same hardware only distro upgraded to 12.04) simply varying the path
```
#!/bin/bash
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype
```

but now it doesn't see the webcam and says
```
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(skype:9225): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(skype:9225): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(skype:9225): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(skype:9225): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

```

Any idea of what has changed and why it is not working anymore?

Thanks

---

### Post by Younio on 2012-06-06
> **ItalOz said:**
> Hi

I have upgraded to 12.04
the solution proposed works for me in 11.04

now I have tried to apply the same (same hardware only distro upgraded to 12.04) simply varying the path
```
#!/bin/bash
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype
```

but now it doesn't see the webcam and says

Any idea of what has changed and why it is not working anymore?

Thanks

Hi,

It seems that the location of the library changed in 12.04.

so the right command would be:
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype
```

---

### Post by ItalOz on 2012-06-10
mmm
seemed to me that my path was correct,
I am not in front of my box at the moment but I'll check as soon as I get to there and update the post.

Thanks

---

### Post by platypuss72 on 2012-07-01
> **Younio said:**
> Hi,

It seems that the location of the library changed in 12.04.

so the right command would be:
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype
```

i am using 64 bit and having the same problems :(

i have tried both locations for the file and still get the same error and no camera when skype starts ???? 
when i go to cheese my camera turns on and works (logitech) little stutters from time to time .... 

LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.

---

### Post by platypuss72 on 2012-07-01
> **platypuss72 said:**
> i am using 64 bit and having the same problems :(

i have tried both locations for the file and still get the same error and no camera when skype starts ???? 
when i go to cheese my camera turns on and works (logitech) little stutters from time to time .... 

LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.

after some more hunting forums .... i have FIXED mine :D:D
i found it on the skype forum ...
i did :- 

sudo gedit /usr/local/bin/skype
#!/bin/bash
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype

so now i get camera working when start skype ;)

but is freezing up but think this is another issue ???

---

### Post by shafin on 2012-11-03
> **platypuss72 said:**
> after some more hunting forums .... i have FIXED mine :D:D
i found it on the skype forum ...
i did :- 

sudo gedit /usr/local/bin/skype
#!/bin/bash
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype

so now i get camera working when start skype ;)

but is freezing up but think this is another issue ???

Thanks a bunch, trying to get skype to work on my 64 bit install was driving me nuts.

---

