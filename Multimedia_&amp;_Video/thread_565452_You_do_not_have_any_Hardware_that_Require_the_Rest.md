---
title: "You do not have any Hardware that Require the Restricted Drivers Manager"
date: 2007-10-02
forum: Multimedia &amp; Video
---

### Post by grunge09 on 2007-10-02
Well I have neem happily using Ubuntu for a few months.  But have been unhappy with Video performance since switching to a widescreen monitor.  

You have to manually edit the xorg.conf to add the extra widescreen resolutions.  And the monitor refresh rates.   After I went widescreen Totem quit as did Openoffice.  Got Floating Exception Point from Totem and OOffice got some kind of fault (can't remember).

My Rig is:

Amd x2 6000+ Stock Cooling
Asus m2n-e MB
Pny Optima 1 GB DDR2 Ram (42 dollar deal @ BB)
Vid Card is a a Sapphire 850 XT PCI Express 256 bit 256 MB GDDR3.  Monitor is Acer 22" Widescreen.
SB Audigy 2
WD SATA II 250 GB HD
DVD Rom Drive + DVD DRW 16x Drive

I had used Restricted Drivers Manager in Feisty to use the Fglrx Drivers.  I had heaard that the ATI Drivers were better.  Guess I should have left well enough alone.  But where is the fun in that.  :lolflag:

I had heard about Envy (ATI and Nvidia driver install).  So I unchecked the driver in restricted drivers manager.  Rebooted.   Downloaded the Envy DEB File.  double clciked on that and installed it, then had it automatically install the ATI Driver.  I thought the performance sucked.  So I used Envy to uninstall the ATI Driver.  Then went into Synaptic Package Manager and uninstalled Envy.  Another reboot.  

Now I go back to Restricted Drivers Manager and use that to re-install xorg fglrx drivers but to my suprise it says my harware is not necessary for the RDM.  Hmmm....I used terminal to re-install xorg fglrx drivers. antoher reboot.  RDM still does not work.  After editing the xorg.conf again for the widescreen resolutions now X loads but is blank.  

I CTRL-ALT-F2 to get to terminal prompt, change xorg.conf so it works.  I got X running again.  Re-installed Envy.  NOW RDM manager works.  I used Envy to manually install the ATI Driver and picked the newest driver.  Another reboot and FGLRX is working now.  Still have to edit the conf file for widescreen resolutions again.  

Totem works, as does open office.  I can understand why totem is tied to the video driver, but open office?  And it was weird that it was just those 2 programs that were affected.  

Maybe I will leave well enough alone for now.  :-\"

---

### Post by vinutux on 2007-10-02
i am using x700 from same vender the new graphical installer and controll center 4 linux available now just like windows............may it will help u


go to amd/ati site [http://ati.amd.com/support/driver.html]("http://ati.amd.com/support/driver.html")


and select linux - and select u r ati model ..................

and download it [more than 35-40 mb] 

right click on that.run file u r downloaded and give permission to execute

then double click it and install


it is worked for me........................:guitar:

---

