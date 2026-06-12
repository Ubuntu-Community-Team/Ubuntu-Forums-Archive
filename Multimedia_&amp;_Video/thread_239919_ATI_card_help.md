---
title: "ATI card help"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by TheAxeR on 2006-08-20
I have finally given in and am posting for help, I have been trying to avoid having to ask for help because I know there is so much documentation on installing the ATI driver.  However, I have scoured the fourms and have not yet seen this problem, I hope I havn't just missed or overlooked it.  

So getting down to it, I am trying to install my ATI Radeon 9250 video card.  I have been trying to install the drivers for the past month ](*,) First, I tried using synaptic and that did not work.  Then,  I tried using Ati's graphical installer.  That didn't work. I then searched the forums and tried following the [sticky]("http://ubuntuforums.org/showthread.php?t=204910") in the Video and Sound forum.  And again that did not work.  Everytime I have actually had the same problem when rebooting the computer fails to load xorg everytime the error stated 'no matching device for instance BusId PCI:1:4:0' and the same for BusId PCI:1:4:1 then it says no devices detected. 

It seems to me that the problem is that it is not physically detecting the card.  Unfortunatly that is the best I can do.  Thank you for any help you guys can give.  Once I get this and more specifically the tvout on the card working it will be one less thing I need windows for.

---

### Post by reubadoob on 2006-09-04
I'm also interested in installing the same card. I've tried using the binary steps 

Seen Here:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

And Here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

But that did no luck. In the end I had to revert to the Xorg driver. My question to the audience is this:

Should I be installing the drivers before I put the card in the PCI slot? I think this has a alot to do with it because of the Intel Onbard Graphics. Because when I install the card with the computer off I have no luck getting my X windows back. Can some please submit some step by step instructions from card install to compiz/xgl running. :-D

---

### Post by stanz on 2006-09-05
Hi All...
Sorry to poke my nose in here...I'm no techie..
but, for TheAxeR; you type: BusId **PCI:1:4:0**' and the same for BusId **PCI:1:4:1** then it says no devices detected...
My Card-being PCI or AGP has always shown: [B]PCI:1:0:0
[/B]This i check in the: */etc/X11/xorg.conf *file and tweak for my liken.
Any problems that may arise at boot, I adjust by running command:
 *sudo dpkg -reconfigure -phigh xserver-xorg   *-then- *  sudo dpkg reconfigure xserver-xorg* 
If Dapper hasn't changed that. 
Did you cruize by [this sticky]("http://www.ubuntuforums.org/showthread.php?t=221320")? 

Hope ya find better help!

---

