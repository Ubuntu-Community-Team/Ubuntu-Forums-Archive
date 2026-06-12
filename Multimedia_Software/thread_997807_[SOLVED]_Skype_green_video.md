---
title: "[SOLVED] Skype green video"
date: 2008-11-30
forum: Multimedia Software
---

### Post by lian1238 on 2008-11-30
Hi,

My skype video used to work before. Before Ibex and even after installing Ibex. But now, it's just a green video (from my webcam). In cheese, everything works fine.

This is the model of webcam:
ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam

There appears to be a workaround. The command is:
```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```But I get the following error:
```
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

```

---

### Post by antiplex on 2008-11-30
i have a completely different webcam model (logitech) but i also get a green and interference-like-looking picture when using it through skype while with cheese everything works fine.

after trying around a little i found this [thread on skype-forums]("http://forum.skype.com/index.php?showtopic=102838") quite helpful; its about using a user-space webcam driver calles 'gstfakevideo'.
this may be a solution rather for the little more experienced user and not really beginners, so be careful and use on your own risk!

it works like a charm in my case although with this, everything a bit more complicated than just starting skype. but if you know how to write simple shell-scripts, it shouldn't be a big hazzle...

oh, note that the green-image was in my case there from the beginning!

regards, anti

---

### Post by justin212k on 2008-12-02
Hi, my webcam (creative PD1110, 041e:401c Creative Technology, Ltd WebCam NX [PD1110]) also works fine in cheese (and xawtv), but shows a green staticky screen in skype.  looks like your v4l1 library wasn't in lib32:

> **lian1238 said:**
> 

The command is:
```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```But I get the following error:
```
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

```

mine wasn't either.  Try ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
That found the library, but didn't fix the green screen problem - I'm still working on that.  Good luck.

---

### Post by davidmaxwaterman on 2008-12-07
I found [this]("http://kaeru.inigo-tech.com/blog/archive/2008/11/04/fixing-green-skype-video-for-logitech-quickcam-pro-for-notebooks").

Worked for me, but I had to *remove* the LD_LIBRARY_PATH thing mentioned above (which I had been trying) - else it still didn't work.

HTH.

---

### Post by lian1238 on 2008-12-07
**davidmaxwaterman**, thanks for the link. Glad it worked for you. But in my config.xml file, I don't have a Video section. Did you add it or was it there. Could you tell me its relative position? (Above/below what)

I tried putting it below SoundDevice, then I restarted skype. The testing showed only green. When I was in a call, skype crashed after a few seconds, and video was still green.

Edit: I turned compiz off already.

---

### Post by davidmaxwaterman on 2008-12-07
> **lian1238 said:**
> **davidmaxwaterman**, thanks for the link. Glad it worked for you. But in my config.xml file, I don't have a Video section. Did you add it or was it there.

It was already there.

>  Could you tell me its relative position? (Above/below what)

I don't have the computer I was using to hand right now, but on this computer it's right under a StatsSender block. It is two indendation levels in, and <Lib> (should be near the top) is it's parent.

> 
I tried putting it below SoundDevice, then I restarted skype. The testing showed only green. When I was in a call, skype crashed after a few seconds, and video was still green.

Edit: I turned compiz off already.

Well, the only other thing I did was to edit the script that runs skype. I'm not sure if this is a script I wrote myself, but for me :
```

$ file `which skype`
/usr/bin/skype: POSIX shell script text executable
$ sudo gvim !$
sudo gvim `which skype`
$ cat !$
cat `which skype`
#!/bin/sh

#LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype.real "$@"
/usr/bin/skype.real "$@"


```

IE, I basically removed the bit that sets LD_PRELOAD.

However, on this machine, it basically makes no difference. I'm not sure if it made a difference on my other computer or not (I think it did) - actually, I'm not sure if it was removing the LD_PRELOAD, or the config.xml thing; perhaps both.

Sorry I can't be more help.

BTW, I am using the Logitech Quickcam for Notebooks Pro, as is the guy who wrote the page above, I think.

---

### Post by genseek on 2008-12-10
you get this error most likely because you are using 32bit skype in 64bit ubuntu, in that case you just need to use the following path to the library:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so

---

### Post by lightchild on 2008-12-10
hi everybody!


i have the same problem with green stripes in skype in my kubuntu... :(

but the link you provided does not function now as i see... actually it writes: "Rethinking Content
Reorganising personal website content" and nothing can be found... 

please help, what can i do with skype video? 

thank you in advance!

---

### Post by pjalegria on 2008-12-10
+1...

---

### Post by davidmaxwaterman on 2008-12-10
> **genseek said:**
> you get this error most likely because you are using 32bit skype in 64bit ubuntu, in that case you just need to use the following path to the library:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so

I"m not using 64bit ubuntu...

Max.

---

### Post by iD Hype on 2008-12-14
Hi all. FWIW justin212k's suggestion ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
``` worked for my logitech quickcam problems. I did not have to install any packages as v4lcompat was already there. Didn't wanna go the gstfakevideo route cause it kills the internal mic.

Registered to just thank the post.

---

### Post by aaaaalex on 2008-12-14
Thanks for the awesome workaround -  but i found it a bit annoying to have a terminal open to run skype.

I made two executable scripts in ~/bin/skype. 

ScreenSkype.sh

```
#!/bin/sh
screen -d -m ~/bin/skype/SkypeLauncher.sh
```

SkypeLauncher.sh

```
#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
exit 0
```

Then i changed the Skype Lancher in the Main Menu to point to ScreenSkype.sh.

Now I can run Skype with working web cam and without having to have a terminal open.

---

### Post by lian1238 on 2008-12-14
My Video is working now! With the command
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```Don't know why it wasn't before, but now it does!

My webcam is MDTech..
```
ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
```*Edit:*
**aaaaalex**, was the extra script necessary? You might have your reasons, but I prefer this method:
Rename (move) /usr/bin/skype to /usr/bin/skype.real
Then create a script at:
/usr/bin/skype
```

#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real

```Then give /usr/bin/skype executable permission. :) My links to skype aren't broken, and there's no need to keep a terminal open just for skype.
Best of all, my video works! (at least, the video test does.)

*****Reminder:** Be sure to call "skype.real" (NOT skype) to the command in the script. Calling skype in the script will cause your system to run out of memory (due to recursive calls). I made this mistake the first time. I did Ctrl+Alt+Backspace just in time. Thank goodness for the 4GB. There was a long blank screen, and then I had to manually start X again.

---

### Post by robin.nightingale on 2008-12-20
Hello everyone,
i just changed from osx to ubuntu and everything looks nice but i have the same issue with skype. I just get a green static screen.
In Cheese everything works fine. I tryied all your workaround suggestions
but nothing seems to work for me.
When i start skype in a terminal i get the following error message

> 
nightingale@xxy:~$ skype
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
libv4l2: error setting pixformat: Invalid argument
Starting the process...


When i start the Cam i see the following error message


Skype Xv: Xv ports available: 17
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 79
libv4l2: error dequeuing buf: Invalid argument
 

I dont know what i did wrong and iam not experienced enough to understand what that means.
Does anybody have an idea, what could help ?

Thanks a lot

---

### Post by dof on 2009-01-11
I'm using similar method (made a skype file in  /usr/local/bin etc...)
Now my webcam works but i can't see other's webcam, it's some random stuff there. Are these things related?

---

### Post by robin.nightingale on 2009-01-11
The Video is working now.

I removed the Skype Version that i installed via apt (the medibuntu Version)
and  i installed a newer Version from the skype Homepage.
 
[http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)

Afterwards things worked fine without any Patch or Workaround.

---

### Post by Arrgoss on 2009-02-14
Hi there,

I've been following the post, since I have the same problem with my logitech cam in skype. I tried the command in both versions
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
and
```
LD_PRELOAD=/usr/lib/lib32/libv4l/v4l1compat.so skype
```
but always get the same error
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```
What am I doing wrong?
FYI I'm using 64bits...

---

### Post by teardel on 2009-03-13
can't seem to get aaaalex or lian1238 to work for me but I can get my webcam to work in a terminal with that command line

---

### Post by lian1238 on 2009-03-14
> **Arrgoss said:**
> Hi there,

I've been following the post, since I have the same problem with my logitech cam in skype. I tried the command in both versions
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```and
```
LD_PRELOAD=/usr/lib/lib32/libv4l/v4l1compat.so skype
```but always get the same error
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```What am I doing wrong?
FYI I'm using 64bits...

Not sure about 64bits. Could you try replacing lib32 with lib64 in the command?

---

### Post by zhamrock on 2009-03-17
You need to make sure you install the 32 bit(lib32v4l) version as well. Then this will work.

```


LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype


```

---

### Post by Denestria on 2009-03-30
> **Arrgoss said:**
> 
I've been following the post, since I have the same problem with my logitech cam in skype. I tried the command in both versions cannot be preloaded: ignored. What am I doing wrong?  FYI I'm using 64bits...

The library I needed to fix my green video was libv4l-0 not lib32v4l so try installing that first then try the LD_PRELOAD again.

---

### Post by brianpeiris on 2009-04-08
Thanks,

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

worked for me on Intrepid (8.10) with my Logitech Quickcam Connect

---

### Post by gregbzh on 2009-04-13
Found this on another thread.  Works for me. Cheers.


> **sisco311 said:**
> try, the command without sudo:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

if it works create a script in /usr/bin
```
gksu gedit /usr/bin/skype2
```


and make it executable:
```
sudo chmod +x /usr/bin/skype2
```

use the skype2 command in the launcher.

---

### Post by Aviendha09 on 2009-04-27
Thx! it works great! I have a question: any idea how to adjust the picture?

---> Use XawTV

---

### Post by studiodude on 2009-06-21
this totally worked and I worked out how to complete the operation using a great guide here [http://linux.byexamples.com/archives/95/writting-executable-script/]("http://linux.byexamples.com/archives/95/writting-executable-script/") and the instructions from post #12 -  thanks to aaaalex and I hope he wont mind me pinching a bit of his post and simplifying it for complete newbies like me.

The following steps worked totally for me. I didn't like skype running with a terminal open so I followed instructions from that post - but here are added very, very basic steps to do what it said. It took a bit of trial and error and I am sure there is an alternative way....this is just how I managed it in the end...it worked for me and gave me another insight into how linux works.


I made two executable scripts in usr/bin/ 

ScreenSkype.sh and SkypeLauncher.sh

to do this I opened a terminal and typed 

```
cd /usr/bin
```

then

```
sudo gedit /usr/bin/ScreenSkype.sh
```

then i pasted into the blank page that came up :

```
#!/bin/sh
screen -d -m usr/bin/skype/SkypeLauncher.sh
```
 
and clicked save and closed the window.

then to make it executable

```
sudo chmod+x ScreenSkype.sh
```

then I repeated the process for the second script


```
sudo gedit SkypeLauncher.sh
```

paste in the following code


```
#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
exit 0
```

Click Save and exit gedit window.

then make that file executable

```
sudo chmod+x SkypeLauncher.sh
```



Then i changed the Skype Launcher in the Main Menu to point to ScreenSkype.sh by going into Applications>Internet I right clicked in the skype icon and clicked "Add this Launcher to panel"

When the Skype icon appeared in the panel next to the firefox icon, i right clicked it and clicked "properties" 

in the box COMMAND i typed "usr/bin/SkypeLauncher.sh" (no quotes) in place of what was there

now when i click this icon Skype opens with the preloaded bit needed for the webcam to work properly.

Hope this helps - hope I didnt make any mistakes in the method I used, like I say it worked for me but as a noob, perhaps I have done it long handed without knowing an easier way - if there is any other easier way of doing it or if I am making any glaring mistakes I would love to know.

i am using 9.04 for the record and was getting a scrambled video signal in skype.

Hope this helps someone.

---

### Post by bachor on 2009-07-07
> **studiodude said:**
> 

I made two executable scripts in usr/bin/ 

ScreenSkype.sh and SkypeLauncher.sh

to do this I opened a terminal and typed 

```
cd /usr/bin
```then

```
sudo gedit /usr/bin/ScreenSkype.sh
```then i pasted into the blank page that came up :

```
#!/bin/sh
screen -d -m usr/bin/skype/SkypeLauncher.sh
```and clicked save and closed the window.

then to make it executable

```
sudo chmod+x ScreenSkype.sh
```then I repeated the process for the second script


```
sudo gedit SkypeLauncher.sh
```paste in the following code


```
#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
exit 0
```Click Save and exit gedit window.

then make that file executable

```
sudo chmod+x SkypeLauncher.sh
```Then i changed the Skype Launcher in the Main Menu to point to ScreenSkype.sh by going into Applications>Internet I right clicked in the skype icon and clicked "Add this Launcher to panel"

When the Skype icon appeared in the panel next to the firefox icon, i right clicked it and clicked "properties" 

in the box COMMAND i typed "usr/bin/SkypeLauncher.sh" (no quotes) in place of what was there

now when i click this icon Skype opens with the preloaded bit needed for the webcam to work properly.

Hope this helps - hope I didnt make any mistakes in the method I used, like I say it worked for me but as a noob, perhaps I have done it long handed without knowing an easier way - if there is any other easier way of doing it or if I am making any glaring mistakes I would love to know.

i am using 9.04 for the record and was getting a scrambled video signal in skype.

Hope this helps someone.


thanx 4 great guide,did everything [except changed chmod+x to chmod +x] only last part with properties:

[SIZE=2]in the box COMMAND i typed "usr/bin/SkypeLauncher.sh" (no quotes) in place of what was there
[/SIZE]
couldn't do running Kubuntu Jaunty because there's no "properties" right click on Skype.

 How do I do it?

sorry 4 newbie question,usually dont post and fixured everything but this time couldn't

---

### Post by danlembek on 2009-07-16
noob here

I'm running Jaunty. I tried instructions #25 to fix the 'green static' in Skype video capture. 

And I don't understand how moving Skype to top panel helps solve the problem. Regardless, it failed with the response: 

Failed to execute child process "usr/bin/SkypeLauncher.sh" (No such file or directory)

Any understandable instructions on getting my Creative Instant to work with Skype?

---

### Post by lian1238 on 2009-07-16
First off, you need to find out which command to launch skype works for you. 
Then you need to put that command (that works) into the launcher script.

> **danlembek said:**
> 
And I don't understand how moving Skype to top panel helps solve the problem. 

Moving to the top panel creates a new launcher. You could also just right-click on your menu, "Edit Menus" and change the command there. It's just preference.

I chose the method of moving skype, and putting the script in skype's place (with the name "skype") so I don't need to create a new launcher.

> **danlembek said:**
> 
Regardless, it failed with the response: 
Failed to execute child process "usr/bin/SkypeLauncher.sh" (No such file or directory)

You left out the leading slash in ```
/usr/bin/SkypeLauncher.sh
```

---

### Post by danlembek on 2009-07-17
SICK! It Works.

Thank you kindly.

---

### Post by mikejgrantham on 2009-07-18
Worked for me too

Thanks for your work :)


Michael

---

### Post by bachor on 2009-07-18
> **bachor said:**
> thanx 4 great guide,did everything [except changed chmod+x to chmod +x] only last part with properties:

[SIZE=2]in the box COMMAND i typed "usr/bin/SkypeLauncher.sh" (no quotes) in place of what was there
[/SIZE]
couldn't do running Kubuntu Jaunty because there's no "properties" right click on Skype.

 How do I do it?

sorry 4 newbie question,usually dont post and fixured everything but this time couldn't

found it,right click on KDE menu>menu editor  and so on :)

video works,thanks a lot all of you ):P

---

### Post by kimw08 on 2009-07-25
> **bachor said:**
> thanx 4 great guide,did everything [except changed chmod+x to chmod +x] only last part with properties:

[SIZE=2]in the box COMMAND i typed "usr/bin/SkypeLauncher.sh" (no quotes) in place of what was there
[/SIZE]
couldn't do running Kubuntu Jaunty because there's no "properties" right click on Skype.

 How do I do it?

sorry 4 newbie question,usually dont post and fixured everything but this time couldn't

This worked perfectly!!! Total noob here, really appreciated the straightforward directions.  I had to make the edits to chmod +x too, and instead of typing the direction into the COMMAND line, I had to browse to it. But otherwise PERFECT.  :popcorn:

---

### Post by Mdyter on 2009-07-31
Worked! Great)
Thank you!

p.s. mic is working at someone?
my mic is not working, is something possible to do with that?

---

### Post by mloskot on 2009-10-18
> **genseek said:**
> you get this error most likely because you are using 32bit skype in 64bit ubuntu, in that case you just need to use the following path to the library:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so

I can confirm this solution works for me on Ubuntu 9.10 (64 bit) with Notebook Webcam Canyon CN-WCAMN1

Cheers,

---

### Post by jptoole on 2009-10-24
I am using Ubuntu 8.10 64-bit and found I had to install the 32-bit v4l drivers before skype would work.  I was trying the following command:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```and was getting the following error:

```
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```To remedy this, I had to install the following 32-bit package:

```
apt-get install lib32v4l-0
```Then change the LD_PRELOAD line to the following:

```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```And it works fine now!

I hope this helps others, since I noticed there were MANY people with the above error, but were unable to find the solution.

---

### Post by habib_seif on 2009-10-31
The script 

> #!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

solves the problem in Intrepid but the problem still exists in Karmic. The screen isn't green completely but quality is very poor...

Any suggestion?

---

### Post by lian1238 on 2009-10-31
That sounds like a different kind of problem.. you should start a new thread.

---

### Post by habib_seif on 2009-10-31
Yeah, I found a thread which discusses the problem in Karmic: [http://ubuntuforums.org/showthread.php?t=1306368](http://ubuntuforums.org/showthread.php?t=1306368)

Is it OK?

---

### Post by boom2k1 on 2009-11-01
I am running Ubuntu 9.10.

I came here because I was looking for a fix for the green video in Skype.
I have a Logitech notebook webcam.


Problem: Cheese works perfectly, but video in skype does not work and shows a flickering green video. I was using the 64-bit version I downloaded from [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/).

I don't know what did it, but I followed the direction here for Ubuntu:
[http://hansdegoede.livejournal.com/7622.html](http://hansdegoede.livejournal.com/7622.html)

and download lib4l from 
```
 http://apps.freshmeat.net/projects/libv4l 
```

```
Ubuntu Multilib instructions:
-----------------------------------
tar xvfz libv4l-<version>.tar.gz
cd libv4l-<version>
make PREFIX=/usr
sudo make install PREFIX=/usr

If you also want to use 32 bit apps (such as skype), you
will need to have the 32 bit libc headers installed, on Ubuntu
this can be done like this:
sudo apt-get install libc6-dev-i386
Then do:
make clean
make PREFIX=/usr CFLAGS=-m32 LDFLAGS=-m32 LIBDIR=/usr/lib32
sudo make install PREFIX=/usr LIBDIR=/usr/lib32 
```

and tested it again with Skype. It still didn't work. However, I then tested the skype I obtained from medibuntu.
So I first removed the skype I installed using the skype.com deb file
Terminal: sudo apt-get remove skype

After that, I installed the skype from the medibuntu repository.


Then it works!

What I don't know is whether hansdegoede fixed it or whether the skype from medibuntu fixed it. All I know is now my skype webcam is fine!

Hope this helps!

---

### Post by lian1238 on 2009-11-01
> **habib_seif said:**
> The script 


solves the problem in Intrepid but the problem still exists in Karmic. The screen isn't green completely but quality is very poor...

Any suggestion?

How is the quality with cheese? or VLC?

---

### Post by habib_seif on 2009-11-01
The quality of video in cheese is OK...

By the way, the instructions for installing v4l and skype from medibuntu didn't solve the problem. Any other idea?

Cheers,
Habib

---

### Post by lasleym on 2009-11-13
I also tried the following steps.  So far the medibuntu solution with 'skype-common' and 'skype-static' is working.  The menu even changes to one visible (albeit not the same as my theme) with my Dust theme.

> **boom2k1 said:**
> I am running Ubuntu 9.10.

I came here because I was looking for a fix for the green video in Skype.
I have a Logitech notebook webcam.


Problem: Cheese works perfectly, but video in skype does not work and shows a flickering green video. I was using the 64-bit version I downloaded from [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/).

I don't know what did it, but I followed the direction here for Ubuntu:
[http://hansdegoede.livejournal.com/7622.html](http://hansdegoede.livejournal.com/7622.html)

and download lib4l from 
```
 http://apps.freshmeat.net/projects/libv4l 
``````
Ubuntu Multilib instructions:
-----------------------------------
tar xvfz libv4l-<version>.tar.gz
cd libv4l-<version>
make PREFIX=/usr
sudo make install PREFIX=/usr

If you also want to use 32 bit apps (such as skype), you
will need to have the 32 bit libc headers installed, on Ubuntu
this can be done like this:
sudo apt-get install libc6-dev-i386
Then do:
make clean
make PREFIX=/usr CFLAGS=-m32 LDFLAGS=-m32 LIBDIR=/usr/lib32
sudo make install PREFIX=/usr LIBDIR=/usr/lib32 
```and tested it again with Skype. It still didn't work. However, I then tested the skype I obtained from medibuntu.
So I first removed the skype I installed using the skype.com deb file
Terminal: sudo apt-get remove skype

After that, I installed the skype from the medibuntu repository.


Then it works!

What I don't know is whether hansdegoede fixed it or whether the skype from medibuntu fixed it. All I know is now my skype webcam is fine!

Hope this helps!

---

### Post by ram130 on 2009-11-13
When will skype do a fix for this??

The  solution worked for me too! thanks!  :popcorn:

Karmic 32bit, skype 2.1

---

### Post by six-geek on 2009-11-26
Thanks!
After removing the installed skype version from skype.com and reinstalling skype from the medibunti source my problem is solved. Cheers!

---

### Post by fonkamex on 2009-11-28
Hi everybody,

I had the same problem with my creative NX ultra webcam, but now the problem is resolved.

I found the solution on skype forums here:

[http://forum.skype.com/index.php?showtopic=252681&st=0](http://forum.skype.com/index.php?showtopic=252681&st=0)

good luck!

---

### Post by zhanglini on 2009-12-18
I did not write any sh script, all I did was enter the following command:
> sudo nice -n -15 sudo -u *username*  LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
into main menu>internet>skype>launcher.
It worked for me

---

### Post by phDaemon on 2010-01-14
> **studiodude said:**
> this totally worked and I worked out how to complete the operation using a great guide here [http://linux.byexamples.com/archives/95/writting-executable-script/](http://linux.byexamples.com/archives/95/writting-executable-script/) and the instructions from post #12 -  thanks to aaaalex and I hope he wont mind me pinching a bit of his post and simplifying it for complete newbies like me.

The following steps worked totally for me. I didn't like skype running with a terminal open so I followed instructions from that post - but here are added very, very basic steps to do what it said. It took a bit of trial and error and I am sure there is an alternative way....this is just how I managed it in the end...it worked for me and gave me another insight into how linux works.


I made two executable scripts in usr/bin/ 

ScreenSkype.sh and SkypeLauncher.sh

to do this I opened a terminal and typed 

```
cd /usr/bin
```then

```
sudo gedit /usr/bin/ScreenSkype.sh
```then i pasted into the blank page that came up :

```
#!/bin/sh
screen -d -m usr/bin/skype/SkypeLauncher.sh
```and clicked save and closed the window.

then to make it executable

```
sudo chmod+x ScreenSkype.sh
```then I repeated the process for the second script


```
sudo gedit SkypeLauncher.sh
```paste in the following code


```
#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
exit 0
```Click Save and exit gedit window.

then make that file executable

```
sudo chmod+x SkypeLauncher.sh
```Then i changed the Skype Launcher in the Main Menu to point to ScreenSkype.sh by going into Applications>Internet I right clicked in the skype icon and clicked "Add this Launcher to panel"

When the Skype icon appeared in the panel next to the firefox icon, i right clicked it and clicked "properties" 

in the box COMMAND i typed "usr/bin/SkypeLauncher.sh" (no quotes) in place of what was there

now when i click this icon Skype opens with the preloaded bit needed for the webcam to work properly.

Hope this helps - hope I didnt make any mistakes in the method I used, like I say it worked for me but as a noob, perhaps I have done it long handed without knowing an easier way - if there is any other easier way of doing it or if I am making any glaring mistakes I would love to know.

i am using 9.04 for the record and was getting a scrambled video signal in skype.

Hope this helps someone.


If your using 9.10 64bit, i found the above fix plus the one from [This Site]("http://blog.export.be/2009/07/fixing-your-webcam-in-ubuntu-jaunty/") Work.
Also should be noted that im using the deb from the skype site itself, as my medibuntu repo is broken for some reason :S
"skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb"


Substitute: 

```
#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
exit 0
```With
```
#!/bin/sh
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype &
exit 0
```Should work now :)

PS: Sorry for reviving an old thread, but its the only one i found.

---

### Post by alex_time on 2010-03-15
> **genseek said:**
> you get this error most likely because you are using 32bit skype in 64bit ubuntu, in that case you just need to use the following path to the library:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so

I have a 64 bit Karmic and I have installed the Skype 64 bit for Intrepid, I had too the following error 

```
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```

running 

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```


but your solution to use the 32 bit library worked...strange...I have a 64 bit Karmic with 64 bit Skype and I have to use 32 bit library?!?!?!

---

### Post by avongil on 2010-04-18
Thank You. Solved my white video problem in 10.04!

---

### Post by peakpc on 2010-04-25
Thanks to everyone for helping me solve my video upside down only in skype problem I used the 64bit line "LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype" and  gregbzhes Quote:
Originally Posted by sisco311 View Post
try, the command without sudo:
Code:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

if it works create a script in /usr/bin
Code:

gksu gedit /usr/bin/skype2


and make it executable:
Code:

sudo chmod +x /usr/bin/skype2

use the skype2 command in the launcher.

it works great on 10.04.

---

### Post by J.G. on 2012-02-10
Try this.  Nothing else worked for me here on this 10.10 64 bit machine.
sudo aptitude install libpt-plugins-v4l2 v4l2ucp subversion libsdl1.2-dev
Then install skype from the ubuntu software centre
:popcorn:

---

### Post by adcpdk on 2012-02-26
> **davidmaxwaterman said:**
>  IF YOU R using 64bit ubuntu...

Max.

 	 		 			 				1. sudo mv /usr/bin/skype /usr/bin/oldskype
2. create file on your desktop "skype"
3. open it and type
 
#!/bin/bash

LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/oldskype

4.  Save it  and close
5.  cd Desktop
6.  chmod +x skype
7.  sudo cp skype /usr/bin
AND START YOUR SKYPE AS USUAL! Have fun!
p.s. you can delete file skype from your desktop

---

