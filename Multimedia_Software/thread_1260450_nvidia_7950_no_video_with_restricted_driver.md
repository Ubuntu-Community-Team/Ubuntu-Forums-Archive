---
title: "nvidia 7950 no video with restricted driver"
date: 2009-09-07
forum: Multimedia Software
---

### Post by sonic6567 on 2009-09-07
Hello,

Please help if you can. I have worked through a number of video issues in the past on other systems but I can't seem to get through this one.

I have two nvidia 7950 gt in sli

a fresh install of ubuntu 9.04

everything works fine with the default drivers. I enable the restricted nvidia 180 driver and reboot.

I never again see a desktop.

Even if I restore an xorg.conf it doesn't matter.  Desktop nevermore.

I can alt-f1 and log in.

how do I use the nvidia 7950 in ubuntu 9.04?

(the hardware is fine, used to have windows installed)

Thank you

Ben

---

### Post by dagrump on 2009-09-07
Go ahead & log in.
Then you need to enter "lspci" this will list your hardware, find & write down the BusID of both cards.
Now enter "sudo nvidia-xconfig", it will ask for your password (there will be no visual feedback when typing your password).
That creates your xorg.conf file. Now to edit it.
You would enter "sudo nano /etc/X11/xorg.conf", nano is an editor.
Now arrow down till the cursor is at the EndSection line of the device section, hit enter twice.
Arrow up twice and enter line looks like so; BusID "XX:YY:ZZ", with XYZ being the numbers recorded earlier, of your primary card.
Drop to the next line & try; Option "SLI" "SFR".
Now crtl+o to write & crtl+x to exit.
And a "sudo shutdown -r now", to reboot & if all goes well you are working.

********
Please note where referencing CLI entries the quote marks should not be used, but during edit of xorg.conf they are needed.
IIRC the "SFR" is split screen rendering.
This is what my xorg.conf looks like, yours will be different due to detected hardware.

---

### Post by sonic6567 on 2009-09-09
Most excellent.  Thank you. Putting the bus id in the xorg was the tip I needed.
Works great.

But I will need to continue to experiment with the options.
For example, when I use the nvidia-xconfig --sli=On  it is put into another section of the xorg.
Also, is there a way to verify that sli is functioning?  In the gui, when using nvidia-settings it only shows one gpu (not two)
(fyi, under ubuntu 8.04 with restricted drivers 16x it shows two)

And fyi, iirc AFR is the best performing under linux.

So i must continue to work on this.  Any other thoughts?

Thank you very much.

---

### Post by sonic6567 on 2009-09-10
I manually added a second Device section to my xorg.conf with the bus id of the second card.

now nvidia-settings does show both GPUs in the list and there is a designation that SLI is in use.

Now I would just like a way to really benchmark the performance.

I know about FPS on Quake 4 - problem is I cannot get Quake 4 to work.

Any other method?

Thanks

---

### Post by Joker23 on 2009-09-17
> **dagrump said:**
> Go ahead & log in.
Then you need to enter "lspci" this will list your hardware, find & write down the BusID of both cards.
Now enter "sudo nvidia-xconfig", it will ask for your password (there will be no visual feedback when typing your password).
That creates your xorg.conf file. Now to edit it.
You would enter "sudo nano /etc/X11/xorg.conf", nano is an editor.
Now arrow down till the cursor is at the EndSection line of the device section, hit enter twice.
Arrow up twice and enter line looks like so; BusID "XX:YY:ZZ", with XYZ being the numbers recorded earlier, of your primary card.
Drop to the next line & try; Option "SLI" "SFR".
Now crtl+o to write & crtl+x to exit.
And a "sudo shutdown -r now", to reboot & if all goes well you are working.

********
Please note where referencing CLI entries the quote marks should not be used, but during edit of xorg.conf they are needed.
IIRC the "SFR" is split screen rendering.
This is what my xorg.conf looks like, yours will be different due to detected hardware.

I just decided to get back into Ubuntu after a (too) long absence.  I have a Dell Precision M50 with a Nvidia Quadro4 500 GoGL.  I did a fresh install of Ubuntu 9.04 on a new partition. I activated the restricted drivers and now I have no video.  I followed your instructions above, but then it puts me in "low graphics mode".

I did notice one thing, however.  When I ran lspci, my video card showed as "01:00.0", so that's how I entered it into xorg.conf.  You mentioned entering it into xorg.conf as "XX:YY:ZZ".  I also see in your text file, yours shows as "01:00:00".  Should I enter it into mine as "01:00:00" instead of "01:00.00"?

I would just try, but I'm at work and it's at home.  I'm trying to research different things to try...

Thanks!

---

### Post by Joker23 on 2009-09-18
OK,

I changed it to:

BusID "01:00:00"

Now I don't get any video, just like before I added the BusID.  At least I'm not in low graphics mode...

I removed the restricted drivers that came with Ubuntu and downloaded the drivers from Nvidia.  Same issue, no video.  I added the BusID and still no video.

---

### Post by Joker23 on 2009-09-18
Some additional information.

I start to boot and everything looks normal.

As soon as the little scroll bar goes all the way to the right to indicate it's ready for my username and password prompt, the backlight goes off on the screen.  I can type in my username and password and hear the music start up, so I know I'm in, I just have no screen...

Edit to add:

Once logged on blind I can ctrl-alt-F1 and get a logon prompt that I can see.

It seems X is not liking something...

---

### Post by sonic6567 on 2009-09-18
Hello,

I am not sure if this has anything to do with your issue but it is something to look into.

I have a new Dell E6500 laptop with nvidia. I had a heck of a time trying to get it working right.  My issue was docking station vs no docking station.

I have always had issues with ubuntu's 'new graphical interface' for managing video configs.  imho i think it is garbage and has never worked right.

I had to boot in the docking station to load the drivers. Then reboot and remove the laptop from the docking station. then use sudo nvidia-settings to configure the external monitor and save that to the x-config (hence requiring sudo)
The boot in the docking station.  sudo nvidia settings. Disable the laptop monitor (yes, disable).
Then reboot.
After all of that, I can now boot either in docking station or not and the video works fine.

And this is the abbreviated process-- imaging how long it took for me the figure this out.

ha ha

Again, don't know if this has anything at all to do with what you are facing, but I do know I have seen wierd stuff on laptops due to second monitors.

Ben

---

### Post by Joker23 on 2009-09-19
> **sonic6567 said:**
> Hello,

I am not sure if this has anything to do with your issue but it is something to look into.

I have a new Dell E6500 laptop with nvidia. I had a heck of a time trying to get it working right.  My issue was docking station vs no docking station.

I have always had issues with ubuntu's 'new graphical interface' for managing video configs.  imho i think it is garbage and has never worked right.

I had to boot in the docking station to load the drivers. Then reboot and remove the laptop from the docking station. then use sudo nvidia-settings to configure the external monitor and save that to the x-config (hence requiring sudo)
The boot in the docking station.  sudo nvidia settings. Disable the laptop monitor (yes, disable).
Then reboot.
After all of that, I can now boot either in docking station or not and the video works fine.

And this is the abbreviated process-- imaging how long it took for me the figure this out.

ha ha

Again, don't know if this has anything at all to do with what you are facing, but I do know I have seen wierd stuff on laptops due to second monitors.

Ben

You rock!

I don't have a docking station, but I do have an older laptop...

I enabled remote desktop in Ubuntu and then used Real VNC Viewer from windows in my other laptop.

The Nvidia settings were trying to default to a CRT with the laptop screen disabled.  After trying several things I finally decided to clone the non-existent CRT with my laptop screen.

I now have video!

Several reboots later and I still have it.

Thanks!!!

---

### Post by sonic6567 on 2009-09-22
Glad you got it going.  And glad I could help.

Ben

---

