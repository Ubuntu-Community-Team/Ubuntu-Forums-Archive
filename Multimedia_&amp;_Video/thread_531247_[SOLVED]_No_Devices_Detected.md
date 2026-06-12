---
title: "[SOLVED] No Devices Detected"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by johnny9794 on 2007-08-21
[SOLVED] EXPLAINED BELOW.

I am trying to run 7.04 on my MSI NX6600 LE graphics card.

My video card is connected and I keep getting an error.

NVIDIA: No matching device section for instance (BUSID PCI:2:0:0) found.

No Devices Detected

Fatal Server Error: No screens found.

Then on the next log files for xserver failed is showing the name of my card.

PCI:*(2:0:00) nvidia corporation NV43 [GeForce 6600 PCIe] rev 162.

any idea's anyone? or how could i fix this.

Im stumped.

---

### Post by raijinsetsu on 2007-08-21
run "lspci -v" and list the output. It sound like you're using the wrong BUS ID for your video card, but uncertain.

---

### Post by johnny9794 on 2007-08-21
Had to hand type all of this and could not hand type the entire lspci -v output.
Will this do.

02:00.0 VGA compatible controller: nvidia corporation nv43 [geforce 6600 PCIe]
(rev a2) (prog-if oo [VGA])
Subsystem: Micro-Star International co., LTD. unknown device 9819
Flags: Bus master, fast devsel, latency 0, IRQ 16
Memory at dc000000 32-bit, non prefetchable) [size=64M]
Expansion ROM at dafe0000 [disabled] [size=128k]

---

### Post by mike6426 on 2007-08-21
you cannot get onto the main desktop?  If so try 7.10, I had a similar problem with 7.04 but 7.10 worked for me.

---

### Post by johnny9794 on 2007-08-21
k thanx, it will be a bit before i reply again, I have to download 7.10 and then install.

---

### Post by johnny9794 on 2007-08-22
Nope,  i cannot even run 7.10, graphics become all scrambled. I cannot run 7.04 ither, I had to install the OS with my internal vga graphics, thinking i could install with internal which i did and then install nvidia driver in the cmd line without GDM running but that failed as well.

Alot of ppl say that the 6600 is compatible, which this MSI NX6600 LE is not, and seems like I am the "only" person with a MSI NX6600 LE and trying to run ubuntu on it. I been trying to use this graphics card on ubuntu for year and a half and cannot. I ran ubuntu on a FX 5500 which worked perfect then i got a new PC that has this annoying MSI 6600 PCI Express x 16 card.

well back to the one OS I do hate XP.

I was never able to run gparted with this card until Gparted came out with a new version that has an option to Force Vesa driver. well i forced vesa driver in gparted, I am able to run gparted, edit,delete,create partitions with it. Prior of gparted 0.3.4.8, I got the same crap, scrambled graphics broken into tiny colored squares, same as i am getting in all the ubuntu distro's.

---

### Post by raijinsetsu on 2007-08-22
> **johnny9794 said:**
> Nope,  i cannot even run 7.10, graphics become all scrambled. I cannot run 7.04 ither, I had to install the OS with my internal vga graphics, thinking i could install with internal which i did and then install nvidia driver in the cmd line without GDM running but that failed as well.

Alot of ppl say that the 6600 is compatible, which this MSI NX6600 LE is not, and seems like I am the "only" person with a MSI NX6600 LE and trying to run ubuntu on it. I been trying to use this graphics card on ubuntu for year and a half and cannot. I ran ubuntu on a FX 5500 which worked perfect then i got a new PC that has this annoying MSI 6600 PCI Express x 16 card.

well back to the one OS I do hate XP.

I was never able to run gparted with this card until Gparted came out with a new version that has an option to Force Vesa driver. well i forced vesa driver in gparted, I am able to run gparted, edit,delete,create partitions with it. Prior of gparted 0.3.4.8, I got the same crap, scrambled graphics broken into tiny colored squares, same as i am getting in all the ubuntu distro's.

I've always had problems with the LiveCD... Try the alternate install CD.

---

### Post by tseliot on 2007-08-22
If you tried the livecd and you was not able to install Ubuntu even when using the Safe Mode:

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

If nothing works and the Xserver just crashes, please post the output of the following command:
```
lspci
```

---

### Post by johnny9794 on 2007-09-30
ok I think I found my problem but still have not been able to solve it.

[http://pclinuxoshwdb.com/index.php?option=com_content&task=view&id=75&Itemid=2](http://pclinuxoshwdb.com/index.php?option=com_content&task=view&id=75&Itemid=2)

---

### Post by johnny9794 on 2007-10-16
> **tseliot said:**
> If you tried the livecd and you was not able to install Ubuntu even when using the Safe Mode:

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

If nothing works and the Xserver just crashes, please post the output of the following command:
```
lspci
```

Closer than before.

Ok good news sorta, I dpkg-reconfigure xserver-xorg and used vesa, the xorg did not crash, I did not get any scrambled graphics and i did not get a input not supported on my monitor, thats the good news, now it boots up fine up to after the login part, after the login part where nautilus little box suppose to pop up, does not, the screen is just a light brown and i can move my mouse pointer around but there is no right click options its just a blank light brown background with my mouse pointer with a loud buzzing noise coming out of my speakers and it sits like this and does nothing but making the loud noise. For the lspci, how do i copy all of lspci under recovery cmd line? how do i export the lspci list, say like to a floppy? I do not have a USB drive. So, I do not know how to copy text under the cmd line nor do i know how to export the results.

Thanx.

---

### Post by johnny9794 on 2007-10-16
[SOLVED] 

Yesss!!!!!!!!!

Thanx so much tseliot, I did not just have a problem with the vesa setting but above I wrote that it would not go past the login, for the reason being I dunno but i decided to go into my bios and disable my onboard sound "which is called azalia controller in the bios" AND BOOM what I have been dreaming for the last past YEAR it booted up holy ******** :) I am so grr happy now jeeze.

Well I was thinking about the the buzzing sound, and said lets disable the onboard sound and see what happens, my nautilus pops up and im on my 7.04 finally as i type.

If this happens to anybody else I am using ASUS P5GL-MX motherboard, I had to disable the onboard sound and use the vesa option stated above with my MSI NX6600LE gfx card and it just plain ole works now :):):):):):). I been trying to fix this on and off for the past year.

---

