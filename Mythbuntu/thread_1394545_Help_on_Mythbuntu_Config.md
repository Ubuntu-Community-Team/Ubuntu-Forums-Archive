---
title: "Help on Mythbuntu Config"
date: 2010-01-30
forum: Mythbuntu
---

### Post by Jojok on 2010-01-30
[FONT=Calibri][SIZE=3]Hi I am new to HTPC, I have done some research and come up with a configuration,  can you tell me if there are any known issues with any of these and mythbuntu ?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]CPU : AMD Athlon AM3 2.5GHZ
Motherboard: ASUS M4A78-EM
HD : WD 1tb Green
Wifi Card : Linksys PCI WMP600N
DVD:  MSI DVD writer DH-34AAS-17
Mem : Corsair XMS2 (2x1GB) DDR2
Remote: Streamzap PC remote
Case: Apex M DM-387  (275 W power supply ???)
Audio/Video - onboard[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I am not planning to use any TV tuner card now just want to use this to store all my videos  and music files and also use YouTube etc.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]My current setup is an Panasonic 42” TH-42PX75U  (Plasma)  connected to Onkyo receiver via HDMI.  I am hoping this  HTPC can be connected to the same receiver so I don’t need to rewire or remove anything from  the wall mounted TV. Does this work ?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I did see  some issues  on audio via HDMI and that issue is resolved right?.  I have installed unbuntu  before on normal computer  . Can I use the plasma TV as my monitor during the initial setup and also use the wifi card from the startup? or I use a regular monitor and connect the Ethernet port on the motherboard and then configure xorg for the TV and also manually configure the Linksys card?. I am hoping I can configure it to work with my onkyo receiver ( TX-SR605) it has HDMI switching and up conversion.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Another wish is to use the remote to shutdown the system. If this setup is successful, the next step would be to add  two  TV tuner cards; I have dish network with DVR and dual-LNB dish (hope this works out) and reconfigure this system as backend and add an other front-end diskless PXE boot .[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Sorry for the long post and I know I am asking too much here, I have only worked  with regular ubuntu server type systems and other linux distros, AV stuff is relatively new to me….[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Thanks [/SIZE][/FONT]

---

### Post by laffinet on 2010-01-31
> **Jojok said:**
> [FONT=Calibri][SIZE=3]Can I use the plasma TV as my monitor during the initial setup and also use the wifi card from the startup? 

Should work. Easiest way to check is download the mythbuntu install CD and boot into the live environment. It should recognise your TV as the display.
You obviously need to configure your wifi conenction but provided the wifi card works under ubuntu (google ;-)): yes.

> **Jojok said:**
> Another wish is to use the remote to shutdown the system.

Can be done. One example is [here]("http://ubuntuforums.org/showthread.php?t=1105817"). Just swap "reboot" with "shutdown".
Once you have tuners you might want to look into automatic shutdown (so your machine comes back up for scheduled recordings. Many guides around, just google "acpi wakeup mythtv". [Here's]("http://ubuntuforums.org/showthread.php?t=1072905&page=4") what I did.

---

### Post by nickrout on 2010-01-31
sounds good to me, but some issues you may hit:

[LIST=1]
[*]audio over hdmi does not work on all chipsets, do some searches on your particular hardware on the mythtv-users mailing list and/or ask there.

[*]the onkyo amp probably does NOT pass thru the edid info from your panasonic monitor, you may need to plug straight into the tv to get a good X setup, then use that when plugged into the amp.

[*]Hard to know if that wireless chipset works with linux, but if you plan at all to be transferring your media over the network (eg remote frontends, NAS etc) then do yourself a favour and run cables! If its just for getting epg info and doing system updates you will be fine with wireless.

[*] do yourself another favour and get an nvidia graphics card capable of vdpau[/LIST]

---

### Post by Jojok on 2010-02-02
[QUOTE=laffinet;8756073]Should work. Easiest way to check is download the mythbuntu install CD and boot into the live environment. It should recognise your TV as the display.
You obviously need to configure your wifi conenction but provided the wifi card works under ubuntu (google ;-)): yes.
 
Thats the plan and if the wifi works out of the box with live CD thats helps a lot

---

### Post by Jojok on 2010-02-02
> **nickrout said:**
> sounds good to me, but some issues you may hit:

[LIST=1]
[*]audio over hdmi does not work on all chipsets, do some searches on your particular hardware on the mythtv-users mailing list and/or ask there.
[/LIST][SIZE=3][FONT=Calibri][COLOR=#0d0d0d]The audio chipset is [/COLOR][COLOR=#0d0d0d][FONT=Arial]ALC887,  and video chip is ATI Radeon HD3200   did some further research, there are issues but most of them got solved by the  radeonhd drivers. Will see[/FONT][/COLOR][/FONT][/SIZE]
[LIST=1]
[*]the onkyo amp probably does NOT pass thru the edid info from your panasonic monitor, you may need to plug straight into the tv to get a good X setup, then use that when plugged into the amp.
[/LIST][COLOR=#0d0d0d][FONT=Arial][SIZE=3][FONT=Calibri]I believe that is the case on edid, I am planning to connect directly to the tv first .  I am not sure whether I need to manually configure the  Xorg[/FONT][/SIZE][/FONT][/COLOR]
[LIST=1]
[*]Hard to know if that wireless chipset works with linux, but if you plan at all to be transferring your media over the network (eg remote frontends, NAS etc) then do yourself a favour and run cables! If its just for getting epg info and doing system updates you will be fine with wireless.

[/LIST][SIZE=3][COLOR=#0d0d0d][FONT=Arial][FONT=Calibri]If the wireless doesn’t work I will connect to the Ethernet port to do the install, but I need to get the wireless working eventually, There is no way I can wire to the place where the tv is [/FONT][/FONT][/COLOR][COLOR=#0d0d0d][FONT=Wingdings][FONT=Wingdings]L[/FONT][/FONT][/COLOR][COLOR=#0d0d0d][FONT=Arial][FONT=Calibri]. I am planning to use webmin  for transferring media etc once everything is set up.[/FONT][/FONT][/COLOR][/SIZE]
[LIST=1]
[*]do yourself another favour and get an nvidia graphics card capable of vdpau
[/LIST][COLOR=#0d0d0d][FONT=Arial][SIZE=3][FONT=Calibri]That’s the ‘plan B’  and I am also looking to see if there is a motherboard that has vdpau support and builtin HDMI port, any suggestions ?[/FONT][/SIZE][/FONT][/COLOR]

 
[COLOR=#0d0d0d][FONT=Arial][SIZE=3][FONT=Calibri]That’s the ‘plan B’  and I am also looking to see if there is a motherboard that has vdpau support and builtin HDMI port, any suggestions ?[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by nickrout on 2010-02-02
Avoid using a radeon card at all costs.

don't know of any motherboards with vdpau capable chipsets on but there definitely are some about. dvi out may give you what you want too.

---

### Post by Jojok on 2010-02-03
Yes.. trying to settle on this one  has onboard HDMI and Nvidia 8200 chip that supports vdpau**[[COLOR=#004b91]ASUS M3N78-VM [/COLOR]]("http://www.amazon.com/M3N78-VM-Nvidia-DDR2-1066-Geforce-Motherboard/dp/B001BL7262/ref=wl_it_dp_o?ie=UTF8&coliid=I2SJAOUK73D0DW&colid=3VC2MIGW2TSDW")**

---

### Post by nickrout on 2010-02-03
> **Jojok said:**
> Yes.. trying to settle on this one  has onboard HDMI and Nvidia 8200 chip that supports vdpau**[[COLOR=#004b91]ASUS M3N78-VM [/COLOR]]("http://www.amazon.com/M3N78-VM-Nvidia-DDR2-1066-Geforce-Motherboard/dp/B001BL7262/ref=wl_it_dp_o?ie=UTF8&coliid=I2SJAOUK73D0DW&colid=3VC2MIGW2TSDW")**

There are some comments on the 8200 and vdpau in the wiki:

[http://www.mythtv.org/wiki/Vdpau](http://www.mythtv.org/wiki/Vdpau)

Or ask on the main mailing list.

---

### Post by Colonelguf on 2010-02-03
> **Jojok said:**
> [COLOR=#0d0d0d][FONT=Arial][SIZE=3][FONT=Calibri]That’s the ‘plan B’  and I am also looking to see if there is a motherboard that has vdpau support and builtin HDMI port, any suggestions ?[/FONT][/SIZE][/FONT][/COLOR]

I have a ECS GF8200A MB with HDMI and nVidia 8200. I have been using it for about 2 months, and so far it works great. I got it for $55 at _[COLOR=Red][NewEgg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813135085")[/COLOR],_ and am supposed to get a $25 rebate. Now it is $70 with $16 rebate.

---

