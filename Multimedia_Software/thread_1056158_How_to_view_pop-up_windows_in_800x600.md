---
title: "How to view pop-up windows in 800x600?"
date: 2009-01-31
forum: Multimedia Software
---

### Post by jktechwriter on 2009-01-31
All,

I am needing to take some screen captures of for various Ubuntu apps but some of the config wizards, when opened, are not able to display all the fields and buttons (such as Finish/Back/Cancel).

I know this is a resolution issue - I'm running this on a bare-bones PC at 800x600 - video is provided by the motherboard and it doesn't appear that Ubuntu video drivers came with the MB.

I am only able to change from 800x600 to 680x480... no higher resolutions that will let me view entire screens.  

Any suggestions?  I tried resizing these windows but most of them are locked to a specific size and can't be dragged "up" so the missing info is visible.

Thanks in advance.

Jim

---

### Post by redroad55 on 2009-01-31
This was taken from this how to [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
this is an excellent guide by the way

 > SCREEN RESOLUTION

To enable the correct display resolution in Ubuntu, you have several options. First of all, there is the fairly useless tool in "System > Preferences", the soon-to-be-dead (unavailable for 8.10+) displayconfig-gtk tool, and finally, RandR - the newest method. There will be a graphical front-end (GUI) for RandR soon (keep an eye out for it in "System > Administration"), but for now you will need to use the command line. Let's say you wanted to change your resolution to 1280x800, you would need to execute the following command:

sudo xrandr -s 1280x800

If that fails, bring up a list of "supported" resolutions with this command:

sudo xrandr -q

Use the first command again and set the highest resolution that RandR claims is supported. Once that is set, try setting the resolution you know is correct, as it may now accept that resolution.

If you're still having issues, and you're not running an 8.10+ version of Ubuntu, press Alt+F2 and type "gksudo displayconfig-gtk" (without "gtk" in Kubuntu), type your password and execute, then select the resolution you want from the list. Some of you may have to select a different screen/monitor in the list before you can successfully change the resolution. Reboot or logout if necessary.

Go to Launchpad and report a bug if you've struggled to set your screen resolution, as it should be automatically detected.

hope this helps ..best to you..post back ..one other thing for whatever reason on initial setup by changing my mouse to a usb optical mouse some problems diappeared ???

---

### Post by jktechwriter on 2009-01-31
Thank you for the quick reply.

I am running U8.10 and tried your commands... when I ran the -q command, I only see 800x600 and 640x480, so I guess I'm stuck.

I'm guessing this is a motherboard/driver issue since I'm using on-board video and I know my LCD can support a higher resolution.

If you have any other ideas, I'd love to hear them... 

Jim

---

### Post by redroad55 on 2009-01-31
try booting live cd and go to screen resolutions in preferences and change there .. I'm running 8.04 so I don't know if this will work in 8.10 .. best to you and post back results and or questions

---

### Post by jktechwriter on 2009-01-31
Just booted my 8.10 LIVE CD... System>Pref and same thing - just 800x600 and 640x480.

I had hope :)

Thanks for the suggestion - that would have been good enough for screen captures, but oh well.

The motherboard is a ECS GeForce 7050M-M if that helps - I visited the website and can find nothing on drivers for Ubuntu.  I think it's just a limitation on the MB - I may actually have to purchase a video card to get higher res.

Thanks again for your help - I'm loving Ubuntu anyway!

Jim

---

### Post by redroad55 on 2009-01-31
I don't know how invested you are in 8.10 but you could also try booting a 8.04 live cd and see if you can get the res you want .. 8.04 will be supported thru 2013 where 8.10 is only supported until next year .. Hope everything works out for you..

---

### Post by jktechwriter on 2009-01-31
Forgive my ignorance here, but isn't 8.04 an older version of Ubuntu?  Why is 8.10 only supported for 1 year but 8.04 for the next 5?  Just curious... thanks.

I may try and get my hands on 8.04 just for screen captures... I'm sure that Evolution works and looks identical on 8.04.

Jim

---

### Post by redroad55 on 2009-01-31
they release an LTS version Long term support which is 8.04 and the candidates for the next LTS version are released each year until 2011 .. I believe thats how it works..In theory 8.04 should get more and more stable ..Hope that helps.

here's the link to download 8.04 [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

---

