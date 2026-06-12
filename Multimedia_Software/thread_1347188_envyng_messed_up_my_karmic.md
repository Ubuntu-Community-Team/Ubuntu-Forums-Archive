---
title: "envyng messed up my karmic"
date: 2009-12-05
forum: Multimedia Software
---

### Post by luis.nando on 2009-12-05
I wasn`t happy with my video behavior and i decided to install ATI drivers by using envyng. When i did it not only it didn`t work, but i couldn`t go back on my previous configuration.
I am a beginner and my english is poor. So sorry for grammar mistakes.
Well i first tried to
envyng --uninstall-all
i ended at a blank screen, with a message from the monitor (analogic)

Then i tried
rename the xorg.conf file and do a recovery mode reboot...
nothing

then,
sudo dpkg-reconfigure xserver-xorg
dexconf
and nothing, i ended at the same blank screen

i tap ctrl+alt+f2 and try sudo gdm i got the following message
gdm-binary[1931]> WARNING> Unable to find users no seat-id found
...
...
...
GdmLocalDisplayFactory maximum number of X display failures reached check X server log for erros

what else can i do?

thanks on advance

---

### Post by freackout on 2010-03-04
> **luis.nando said:**
> I wasn`t happy with my video behavior and i decided to install ATI drivers by using envyng. When i did it not only it didn`t work, but i couldn`t go back on my previous configuration.
I am a beginner and my english is poor. So sorry for grammar mistakes.
Well i first tried to
envyng --uninstall-all
i ended at a blank screen, with a message from the monitor (analogic)

Then i tried
rename the xorg.conf file and do a recovery mode reboot...
nothing

then,
sudo dpkg-reconfigure xserver-xorg
dexconf
and nothing, i ended at the same blank screen

i tap ctrl+alt+f2 and try sudo gdm i got the following message
gdm-binary[1931]> WARNING> Unable to find users no seat-id found
...
...
...
GdmLocalDisplayFactory maximum number of X display failures reached check X server log for erros

what else can i do?

thanks on advance
i've had some success with envyng in the past however changing to koala on my old ati 9200 pro ive had difficulties, there are changes between distros xorg and drivers are release and sometimes supported cards are no longer.. i'm supprised how linux and envyng are actually easy to install.
however you may be better installing from fresh then next time backup the xorg.conf.
ive recovered a desktop by

sudo apt-get remove --purge xserver-xorg

then re-install it with
sudo apt-get install xserver-xorg

the whole card and display settings returned to normal for me.

however i'm stuggling with my old card on karmic possibly not supported on karmic ie dropped?
thus going back to older distro 9.04 8.10 8.04 thus will pick up device again. with envyng,, without saying not supported or not reccommended in its tick boxes. envyng-qt is for older cards. new drivers work with new versions of Xorg i am assuming ok.

---

### Post by Mark Phelps on 2010-03-05
Didn't see what ATI card you have, but unless it's one of the newer HD 3x/4x/5x cards, it is no longer supported with Linux drivers by ATI.  Trying to force such a driver install will only corrupt your display -- as you have found out.

The link below has some instructions on removing the ATI drivers and replacing them with the open source drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

