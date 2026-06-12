---
title: "choppy DVD playback"
date: 2012-11-30
forum: Multimedia Software
---

### Post by carnivroar on 2012-11-30
I don't know what the problem is.

I have the same set up as I had in my old laptop, which worked fine.

This is the [new laptop]("http://www.microcenter.com/product/401596/N56VZ-RH71_156_Laptop_Computer_-_Black").

I already downloaded all the codecs.

Also the restricted-extras package.

I'm not sure if I have a driver for my NVIDIA 650m.

Please help... :confused:

---

### Post by sudodus on 2012-11-30
> **carnivroar said:**
> I don't know what the problem is.

I have the same set up as I had in my old laptop, which worked fine.

This is the [new laptop]("http://www.microcenter.com/product/401596/N56VZ-RH71_156_Laptop_Computer_-_Black").

I already downloaded all the codecs.

Also the restricted-extras package.

I'm not sure if I have a driver for my NVIDIA 650m.

Please help... :confused:

Hi carnivroar, and welcome to the Ubuntu Forums :-)

The computer specs indicate that it certainly has enough horsepower to show high definition video, so DVD should work.

There is probably some issue with the graphics driver.

You can check which driver is used and which are available with the terminal window command
```
jockey-gtk
```

I use older computers with nvidia cards/chips, and I have found that it works the best with the ultra-light desktop environment LXDE as in Lubuntu. But with your computer it should work well also with Unity, unless the graphics card is too new to be supported by a proprietary driver "NVIDIA's accelerated driver ..."

If available, select a proprietary driver using ***jockey-gtk***!

If no proprietary driver is available, and you have to use nouveau, you will probably get good enough playback of video if you install lubuntu-desktop and select that at the login screen.

```
sudo apt-get install lubuntu-desktop
```

---

### Post by carnivroar on 2012-11-30
Thanks for the quick reply.

As per jockey-gtk, the only drivers I have installed is an Ethernet one.

I don't know how to install an NVIDIA driver. I did everything I could find online:

[http://www.techlw.com/2012/06/install-nvidia-driver-in-ubuntu.html](http://www.techlw.com/2012/06/install-nvidia-driver-in-ubuntu.html)

I also installed Bumblebee, which resulted in my Graphics being now shown as "Intel® Ivybridge Mobile" on the Details window. After doing that step I am now able to view shadows around windows and stuff, so that's good I guess.

But no progress with the NVIDIA chip.

---

### Post by sudodus on 2012-11-30
Does jockey-gtk should any available drivers? If this is the case, select one of them for installation (and reboot)! Otherwise, try with a less resource hungry desktop environment:

LXDE - ultra light weight - lubuntu-desktop
XFCE - light weight - xubuntu-desktop
MATE - medium weight (fork of old Gnome 2)
KDE - heavy weight and fancy - kubuntu-desktop
Unity - heavy weight and fancy - 'vanilla ubuntu desktop'

Probably within a few months, there will be a new proprietary driver, that works with your nvidia card, and you will be able to play video in the fanciest of desktop environments.

Edit: Jockey-gtk finds no suitable nvidia graphics driver. So try a lighter desktop environment. In this OS, that I am using now, I have Ubuntu 12.04 (upgraded from 10.04) and I have installed several desktops like this:

```
sudo apt-get install lubuntu-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get install kubuntu-desktop

```
Right now (and most of the time) I run lubuntu-desktop 'Lubuntu', selected at the login screen.

---

### Post by carnivroar on 2012-11-30
Check out the screenshot on the post above. I don't see anything for NVIDIA.

---

### Post by sudodus on 2012-11-30
> **carnivroar said:**
> Check out the screenshot on the post above. I don't see anything for NVIDIA.
Yes, I found it out after writing, so I edited the post. Maybe you did not notice the edit note.

Anyway, I suggest that you try a lighter desktop environment :-)

---

### Post by carnivroar on 2012-11-30
I did, I am now on Lubuntu and I have the same exact problem.

---

### Post by sudodus on 2012-11-30
Which video player are you running?

I get good results with mplayer and vlc.
```
sudo apt-get install vlc
```
 mplayer should come with lubuntu, otherwise install it too.
```
sudo apt-get install mplayer
```

---

### Post by sudodus on 2012-11-30
Also you should check which programs keep the computer busy:

***htop*** is a good tool for that (runs in a terminal window)

```
sudo apt-get install htop
```

---

### Post by carnivroar on 2012-11-30
Yes, I use VLC.

By the way, YouTube videos look perfect, if that makes a difference.

Could it still be some codec problems?

---

### Post by sudodus on 2012-11-30
> **carnivroar said:**
> Yes, I use VLC.

By the way, YouTube videos look perfect, if that makes a difference.

Could it still be some codec problems?
Could be. But it could also be some process that is keeping the computer busy.
-o-
Linux Mint, that is based on Ubuntu, is delivered with full multimedia support out of the box. I suggest that you download the MAYA iso file with the cinnamon or mate desktop environment, and test if that will give you a better video experience. It should be sufficient to test it live (booted from the CD/DVD/USB drive), and run the video.

---

### Post by carnivroar on 2012-11-30
How do I install the nvidia accelerated graphics driver?

---

### Post by sudodus on 2012-11-30
I just started to think that maybe you have been tweaking VLC to make it work better. Doing so, you might have made it faster but less accurate (and you may get tearing).

When you have a light desktop environment, you can reset VLC to more accurate rendering of the video, and it might still be possible to show without getting choppy.

---

### Post by sudodus on 2012-11-30
> **carnivroar said:**
> How do I install the nvidia accelerated graphics driver?
There is no easy way to do it, because jockey-gtk cannot find any suitable candidate to install. However, if you want to test the newest versions directly from nvidia's web site, look at the following link,

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1948324[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1948324")

But in your system I think lightdm is used instead of gdm, so that is the process to stop. Try from the text screen:
```
sudo /etc/init.d/lightm stop
```
...

---

### Post by carnivroar on 2012-11-30
Okay. After doing yet another reinstall, I did exactly that. Then I rebooted and my screen was set to 640:480. Then I did

sudo apt-get purge xserver-xorg*
sudo apt-get install xserver-xorg xserver-xorg-video-all

And it was back to normal, but all my drivers (including some experimental NVIDIA ones that showed up), including the Ethernet one, were gone.

Installed VLC then

sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh

sudo apt-get install ubuntu-restricted-extras

And now the DVD plays fine. :o

Thanks. But how can I make sure that the NVIDIA card is really working? I bought this laptop just for that. I need it for CUDA programming.

On the Details window it says "Unknown" under graphics.

---

### Post by sudodus on 2012-11-30
> **carnivroar said:**
> ...

And now the DVD plays fine. :o

Thanks. But how can I make sure that the NVIDIA card is really working? I bought this laptop just for that. I need it for CUDA programming.

On the Details window it says "Unknown" under graphics.
If you connect the monitor to the card, and you get a picture on the screen, the card is working. But *how* does it work? That is another question.

***jockey-gtk *** - should indicate if you use a proprietary driver or not.

***hardinfo *** - the GUI application at
[Computer--Display]
will indicate what is active. For example this computer shows
```
OpenGL
 Vendor             NVIDIA Corporation
 Renderer           GeForce GT 430/PCIe/SSE2
 Version            4.2.0 NVIDIA 295.40
 Direct Rendering   Yes
```
295.40 is the version of the proprietary driver. If it looks similar in your computer (but for your card), it is recognized and used as it should. If you are using the built in graphics driver (nouveau), you will probably not get all the horsepower. For example, I think you need the proprietary driver to use VDPAU.

---

### Post by carnivroar on 2012-11-30
I downloaded hardinfo.

It still says Unknown for the GPU stuff.

However, I tried to reinstall the NVIDIA drivers from your post above, and it told me that I already had a driver installed, version 3xx.xx, I forgot.

---

### Post by sudodus on 2012-11-30
OK, you probably have that '3somenumbers' driver installed. But it is not cooperating well enough with the chip. If you want to test another driver from nvidia's site, you need to remove it before you can install the next candidate.

And that must be done in the graphic screen too (with lightdm stopped). I know, it is tricky, but possible ;-)

Have you found some information about linux drivers for your card at the nvidia site? Do they write that it should work? Or is there some search engine, that indicates which driver to use?

---

### Post by carnivroar on 2012-11-30
> **sudodus said:**
> OK, you probably have that '3somenumbers' driver installed. But it is not cooperating well enough with the chip. If you want to test another driver from nvidia's site, you need to remove it before you can install the next candidate.

And that must be done in the graphic screen too (with lightdm stopped). I know, it is tricky, but possible ;-)

Have you found some information about linux drivers for your card at the nvidia site? Do they write that it should work? Or is there some search engine, that indicates which driver to use?

Yeah I followed the instructions and disabled lightdm and did it from the ctrl+alt+f1 screen.

It worked but then the resolution went down to 640:480, but I managed to "fix" it.

Then just in case, I tried installing it again but it told me I already had a 3xx.xx version installed (I forgot which one exactly because I have since then reinstalled the OS, because I attemped to reinstall the driver anyways and that caused problems.)

EDIT: here [http://www.nvidia.com/object/linux-display-amd64-310.19-driver.html](http://www.nvidia.com/object/linux-display-amd64-310.19-driver.html)

By the way, the choppy DVD playback stuff was a codec problem. Maybe I should start a new thread for this NVIDIA stuff now, but let's see if we can find a solution...

---

### Post by carnivroar on 2012-11-30
[http://nvidia.custhelp.com/app/answers/detail/a_id/2821](http://nvidia.custhelp.com/app/answers/detail/a_id/2821)

Talked to a chat person on NVIDIA and they said I can't use it on Linux. At all.

I guess I will have to return this laptop then...

---

### Post by sudodus on 2012-11-30
> **carnivroar said:**
> Yeah I followed the instructions and disabled lightdm and did it from the ctrl+alt+f1 screen.

It worked but then the resolution went down to 640:480, but I managed to "fix" it.

Then just in case, I tried installing it again but it told me I already had a 3xx.xx version installed (I forgot which one exactly because I have since then reinstalled the OS, because I attemped to reinstall the driver anyways and that caused problems.)

There used to be a particular uninstalling option to be used with the install shell-script from nvidia. You need that to uninstall before installing with the next script.
> 
EDIT: here [http://www.nvidia.com/object/linux-display-amd64-310.19-driver.html](http://www.nvidia.com/object/linux-display-amd64-310.19-driver.html)

By the way, the choppy DVD playback stuff was a codec problem. Maybe I should start a new thread for this NVIDIA stuff now, but let's see if we can find a solution...

Glad you found that there was a codec problem :-) I guess it means that you can play video with the built-in nouveau driver now.  And I see, that nvidia claims, that the driver you installed is working with your card/chip.

I agree, it is a good idea to start a ***new thread*** to attract people who are interested and have experience in the new topic. So make a ***good descriptive title*** (and put a link to the new thread in a final(?) post here).

---

### Post by carnivroar on 2012-11-30
Okay I managed to get through this tutorial fine

[http://eternalvoid.net/tutorials/linux-optimus-gt650m/](http://eternalvoid.net/tutorials/linux-optimus-gt650m/)

But it still says "Unknown" on my GPU info. 

It appears to be working:

raphael@raphael-N56VZ:~$ optirun glxspheres
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 650M/PCIe/SSE2
172.903105 frames/sec - 192.959865 Mpixels/sec
176.481261 frames/sec - 196.953087 Mpixels/sec
177.755995 frames/sec - 198.375691 Mpixels/sec
175.475567 frames/sec - 195.830733 Mpixels/sec
raphael@raphael-N56VZ:~$ glxspheres
Polygons in scene: 62464
Visual ID of window: 0xb4
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Ivybridge Mobile 
60.299032 frames/sec - 67.293720 Mpixels/sec
59.943691 frames/sec - 66.897159 Mpixels/sec
59.960958 frames/sec - 66.916429 Mpixels/sec
59.972947 frames/sec - 66.929809 Mpixels/sec
59.933598 frames/sec - 66.885895 Mpixels/sec
59.959422 frames/sec - 66.914715 Mpixels/sec

Here's what I find when I do $ lspci -v | less

01:00.0 VGA compatible controller: NVIDIA Corporation Device 0fd1 (rev ff) (prog-if ff)
        !!! Unknown header type 7f

---

### Post by sudodus on 2012-12-01
If you are happy with the performance now, please click on **Thread Tools** at the top of this page and mark this thread as SOLVED.

---

