---
title: "Installing a pci graphics card in a computer with onboard graphics"
date: 2006-08-30
forum: Multimedia &amp; Video
---

### Post by madsporkmurderer on 2006-08-30
I am trying to get an old computer to output to a tv in order to use it as a bit of a crap media center, it has onboard graphics but no tv-out. To remedy this I am tryying to install a pci graphics card with tv-out. 

The problem is that if I select the BIOS option of "primary video controller=onboard" it, suprisingly enough, uses the onboard chip, but if I choose the only other option "auto" it uses the pci card from power on until the end of the ubuntu loading screen then displays a blank, black screen.

The computer is a Dell OptiPlex GX110 with intel 82810e dc-133 cgc graphics controller and the pci card is a SiS 6326 8Mb PCI.

Is there a way to use the pci card instead of the onboard graphics?

---

### Post by Jose Catre-Vandis on 2006-08-31
Seems like you have your bios sorted out, but that xorg.conf is still looking for the on board card to provide settings for. I suggest you put the bios back to on board, then have a look at the settings in /etc/X11/xorg.conf for your monitor.

You could also try booting in recovery mode which will bring you to a command prompt then you can reconfigure the xserver:
```
 sudo dpkg-reconfigure xserver-xorg 
```
This will take you through the steps you hopefully need to get your new pci card going. Aim low to start off with so try not to go for high resolutions and high colours, suggest 800x600 and 16m colours. If this works you can then up things a bit if your card can take it.

---

### Post by tseliot on 2006-08-31
> **madsporkmurderer said:**
> I am trying to get an old computer to output to a tv in order to use it as a bit of a crap media center, it has onboard graphics but no tv-out. To remedy this I am tryying to install a pci graphics card with tv-out. 

The problem is that if I select the BIOS option of "primary video controller=onboard" it, suprisingly enough, uses the onboard chip, but if I choose the only other option "auto" it uses the pci card from power on until the end of the ubuntu loading screen then displays a blank, black screen.

The computer is a Dell OptiPlex GX110 with intel 82810e dc-133 cgc graphics controller and the pci card is a SiS 6326 8Mb PCI.

Is there a way to use the pci card instead of the onboard graphics?
Try this guide:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

You don't need to put NvAgp, you can also skip point 5.

The rest of that guide should work with your card (even if it's not nvidia)

---

### Post by madsporkmurderer on 2006-08-31
using Jose Catre-Vandis' method all works fine until selecting the monitor colour depth, whatever is chosen I get put back to the command line with error:

"xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20060831035218"

It then gives no option to continue regardless

EDIT: Don't worry, I got it working with a clean install of mandriva 2006.

---

### Post by Jose Catre-Vandis on 2006-09-01
That warning is just about the overwriting of the old xorg.conf file with the new one. The old one gets backed up in the same directory so no real problem. SHould just be a press on the Return key to move on.

Worth checking your xorg.conf (or similar) in Mandriva and saving it out somewhere. Might help with future configs when you come back to Ubuntu :lol:

---

