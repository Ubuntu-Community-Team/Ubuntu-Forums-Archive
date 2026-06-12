---
title: "Can't start Blender in Ubuntu 17.04"
date: 2017-04-28
forum: Multimedia Software
---

### Post by joedkoop on 2017-04-28
Hey everybody!
I won't call myself a noob at ubuntu or its terminal, but I'm not an Einstein either... Here's my problem:

I downloaded Blender from their website, extracted the tar.bz2 file, and ran:
```
[FONT=courier new]user@comp:~$ ./Downloads/blender-2.78c-linux-glibc219-x86_64/blender[/FONT]
```
But it returned:
```
[FONT=courier new]Error! Blender requires OpenGL 2.1 to run. Try updating your drivers.[/FONT]
```

So I tried to install it:
```
[FONT=courier new]user@comp:~$ sudo apt-get install opengl2.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libtaoframework-opengl2.1-cil' for regex 'opengl2.1'
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

user@comp:~$ sudo apt-get install libtaoframework-opengl2.1-cil
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libtaoframework-opengl2.1-cil is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  libtaoframework-opengl3.0-cil libtaoframework-opengl-cil-dev
E: Package 'libtaoframework-opengl2.1-cil' has no installation candidate

user@comp:~$ sudo apt-get install libtaoframework-opengl3.0-cil libtaoframework-opengl-cil-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libtaoframework-opengl-cil-dev is already the newest version (2.1.svn20090801-14).
libtaoframework-opengl3.0-cil is already the newest version (2.1.svn20090801-14).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT]
```

But I still didn't work.
```
[FONT=courier new]Error! Blender requires OpenGL 2.1 to run. Try updating your drivers.[/FONT]
```

Here are some specs:
Processor: Intel® Core&#8482;2 Duo CPU E6550 @ 2.33GHz × 2
     Graphics: Intel® Q35
     Ram: 3.4 GiB
     OS type: 64-bit
Please don't criticise me.

So, any ideas? Thanks!

---

### Post by #&amp;thj^% on 2017-04-28
The same version is in the universe Repos....unless I'm missing something.
```
apt policy blender
blender:
  Installed: 2.78.a+dfsg0-4
  Candidate: 2.78.a+dfsg0-4
  Version table:
 *** 2.78.a+dfsg0-4 500
        500 http://us.archive.ubuntu.com/ubuntu zesty/universe amd64 Packages
        100 /var/lib/dpkg/status


```

I just installed it via:
```
sudo apt install blender
```
I always find it best to stay within the packages provided by the package manager.
Unless I just need the newer outside package.

---

### Post by monkeybrain20122 on 2017-04-28
install mesa-utils 
```
sudo apt install mesa-utils

```
then run

```

glxinfo | grep OpenGL

```

and post the output.

---

### Post by monkeybrain20122 on 2017-04-28
> 
I always find it best to stay within the packages provided by the package manager.
Unless I just need the newer outside package.

I kind of disagree. The packages in the repo are often outdated (especially in the LTS which one would like to use for other reasons) 

In this case the repo version is not too much out of date (if you are on 17.04 instead of 16.04) But installing from the repo pulls in tons of dependencies whereas blender provides a binary which doesn't require any installation. Download, click and that's it. Can't be cleaner than that.

---

### Post by #&amp;thj^% on 2017-04-28
> **monkeybrain20122 said:**
> _**I kind of disagree. The packages in the repo are often outdated **_(especially in the LTS which one would like to use for other reasons) 

In this case the repo version is not too much out of date (if you are on 17.04 instead of 16.04) But installing from the repo pulls in tons of dependencies whereas blender provides a binary which doesn't require any installation. Download, click and that's it. Can't be cleaner than that.

Isn't choice grand :D
Regards

---

### Post by monkeybrain20122 on 2017-04-28
Your graphic card is too old. 

[http://www.intel.com/content/www/us/en/support/graphics-drivers/000005524.html](http://www.intel.com/content/www/us/en/support/graphics-drivers/000005524.html)

Seems that it only supports opengl <= 1.3. There isn't anything you can do other than upgrading your hardware.

---

### Post by kostkon on 2017-04-28
You could try the snap package, which will give you the latest version, 2.78c. Just open Ubuntu Software, search for *blender* and select the *blender-tpaw* version for installation. You might get better results with that.
> **monkeybrain20122 said:**
> Your graphic card is too old. 

[http://www.intel.com/content/www/us/en/support/graphics-drivers/000005524.html](http://www.intel.com/content/www/us/en/support/graphics-drivers/000005524.html)

Seems that it only supports opengl <= 1.3. There isn't anything you can do other than upgrading your hardware.
Interesting, because the snap version runs fine on my netbook with opengl1.4.

---

### Post by Yellow Pasque on 2017-04-29
[QUOTE=kostkon]Interesting, because the snap version runs fine on my netbook with opengl1.4. [/QUOTE]

AFAICT, the OP's system has GMA 3100, which does not support hardware vertex shaders and advertises OpenGL 1.3. Your "Pineview" Atom N4xx uses GMA 3150, supports hardware vertex shaders, and advertises OpenGL 1.4. Depending on what OpenGL features Blender needs and how Blender checks for them, that could easily explain the difference. In other words, the error message about needing OpenGL 2.1 is probably oversimplified.

EDIT: OP might have better luck with Blender 2.76, which doesn't require as many OpenGL features.

---

### Post by jeremy-spagnet on 2017-05-15
I ran into a libopencv.highgui.2.0 dependency preventing blender from starting

    ```
blender: error while loading shared libraries: libopencv_highgui.so.2.4: cannot open shared object file: No such file or directory
```

symlinking to the newer libopencv.highgui.3.1 seems to have resolved the issue

    ```
sudo ln -s  /usr/local/lib/libopencv_highgui.so.3.1.0 /usr/local/lib/libopencv_highgui.so.2.4
```

---

