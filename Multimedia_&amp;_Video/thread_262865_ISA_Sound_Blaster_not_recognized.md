---
title: "ISA Sound Blaster not recognized"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by aconley1 on 2006-09-22
Help...I'm a total Newbie at this.... 
I have an old machine that i set up with Xubuntu and it works great.  The machine is an AMD k6, 128mb ram and 40gig HD.  I have wireless internet with an atheros chipset adapter...so easy to setup, everyone should get one.
Anyway, the only thing that doesn't work is my sound card...xubuntu doesn't recognize that one is present.  I tried to follow a post I read about setting up this type of card...the first command I was supposed to use was gedit to add snd-sb16 to /etc/modules....  my system just says "unrecognized command".  Being unable to edit the /etc/modules prevented me from even trying the commands that are listed next.  Any help is greatly appreciated.

---

### Post by pseudonym on 2006-09-22
Hi,

I used to have a PII with an ISA sound blaster. What I did to get it working was -

1. With most ISA devices, you need to assign resources manually. This can vary depending on which slot your card is plugged into, but the common settings for soundblasters are IO=0x220, IRQ=10, DMA=1, DMA16=5. Look in /var/log/syslog for which settings the system detects your card at. Write them down.

2. Reboot and check your BIOS for a setting like 'ISA Legacy Resources'. It is usually helpful to first enter the settings in step 1 here.

3. When you are booted up again run sudo alsaconf to set up alsa. You will probably be asked to 'probe legacy cards' (or whatever it is). Say yes and your card should be detected.

4. Add this line in /etc/modules, usually above other extra modules like video or network you may have in there (you need to run your texteditor as sudo)and in lowercase -

snd-sb16 io=0x220, irq=10, dma=1, dma16=5 (or whatever your numbers are)

This will ensure resources are assigned to your card during each reboot.

5. [humour] when you realise ISA sound cards don't really cut it anymore (due to bus saturation), buy a cheap PCI one and install that. :)

HTH

---

### Post by aconley1 on 2006-09-22
Thanks for your answer...I have one more question...how do I run my text editor in sudo?

---

### Post by pseudonym on 2006-09-22
It's the command to run something as privileged user ('SUper user DO..'). Open up a terminal and type sudo gedit (or the name of whichever editor you use) and the name of the file you want to edit (/etc/modules). Running the editor in this mode will enable you to write changes to the file.

Also, you may not need to worry about step 3 above. I've just come back to Ubuntu and noticed that the version of alsa is slightly different to what I've been using. It doesn't look like alsaconf is one of its commands.

Complete step 4 and then run 'sudo /etc/init.d/alsa-utils restart' to reload alsa sound driver(/etc/init.d contains several startup scripts fyi) and you should be good to go...

---

