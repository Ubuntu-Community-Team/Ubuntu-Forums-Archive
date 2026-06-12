---
title: "[SOLVED] O.K., this is gettin silly, which video/sound cards are the best  feisty and"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by S.S.S.P5 on 2007-09-25
I cant get my video card (ati rv280) or sound card (creative sb0200) to work

i can find the ati card, but the creative wont even show up


plz help!!!!

---

### Post by S.S.S.P5 on 2007-09-25
like do i need to go out and buy new cards? theres gotta be an eaisier n00b way to do this without reading a novel

---

### Post by reckless2k2 on 2007-09-25
the creative card should be ok with a tweak or 2 in the community docs but what do you mean that the ati card is not working?

about sound:
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by S.S.S.P5 on 2007-09-25
it shows up when i type lspci....

james@james-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

but i cant run desktop effects or beryl/emerald i get a white screen in desktop effects, or if i mess with it enough by following the online guides, it crashes the GUI on reboot, i then have to reconfigure the xserver back to vesa- lol i just started on linux last week, i cant beleive how much ive learned already, but its painfully obvious that ive only cracked the surface, and still have absolutley no clue what im doing! haha, atleast i can recover from the black screen without the need of a second computer and the internet now!

---

### Post by S.S.S.P5 on 2007-09-25
james@james-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by S.S.S.P5 on 2007-09-25
james@james-desktop:~$ cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory
james@james-desktop:~$

---

### Post by Siph0n on 2007-09-25
in response to

> james@james-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device 

I googled around and found someone else with the same error, also did this command:

> > Result from ls /dev/snd/controlC0:
> crw-rw----    1 root  audio   116,  0  Jun  5 12:31
> /dev/snd/controlC0

And the response was:

> Maybe you should make that "crw-rw-rw-", if you want to use it as non-root: chmod o+rw /dev/snd/controlC0

Just what I found out :) give it a try? :)

---

### Post by S.S.S.P5 on 2007-09-25
ok i just enabled the onboard sound card and this is what i get now...

james@james-desktop:~$ cat /proc/asound/cards
 0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with CMI9739 at 0xdc00, irq 20
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x300, irq 5


and....

james@james-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)


and the aslamixer now works

---

### Post by S.S.S.P5 on 2007-09-25
and this...

james@james-desktop:/proc/asound$ ls
card0  cards    modules  pcm  SI7012  UART
card1  devices  oss      seq  timers  version

---

### Post by reckless2k2 on 2007-09-25
i think i'm reading that you are not using alsa. you are using oss. as far as ati and beryl.....check this out if you have not already..(ati isn't great though)

[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://easylinux.info/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

---

### Post by S.S.S.P5 on 2007-09-25
right, as usual i get stopped half way...

james@james-desktop:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
Password:
gpg: no valid OpenPGP data found.
james@james-desktop:~$

---

### Post by S.S.S.P5 on 2007-09-25
thanks for all the advice, desktop effects is now up and running!

---

