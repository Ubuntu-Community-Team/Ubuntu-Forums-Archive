---
title: "fullscreen pixelated in VLC"
date: 2008-07-26
forum: Multimedia Software
---

### Post by juanitobanana on 2008-07-26
Hello,

this is one of the few things holding me back from erasing windows completely (the other one is a crappy giga pocket for which AFAIK there are no drivers on linux)

When I play on fulllscreen on VLC, the image is pixelated. I tried a lot of things and read all the posts about it.

my graphic card:
lspci:  VGA compatible controller: ATI Technologies Inc RV380 0x3e50 [Radeon X600]

I have fglrx and fglrxinfo gives:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600/X550 Series
OpenGL version string: 1.4 (2.1.7412 Release)

which is correct.

I tried Mplayer and the same problem is there.
On VLC->Preferences->Video-> Output Modules ->video output module

the only ones really working are X11 Video output and Xvideo extension video output

(by the way if I disable alternate fullscreen method on X11, the image is slow)

I tried de-interlacing with no good results.

I assume my problems could be 2 things, since in Windows I get a correct image:
1) there is some parameter that would apply some aliasing or something, that I can't see
2) my fglrx drivers are not good enough for this kind of stuff

has anyone trid radeonHD drivers for this ATI card? just to be sure that is not the problem.

please help me I tried to make this as detailed as possible. My thread is probably related to 
[http://ubuntuforums.org/showthread.php?t=493901](http://ubuntuforums.org/showthread.php?t=493901)
and
[http://ubuntuforums.org/showthread.php?t=810291](http://ubuntuforums.org/showthread.php?t=810291)

the images are like described in [http://ubuntuforums.org/showthread.php?t=668208](http://ubuntuforums.org/showthread.php?t=668208)

I'll try to solve this as hard as I can and then go for the gigapocket thing, so I can hopefully erase my wondows XP

many thanks

---

### Post by markbuntu on 2008-07-26
Try some of the adjustments here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

VideoOverlay "off" 
OpenGLOverlay "off"

are probably the ones you want and the others will help speed things up.

If you want the latest 8.7 driver, the updated directions for installing it are here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)


There are also adjustments you can make in the Catalyst Control Center.

---

### Post by juanitobanana on 2008-07-30
none of those worked for my specific VLC problem (the rest worked just fine)

I installed ati open drivers (apparently better for older chips like mine r300) and everything worked smoothly, VLC is perfect now.

f^%$ck it that will learn me to avoid propietary blobs.

BTW I used this how-to:
[https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879](https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879)

thanks anyway

---

### Post by markbuntu on 2008-07-30
I am not so lucky, still waiting for the open source drivers to catch up with my card.

---

