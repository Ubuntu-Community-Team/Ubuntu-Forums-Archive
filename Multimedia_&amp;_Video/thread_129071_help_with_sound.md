---
title: "help with sound"
date: 2006-02-12
forum: Multimedia &amp; Video
---

### Post by abu-fatu on 2006-02-12
i am new to ubuntu. installed it on a older machine dell optiplex gx1 pentium3 600mhz with 128 ram . everything seems to work video , usb devices a.external burner, olympus digital camera was recogniced the first time with out any trouble. usb hp printer working . 
the only proble is with my sound at first install of ubuntu i belive that the sound was from an on board card, and it was not recogniced by ubuntu the sound icon next to date and time was crossed out as if muted  when cliking on it i would get a message that there was no sound device installed. ok i nstalled a creative sound blasterlive 24 bit pci card after rebooting the sound icon was normal. when i clik on it i get the volume control: ca0106 (alsa mixer) sound comes out but very scratchy very low quality. i would note that when i open the multimedia system selector and test: esd,artsd,alsa, and oss. artsd,alsa,oss whentesting this massage appears :"failed to construct test pipe line". only esd test but again the sound quality is extremly poor. is there a connection between the volumme control being : ca 0106 (alsa mixer) and (esd) being the only one that tested in the multimedia system selector? should i have a (esd mixer) in volume control? if so how do i achive this?also i would like to mention that while the volume icon now appears it does not seem to work even in the volume control panel raising and muting the volume does not seem to affect the sound level it remains the same. i tried several speakers and head phones with the same results.
thank you for your help.
i really enjoy ubuntu this is the only issue that i need to resolve.

---

### Post by gigi1234 on 2006-03-30
Have you resolved this problem yet?

I have the same machine and the same problem.

A temporary fix (which you have to repeat every reboot) is:

In terminal: 

$ sudo modprobe snd-cs4236

Another (permanent) fix I found by searching the forums is:

In terminal add the following line to /etc/modules:

"snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5"

This worked for me and for others as well but it seems like sometimes it does not work. Give it a try!

---

