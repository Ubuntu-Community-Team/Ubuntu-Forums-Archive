---
title: "Oddball Login Screen Problem"
date: 2006-08-30
forum: Multimedia &amp; Video
---

### Post by younvrknow on 2006-08-30
Yes, it really appears oddball. I've done some casual research over the net with this problem and it appears that it's something not so common, so I'll just ask it straightout.
Ubuntu starts up normal until it gets to the login screen and things just get funky: the screen is there for a second or two, flashes, horizontal lines start dashing through it and then in randomly starts going black, in and out until it states (from the monitor) "cannot display digital input". However, if you wait, the login screen will come back even after the black screen does it's part. 
Of course, this corresponds entirely to the fact that I changed my graphics card (ATI 9800xt) input from analog to digital. Previously the text had fuzzy, even with moniotr adjustments made, digital fixed that and alot else. I'm not looking to revert to analog because when I DO log in to Ubuntu the screen is in perfect sync. Always. The problem is pretty apparent, it's just I have no idea how to fix it. 

BTW - I am still able to log into Ubuntu, just can't watch myself doing it. (my family is rather mystified by this behavior ;D) I still get login sound  and it shows nautilus and all loading, so good there. I'm going to see if there is a linux driver specifically for this monitor...hmmm.

Running Dapper 6.06, Gnome and AMD 64 (saw that forum, hoping this is the right one)

---

### Post by Omnios on 2006-08-30
Sounds like the monitor is being pushed to hard. I have had a similar thing happen with my old P2 KTX monitor set up with both BSD and Debian. What happenes is that xserver tryes to use the max setting in xserver for start up till you log in and possibly if this is the problem pushing the monitor frequency to high. It has been a long time since I had to fix this but basicly I whent into 
```
sudo nano /etc/X11/xorg.conf
``` or gedit and lowered the frequency setting on the second value to what what would be the normal frequency in the screen reselution. Now I do not remember if it was the first HorizSync or VertRefresh but am pretty shure it was  
VertRefresh. Anyways it should be safe to lower the number but never increase it past what it was set at. Alos you might want to make a backup file or keep your old setting as a note  with a # in front of it.

```
Section "Monitor"
    Identifier    "A91f+"
    Option        "DPMS"
    HorizSync    30-100
    VertRefresh    50-160
EndSection
```

---

### Post by younvrknow on 2006-08-31
Ahhhh, yes....as is sometimes the case what it is supposed to do (what "should be safe" ;D) and what I manage to make it do have their differences. 
It crashed xserver.
I tried to login after editing my lower VertSync from 43 to 30 and Ubuntu crashed upon the login window. Stalls for a second and then goes stright to the Ubuntu Blue Screen with the error in the /etc/x11/xorg.conf file. 
Reasons for the crash? I'm thinking I lowered the vertSync much too low and that the problem may lie with horizSync because the lines are *horizontal* themselves
I'm rather new at editing with commands and whatnot, but I was able to access nano and open a "new buffer" and such, but what I really need to do is re-edit the vertRefresh back to 43. How can I do that, if possible? sudo nano /etc/x11/xorg.conf doesn't open it. Unfamiliar territory here.
   
Also, I have a Dell 1703fp monitor

---

### Post by Omnios on 2006-09-01
> How can I do that, if possible? sudo nano /etc/x11/xorg.conf doesn't open it. Unfamiliar territory here. 
Its 
```
/etc/X11/xorg.conf
large X in X11
``` 
 Anyways be very carfull not to raise the rates past what they where, this may cause damage to the monitor. If I rememnered correcty I just lowered the second entry
```
VertRefresh    50-160
``` 
 Now there is also a second part to this, I took thescreen refresh drom windows or was it linux and used this for the upper refresh rate. Which I think was 65 or something like that.

 There is also 
```
sudo dpkg-reconfigure xserver-xorg
``` Which a turtle like xserver reconfigure thing this will autodetect your settings to the monitor default

 Also with nano you navigate your text file with the arrows and backspace etc work in it and there are ctrl-? options such as ctrl-X to exit they are listed on the bottom of the file

---

### Post by younvrknow on 2006-09-01
Wow, okay, it was the uppercase X that was the problem. I first tried to manually adjust the values back to their previous state with no luck in restarting xserver. However, with the reconfigure, the xorg.conf file changed from it's previous monitor status of "generic monitor" to "1703fp".  Perfect. The login screen now comes in beautifully especially with the monitors own setting set to default. The picture couldn't be much better. 

Just a few other questions - With the upgrade from "generic monitor" to "1703fp" the values have disappeared, what does that mean? Shouldn't it still have vertRefresh and HorizSync? I'd might like to adjust those a little because I'm still getting one random one pixel blinking bar across the center of the screen for a few seconds every few minutes.

Screen Refresh Drom Windows?

---

### Post by younvrknow on 2006-09-01
Update: Login screen was good for one login, it's now as bad as ever, if not worse. Comes down down to the question I asked above about the values. Now I'll let the file speak for itself.

```
Section "Monitor"
        Identifier   "DELL 1703FP"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection
```

Also, running ATI Proprietary Driver. Sorry for these little sidenotes, I remember them too late.

---

