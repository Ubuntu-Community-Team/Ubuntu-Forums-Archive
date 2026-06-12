---
title: "No Sound After Installation"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by DonE on 2007-06-05
NEWBIE with NO SOUND, after an otherwise successful, uneventful dual-boot (Linux 7.04 & Windows Me) install of Feisty on my HP Pavlion XT868 desktop. The computer is equipped with a a Riptide Audio/Conexant Communications Combo Modem PCI Card. Feisty is installed on the 2nd (logical) partition on my C: hard drive with all other aspects of the install working properly.

I found the Comprehensive Sound Problem Solutions Guide v 0.5e Post, and went through it step by step, but it revealed no problems with my audio installation. The card was detected and recognized. I double checked the Alsamixer sound settings and made sure they were not muted. I checked for the correct audio rights for this user. I checked my boot-up bios settings and for sound in Windows Me. Everything checked properly, with sound during boot-up and in Windows, but only silence in Feisty, from all sources. I played an audio CD, the player came up and I could play the disk but still silence. Same problem with Sound Preferences option. Testing any of the Feisty sounds failed to work.

I then assumed I needed Linux drivers for the audio card. The only drivers I found for this card were on the Linuxant.com website. My research on the card revealed I needed the HSF plus the Riptide drivers. I followed the download procedures with the automatic installer (cnxtinstall.run) provided by Linuxant during the driver install. The installer installed the HSF drivers, then informed me that it was preferred to install the Riptide drivers also, but it refused to install those drivers because it said I had the wrong Linux Kernel!! It then ended the install of drivers. Once again I checked everything, and it was clear that Linux recognized my audio device and the HSF drivers, but still not a sound to be heard!

I wanted to try downloading & installing the Riptide Drivers manually, in accordance with the Linuxant instructions, but I am too newbieish (is that a word?) to know how to use the RPM Package Installer, & follow their terse instructions. I could use a lucid explanation of the manual driver install process. I am also quite concerned about the large number of disclaimers from Linuxant, and the age of these unsupported drivers which they say only support OSS. I don’t know what that means either, but it doesn’t sound good. 

Can anyone help me get the sound turned on? Has anyone ever gotten sound out of Linux with the Riptide/Conexant Combo Card (aka Chameleon Card)??

Thanks for listening!

DonE

---

