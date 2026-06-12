---
title: "Nvidia 7300GT Not Working: Smash It or Fix It?"
date: 2008-11-07
forum: Multimedia Software
---

### Post by justacreep on 2008-11-07
I'm trying to install ubuntu or a PC with a Nvidia 7300GT video card. I've installed 8.10 and 8.04 with the same results. At first the video would just flicker after install but I reconfigured xserver-xorg and now I have a display. The problem is; after reboot the system goes into "low graphics" mode. If I hit "configure" from that prompt it will allow me to change the driver and boot into the OS. But every time I reboot I end up back in "low graphic" mode.

I searched the forum and found lots of threads where this card is giving people headaches. Should I just take it out and smash it or is there hope for it yet? If I should toss it; what's a good graphics card thats easy to setup, supports dual monitors with DVI, and will basically be used for HD movies and pron?

---

### Post by justacreep on 2008-11-07
Any of you morning people have any ideas or suggestions?

---

### Post by timcredible on 2008-11-07
well, ati cards are now supported very well since their drivers are open source.  i hate to see you spend money on replacing a video card, but if you can't get the nvidia to work, ati would be a good choice.  the ati card in my laptop was recognized and ran correctly (with the 3d drivers activated) from the 8.10 livecd.  in 8.04 i had to install via 'safe graphics mode' and then download the drivers.

---

### Post by nedmar on 2008-11-07
**[COLOR="DarkRed"]Only for Ububtu 8.04 32bits[/COLOR]**
Method 1. ( worked for me )

Download the latest [nVidia driver]("http://us.download.nvidia.com/XFree86/Linux-x86/177.80/NVIDIA-Linux-x86-177.80-pkg1.run") then go Ctrl+Alt+F1 ( to return in graphic mode pres ALT+F7 ).

While in "text mode" do the following:

```
sudo /etc/init.d/gdm stop 
``` This will stop Your Xserver.

Then: ```
sudo sh [COLOR="Red"]/path_to_your_downloaded_nvidia_driver/[/COLOR]NVIDIA-Linux-x86-177.80-pkg1.run 
```

#in case you saved it to your Desktop this should be: ```
[COLOR="Red"]sudo sh ~/Desktop/NVIDIA-Linux-x86-177.80-pkg1.run[/COLOR] 
```

Follow the install instructions( you'll see what i meant);when finished:
```
sudo /etc/init.d/gdm start
```



Method 2. ( tested with success)
Get Envy 
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A) -- just follow instructions on the website.You'll find solutions for different ubuntu distro's.


---
---

[COLOR="Red"]
After driver install[/COLOR]:
Only if not already present in xorg.conf
```
sudo gedit /etc/X11/xorg.conf
``` add under Section "Device"
```
 Driver         "nvidia" 
``` 

and under Section "Screen" 
( [COLOR="Red"]Those modes are only as example.Remove/edit modes not supported by your Monitor and edit refresh rate according to your Monitor specifications. The format is: **Modes "resolution@refresh_rate"**[/COLOR] )

```
 Modes      "800x600@85" "1024x768@85" "1152x864@75" "1280x1024@75" "1400x1050@60" "1400x1050@75" "1600x1200@85" "1920x1440@75"
``` 
Find your monitor manual and check HorizSync and VertRefresh . You can specify those values under: Section "Monitor" as in the example :
([COLOR="Red"]**DON'T** COPY/PASTE THE VALUES IN THE EXAMPLE**!FIND** THE VALUES FOR YOUR MONITOR AND USE THEM[/COLOR])
```
 Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Dell"
    ModelName      "Dell P1110"
   [COLOR="Red"] HorizSync       30.0 - 121.0
    VertRefresh     48.0 - 160.0[/COLOR]

```

I hope this will somehow helped.

---

