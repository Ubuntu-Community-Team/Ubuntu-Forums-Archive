---
title: "Is it ATI or am I just not getting it..."
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by niagara-joe on 2007-03-14
I have tried to install the ATI drivers for my X1650 AGP 3 times now and each time when I reboot my monitor goes out of sync and I can't see X Can someone give me instructions on how to get rid of the ATI and restore the old MESA so I can try it yet again???:lolflag:

---

### Post by dreadlord_chris on 2007-03-14
You can boot to a command shell, right?

```
sudo dpkg-reconfigure xserver-xorg
```

then under Driver select **vesa**, go through the rest of the dialogs answering for your hardware, save & reboot...

Getting rid of the ATI drivers you installed will depend on how you installed them...

---

### Post by jdzitro on 2007-03-15
I've tried to install ATI drivers for weeks. I think I have tried everything. Once I restart X org or even the computer entirely and then try to verify they were installed correctly, they weren't. 

I have been going off of these instructions
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

AND
If I go back to Xorg {sudo dpkg-reconfigure xserver-xorg} and restore {sudo apt-get install --reinstall libgl1-mesa} does that mean that I just can't have updated ATI drivers??

*cries* I don't understand.

---

### Post by AR_Kozz on 2007-03-15
When I first tried to install the ATI drivers manually it never worked either. Finally I reinstalled Ubuntu with the card in socket and the freesource drivers installed just fine. However I never got the fglrx installed myself either. Finally I used a utility called Envy, you'll find on these forums, that can install and uninstall the proprietary ATI (fglrx) automatically. It looks crappy except on my TV,  but it installed. It might get you somewhere, at least.

---

### Post by jdzitro on 2007-03-15
Thanks for the tip!
*hopeful*

---

### Post by jdzitro on 2007-03-15
So I used Envy to install ATI drivers. I went with the "automatic" install (I guess to be on the safe side). 
I restarted the comp.... the Ubuntu loading screen loaded all the way through the progress bar.... screen flickered and then no signal. Monitor is always plugged into the vid card itself so I tried plugging it into the mobo output. Still nothing.

It really blows having to run off the CD....


Can I roll back? How? I can't install Envy while running the live CD.

---

### Post by dreadlord_chris on 2007-03-15
> **jdzitro said:**
> So I used Envy to install ATI drivers. I went with the "automatic" install (I guess to be on the safe side). 
I restarted the comp.... the Ubuntu loading screen loaded all the way through the progress bar.... screen flickered and then no signal. Monitor is always plugged into the vid card itself so I tried plugging it into the mobo output. Still nothing.

It really blows having to run off the CD....


Can I roll back? How? I can't install Envy while running the live CD.

Boot into Recovery Mode

type envy <ENTER>

Uninstall the drivers

---

### Post by niagara-joe on 2007-03-15
Thanx fo rthe help guys, next time I will be a little more clear. When I restarted after installing the driver my monitor went out of sync.  I was able to get is going though.  I realized that the default monitor in the xorg.conf had a vertical sync and horizontal sync. I just had to enter the Vertical sync and Horizontal sync for my monitor in xorg.conf under the ati monitor section and "Voila!" X works awesome.

Thanx again for all the tips though.  

Now that my video works, I have to find out why my sound, which was working is not now!!!!:confused:

---

### Post by jdzitro on 2007-03-16
.....wait - horizontal and verical sync? What did you put in the configuration file to correct? My monitor kept going out of sync too. Maybe THIS is the problem I keep having.

---

### Post by doobydave on 2007-03-16
Might be a little late for this hint, but if the login screen is in an incorrect resolution then you can use CTRL ALT + or CTRL ALT - to scan through resolutions.

The other possibilty is the crappy fglrx drivers have caused x to hang.

---

