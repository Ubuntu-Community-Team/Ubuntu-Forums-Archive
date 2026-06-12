---
title: "WinTV NOVA-T-500 onboard amplifier activation"
date: 2008-06-25
forum: Mythbuntu
---

### Post by jammy24 on 2008-06-25
I'm new to Linux but have just installed Mythbuntu will the aim of building a media center PC after I get all the things up and running on my main PC. I would like to know how I activate the onboard amplifier on my WinTV NOVA-T-500 tuner card. I have entered the following in the terminal; 
"sudo gedit /etc/modprobe.d/options"
and am presented with the following;

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

Where do I add the line; "options dvb-usb-dib0700 force_lna_activation=1", is it at the end, in the middle, etc. 
Please help. Thank you

---

### Post by zzztownsend on 2008-06-25
hi there jammy24

it doesn't matter. I put it at the end in mine

I also found that adding the line 

options usbcore autosuspend=-1

reduces the number of times that the second tuner crashes, requiring a reboot
(see [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500) )
unfortunately the card is still a bit unreliable even with this

cheers
matt

---

