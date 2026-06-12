---
title: "ATI - Did it work for you ?"
date: 2008-05-31
forum: Multimedia Software
---

### Post by sim-value on 2008-05-31
Now the Ultimate Question : Did you get your ATI card working with full functionality ? (3D acceleration etc..) or didnt you ?

Please vote only after several Tries.

greetings /me

PS: if you did / didnt please post your card

---

### Post by mrreality13 on 2008-05-31
ive tried sevral ati's 9250,9550,9600 all older i know but not worth the aggrivation,,i went and got a few cheep:guitar: nvidia 5200's(actually made a few bucks on the swap)

---

### Post by Silent Warrior on 2008-06-01
Some drivers have worked flawlessly with my Radeon X1900XT, though the latest drivers are vastly shortening my life-expectancy... I voted 'yes (fglrx)' because it seems to have proven to be possible. Just remember to sort out your xorg.conf it necessary.

---

### Post by pro003 on 2008-06-01
in gutsy things were terrible and with hardy they got better, as far ati driver is concerned..

i would still like to get back on nvidia, but some things are simply not ment to be that easy...

---

### Post by Trollslayer on 2008-06-01
X1250 on motherboard works, had problems at first reading EDID.

---

### Post by pietjanjaap on 2008-06-01
ati 9600 , got it after 3 day's trying working.
Tried everything on the forums, and suddenly it worked.

1
/etc/modprobe.d/blacklist

copied this inside the file blacklist

blacklist i82875p_edac
blacklist edac_mc

2
Setup Compiz Fusion with open source ati radeon drivers

Older ATI cards have been blacklisted for Compiz Fusion because of a bug in the driver, but there is an easy workaround for many cards that use the open source ati drivers. Radeon 9500 are the oldest cards to support the restricted "fglrx" drivers, so everything older requires the open source drivers to function properly.



First edit the launcher for Compiz Fusion:

gksudo gedit /usr/bin/compiz

Near the top, add the line

SKIP_CHECKS="yes"

I added it under VERBOSE="yes"

You may also need to install the Compiz settings manager program that you can access from System->Preferences->Advanced Desktop Effect Settings | 1-click install or:

sudo apt-get install compizconfig-settings-manager

You can now load Compiz Fusion with

compiz --replace

and revert to Metacity (the basic window manager) with

metacity --replace

I suggest making launchers in a panel for this.

Remember that this is a workaround and may not work for everybody. If you have further problems, you should consider running a forum search and then posting on one of the main support forums if you still need help.
For the record, my card is an ATI Mobility Radeon 9000.

3
after this i reboot and install the video driver with envy.

---

### Post by markbuntu on 2008-06-01
Fresh install with i386 recognized my card immediately and I enabled the restricted driver 8.47.3 and everything works pretty great except suspend still broken. atievent is the culprit there.

Many 3d modes not recognized by AIGLX and compiz still stuck without dri but overall a good expererience. Processor loading much reduced.

replacing firefox 3b5 with 3.0rc1 made the biggest difference with compiz etc. no more crashes except intermitentlyly on a few flash sites like hulu.

ATI Radeon HD3650 1GB
24" and 19" monitors in big desktop mode

---

### Post by Melcar on 2008-06-01
HD2900XT and 200M work perfectly.

---

### Post by bregale on 2008-06-01
i voted no because after a week of trying i cant get my card to run 3d , must admit though system has been prety stable even with my installing and removal process

---

### Post by xfceuser on 2008-06-01
ati radeon 7500 , mobility, used to work 3D , not after ubuntu 7.10 when they removed a prop. driver.
more details here:
[http://ubuntuforums.org/showthread.php?t=814518](http://ubuntuforums.org/showthread.php?t=814518)
:confused:

---

