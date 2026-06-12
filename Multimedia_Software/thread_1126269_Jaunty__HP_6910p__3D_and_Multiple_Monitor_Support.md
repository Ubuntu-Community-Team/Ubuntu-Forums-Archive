---
title: "Jaunty / HP 6910p / 3D and Multiple Monitor Support"
date: 2009-04-15
forum: Multimedia Software
---

### Post by webwiz on 2009-04-15
Greetings Team

I am running Jaunty 9.04 with the latest updates.  I have an HP6910P with an ATI Mobility Radeon X2300 video card.

This is a fresh install.  Usually the restricted driver manager would come up and detect I have an ATI Card, and then install the driver and I reboot, and voila it works.  But in this release,  the restricted driver manager doesn't detect my X2300 card.

I tried to install the driver by 'hand' using the apt-get install xorg-driver-fglrx  and I rebooted, and now my display shows the random colors and streaking (unable to see the desktop)

I now reboot into save mode console only,  and wondering what I can do to get my drivers working correctly

I would like to have 3D Support and Multiple monitor support, which worked out of the box (TM) in the past releases.

Thanks guys

---

### Post by markbuntu on 2009-04-15
Sorry, your card is not supported by the ati restricted driver 9.4 in Jaunty.

---

### Post by ilmar on 2009-04-25
Have same card and same problems. Webwiz, remove xorg-driver-fglrx from the console, and you will be able to normal boot.

Are there any open-source drivers avalaible or coming soon?

---

### Post by janne5011 on 2009-04-25
I got the same HP 6910p
with no 3D support.. bye to Ubuntu and back to vista. :(
Anyone know if this is will be solved?

---

### Post by ilmar on 2009-04-25
update:
found [ this]("http://www2.ati.com/drivers/linux/fglrx_6_8_0-8.28.8-1.i386.rpm")  package (need to convert it to *.deb, using alien). Package is wierd a bit, but it really tuned up performance in compiz and games

---

### Post by donaldchaves on 2009-04-27
I have a HP 6910p and everything works fine, video, audio, docking, sound card, wireless. 
Also i have noticed that theres a new driver from ATI, and i tried to installed it, but they did not work, however the 3d apps, such, compiz, and other ones, worked very well.


Hope this can be good.



Updated on Octuber 12th, 2009 by Me Donald.... after reading and trying many things i found a nice solution... It was fully tested by me on a HP 6910p and the only i could do it was to downgrade my Xserver....... for those of you who may have the same situation.. you have 2 choices... Blame ATI for not having an updated drivers or continue using the same defualt driver from the original installation.... It is up to you...also ...I've tried as well to test either Ati Catalys 9.8 and 9.9 due they are "suppost" to have suppor some Older Mobility Ati like mine.

 lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M64-S [Mobility Radeon X2300]

Very easy.
1.Sources.
2.Unistall few things.
3.Install new xserver.
4.Lock some packages with Synaptic or console.
4.Enable Ati Driver from "Hardware Drivers"
5.Restart. 

And i am pretty sure i will like to have a recent Xserver version however i have a very old Ati Video card that have been with me in games suck Quake4, Doom3 and Cedega. I still want to play some games fellas...

The link was taken by me on this post from some one i will have to say thank you....

[http://ubuntuforums.org/archive/index.php/t-1252015.html](http://ubuntuforums.org/archive/index.php/t-1252015.html)

---

### Post by ssri on 2009-05-09
> **markbuntu said:**
> Sorry, your card is not supported by the ati restricted driver 9.4 in Jaunty.

ATI/AMD's [_release notes_]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_94_linux.pdf") from Catalyst 9.4 (8.602) say that ATI Mobility Radeon X2300 chips in 6910p's are supported.  Tried it in intrepid with xserver 1.5.2, but came up empty.

---

### Post by donaldchaves on 2009-10-12
Updated on Octuber 12th, 2009 by Me Donald.... after reading and trying many things i found a nice solution... It was fully tested by me on a HP 6910p and the only i could do it was to downgrade my Xserver....... for those of you who may have the same situation.. you have 2 choices... Blame ATI for not having an updated drivers or continue using the same defualt driver from the original installation.... It is up to you...also ...I've tried as well to test either Ati Catalys 9.8 and 9.9 due they are "suppost" to have suppor some Older Mobility Ati like mine.

lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M64-S [Mobility Radeon X2300]

Very easy.
1.Sources.
2.Unistall few things.
3.Install new xserver.
4.Lock some packages with Synaptic or console.
4.Enable Ati Driver from "Hardware Drivers"
5.Restart.

And i am pretty sure i will like to have a recent Xserver version however i have a very old Ati Video card that have been with me in games suck Quake4, Doom3 and Cedega. I still want to play some games fellas...

The link was taken by me on this post from some one i will have to say thank you....

[http://ubuntuforums.org/archive/inde...t-1252015.html](http://ubuntuforums.org/archive/inde...t-1252015.html)
Last edited by donaldchaves; 1 Minute Ago at 05:53 PM..

---

