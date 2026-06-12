---
title: "Theme to improve EPG view"
date: 2009-11-17
forum: Mythbuntu
---

### Post by jodajen2 on 2009-11-17
Is there a way to make the program guide or epg look more like this
[http://tech2.in.com/media/images/2008/Dec/img_103851_help_gb-pvr_003.jpg](http://tech2.in.com/media/images/2008/Dec/img_103851_help_gb-pvr_003.jpg)
or similar?  

I am getting 3 channels in the view and 1 hr.  It is terrible for looking to see what is on.  I was use to the GBpvr epg that was great this lots of the  channels in view at once.  Thanks

---

### Post by Al_Vampyre on 2009-11-17
Not in front of my machine just now but there are settings in the frontend appearance settings somehwere that allow you to change the number of rows and columns visible in the EPG.

You may have to play about with font sizing though to get everything to fit.

---

### Post by jodajen2 on 2009-11-17
> **Al_Vampyre said:**
> Not in front of my machine just now but there are settings in the frontend appearance settings somehwere that allow you to change the number of rows and columns visible in the EPG.
 
You may have to play about with font sizing though to get everything to fit.
 
 
I would love to know where the row and column settings are?  I tried to make the font smaller but that didn't seem to help.  Thanks for the response.  I was beginning to think my question was to obivous to merit a response.

---

### Post by Al_Vampyre on 2009-11-18
Actually this is really odd, they should be in Utilities/Setup, Setup, TV Settings, Program Guide

and the MythTV wiki [agrees]("http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend#Program_Guide") but they aren't there on my system anymore. They were definately there in 0.21, maybe something has changed in 0.22.

Sorry, hopefully someone will come along with the correct answer soon.

---

### Post by xinix on 2009-11-18
These settings are built into the theme.  If you want to change things you'll have to edit the schedule-ui.xml file.  Just to be sure, it's the number of columns and rows you want to change and not so much the look of the theme right?  I'll be happy to post a modded file later if you want, but I'd need to know how many columns and rows to make.

---

### Post by williammanda on 2009-11-18
Xinix
It would be nice to see what you are going show since I posted about this issue several weeks ago without a reply.

[http://ubuntuforums.org/showthread.php?t=1307055]("http://ubuntuforums.org/showthread.php?t=1307055")

---

### Post by xinix on 2009-11-18
I have attached a version of schedule-ui.xml that has six 30 minute timeslots and seven channels. Copy it to your mythbuntu theme folder. Keep a copy on hand since updates can replace this file with the standard version.  Here are the CLI commands to copy it, start in the folder you downloaded the this file to.
Backup the old version:
```
sudo mv /usr/share/mythtv/themes/Mythbuntu/schedule-ui.xm /usr/share/mythtv/themes/Mythbuntu/schedule-ui.xml.old  
```
Add the new one:
```
sudo cp schedule-ui.xml /usr/share/mythtv/themes/Mythbuntu/schedule-ui.xml 
```

 These are the changes that I made:

Add more columns and row to the guide grid:
Line 37:```
<channels>5</channels>
```
to:```
<channels>7</channels>
```

Line 38:```
<timeslots>4</timeslots>
```
to:```
<timeslots>6</timeslots>
```

Make the time listed above the grid match the timeslot spacing:
Change the background,
Lines 66 and 69:```
<area>0,0,258,36</area>
```
to:```
<area>0,0,172,36</area>
```
and the text,
Line 75: ```
<area>10,0,238,36</area>
```
to:```
<area>0,0,152,36</area>
```

Make the channel numbers match grid timeslots:
change the button area,
Line 115:```
<area>0,0,190,74</area>
```
to: ```
<area>0,0,190,56</area>
```
the background,
Line 118: ```
<area>0,0,190,78</area>
```
to:```
<area>0,0,190,56</area>
```
make the icon fit the new slot spacing,
Line 124: ```
<area>10,15,40,40</area>
```
to:```
<area>12,9,40,40</area>
```
move the text to match the spacing,
Line 127:```
<area>55,0,130,78</area>
```
to:```
<area>55,0,130,55</area>
```

---

### Post by xinix on 2009-11-18
Sorry the first try to attach the file didn't work.  I had to make a .tar.gz for the forum to accept it.
Decompress it with :
```
tar xzf schedule-ui.xml.tar.gz
```

---

### Post by SiHa on 2009-11-18
Nice, I might make use of that myself, thanks!

Out of interest, do you know why it is now fixed in the theme? As people will be using this with vastly different sized screens, it seems one bit of functionality that's very useful to have.

---

### Post by xinix on 2009-11-18
> **williammanda said:**
> Xinix
It would be nice to see what you are going show since I posted about this issue several weeks ago without a reply.

[http://ubuntuforums.org/showthread.php?t=1307055]("http://ubuntuforums.org/showthread.php?t=1307055")
Here's a version that has 12 channels like you asked about in your thread.  I had to add an entry for a smaller font to avoid cutting off letters that hang below others.


SiHa, 
I really don't know why the option is no longer something you can change in the config screens.  I suspect it has to do with the new myth-ui structure, but I'm just an end user so it's just a guess.

---

### Post by jodajen2 on 2009-11-19
> **Al_Vampyre said:**
> Not in front of my machine just now but there are settings in the frontend appearance settings somehwere that allow you to change the number of rows and columns visible in the EPG.

You may have to play about with font sizing though to get everything to fit.


I finally found what you were mentioning  with the columns and rows.  
SETUP-->TV SETTING--> PROGRAM GUIDE
Thanks for your help I am sure I would have made it much hard to get done.

---

