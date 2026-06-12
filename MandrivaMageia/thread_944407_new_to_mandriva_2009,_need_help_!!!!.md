---
title: "new to mandriva 2009, need help !!!!"
date: 2008-10-11
forum: Mandriva/Mageia
---

### Post by smooth3006 on 2008-10-11
first off i love mandriva so far but i have alot of questions as this is much different from ubuntu.


what are the most common terminal commands ? in ubuntu it is apt-get or sudo su, etc.... 


the system does not seem to pick up my nvidia gpu correctly. it says i have 256 ram when i have on 64. also in the drivers it does not list my geforce 7150m only the option for geforce 6100 or later or geforce 7050 ? which should i use ?

can you guys recommend any needed apps ? such as for video, audio players, p2p, etc....

one more thing, how can i get my lexmark x1270 all in one to work ?

---

### Post by SuperSonic4 on 2008-10-11
I'm not sure on the X server mine (8500GT) worked out of the box. What happens if you go into the Mandriva Control Centre and under the hardware tab press configure the graphical X server?

For root access in terminal type **su**
To give gui access as root type **su -**
sudo command is pretty much **su -c 'command'**
apt can be installed from the repos if you like but I wouldn't
I usually use the GUI to get new programs but from terminal you can type **urpmi packagename** as root.

[Installing and Removing software: Mandriva Wiki]("http://wiki.mandriva.com/en/Docs/Basic_tasks/Installing_and_removing_software")

For apps can you not use the same ones as in ubuntu? These are KDE apps for the most part since I run KDE on mandriva.

Amarok - 1.4.10, Available in main backports
KMess - 2 alpha 2, Needs to be compiled as SVG but version 1.5 is in the repos or from the kmess site.
VLC - 0.93
Mplayer with SMplayer frontend
deluge 1.0.0 for p2p
firefox for web browsing

As for the all in one what does the set up a printer tab say (i think it's the hardware tab). The MCC is a lovely tool :p

---

### Post by AdamWill on 2008-10-11
As I wrote in the other thread, just pick "6100 or later". For the printer, follow SuperSonic's instructions, but also see:

[http://wiki.mandriva.com/en/2009.0_Errata#Printer_configuration_tool_not_installed_by_default_in_One_editions](http://wiki.mandriva.com/en/2009.0_Errata#Printer_configuration_tool_not_installed_by_default_in_One_editions)

for apps, again I agree with Sonic, why not just use whatever you liked on Ubuntu?

---

### Post by smooth3006 on 2008-10-11
> **SuperSonic4 said:**
> I'm not sure on the X server mine (8500GT) worked out of the box. What happens if you go into the Mandriva Control Centre and under the hardware tab press configure the graphical X server?

For root access in terminal type **su**
To give gui access as root type **su -**
sudo command is pretty much **su -c 'command'**
apt can be installed from the repos if you like but I wouldn't
I usually use the GUI to get new programs but from terminal you can type **urpmi packagename** as root.

[Installing and Removing software: Mandriva Wiki]("http://wiki.mandriva.com/en/Docs/Basic_tasks/Installing_and_removing_software")

For apps can you not use the same ones as in ubuntu? These are KDE apps for the most part since I run KDE on mandriva.

Amarok - 1.4.10, Available in main backports
KMess - 2 alpha 2, Needs to be compiled as SVG but version 1.5 is in the repos or from the kmess site.
VLC - 0.93
Mplayer with SMplayer frontend
deluge 1.0.0 for p2p
firefox for web browsing

As for the all in one what does the set up a printer tab say (i think it's the hardware tab). The MCC is a lovely tool :p

my laptop has a 7150m gpu. under x server it says it is a 6100 ? when i look under nvidia control panel it lists the correct gpu but the memory is not 256, it should be at 64. why won't my card work out of the box ? i wish envy would work for mandriva. this is a pain in the butt, my gpu is very common for laptops.

---

### Post by TeaAge on 2008-10-11
> **smooth3006 said:**
> first off i love mandriva so far but i have alot of questions as this is much different from ubuntu.


what are the most common terminal commands ? in ubuntu it is apt-get or sudo su, etc.... 


the system does not seem to pick up my nvidia gpu correctly. it says i have 256 ram when i have on 64. also in the drivers it does not list my geforce 7150m only the option for geforce 6100 or later or geforce 7050 ? which should i use ?

can you guys recommend any needed apps ? such as for video, audio players, p2p, etc....

one more thing, how can i get my lexmark x1270 all in one to work ?

For your graphiccard: Take the entry that is already chosen. Important is the graphicchips and the detection tool makes the right decision.
Simply click "Next" in the list of graphic cards and will be hopefully asked if you want to use the proprietary driver.

I think you have installed the One Edition?
If so, install the package 'system-config-printer'. After that, plug your printer and the printer will be configured automatically. If not, go to the Mandriva Control Center  > Hardware > Configure your printer
Does this work?

For your repositories:
The most important sources are already configured. You can also set up PLF media. Which will give you access to some codecs and libdvd2css ...
To set up those, go to [http://easyurpmi.zarb.org/](http://easyurpmi.zarb.org/) and choose "Add PLF medias".

Regards,
TeaAge

---

### Post by smooth3006 on 2008-10-11
> **TeaAge said:**
> For your graphiccard: Take the entry that is already chosen. Important is the graphicchips and the detection tool makes the right decision.
Simply click "Next" in the list of graphic cards and will be hopefully asked if you want to use the proprietary driver.

I think you have installed the One Edition?
If so, install the package 'system-config-printer'. After that, plug your printer and the printer will be configured automatically. If not, go to the Mandriva Control Center  > Hardware > Configure your printer
Does this work?

For your repositories:
The most important sources are already configured. You can also set up PLF media. Which will give you access to some codecs and libdvd2css ...
To set up those, go to [http://easyurpmi.zarb.org/](http://easyurpmi.zarb.org/) and choose "Add PLF medias".

Regards,
TeaAge

i already added the plf media with that link yesterday. no my printer is detected but won't work as there is no driver for it. i think i have to install the z600 drivers ? pretty much the same as in ubuntu. im just shocked mandriva doesn't pick up on the proper driver for my nvidia gpu. it works but i don't think it is configured right. i miss envy, lol. 

in ubuntu you have software sources where you can choose to update backports and such. how does this work with mandriva ? 

im a total noob right now.

---

### Post by AdamWill on 2008-10-11
smooth: it's configured right. Trust me on this. I maintain the graphics card driver detection tables, so I know. :) I spend several hours each release cycle with my head stuck in various obscure bits of NVIDIA documentation and driver sources to get it right. We have better graphics card detection than anyone else, actually.

The point is, I don't bother having a differently named entry for *every single video card ever*. Life's too short and it'd be a pain to maintain. In practice, many different cards share the same driver settings, so I group cards together.

For NVIDIA cards, all cards from the GeForce 6100 onwards use the exact same driver settings. They use the 177.xx proprietary driver, or the nv free driver. There's no need for every one of these cards to have its own separate named entry in the list, because they all use the exact same settings. So there's just a big group labelled 'GeForce 6100 and later' which covers all these cards. That's what your card is detected as: it's not detected as an actual 'GeForce 6100', just as an NVIDIA card that's a GeForce 6100 or newer.

I don't know why (or what) is showing your card as having more memory than it actually has, but it's not anything Mandriva-specific. Mandriva's tools do not care how much memory your graphics card has, they never bother even trying to find out. All they care about is the model of the card. If you say exactly what tool is getting it wrong I can take a look, but I don't think it will be affecting things at all.

edit: oh, I see now it's the NVIDIA control panel. I don't know why it would think that, but that's down to NVIDIA, not us. We don't do anything odd to it.

For backports, see: [http://wiki.mandriva.com/en/Docs/Basic_tasks/Installing_and_removing_software#Advanced_use:_Backports_and_candidate_updates](http://wiki.mandriva.com/en/Docs/Basic_tasks/Installing_and_removing_software#Advanced_use:_Backports_and_candidate_updates)

---

### Post by smooth3006 on 2008-10-11
> **AdamWill said:**
> smooth: it's configured right. Trust me on this. I maintain the graphics card driver detection tables, so I know. :) I spend several hours each release cycle with my head stuck in various obscure bits of NVIDIA documentation and driver sources to get it right. We have better graphics card detection than anyone else, actually.

The point is, I don't bother having a differently named entry for *every single video card ever*. Life's too short and it'd be a pain to maintain. In practice, many different cards share the same driver settings, so I group cards together.

For NVIDIA cards, all cards from the GeForce 6100 onwards use the exact same driver settings. They use the 177.xx proprietary driver, or the nv free driver. There's no need for every one of these cards to have its own separate named entry in the list, because they all use the exact same settings. So there's just a big group labelled 'GeForce 6100 and later' which covers all these cards. That's what your card is detected as: it's not detected as an actual 'GeForce 6100', just as an NVIDIA card that's a GeForce 6100 or newer.

I don't know why (or what) is showing your card as having more memory than it actually has, but it's not anything Mandriva-specific. Mandriva's tools do not care how much memory your graphics card has, they never bother even trying to find out. All they care about is the model of the card. If you say exactly what tool is getting it wrong I can take a look, but I don't think it will be affecting things at all.

edit: oh, I see now it's the NVIDIA control panel. I don't know why it would think that, but that's down to NVIDIA, not us. We don't do anything odd to it.

For backports, see: [http://wiki.mandriva.com/en/Docs/Basic_tasks/Installing_and_removing_software#Advanced_use:_Backports_and_candidate_updates](http://wiki.mandriva.com/en/Docs/Basic_tasks/Installing_and_removing_software#Advanced_use:_Backports_and_candidate_updates)


the only thing that is really keeping from mandriva right now is i can't get my lexmark x1270 to work at all. i can get it to work very easily in ubuntu with 2 deb installs. :confused:

---

### Post by Antman on 2008-10-11
> **smooth3006 said:**
> the only thing that is really keeping from mandriva right now is i can't get my lexmark x1270 to work at all. i can get it to work very easily in ubuntu with 2 deb installs. :confused:
Try installing this package:
**task-printing-lexmark**

---

### Post by AdamWill on 2008-10-12
What happens if you just try and configure it via the printing config tool (system-config-printer , as it is now)?

---

