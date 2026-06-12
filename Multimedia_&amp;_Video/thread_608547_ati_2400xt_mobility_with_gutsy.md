---
title: "ati 2400xt mobility with gutsy"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by mwolfe on 2007-11-10
anyone have a 2000 series ati card on a laptop and have the fglrx drivers working? I've tried the ubuntu way and the manual way using the newest drivers (8.42.3) and no luck. It always says mesa when i try the fglrxinfo command.. Any ideas? I have an ati 2400xt mobility in this laptop.

lspci just gives me
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c8
01:00.1 Audio device: ATI Technologies Inc Unknown device aa10

related to the card.. Looks like linux isn't quite ready for this card.. Hopefully in a few months an ati driver will work with my system.. 
What about upgrading my kernel to the newest? Any idea if that would help?

---

### Post by Yellow Pasque on 2007-11-10
Did you try the raeonhd driver?

Also try running:
```
sudo update-pciids
```
to see if those PCI devices have names in the database yet. Then try lspci

---

### Post by mwolfe on 2007-11-14
Thanks for the ideas.
Unfortunately i tried the radeonhd driver and it broke my video altogether.. I'm not sure if i had all remnants of the standard radeon driver out of the system though correctly so most likely something got messed up.. Also i'm not even sure if i installed the radeonhd driver correctly. 
Is there a tutorial for how to install the radeonhd driver?? I didnt see one although the poster said that he was going to write up an install guide.

So now my questions are: if X doesnt start how do i get back to normal?
and, does anyone have instructions for installing the radeonhd driver?

Thanks.

---

### Post by mwolfe on 2007-11-15
alright so i found a tutorial on installing the radeonhd driver in ubuntu here:
[http://www.phoronix.com/scan.php?page=article&item=843&num=1](http://www.phoronix.com/scan.php?page=article&item=843&num=1)

I followed the steps but after tring to restart x my screen froze and i could not get into ubuntu.. I restarted the computer but i couldnt get it to load into gdm, the screen was blank and pressing control+alt+f1 didnt work or any other combination i could think of.. So i started in the safe mode (whatever its called, i forget) for ubuntu and then changed the driver back to vesa and then it loads again..
I installed the newest radeon driver also and it works ok except it says its still using mesa and it scrolls really slow. However it gives me 1280x800 which is my screens native resolution. If i dont install the radeon driver i do not get the option for this resolution and so everything looks distorted..

What i'd like to do while waiting for radeonhd driver to become stable is use the vesa driver and use 1280x800 since it didnt scroll really slow like the radeon driver does.
Is there an easy way to do this?

I found this: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
tutorial and ran through it but after running the command
 sudo dpkg-reconfigure -plow xserver-xorg
and following the instructions my display looked all messed up so i reverted the xorg file to the original.

GRR i wish this damn laptop had come with an nvidea card.

---

### Post by mwolfe on 2007-11-16
has anyone got a 2400 mobility working with the regular fglrx drivers? Mine always say mesa.. But i thought i read somewhere that this card was supported by the newest fglrx drivers? Help please. 
Scrolling on this thing is absurdly slow and it drives me nuts. I don't have compiz on or anything either.

---

### Post by markoloka on 2007-11-17
I have 2400HD card. It took while but i managed to get it working...only problem is that i have still some problems... like i need to ctrl+alt+backspace every once in while to get x start.

Anyway... how i did installation... i used this guide, manual part of it: 
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

What made my thing work was this: 
Compile kernel module:
sudo module-assistant prepare,update
sudo module-assistant build,install fglrx -f
sudo depmod -a

I had to do it 2 times. Second time after reboot if i remember correctly. 
Look also help from: [http://www.phoronix.com/forums/forumdisplay.php?f=19](http://www.phoronix.com/forums/forumdisplay.php?f=19)
For doing that kernel module thing i found hint from this: 
[http://didier.misson.net/didier/index.php?2007/09/23/140-ubuntu-gutsy-710-et-driver-ati-radeon-hd-2400-pro](http://didier.misson.net/didier/index.php?2007/09/23/140-ubuntu-gutsy-710-et-driver-ati-radeon-hd-2400-pro)
  

Hope this helps at least a bit.

---

### Post by zbyszek_zbl on 2007-11-19
Hi
I have Acer 7520 with ATI mobility Radeon HD 2400XT and 64bit Gutsy. In my case just after install I had vesa driver. I've used envy. On the beginning I've (just in case) removed old ATI drivers. Then I've chosen manual install and te newest fglrx driver. The last thing I had to do was to add 1440x900 (resolution of my laptop's LCD) to modes in xorg.conf and add Option "Composite" "Enable" to enable compiz. During installation Envy has automatically changed vesa to fglrx and added two lines to Section "Device": 
Option	"VideoOverlay" "on"
Option	"OpenGLOverlay" "off"
For me it works. I have proper resolution and compiz working.
For now I have three more problems with this card to resolve:
1. When I want to change brightnes LCD of my laptop is flickering
2. I can't enable external monitor output
3. When I have compiz enabled I can't watch movies in Totem, mplayer or VLC - they are flickering. The same with some games. Disabling compiz removes problem but it is a bit annoying to change desktop effects every time I want to watch a movie...

---

