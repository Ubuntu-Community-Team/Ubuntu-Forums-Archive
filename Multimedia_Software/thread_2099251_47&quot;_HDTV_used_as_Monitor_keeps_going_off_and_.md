---
title: "47&quot; HDTV used as Monitor keeps going off and on at times"
date: 2012-12-29
forum: Multimedia Software
---

### Post by cybrsaylr on 2012-12-29
Have a Dell Inspiron 1525 model pp29l core2 duo laptop, running 64 bit 12.04, that is connected to a 47" LG LED HDTV via HDMI cable. It generally runs great as a PC monitor. It is set up where the laptop monitor is off and only the HDTV is on, showing the 12.04 desktop. Have discovered online stuff just runs better when the laptop monitor is turned off in the 'Display' settings and only the HDTV is running.

I can control most of the laptop with a wireless mouse, that acts as a TV remote. When I am using any browser and surfing the web, when pages are changed, sometimes the HDTV will momentarily go off & on. 

This never happened when I connected my Toshiba laptop in my signature, which was connected to this same HDTV via VGA to VGA cable. In this case the HDTV just ran and never went off & on.

Last night while playing around, I discovered while playing the game AisleRiot Solitaire this off & on happened so much that it was just about impossible to play that card game! Also the sound clicks on that game didn't work all the time but when the sound did work the frequent off & on of the HDTV stopped happening! 

Anyone else have this problem of their TV shutting off & on while connected to their laptop and know what causes it? And how it can be fixed?

---

### Post by 2F4U on 2012-12-29
Just to be clarify my understanding, you are not experiencing a crash. After the monitor turns off and comes back again, the system continues at the point as before the incident with all applications running?
Do you experience this behaviour on particular web sites or applications, such as Flash, or is it rather independent from the applications used?

---

### Post by cybrsaylr on 2012-12-29
Yes, there is no OS crash.
Just the monitor goes off for a second or two then comes back on to exactly where it was before.

It seems to happen on any website.

Just tried out Solitaire again and it is far worse with that game! Happens most when it is silent but when the sounds on Solitaire returns all is normal. Then Solitaire goes silent and it begins again to go off & on again every few seconds until the sound to that game returns! 

Haven't tried out other Ubuntu games.

---

### Post by cybrsaylr on 2012-12-30
Bump....any help here?

---

### Post by cybrsaylr on 2013-01-01
Still hoping for some help on this one?

---

### Post by xc3RnbFO8P on 2013-01-01
It sound like a HDMI cable failure to me.
What is the output of 
> lspci |grep VGA 

---

### Post by cybrsaylr on 2013-01-01
Here's the output
> ca@ca-Inspiron-1525:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
ca@ca-Inspiron-1525:~$ 

---

### Post by gonzoks on 2013-01-01
Have to agree it sounds a bit like a cable failure.  Any chance of trying the cable against another device connected to the TV?

---

### Post by cybrsaylr on 2013-01-01
OK, just tried using another HDMI cable and plugged it into another HDMI port on HDTV and get this output, same as the other:

> ca@ca-Inspiron-1525:~$ lspci |grep VGA
 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
 ca@ca-Inspiron-1525:~$

But I can now play Solitaire without any blinking off & on! Solitaire plays normally. 

However when playing Youtube videos, they still blink off and on once and whenever a page is changed.


Could the Dell laptop HDMI port be suspect?

---

### Post by gonzoks on 2013-01-01
I suppose that is possible (the port going bad) but I wouldn't think so.  You wouldn't have one application blinking with another not.  I could be wrong on this however.

---

### Post by cybrsaylr on 2013-01-01
OK been playing around and swapped the HDMI cables. 
Swapped the one that originally went to the HDTV and HD Digital box, with the cable that was acting up causing blinking when used with laptop and they both seem to run fine now after being swapped!

Could the cable going from laptop to HDTV be more 'finicky' than the one that goes from HD cable box to the HDTV?

---

### Post by gonzoks on 2013-01-01
Depending on length, etc, yes.   I firmly believe that a cheaper cable causes issues.  I've also seen it where a cheaper cable just doesn't 'fit' right causing issues like you've described.  My two cents.  Best of luck!

---

### Post by cybrsaylr on 2013-01-02
Well after reversing the two HDMI cables things are definitely better the last couple hours testing this. Am using the HDMI cable on laptop that was came with the HD cable box and theoretically is the better cable. The other HDMI cable that I got from Newegg last year 2011, on black Friday (and looks exactly like the one my cable company gave me, it has the same matching logos, style, gold ends, etc) is now used to connect HDTV to HD cable box. They are all 6 ft long. 

I realize there is a lot of controversy on HDMI cable quality but just went along with Consumers Reports and a couple tech reports that claim it's best to buy HDMI cables by price since they claim they are all equal. These reports were mainly intended to knock Monster Cables that are sold on a ridiculously high markup.

---

### Post by cybrsaylr on 2013-01-03
OK after playing around and testing this another day it does seem to be HDMI cable related. The HDMI cable that came with the HD Digital box does appear to work better than the cheap one I bought for the laptop but still blinks off and on occasion. However my cheaper HDMI cable works fine for connecting the HDTV to the HD Digital box.

Based on this I marked this thread solved.

---

### Post by dannyboy79 on 2013-01-03
it could also be related to DPMS and the signal over the HDMI isn't the best due to cable cheapness so the monitor thinks it can go into DPMS mode. I believe you can add an option to your xorg.conf file to completely turn off DPMS. You'll have to check whether it's FALSE or OFF as the setting for DPMS

here's some reading for you: [http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

---

### Post by cybrsaylr on 2013-01-03
dannyboy79 Thanks, will look into that.

Had a feeling it may have something to do with the different ways the laptop to HDTV does things compared to the way the HD Digital box to HDTV connection does things.

---

