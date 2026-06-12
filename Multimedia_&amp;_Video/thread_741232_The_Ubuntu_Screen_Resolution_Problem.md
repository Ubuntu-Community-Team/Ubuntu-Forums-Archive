---
title: "The Ubuntu Screen Resolution Problem"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by iamthenoob on 2008-03-31
I am now suffering

After 2 days of searching on all the forums and posts etc i can find to try and get a screen resolution where i can see both the top and bottom of the screen i am currently using a resolution of 640x480@51hz on my lovely 1080 hd 27" screen

as you can probably imagine it looks pretty crap and i will not be beaten by this.

So far i have tried various different methods of trying to show a desktop which fits onto my screen but i am now at a complete loss.

i seem to have screwed up the one setting which let me see the top and bottom bars and cant get the setting abck again

My screen is a sagem hd l27 i have read the datasheet and from what i can see it is a 1280x720display as it is widescreen and i believe the refresh rate is 50hz

at some point i did get to use the 
```
 sudo nvidia-settings
```
and that showed that my screen had been correctly identified and that the native resolution of 1280x720 was in use.

if it was in use then why the hell cant i see the top and bottom of the screen???

i have also tried sudo dpkg-reconfigure xserver-xorg and going through that way to configure but i seem to get different results after every try.

Can someone please advise me how to get ubuntu to display correctly on a sagem HD-L27 and i will be forever grateful.  

just as a side note 

since i had it displaying correctly at 640x480 i have rerun sudo dpkg-reconfigure xserver-xorg and tried to add 1280 x960 as i thought if 640x480 was running then why not double it and now i cant get the 640x480 working again so i once again cant see the top and bottom of my desktop as its off the screen.

I look forward to your advice

T

---

### Post by forceofnature on 2008-03-31
You might have to manually configure in /etc/X11/xorg.conf  I believe there is a thread on how to do that here.

---

### Post by iamthenoob on 2008-03-31
i have read through quite a few different threads now and most seem to come down to using gtf to get my native resolution and then entering that into xorg.conf which i am not sure if i have done correctlty. How do you check?

at any rate i think i did that correctly and the onyl resolution i have which allows me to see the whole desktop is 640x480@51hz

which i would prefer to be a bit bigger

BTW goig to restricted driver option and enabling nvidia driver and then restarting allowed me to get the 640x480 back working again after a restart

Still looking for help to get 1280 out of it though

---

### Post by Fire_Chief on 2008-03-31
You could try using the screens and graphics tool under the System -> Administration menu. Choose a generic lcd monitor definition like 1440x900 or something and then check the widescreen option in the bottom left. If you have the horizontal and vertical refresh rates for your monitor you may want to create your own definition and use that instead of the predefined lcd monitors. Once you choose the screen, you can then select the resolution and (sometimes) the refresh rate (Hz). Checking the previously mentioned widescreen option gives you the ability to choose the 1280x720 res that you want. Reboot after making the changes and *maybe* it then *just works*? :-k

Cheers

---

### Post by zdude on 2008-03-31
I just went through this and I spent about 10 hours on it. Nvidia driver 100.14 (Gutsy) seems to have some weird bug with large screens > 1280, I don't think it is reading the EDID info correctly. I ended up installing the newer nvidia drivers (169.12) via Envy and my projector now syncs up correctly! This occurred when I did an update and then no more worky!
Good luck.

---

### Post by iamthenoob on 2008-03-31
does anyone think it will be any better to just go straight onto the current hardy heron beta and see if that works anny better?

as a quick side note using the screens and graphics tool and putting in the settings you suggested i got a 800x600 that fits if i use the 1440 x 900 widescreen monitor as a base

wierd but i am gonna try envy now

---

### Post by iamthenoob on 2008-04-01
I have got a working large resolution now

i used Envy to get the latest nvidia drivers and changed the resolution to 1280x1024 and it just dropped in perfect.

not sure why this res works where 1280x720 wjhioch is the native resolution doesnt but who cares it works now :-)

---

### Post by Ac_David on 2008-04-04
I have a similar problem, but I am not sure Envy is the right way to go for me since Ubuntu knows what screen size I have.  My problem is strictly with the refresh rates.  The nvidia drivers detect the graphics card fine, and tell me the refresh rate is set at 60 which the xorg file supports.  However the Screens and Graphics application tells me that the refresh rate is set at 50, and I get no option of changing it, hence I get choppy window movement and redraw errors.  

can some one point me in the right direction of how I might go about making the refresh rate stay at 60?

Thanks

---

### Post by Fernando Negro on 2008-04-06
Ac_David:

The "Screen and Graphics" application, I read somewhere in this forums, has a bug and doesn't show the correct values.

Check the menu in your monitor to see how many Hertz you really have.

In my case, the application says I'm working with 50 Hz and when I press the buttons in the monitor I can see it' s working with 75 Hz.

---

### Post by hazysonic on 2008-06-21
I'm having similar problems and no luck. I'm on a toshiba satellite A25 laptop with 15" LCD and trident graphics. It should display at 1024x768 but I'm getting 800x600 in the center of the screen with a large black frame around it.

I couldn't find the "screens and graphics tool" that was mentioned under System>Administration. I've searched high and low and tried editing /etc/X11/xorg.conf by adding the desired resolutions and appropriate driver info. At one point I had a screen come up during login which let me change the monitor and graphics driver. I used a generic display under "toshiba" and selected the trident driver. It worked briefly but as soon as I power cycled, it reverted back to the low resolution and now i can't get it back. 

I've also tried "sudo dpkg-reconfigure xserver-xorg" which blows away the lines added to xorg.conf (which I believe I need) having to do with my monitor and desired screen resolution. I found a post saying i could correct the problem by running "fbset", which I installed, but when I try to run it says "no such file or directory".

This is beyond me. Any help is greatly appreciated!

---

