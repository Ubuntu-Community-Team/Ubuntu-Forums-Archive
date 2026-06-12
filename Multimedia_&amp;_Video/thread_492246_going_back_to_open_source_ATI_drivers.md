---
title: "going back to open source ATI drivers"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by ajpug on 2007-07-04
When I first installed Ubuntu Feisty (fresh install), the included ATI drivers worked like a charm (had only to fix resolution). Installed Beryl and that also worked perfectly. Then I read somewhere that in order to have 3D acceleration enabled, I had to install the FGLRX drivers. So I made a backup copy of Xorg.conf and installed teh fglrx drivers by using the option included in the VMware player (you can select to install those drivers from their application). After doing so I restarted the the machine and all I had was a blank screen.

As the next step I re-enabled my backup copy of Xorg.conf (the one with "ati") and everything came back on. HOWEVER, Beryl does not work any more. Or to be more precise, when I select Beryl from the Beryl manager, it seems like something is going to happen but then it forces itself back to Metacity.

Any idea of what is going on?

Thanks,
ajpug

---

### Post by HuwSy on 2007-07-04
the propriatory drivers overwrite libgl with a custom version. at the bottom of the guide on the following page it says how to replace this.
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by ajpug on 2007-07-04
I have followed the instruction on the link  you suggested. After doing that I rebooted and the Xserver failed to crash giving me the following errors:

(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1)
(EE) RADEON(0): MergedFB does not work with Option UseFBDev, MergedFB mode is disabled
(EE) RADEON(0): mmap mmio: Invalid argument

Fatal server error:
AddScreen/ScreenInit failed for driver 0


After this I edited the Xorg.conf according to my backup copy. That is, I added ' Load    "i2c" ' in the 'Module' section and removed ' Option          "UseFBDev"              "true" ' from the ' Device ' section.

After doing this, the Xserver started fine but I still have the same problem with Beryl and the Beryl manager.
Metacity is forced anytime I try to change to Beryl. The odd thing is that if I try to change to Compiz, it changes just fine.

Any idea?

Thanks,
ajpug

---

### Post by HuwSy on 2007-07-05
Hum... not sure, attached is my xorg.conf incase theres anything in there that might help.  But i dont remember changing anything more after getting compiz working.

---

### Post by sam0t on 2007-07-05
Total newbie in these matters but I looked at you xorg.conf and there are some stuff missing, if you compare to this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)


I have used that guide many times and everytime I have gotten my 3D acceleration working, including Beryl. Atleast you don´t have these in the bottom of your xorg.conf:

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

---

### Post by HuwSy on 2007-07-05
Nah mine works fine with beryl, its there incase anyone can spot anything that iv added that they might need to get beryl working on theres. The only things missing from it are the odd few options such as overlays which are specifig to fglrx and xxa acceleration which disagrees with my system setup for various reasons.

---

### Post by stchman on 2007-07-05
> **ajpug said:**
> When I first installed Ubuntu Feisty (fresh install), the included ATI drivers worked like a charm (had only to fix resolution). Installed Beryl and that also worked perfectly. Then I read somewhere that in order to have 3D acceleration enabled, I had to install the FGLRX drivers. So I made a backup copy of Xorg.conf and installed teh fglrx drivers by using the option included in the VMware player (you can select to install those drivers from their application). After doing so I restarted the the machine and all I had was a blank screen.

As the next step I re-enabled my backup copy of Xorg.conf (the one with "ati") and everything came back on. HOWEVER, Beryl does not work any more. Or to be more precise, when I select Beryl from the Beryl manager, it seems like something is going to happen but then it forces itself back to Metacity.

Any idea of what is going on?

Thanks,
ajpug

The restricted drivers do enable OpenGL.  Enable the restricted drivers and run glxgears to confirm.  The fact that Beryl works proves that OpenGL is working.

---

### Post by HuwSy on 2007-07-05
The opensource drivers run glxgears too, not quite as fast as fglrx. But iv noticed some apps, like stelarium and the odd few games dont like fglrx on my computer atleast. Anyone know if theres any difference in the o.gl api from the applicatuion side of these drivers?

---

### Post by ajpug on 2007-07-05
I was able to finally get the open-source drivers to work with Beryl again by completely uninstall the fglrx drivers via synaptic. 
Unfortunately, after that I installed google earth and realized that I really need fglrx at least until the open-source drivers do not support 3d acceleration.

This is a big BUMMER since the fglrx drivers gave me just a blank screen. I have read posts around but no one seems to match my case. Do you know of any tweaking necessary to do after installing the fglrx drivers? ... like I said, all I get is a blank screen :(

Thanks a lot,
ajpug

---

### Post by Melcar on 2007-07-05
Did you try the [wik]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")i?  That's how I got mine to work in Feisty.

---

