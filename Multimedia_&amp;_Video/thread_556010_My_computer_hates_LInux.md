---
title: "My computer hates LInux"
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by Het Irv on 2007-09-20
I have an ATI Radeon 9200. 

```
lspci
VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)

```

I cannot find Drivers that will work on 7.04.  I have tried the X.Org from Add/Remove Programs. Whenever I install them the program I am working on (right now it's Regnum Online) still won't work and the programs that do work stop working (i.e. OpenArena, Tremulous)

I have also tried ATI's proprietary ones from [here]("http://http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html") but when installing I get this error.

```
grail@grail-desktop:~$ /home/grail/Desktop/Installs/ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8..................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

```

I hope this is enough Information to solve this problem.

---

### Post by d_iane1954 on 2007-09-20
i think the easiest way of getting drivers is downloading envy and using it!!!!! hope this helps you.

---

### Post by Het Irv on 2007-09-20
I have just tried that 

ENVY Error: ATI's legacy driver does not support your operating system.

My computer still hates Linux.
I there a way I can Download the files needed to make it work and if so where are they?

---

### Post by w4ett on 2007-09-20
Your card is not supported by the ATI proprietary (restricted) driver fglrx...it IS supported by the xorg driver ati:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

To select the correct driver start by reconfiguring your xorg.conf.....boot into recovery mode.

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"] "ati"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This driver DOES support 3D and will give you a glxgears framerate og +/-900 fps and is Compiz Fusion capable....(I'm running a 9200SE now with CF enabled)

Good Luck

---

### Post by Het Irv on 2007-09-21
Last night I tried intsalling the envy drivers Manually and I think It came to a point were it needed to config the Xserver.  Now I cannot boot to the GUI but I can boot in recovery mode I just don't know how to fix it. Any Ideas?

Edit: nvm w4ett can read minds and the above post fixed that problem.  But it doesn't fix my original problem

---

### Post by w4ett on 2007-09-21
> **Het Irv said:**
> Last night I tried intsalling the envy drivers Manually and I think It came to a point were it needed to config the Xserver.  Now I cannot boot to the GUI but I can boot in recovery mode I just don't know how to fix it. Any Ideas?

Edit: nvm w4ett can read minds and the above post fixed that problem.  But it doesn't fix my original problem

Yea, well like I said before, the fglrx drivers won't work with your card......neither is it game capable in linux....

It will work for light duty 3D applications like Google Earth and it is compiz capable, but for gaming, you are going to have to upgrade your card.  Currently Nvidia has the best driver support and better gaming capabilty, but AMD/ATI has released new drivers this month, and the next release of their drivers (which will support aiglx) are due out in October.  

The problem is that the ATI legacy card drivers aren't considered important by the manufacturer...(case in point..the last 9200 card I bought was $4.75 new in box) so there is no monetary incentive to upgrade drivers for cards that are not in production.....At this point, even the 9800 cards are available new for less than $20, so I don't expect much support for the RV2XX based cards for much longer.

---

