---
title: "Cant get maximum refresh rate out of my monitor"
date: 2009-02-04
forum: Multimedia Software
---

### Post by rickrob on 2009-02-04
New to ubuntu 8.10.To start.Now i cant get my maximum refresh rate  on my monitor that is 1440x900_75.I have have the latest ati driver installed but it wont go higher than 1440x900_60.Now ive also have some kind of video lag i cant figure out.Ive installed with envy,the restricted driver manager and now im using the installer from the ati site.Always the same problem with the refresh rate.In system-preference-screen resolution it also only displays this but without the driver installed it detects my resolution and screen but once the driver is installed its limited and does not detect my screen.Is their a way for me to add the refresh rate manually?Oh yes almost forgot , catalyst control center says i only have the 2d driver ?

---

### Post by sonofusion82 on 2009-02-04
i also cant seems to change the display refresh rate.
however, if you are using LCD display, refresh rate is no longer important as LCD does not flicker. in fact, especially if you are using digital interface (DVI, HDMI or future display port) it might be better just use the lower refresh rate. u can try to google for LCD diplay and refresh rate for more info.

---

### Post by redroad55 on 2009-02-04
Try this link
  [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

Hope this helps .. Post back .. Best to you

---

### Post by rickrob on 2009-02-04
No luck tried with xrandr but nothing changed.It doesn't seem to recognize the commands I'm using.Strange cause i got them from the link you gave me ,this is all that comes up when i use xrandr 

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1440 x 1024
default connected 1024x768+0+0 0mm x 0mm
   1440x900       60.0  
   1280x1024      75.0     70.0     60.0  
   1280x960       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1152x864       75.0     70.0     60.0  
   1024x768       75.0*    72.0     70.0     60.0  
   800x600        75.0     72.0     70.0     60.0     56.0  
   720x480        60.0  
   640x480        75.0     72.0     60.0  
   640x400        75.0     60.0  
   512x384        75.0     60.0  
   400x300        75.0     60.0  
   320x240        75.0     60.0  
   320x200        75.0     60.0  
It has 1440x900 but i want the 75 refresh rate its strange cause when its at 60 the video lags i had to put a lower resolution.In Windows it has no problem running at 1440x900 75.

---

### Post by rickrob on 2009-02-04
Reply for sonofusion. well its strange cause my Catalyst control center tells me I'm using an analog monitor.But has the display name and model right?

---

### Post by redroad55 on 2009-02-04
does the monitor it self have a setting change for analog or other mode..Post back ..Best to you

---

### Post by rickrob on 2009-02-06
No it doesn't!

---

### Post by redroad55 on 2009-02-06
Do you have "advanced desktop effect settings" ? .. It would be in
Applications > System > Preferences .. If so Post Back

---

### Post by 123Mike on 2009-02-06
Higher is not better. Setting it higher means that the CPU has to work harder to provide smooth motion in animation, games, and video.
High frame rates fad has gone once LCD's become norm.

---

### Post by rickrob on 2009-02-06
I understand that higher is not better but when im at maximum resolution everything lags.And all i have  in system -preference is appearance and copmiz setting manage.

---

### Post by redroad55 on 2009-02-06
In appearance > effects tab does it give you the custom choice..post back

---

### Post by Ouoertheo on 2009-02-06
Had this same issue on my nvidia. I added these lines to my /etc/X11/xorg.conf

```

    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
```
 Let me select the proper refresh rates after quick reset of x (running on a CRT monitor, low refresh rates hurt!)

Don't know about the other issues, but this should knock one out.

Edit: put that code in the "Monitor" section.

---

### Post by rickrob on 2009-02-06
Ok i dont have a custom setting and also how do i change the settings in xorg-conf cause it says i dont have permission when i go straight to the file and change it.

---

### Post by redroad55 on 2009-02-06
In synaptic find "simple-ccsm" install .. that will give you the custom setting in appearance as described before ..select custom and then open preferences box >  at the top in the "profil:" box at the right the small triangle will give you the drop down box choose something other than default and then click on large check mark > then close > then log out and back in ..Post back ..best to you

---

