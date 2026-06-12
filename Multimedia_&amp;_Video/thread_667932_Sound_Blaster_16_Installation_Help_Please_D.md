---
title: "Sound Blaster 16 Installation Help Please :D"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by aflog on 2008-01-14
I have a Sound Blaster  sound card (from creative)... the thing is, Xubuntu hasnt installed drivers for it... now it works fine in Windows XP however i cannot seem to find how to install the drivers manually for the device... i have also searched the forums and the internet but nothing useful... any help please?

Jden

---

### Post by aflog on 2008-01-16
Ok so i tried the whole modprobe thing (sudo modprobe snd-sb16) then (alsamixer) and says no device detected.... :S

Any solutions?

Jayden

---

### Post by aflog on 2008-01-18
Ok this is really annoying me now... i have tried just about every method on [this page]("https://help.ubuntu.com/community/SoundTroubleshooting") with no results. I have tried just about everything... and i tried it in windows about 20 minutes ago and it works fine. I have found out some more information about the card:

> Maker: Creative Labs
Name: Sound Blaster 16
Made in: Singapore in 1994 (yes its old)
Model Number: CT 2230
Where it is: SLOT1 (NOT PCI1)

I have alsamixer... this is what i try in a terminal:
> root@xjden:~# modprobe snd-sb16
root@xjden:~# sudo alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
root@xjden:~# 

Things like xfmedia, amarok and gxine all report no audio output device... some help please? If anyone would like to help, i am on msn often...

Also i have the windows drivers installation exe... if there is a way there then im up for it :D

Thanks alot (for any help)

Jayden

---

### Post by aflog on 2008-01-18
Well alright then..... basically what i was implying in that last post, was whether there is a way to use something like ndiswrapper with some windows drivers to run the sound card... they seem to work normally :S

Jayden

---

### Post by aflog on 2008-01-19
im going to ask... no... BEG again... if ANYONE can help .... PLEASE PLEASE PLEASE help :-| 

Jden

---

### Post by kostkon on 2008-01-19
Your have a very old ISA sound card. The Linux kernel does not even try anymore to auto detect ISA devices because they are deprecated.

Please read [this how-to from the Ubuntu documentation]("https://help.ubuntu.com/community/HowToSetupSoundCards") to set up your card. For any question that will arise from following this guide don't hesitate to ask here.

---

### Post by aflog on 2008-01-19
Ok... yea i had tried that a while ago... but it occured to me to take ANOTHER look through BIOS and i found an entry called "IRQ x used by PNP ISA?"... it had been set to "No/ICU". Then i remembered that in windows it used IRQ 5 for the card by default (which always annoyed me as it clashed with my network card)... so yea, i thought id try setting it to "Yes"... F10 ... reboot ... login to X and open up the terminal and it worked!

So i have now added snd-sb16 to /etc/modules...

Thanks to kostkon for the jog of me memory :D
Thanks to everyone else who viewed this post and didnt reply....
And NO thanks to people who couldnt be bothered :D

Jayden

---

