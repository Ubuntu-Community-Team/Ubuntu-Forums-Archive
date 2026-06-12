---
title: "Static after Mythbuntu splash screen on TV Out"
date: 2011-11-23
forum: Mythbuntu
---

### Post by alotau on 2011-11-23
I think I have everything that I need working on my setup when displaying to a monitor (I can play videos, watch/record live TV, etc.).  Now, I'd like to get the TV involved and am having problems.

My video card is a GeForce 8400 GS with s-video out (Zotac TC512?).  After initial installation of the card and hooking it to the TV, I could see the motherboard splash screen on the TV while booting, then the screen would become scrambled (not static).  Then I installed nvidia-current using apt-get.  Now after the motherboard splash screen, I can see the Mythbuntu splash screen ("Mythbuntu" with five dots under it) then after a couple seconds it goes to static.

Interestingly, with this static on the screen, when I press the power button on my machine to turn it off, I see the Mythbuntu splash screen again as one normally would.

I have no idea what to check to make this work.  I'd be happy to provide further details if it will help diagnose things.

Thanks in advance.

---

### Post by alotau on 2011-11-24
Well, just struggling along on my own here.  Some more info if it can help anyone help me:

By playing with the nvidia setting gui, I can get the TV to act as a sort of 2nd monitor when my LCD monitor is also attached.  I save that xorg.conf file to /etc/X11/.  I think I chose "TwinView" as a setting option somewhere.

So I know the card can handle displaying to the TV (note previous entry describing the splash screens).  But when I try to boot with just the TV attached, the same problem occurs:  static fills screen after the Mythbuntu splash screen and stays until I power down, at which time the Mythbuntu splash screen reappears.

I have no idea what to do.  Was hoping to give this setup to family member tomorrow (Thanksgiving day).  Not looking good.

Any help appreciated.

---

### Post by nickrout on 2011-11-24
> **alotau said:**
> Well, just struggling along on my own here.  Some more info if it can help anyone help me:

By playing with the nvidia setting gui, I can get the TV to act as a sort of 2nd monitor when my LCD monitor is also attached.  I save that xorg.conf file to /etc/X11/.  I think I chose "TwinView" as a setting option somewhere.

So I know the card can handle displaying to the TV (note previous entry describing the splash screens).  But when I try to boot with just the TV attached, the same problem occurs:  static fills screen after the Mythbuntu splash screen and stays until I power down, at which time the Mythbuntu splash screen reappears.

I have no idea what to do.  Was hoping to give this setup to family member tomorrow (Thanksgiving day).  Not looking good.

Any help appreciated.

I guess you don't have any modern inputs on the TV (HDMI, DVI, component, vga)?

s-video won''t go over about 800x600, so what resolution are you trying to run it at? (Although if you overdrive the tv i would expect a black screen or destroying the TV rather than anything else.)

---

### Post by alotau on 2011-11-24
Hi Nick, thanks for the response.

> **nickrout said:**
> I guess you don't have any modern inputs on the TV (HDMI, DVI, component, vga)?

That is completely correct.  Only has the coax connection.

> 
s-video won''t go over about 800x600, so what resolution are you trying to run it at? (Although if you overdrive the tv i would expect a black screen or destroying the TV rather than anything else.)

I think I set it to 640X480, but it also seemed to work at higher resolutions.  I am getting output to the TV when both the monitor and TV are connected to the video card (though none of the Myth stuff goes to the TV, I just see like a desktop).  When I try to boot up with ONLY the TV connected am I having issues.

Any ideas?

---

### Post by nickrout on 2011-11-24
try looking at the X log file. /var/log/Xorg.0.log*

---

### Post by alotau on 2011-11-25
Just got back to a computer with Internet connection.  Thanks again for the response.

Anything in particular I should look for in that log file?

Just an added data point:  I was able to get the Mythbuntu front end working on the TV by using the Nvidia setup GUI and selecting the TV to be the primary display in "TwinView".  But this only worked if I had the monitor connected also.  Once I tried to boot with only the TV connected, the same problems arose.  This makes me feel like if I just had the correct, magical xorg.conf, then the setup will work.

I'll post again tomorrow after I have time to hook up the machine either to a monitor or a network connection.  The process has been hindered by the fact I only own one TV and one monitor and that I can only have the Mythbuntu machine hooked up to either the TV or the Internet, but not both.  Ugh.

Will follow-up tomorrow.

---

