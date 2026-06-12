---
title: "nvidia performance check"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by xargon on 2007-06-14
Hi everyone,

I just upgraded to a new machine with nvidia 7600 GS and got it up and running with ubuntu 7.04 and the glx nvidia drivers.

When I run flxgears with full screen (I am running 20 inch wide screen at 1650 X 1050), I am getting a frame rate of about 400. Is this good enough? The reason I ask is that I run my application which is OpenGL based and I do not notice any speed/performance increase from my old machine. I ran the application on windows with a GeForce Go card laptop and I( could clearly tell a huge performance boost.

So, just wondering if someone could confirm these frame rates.

Thanks a lot guys.

xarg

---

### Post by dabl on 2007-06-14
Interesting -- I haven't tried flxgears, but I will tonight!

If it's of any interest, I get close to 11,000 with glxgears on my GeF 7900GS card. I run a 1600 x 1200 desktop, but of course glxgears runs in a little window.

HTH  :)

---

### Post by dimitrispao on 2007-06-14
[IMG]http://s3.bitefight.gr/c.php?uid=16402[/IMG]

---

### Post by dannyboy79 on 2007-06-14
> **xargon said:**
> Hi everyone,

I just upgraded to a new machine with nvidia 7600 GS and got it up and running with ubuntu 7.04 and the glx nvidia drivers.

When I run flxgears with full screen (I am running 20 inch wide screen at 1650 X 1050), I am getting a frame rate of about 400. Is this good enough? The reason I ask is that I run my application which is OpenGL based and I do not notice any speed/performance increase from my old machine. I ran the application on windows with a GeForce Go card laptop and I( could clearly tell a huge performance boost.

So, just wondering if someone could confirm these frame rates.

Thanks a lot guys.

xarg
Not sure as I've never used that. I am curious why you would use FLXgears? I think that's for the FGLRX driver isn't it? Try out glxgears since that's testing the gl capabilities. Not to mention, glxgears is not really a good benchmarking tool. I have seen a better but never used it and don't remember what it was. Also, which glx drivers are you using, you should be using the nvidia-glx-new drivers, those are hte latest stable nvidia available.

---

### Post by xargon on 2007-06-14
Hi HTH,

I would be really grateful, if you did and post the results here. On my small window, I get about 6000 FPS.

That was a typo...I indeed do run glxgears!

Cheers,
xarg

---

### Post by vronp on 2007-06-14
> **dabl said:**
> Interesting -- I haven't tried flxgears, but I will tonight!

If it's of any interest, I get close to 11,000 with glxgears on my GeF 7900GS card. I run a 1600 x 1200 desktop, but of course glxgears runs in a little window.

HTH  :)

Dabl,

I have the same graphics card and get only 790 FPS.

Obviously, I must be doing something wrong.

This is a new Feisty install on a Dell 9400 laptop.

Which Nvidia drivers do you have?

---

### Post by vronp on 2007-06-14
Fixed it.  I had not installed the Nvidia drivers.

glxgears
88183 frames in 5.0 seconds = 17636.477 FPS
88331 frames in 5.0 seconds = 17666.115 FPS
87296 frames in 5.0 seconds = 17459.106 FPS
87582 frames in 5.0 seconds = 17516.301 FPS
86843 frames in 5.0 seconds = 17311.034 FPS
83131 frames in 5.0 seconds = 16626.103 FPS
73501 frames in 5.0 seconds = 14699.894 FPS
73204 frames in 5.0 seconds = 14636.751 FPS
88964 frames in 5.0 seconds = 17792.651 FPS
75984 frames in 5.0 seconds = 15196.775 FPS
78890 frames in 5.0 seconds = 15777.912 FPS
86073 frames in 5.0 seconds = 17214.542 FPS
85253 frames in 5.0 seconds = 17048.864 FPS
82591 frames in 5.0 seconds = 16518.061 FPS

---

### Post by dabl on 2007-06-14
Yep, you are hummin' now, vronp!

But, your screen resolution and refresh rates will affect the glxgears performance, I think -- at least I got that impression the last time I ran it which was a while ago.  Like maybe it would really fly at 640 x 480, 50 Hz, but not so much at 1600 x 1200, 80 Hz.  Whaddaya think?  :)

p.s. did you try overclocking with "Coolbits" yet?

---

### Post by vronp on 2007-06-14
> **dabl said:**
> Yep, you are hummin' now, vronp!

But, your screen resolution and refresh rates will affect the glxgears performance, I think -- at least I got that impression the last time I ran it which was a while ago.  Like maybe it would really fly at 640 x 480, 50 Hz, but not so much at 1600 x 1200, 80 Hz.  Whaddaya think?  :)

p.s. did you try overclocking with "Coolbits" yet?

Hi,

This is on a Dell Inspiron 9400 laptop.  My screen resolution was 1920 x 1200 when I ran that test (50 Hz).

To be honest, I haven't heard of Coolbits but I'll check into it.

thanks,
Dave

---

### Post by xargon on 2007-06-14
So, I am definitely doing something wrong! 

With my 7600 GS, I am only getting 6000 FPS. Can someone with the working nvidia card post their xorg.conf file?

Cheers,
xarg

---

### Post by dabl on 2007-06-14
vronp, put the "Coolbits" option in your "Screen" stanza of /etc/X11/xorg.conf, like this:


```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7900 GS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "Coolbits" "1"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768"  .......
```

Then when you run your "nvidia-settings" panel, you will have the option of overclocking.  In their Linux drivers, You have to accept their license/disclaimer, and then choose the 3D settings.  I have only seen "Auto-detect" work one time ( a prior driver version ), so you probably won't be able to do that.  But, on my 7900GS, I learned under Windows that I can safely run the gpu at 580, and the memory at 780, so I do that under Linux too, sometimes.  Your mileage may vary, of course ....  :)

Here is my glxgears in Kubuntu Feisty 32-bit, with a 1600 x 1200 screen at 75Hz:

don@feisty:~$ glxgears
54968 frames in 5.0 seconds = 10993.455 FPS
56128 frames in 5.0 seconds = 11225.457 FPS
56388 frames in 5.0 seconds = 11276.664 FPS
56557 frames in 5.0 seconds = 11311.330 FPS
56286 frames in 5.0 seconds = 11257.141 FPS
56424 frames in 5.0 seconds = 11284.791 FPS
56506 frames in 5.0 seconds = 11301.037 FPS
56223 frames in 5.0 seconds = 11244.591 FPS
56334 frames in 5.0 seconds = 11266.775 FPS
55230 frames in 5.0 seconds = 11045.834 FPS

and here is glxgears when the screen is 1280 x 1024 @60Hz:

don@feisty:~$ glxgears
61536 frames in 5.0 seconds = 12305.571 FPS
62044 frames in 5.0 seconds = 12408.651 FPS
60214 frames in 5.0 seconds = 12042.774 FPS
59795 frames in 5.0 seconds = 11958.883 FPS
57042 frames in 5.0 seconds = 11408.348 FPS
60977 frames in 5.0 seconds = 12195.276 FPS
61474 frames in 5.0 seconds = 12294.743 FPS
61389 frames in 5.0 seconds = 12277.766 FPS
60523 frames in 5.0 seconds = 12104.530 FPS

See what I mean about the screen settings affecting the frame rate?

---

### Post by xargon on 2007-06-14
Which drivers did you install? The nvidia-glx or nvidia-glx-new. I am wondering if they are actually the same package...

xargon

---

### Post by dabl on 2007-06-14
It's nvidia-glx-new.  That's the -9755 driver.  I haven't screwed up my courage to install the latest one, which has to be downloaded from Nvidia and installed manually.  Which one do you use?

EDIT:  They are not the same -- nvidia-glx has an earlier driver -- I believe it is -9639, for some of the earlier chips.

---

### Post by xargon on 2007-06-15
Hi there,

I installed the nvidia-glx one. Maybe I should try the nvidia-glx-new and see how that works.

Cheers,
xarg

---

### Post by dabl on 2007-06-15
Unless you have a GeForce 4, nvidia-glx-new should work for you.  If you have a TNT, GeForce, or GeForce2, you need the nvidia-glx-legacy driver.  Details here: [https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/2.6.20.5-14.17](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/2.6.20.5-14.17)

---

### Post by dannyboy79 on 2007-06-15
> **xargon said:**
> Hi there,

I installed the nvidia-glx one. Maybe I should try the nvidia-glx-new and see how that works.

Cheers,
xarg
suggested this in post #4. I am sure you'll get better performace from it.

That coolbits thing looks really cool although I don't game so I don't know the real advantage?

---

### Post by vronp on 2007-06-15
Dabl,

Thanks for the info !!!  That's great.

However, I am having trouble with the GPU and Memory frequency settings.  I use the sliders but when I use the Apply button, they revert to their normal setting.

I can change one of the numeric values directly by typing over them but I can only change one at a time.

Anyway, with the GPU at 600 MHz and the Memory at 507 MHz, I get the numbers below.  By the way, these are 3D clock frequencies.  I haven't messed with 2D clock frequencies.

I sure wish I could fix the slider problem as I'd like to raise both frequencies at the same time.

Have you changed the 2D frequencies?

vronp

glxgears
86888 frames in 5.0 seconds = 17377.562 FPS
86218 frames in 5.0 seconds = 17243.417 FPS
86613 frames in 5.0 seconds = 17322.590 FPS
86306 frames in 5.0 seconds = 17261.162 FPS
86306 frames in 5.0 seconds = 17261.079 FPS
86022 frames in 5.0 seconds = 17204.331 FPS
86560 frames in 5.0 seconds = 17311.899 FPS
85668 frames in 5.0 seconds = 17133.453 FPS
85937 frames in 5.0 seconds = 17187.239 FPS
86354 frames in 5.0 seconds = 17270.745 FPS

---

### Post by vronp on 2007-06-15
Update....

Ignore the frequencies I posted in my last post.  I apparently can't change them at all.  They seem to be pegged at 375 MHz on the GPU and 507 MHz on the Memory.

I can change the values but they revert to these defaults whenever I click on Apply.

Dave

---

### Post by xargon on 2007-06-15
Hi all,

Update: Used the nvidia-glx-new drivers with the 7600 GS card and still get the same results.

Not more than 6000 fps on the GeForce 7600 GS :((

---

### Post by vronp on 2007-06-15
xargon,

I followed this guide to the letter:

[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

However, I used Synaptic to download the driver.

Go over that guide carefully and make sure you didn't miss anything.

Dave

---

### Post by dabl on 2007-06-15
@xargon, don't know what to say -- if glxgears runs, then the driver must be installed correctly.  May relate to the rest of your system (CPU, RAM, PCI bus speed, etc.)

@vronp, it sounds a little fishy -- like maybe something isn't quite right with the driver installation.  Does glxgears run for you? I've never seen the problem as you describe it (can't change the 3D clocks).  I have seen a kinda "half-installed" Nvidia driver once, and read a post where someone else had it too. The driver panel will open, but you can't do much of anything with it, including changing resolution and refresh, nor do the glx settings and functions show up.  So, I'm scratching my head .... :(

No,I don't think you can fiddle the 2D clocks.

---

### Post by vronp on 2007-06-15
Dabl,

Yes, xlgears runs and I get very good numbers.  Also, everything else in the Nvidia control panel seems to work.

I just cannot make permanent changes to the 3D frequencies.

This is on a laptop.  Do you think it's possible the clock frequencies on this 7900 cannot be changed?

vronp

---

### Post by dabl on 2007-06-15
It may be that the power-saving modules for your laptop supercede the graphics clocking. In other words, acpi, powernowd, and some of those modules to save your battery may prevent overclocking, which does consume power.  ;)

---

