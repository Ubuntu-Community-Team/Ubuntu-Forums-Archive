---
title: "Radeon Xpress 200m and ATI drivers"
date: 2006-06-23
forum: Multimedia &amp; Video
---

### Post by jhr79 on 2006-06-23
After playing and trying everything I have found for making ATI drivers to work, I have to come to the conclusion that it's impossible to get those drivers to work 100% correctly with my laptop (HP ZV6066) ](*,) . Right now I have switched my laptop to run on UMA only mode from BIOS. Anything else (Sideport+UMA, Sideport only) will just give the black screen after a boot. With this setting the default packages available from Ubuntu repositories work out of the box and I get following results:

```
w0rm@w0rmhole:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

```
w0rm@w0rmhole:~$ glxgears -printfps
4312 frames in 5.0 seconds = 862.279 FPS
4161 frames in 5.0 seconds = 832.167 FPS
4165 frames in 5.0 seconds = 832.906 FPS
4163 frames in 5.0 seconds = 832.433 FPS
4163 frames in 5.0 seconds = 832.574 FPS
4164 frames in 5.0 seconds = 832.742 FPS
```

```
w0rm@w0rmhole:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
591 frames in 5.0 seconds = 118.200 FPS
586 frames in 5.0 seconds = 117.200 FPS
587 frames in 5.0 seconds = 117.400 FPS
625 frames in 5.0 seconds = 125.000 FPS
604 frames in 5.0 seconds = 120.800 FPS
```

Not great but far better than with the default driver and without DRI. On the negative side I'm losing 64MB of my main memory to achieve this :( 

To get to this I simply did:

```
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx

```

And changed the driver in xorg.conf to *fglrx*.

If someone has a working solution on how to get Sideport+UMA mode working, it would be great to know!!

Some of the threads etc. I have tried include (there were so many more that I can't even count them):

[http://www.ubuntuforums.org/showthread.php?t=197471](http://www.ubuntuforums.org/showthread.php?t=197471)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_new_driver](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_new_driver)

---

### Post by tommohawk on 2006-06-23
jhr79,

I would suggest you read the whole thread [http://www.ubuntuforums.org/showthread.php?t=197471](http://www.ubuntuforums.org/showthread.php?t=197471) because I have posted a guide within it which explains how to get this card working.  Look....
```

ken@ken-laptop:~$ glxgears -printfps
6236 frames in 5.0 seconds = 1247.093 FPS
6521 frames in 5.0 seconds = 1304.192 FPS
6522 frames in 5.0 seconds = 1304.241 FPS
ken@ken-laptop:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1225 frames in 5.0 seconds = 245.000 FPS
2513 frames in 5.0 seconds = 502.600 FPS
2514 frames in 5.0 seconds = 502.800 FPS
3611 frames in 5.0 seconds = 722.200 FPS
4888 frames in 5.0 seconds = 977.600 FPS
4908 frames in 5.0 seconds = 981.600 FPS
ken@ken-laptop:~$
ken@ken-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 2.0.5755 (8.24.8)

```
Your problem is the drivers you are using - 8.25.18 are no good for the 200M card.

---

### Post by jhr79 on 2006-06-23
[QUOTE=tommohawk]jhr79,

I would suggest you read the whole thread [http://www.ubuntuforums.org/showthread.php?t=197471](http://www.ubuntuforums.org/showthread.php?t=197471) because I have posted a guide within it which explains how to get this card working.  Look....
[/QUOTE]

Thanks for the quick reply tommohawk! Well, I have tried everything else on that thread except compiling kernel. Is that really needed? If it is, how do I do it with Ubuntu? Is there an easy way to get a preconfigutation or do I have to do it the hard way by configuring it by hand? 

I tried to play with the old ATI driver package and tried with both libGL.so.1.2 files there (there is one in folder arch and another one in folder x410). It doesn't matter which one I choose, right after copying libGL.so.1.2 from there to /usr/lib/ I get the awful mesa driver information with fglrxinfo. 

Any suggestions?

---

### Post by tommohawk on 2006-06-23
Right, you need to look at posts #33 and #35 of the thread that I gave you above.  This will explain everything you need to do in order to get hardware accelerated 3D on the 200M card.  You have been looking in the right areas you just need to do as I have advised on the other thread and it will work.

Simply replacing the libGL.so.1.2 file with the one from the old driver will not do it for you - you must follow each step as I have written.

One day I will write a proper HOWTO for the Xpress 200M but right now that other post and this advice is the best I can do.

I have even managed to get Xgl working - it is mind blowing - if Vista wants to make a mark then it is going to have to work very hard to beat Xgl - the effects are fantastic.

If you get stuck then post again and I will try to help.

---

### Post by jhr79 on 2006-06-24
Did you mean that I should recompile the kernel modules with this

> 5. Recompile the Kernel.

as noted on [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_new_driver]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_new_driver") or did you mean that I should recompile thw whole kernel? I have already tried those instructions too but maybe I go for it one more time after I have prepared backup image of my currect system.

---

### Post by tommohawk on 2006-06-24
jhr79, I know you have already tried it but you were using the 8.25.18 drivers and as I said before, that is the problem.  You need to use those instructions but replace 8.25.18 with 8.24.8.

The 8.24.8 drivers work with this card and the 8.25.18 drivers do not!

Follow those instructions and carry out the additional steps that I posted and it should all work.

Trust me - it worked on my laptop (HP DV8000) and still does.

---

### Post by jhr79 on 2006-06-24
[QUOTE=tommohawk]jhr79, I know you have already tried it but you were using the 8.25.18 drivers and as I said before, that is the problem.  You need to use those instructions but replace 8.25.18 with 8.24.8.

The 8.24.8 drivers work with this card and the 8.25.18 drivers do not!

Follow those instructions and carry out the additional steps that I posted and it should all work.

Trust me - it worked on my laptop (HP DV8000) and still does.[/QUOTE]

In the matter of fact, I used that driver version when I tried but I will try once more. Hopefully I missed something critical last time or my system was already lost after all those tries :neutral: 

I will inform how it went when I'm done!!

---

### Post by jhr79 on 2006-06-25
WOW!! It's working :D Check this out:

```
w0rm@w0rmhole:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 2.0.5755 (8.24.8)

w0rm@w0rmhole:~$ glxgears -printfps
8129 frames in 5.0 seconds = 1625.619 FPS
8315 frames in 5.0 seconds = 1662.935 FPS
8316 frames in 5.0 seconds = 1663.050 FPS
8314 frames in 5.0 seconds = 1662.645 FPS
8286 frames in 5.0 seconds = 1657.167 FPS
w0rm@w0rmhole:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1198 frames in 5.0 seconds = 239.600 FPS
1168 frames in 5.0 seconds = 233.600 FPS
1160 frames in 5.0 seconds = 232.000 FPS
1164 frames in 5.0 seconds = 232.800 FPS
1114 frames in 5.0 seconds = 222.800 FPS
```

Double scores now when it's running on Sideport+UMA mode. I did everything exactly as in [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_new_driver](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_new_driver) except using older driver version as tommohawk has advised. Before the installation procedure I have installed fglrx drivers from Ubuntu repositories so this doesn't even need a clean install. Prior install I however changed my kernel version to k7. I did the installation using recovery mode in console and first just uninstalled Ubuntu packages for fglrx.

Someone definitely needs to write a wiki article about this because so many people are having problems with this.

Tommohawk: Thanks for the instructions and support. Without you I would't tried this once more :neutral:

---

### Post by jhr79 on 2006-06-25
Ok, played a little bit more with this. Driver seems to need that the Sideport+UMA setting is on so that there is 128MB+128MB memory. With anything else I get only black screen after boot. So I think it's time to get some more memory :) 

Another thing is that I had to lock the version numbers of fglrx packages. Without that update manager is trying to update the driver to the newer, non-working version. I also plan to lock my kernel version because if I had understood right, the install procedure needs to be done again after every kernel update. Is this correct?

Besides those things, it's running smoothly.

---

### Post by tommohawk on 2006-06-25
[QUOTE=jhr79]Ok, played a little bit more with this. Driver seems to need that the Sideport+UMA setting is on so that there is 128MB+128MB memory. With anything else I get only black screen after boot. So I think it's time to get some more memory :) 

Another thing is that I had to lock the version numbers of fglrx packages. Without that update manager is trying to update the driver to the newer, non-working version. I also plan to lock my kernel version because if I had understood right, the install procedure needs to be done again after every kernel update. Is this correct?

Besides those things, it's running smoothly.[/QUOTE]

Excellent - happy that you got it working - I know how frustrating it is.  You have a point about locking the packages in synaptic - I forgot to put that on the guide!  Don't think you need to worry about the kernel - you should just be able to run through the same process again to get it working if there is a kernel update.  Hopefully, ATI will have got their act together and released a new driver that works by the time the next kernel update comes out.

Now you have to try to get Xgl working - look here....  [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

---

### Post by jhr79 on 2006-06-25
[QUOTE=tommohawk]Now you have to try to get Xgl working - look here....  [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)[/QUOTE]

I think I leave that to others ;) I'm happy now when I'm able to play games when I have some time and to look those 3D-screensavers eating my CPU time :D 

Maybe I even start to write a wiki article about this...

---

### Post by Moldy Jello on 2006-07-02
hey i followed this, i mean the post that you linked to tommohawk, the thing is, i cannot find the /xorg/ folder, thus i cannot get the /xorg/fglrx file to replace, so could you explain or tell me what is going on or something, but i was looking in another post and they were sayin the steps you took just in a different folder, is that what you mean

---

### Post by jhr79 on 2006-07-03
[QUOTE=Moldy Jello]hey i followed this, i mean the post that you linked to tommohawk, the thing is, i cannot find the /xorg/ folder, thus i cannot get the /xorg/fglrx file to replace, so could you explain or tell me what is going on or something, but i was looking in another post and they were sayin the steps you took just in a different folder, is that what you mean[/QUOTE]

Forget previous, if you read it. Did you mean the xgl installation or 200m driver installation?

EDIT: Deleted previous message.

---

### Post by Moldy Jello on 2006-07-03
nope, in the regular driver install, step 8

1. Clean Dapper Install.
2. Upgrade and update everything.
3. Download the 8.24.8 drivers from the ATI website.
4. Build the ubuntu packages from these drivers.
5. Recompile the Kernel.
6. Extract the libGL.so.1.2 driver from the ATI package you downloaded in step 3.
7. Replace the libGL.so.1.2 file in /usr/lib
8. Remove and *mesa* files from /xorg/fglrx and place the libGL.so.1.2 file in that directory also.
9. Configure your xorg.conf file in accordance with previous posts in this thread.
10. Blacklist the fglrx driver as detailed above.
11. Reboot and all should work.

---

### Post by tommohawk on 2006-07-03
Step 8 - Sorry - you need to replace the libGL.so.1.2 file in the /usr/lib/fglrx folder.

Don't know why it is written that way??

---

### Post by jhr79 on 2006-07-04
[QUOTE=Moldy Jello]nope, in the regular driver install, step 8

1. Clean Dapper Install.
2. Upgrade and update everything.
3. Download the 8.24.8 drivers from the ATI website.
4. Build the ubuntu packages from these drivers.
5. Recompile the Kernel.
6. Extract the libGL.so.1.2 driver from the ATI package you downloaded in step 3.
7. Replace the libGL.so.1.2 file in /usr/lib
8. Remove and *mesa* files from /xorg/fglrx and place the libGL.so.1.2 file in that directory also.
9. Configure your xorg.conf file in accordance with previous posts in this thread.
10. Blacklist the fglrx driver as detailed above.
11. Reboot and all should work.[/QUOTE]

I would suggest that you try this: [Installing the new driver]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually"). This is the way I did it and it worked flawlessy. And there is no need for that part I guess...

---

### Post by tommohawk on 2006-07-04
>     *
          o ATI Driver 8.26.18, does not work with the Radeon Express 200M. Some HP/Compaq laptops only have working 3D support with ONLY UMA video memory( Sideport+UMA won't work ). This is due to a 1 year old flaw in the ATI driver. If you want to use your onboard/Sideport memory, you can only get 2D support by adding [ Option "no_dri" "yes"] to the fglrx driver section of /etc/X11/xorg.conf 


The above is from the Ubuntu Wiki - _you have all been warned_.

Use the 8.24.8 drivers - we know they work properly.

---

### Post by Moldy Jello on 2006-07-04
thanks guys, it seems as if i have it working sometimes, but then i try running the solar wins screensaver and it is either real choppy and slow or it is a bunch of dots rather than being strings and overall just does not work, i am gonna try putting xgl on the way taht i have it now and then if that does not work i will try it all from the beginning of the moddified way that you have posted here

---

### Post by d-E-a-D on 2006-07-05
Ok, after more than 10 formats and thousand tries to make it work, i get 8.26 drivers working on my hp pavilion dv5172 with ati radeon Xpress 200m.
***_I'm using UMA+SIDEPORT 128Mb._***
It gives me the right fglrxinfo:

OpenGL vendor string: ATI technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5879 (***_8.26.18_***)

Now my issue is that glxgears and fglx_gears hangs when i try to run it _***but things like screensaver and games do it great on OpenGL and fps.***_ but it is unstable. sometimes crash, others not.

The worst issue is that it seems that it doesn't refresh the image, everything just is it seems that the windows are over ones of the others, I see the images overlapped, icones disappears when I open something over them and closes.
To read console i have to underline the mouse over the letters. but if i maximize the console i can read it all great.

Now the steps.
Fresh Install of Ubuntu 6.06
update
distro-upgrade
restart
follow this thread but ***_WITH 8.26.18 DRIVER DOWNLOADED FROM ATI_***:
[http://www.ubuntuforums.org/showthread.php?t=199421&page=2&highlight=ati+8.24+200m]("http://www.ubuntuforums.org/showthread.php?t=199421&page=2&highlight=ati+8.24+200m")
restart

For now i can't go further... does anyone goes further than this with 8.26.18 drivers?

NOTE: 8.24.18 drivers worked for me with the thread i said. but i can't get XGL and COMPIZ working. And with fglx_glxgears i just see one piece rolling, the others don't appear like in glxgears.

If someone have this 200M card working well and with XGL and COMPIZ please give us a HOW-TO step by step !!!!

SORRY MY BAD ENGLISH.

Cumps

---

### Post by ZraS87 on 2008-05-21
Hello, my name is zach I am new to linux I own a ml3109 notebook from gateway .....and it has a ati radeon express chip in it ....unfortunately i have tried know how to do so far this includes:

using the normal restricted drivers when you first start ubuntu up....
then i got envy for my ubuntu ....but this didnt help either .....

so is there anyway ....to be able to fix this problem yet???
and if there is ......could some body teach me how to do it ...so I know in the future????


-thank you!!!!:confused:

---

