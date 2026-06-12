---
title: "ALSA Support for CS4235/CS4236/CS4236B/CS4237B/CS4238B/CS4239 based sound cards"
date: 2006-02-10
forum: Multimedia &amp; Video
---

### Post by MeanEYE on 2006-02-10
For all those people who are heaving problems with sound card based on CS4235/CS4236/CS4236B/CS4237B/CS4238B/CS4239 chipset using ALSA this might help. Please note that this text is quoted from [http://www.bigwebmaster.com/General/Howtos/Alsa-sound-5.html](http://www.bigwebmaster.com/General/Howtos/Alsa-sound-5.html) and I only posted it here. Have fun...

> According to the INSTALL file you need to supply the main port and control ports for this card. Note that with a CS4237B card, I ended up supplying all information (except DMA-size), otherwise the driver did not work. So you may as well use the whole command line to insert the driver, and not only supply snd_port and snd_cport. If you initialized the card with the isapnp-tools, you can probably get info from the /etc/isapnp.conf file for the following values: 


snd_port - port # for CS4232 chip (PnP setup - 0x534)
snd_cport - control port # for CS4232 chip (PnP setup - 0x120)
snd_mpu_port - port # for MPU-401 UART (PnP setup - 0x300), -1 = disable
snd_fm_port - FM port # for CS4232 chip (PnP setup - 0x388), -1 = disable
snd_jport - joystick port for CS4232 chip (PnP setup - 0x200), -1 = disable
snd_irq - IRQ # for CS4232 chip (5,7,9,11,12,15)
snd_mpu_irq - IRQ # for MPU-401 UART (9,11,12,15)
snd_dma1 - first DMA # for CS4232 chip (0,1,3)
snd_dma1_size - max first DMA size in kB (4-64kB)
snd_dma2 - second DMA # for Yamaha CS4232 chip (0,1,3), -1 = disable
snd_dma2_size - max second DMA size in kB (4-64kB)

You would do a "**modprobe snd-card-cs4236 snd_port=0x534 snd_cport=0x120 snd_mpu_port=-1 snd_fm_port=0x388 snd_jport=-1 snd_irq=5 snd_dma1=0 snd_dma1_size=[COLOR="red"]NN[/COLOR] snd_dma2=1 snd_dma2_size=[COLOR="Red"]NN[/COLOR]**" to load the driver. 

(This is without midi-support, see address above for more information)

Notes: the "NN" values need to be supplied, only I do not know what would be reasonable values. My CS4237B works fine without explicit dma size option. 


Also, note that in Ubuntu 5.10 Breezy you might need to exclude **-card** from module name, for example instead of **modprobe snd-card-cs4236 **you should type **modprobe snd-cs4236**. In case you do not have administrator privileges (if you are logged on you own username not root) you will need to **sudo **these commands. (**sudo modprobe snd-cs4236**).

---

### Post by Thibaud74 on 2006-05-22
Thanks you for your report, but that don't work for me. I'm using a Crystal Cyrrus Logic card CS4237B and a Dell Latitude CP MMX 233 ST pentium II. Alsaconf find the driver under Mandrake 9.1, but not under Ubuntu. Why ?!

---

### Post by MeanEYE on 2006-05-22
Neither for me, am still without sound! Am using CS4235 on FujitsuSiemens XL400.

---

