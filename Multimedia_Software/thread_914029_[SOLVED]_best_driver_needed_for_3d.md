---
title: "[SOLVED] best driver needed for 3d"
date: 2008-09-08
forum: Multimedia Software
---

### Post by lowstand on 2008-09-08
I play eve-online an few other games it works fine on the windows box xp   same setup  just different os  this is how its installed mind you my graphics as they are are great but will not load that game opens starts an just go's  away


cpu: Intel(R) Celeron(R) CPU 2.20GHz
cpu_ghz: 2.2
memory: 2018
videocard_manufacturer: Tungsten Graphics, Inc
videocard_type: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
videocard_ram: 2048
agp_aperture_size: N/A
videocard_driver_version: 1.3 Mesa 7.0.3-rc2
soundcard: Intel 82801DB-ICH4 with ALC202 at irq 2
soundcard_driver: ALSA Version 1.0.15
machine_bitness: 32
kernel: 2.6.24-19-generic
x_version: 
distro: Debian lenny/sid
GUI version: eve-000066




anyone got any type of how to make it allow me to inable the 3d ?

---

### Post by lowstand on 2008-09-08
i love when i post no one show up an knows anything

---

### Post by overdrank on 2008-09-08
> **lowstand said:**
> i love when i post no one show up an knows anything

Hi and I can not speak for debian but Ubuntu drivers work well with intel graphics. I do not play on line games with the intel graphics and for that matter do not play any games but the desktop effects work well.

---

### Post by lowstand on 2008-09-09
yes i agree  my desktop is awesome   on this old box   are great i just can't seem to magically make it do all it can do on this built in video  but thats cool i guess give me more time to study an learn Linux :popcorn:

---

### Post by aeiah on 2008-09-09
you shouldnt have a problem with intel graphics, its more likely a problem with your installation of eve. is it the proper linux package or a manual wine install? i think eve uses wine for linux anyway but its probably best if they have an official package. what happens when you launch the game from a terminal? does it give any error messages before exiting? have you followed a tutorial or used any hints from the game's winehq.org page? sometimes you need to apply a patch or use a specific version of wine, set a specific setting etc.

---

### Post by lowstand on 2008-09-09
no error that i can see i normally just try an start it threw games thats where it installed to yes it  is a linux base install  i run the harware test that the game configure came with an it says my card  failed however it will not allow me to run the 3d i have great resolution in my desktop an such  awesome looking  its just a driver issue apparently i have went an reinstalled twice an incase of a bad download even filled a compliant with there tech department an they say its my driver but they can't seem to point me in the correct direction to get it  is there a way in ubuntu  to update the driver itself via it searching for  the correct driver that will allow the 3d  to enable    ? 


this seems to be the only lil glitch i have with ubuntu i really like this Linux version and i am slowly understanding it more an more everyday



This is what is how the cd  install set my pc up an works great other then the 3d  issues  



cpu: Intel(R) Celeron(R) CPU 2.20GHz
cpu_ghz: 2.2
memory: 2018
videocard_manufacturer: Tungsten Graphics, Inc
videocard_type: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
videocard_ram: 2048
agp_aperture_size: N/A
videocard_driver_version: 1.3 Mesa 7.0.3-rc2
soundcard: Intel 82801DB-ICH4 with ALC202 at irq 2
soundcard_driver: ALSA Version 1.0.15
machine_bitness: 32
kernel: 2.6.24-19-generic
x_version: 
distro: Debian lenny/sid
GUI version: eve-000066

---

### Post by aeiah on 2008-09-09
i dont know about intel graphics drivers per se, but they tend to be included in the repositories. you could open synaptic, hit refresh to update your info and then do a search for intel and see if there are any newer drivers. failing that, it may be a similar issue to this one:

[http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-install-trouble-with-intel-82845g-graphics-card-557840/](http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-install-trouble-with-intel-82845g-graphics-card-557840/)

note the post at the bottom of the page. perhaps you could try that. backup first in case you bork everything though but you should be fairly safe since you're using intel.

you may simply not have a powerful enough graphics card. on board intel graphics dont tend to be very powerful, not compared to an actual graphics card. if you decide to buy one, investigate which ones work the best in ubuntu. super-new cards tend to be harder to set up than established ones. i have an nvideo gt 7800 that works fantastic, but its getting a bit old-hat now for new games.

---

### Post by lowstand on 2008-09-09
yup i got back ahold of eve tech   i am going to need a biger box   with better card sence i have no agp  setup on the board  seems it will run on windows xp on here but its not sopported as yet for this card by eve for linux so oh well no eve lmao



Minimum Requirements

    * 32 or 64 bit Ubuntu 7.04 or higher, Linspire 6 or higher, OpenSuSE 10.2 or higher
    * 64 MB GeForce FX class card or better, ATI graphics cards are not supported.
    * 512 MB of RAM
    * 6 GB of HD Space
    * 1.1 GHz CPU 

Recommended System Requirements

    * 32-Bit Ubuntu, OpenSuSE, Linspire with a GeForce 6XXX series card or better, ATI graphics cards are not supported.
    * 1.5 GHz CPU or better
    * 1 GB of RAM
    * Alsa supported soundcard 

Kernel

    * Kernel 2.6.20 or newer
    * XFree86 4.0 or higher (4.3 is recommended) or the latest Xorg release 

OpenSuSE Dependencies:

# python >= 2.4
# python-gtk >= 2.6
# gtk2 >= 2.6
# wget
# dbus-1-python

Ubuntu/Linspire Dependencies

    * libc6 (>= 2.2.4-4)
    * xlibmesa3 | libgl1
    * python (>= 2.4)
    * python2.4-dbus
    * python-gtk2 (>= 2.6)
    * python-glade2, wget

---

