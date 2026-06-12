---
title: "[64bit] No sound after updating Alsa"
date: 2011-04-12
forum: Multimedia Software
---

### Post by cherrypie on 2011-04-12
Hi, i just installed the newest alsa and i have simply no sound. 
alsa mixer looks like that : [http://img402.imageshack.us/img402/7413/zrzutekranu3u.png](http://img402.imageshack.us/img402/7413/zrzutekranu3u.png)
```
edyta@edyta-laptop:~$ sudo lshw -c sound
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d9c00000-d9c03fff

```Im a newbie, please help !

---

### Post by BcRich on 2011-04-12
Hi cherrypie
Have you tried installing PulseAudio Volume Control? it's called pavucontrol in the repositories. as i understand pulse audio adds controls to audio levels by default even if you do use ALSA or OSS a description from the repos follows
> PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume
control tool (mixer) for the PulseAudio sound server. In contrast to
classic mixer tools this one allows you to control both the volume of
hardware devices and of each playback stream separately. It also allows
you to redirect a playback stream to another output device without
interrupting playback.

---

### Post by cherrypie on 2011-04-12
yes i had pavucontrol before(from when i installed 10.10 i belive). The thing is that all the devices in pavucontrol disappeared after updating alsa :O  : [http://img716.imageshack.us/img716/200/zrzutekranu1fi.png](http://img716.imageshack.us/img716/200/zrzutekranu1fi.png)

---

### Post by lidex on 2011-04-12
Alright newbster, need more info.
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by cherrypie on 2011-04-13
[http://www.alsa-project.org/db/?f=5c4bcfe1c49266d6becf5df4c30aae40a6a5671f](http://www.alsa-project.org/db/?f=5c4bcfe1c49266d6becf5df4c30aae40a6a5671f)

here u go

---

### Post by mastablasta on 2011-04-13
How did you update it? It seems to me like you left out a step.
 
:
 
> !!ALSA Version
!!------------
 
Driver version: 
Library version: 1.0.23
Utilities version: 1.0.23
 
 
!!Loaded ALSA modules
!!-------------------

 
More importanty, why? Ubuntu 10.10 already has 1.0.23 by default.

---

### Post by cherrypie on 2011-04-13
well i used a script that worked for me well in 10.04 when i had terrible sound issues. in 10.10 my mic doesnt work and i thought (silly me) that after updating alsa i may get it work :/ any ideas what to do ? 

anyway heres the not working anymore script : 
```
#!/bin/bash function quest { echo " " echo " " echo "Jakiego &#347;rodowiska graficznego?" echo "Je&#347;li GNOME kliknij 1" echo "Je&#347;li KDE kliknij 2" echo "Je&#347;li KDE4 kliknij 3" echo "Inne kliknij 4" read -n 1 graf  case "$graf" in "1") echo "" ; echo "Czyli u&#380;ywasz GNOME. Instaluj&#281; mixer..." ; sudo apt-get install gnome-alsamixer ;; "2") echo "" ; echo "Czyli u&#380;ywasz KDE. Instaluj&#281; mixer..." ; sudo apt-get install kmix ;; "3") echo "" ; echo "Czyli u&#380;ywasz KDE4. Instaluj&#281; mixer..." ; sudo apt-get install kmix-kde4 ;; "4") echo "" ; echo "Przechodz&#281; do dalszych zada&#324;..." ;; *) echo "" ; echo "Poda&#322;e&#347; z&#322;&#261; cyfr&#281;!" ; quest esac }  function instalacja { sudo apt-get install tar wget build-essential linux-headers-`uname -r` libncurses5-dev gettext gcc libgcc1 sudo /etc/init.d/alsasound stop cd ~/alsa # driver if [ -e $d ]; then rm -Rf $d sudo rm -Rf alsa-driver-$w wget -c ftp://ftp.alsa-project.org/pub/driver/$d $r $d else wget -c ftp://ftp.alsa-project.org/pub/driver/$d $r $d fi # lib if [ -e $l ]; then rm -Rf $l sudo rm -Rf alsa-lib-$w wget -c ftp://ftp.alsa-project.org/pub/lib/$l $r $l else wget -c ftp://ftp.alsa-project.org/pub/lib/$l $r $l fi # utils if [ -e $u ]; then rm -Rf $u sudo rm -Rf alsa-utils-$w wget -c ftp://ftp.alsa-project.org/pub/utils/$u $r $u else wget -c ftp://ftp.alsa-project.org/pub/utils/$u $r $u fi    if [ -d ~/alsa/alsa-driver-$w ]; then cd ~/alsa/alsa-driver-$w ./configure make sudo make install sudo ./snddevices else echo $k echo "$e2 alsa-driver-$w. $e" echo $k sleep 10 fi  if [ -d ~/alsa/alsa-lib-$w ]; then cd ~/alsa/alsa-lib-$w ./configure make sudo make install else echo $k echo "$e2 alsa-lib-$w. $e" echo $k sleep 10 fi  if [ -d ~/alsa/alsa-utils-$w ]; then cd ~/alsa/alsa-utils-$w ./configure make sudo make install else echo $k echo "$e2 alsa-lib-$w. $e" echo $k sleep 10 fi  sudo cp -v /lib/modules/`uname -r`/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/`uname -r`/ubuntu/media/snd-hda-intel/snd-hda-intel.ko sudo cp -v ~/alsa/alsa-driver-$w/modules/* /lib/modules/`uname -r`/kernel/sound/ sudo alsaconf sudo depmod -a sudo /etc/init.d/alsasound start quest echo " " echo " " echo "Gratulacje! Alsa zosta&#322;a zaaktualizowana do wersji $w. Prosz&#281; nie usuwa&#263; katalogu $HOME/alsa !!! Je&#347;li nie b&#281;dziesz mia&#322; d&#378;wi&#281;ku lub b&#281;dzie zbyt cicho to pobaw si&#281; suwakami w jakim&#347; mixerze systemowym." echo " " echo " " }  echo "Update Alsa by Ari" sleep 2 s="http://alsa-project.org w tabeli Current Version" r="tar -xjf" k="..................." e="By&#263; mo&#380;e wyst&#261;pi&#322; b&#322;&#261;d przy pobieraniu lub &#378;le poda&#322;e&#347; wersj&#281;! Sprawd&#378; dok&#322;adnie na stronie $s. Je&#347;li jest to wersja stabilna np. 1.0.16 to wpisz 1.0.16, a je&#380;eli jest to wersja rc np. 1.0.16rc3 to wpisz 1.0.16rc3" e2="Nie odnalaz&#322;em którego&#347; z plików!" i="Instaluj&#281; &#378;ródla Alsy do $HOME/alsa" echo "Witaj $USER. Podaj najnowsz&#261; wersj&#281; Alsy przyk&#322;adowo 1.0.16. Mo&#380;esz j&#261; sprawdzi&#263; na stronie $s" read w d="alsa-driver-$w.tar.bz2" l="alsa-lib-$w.tar.bz2" u="alsa-utils-$w.tar.bz2" echo "Aktualizuj&#281; Als&#281; do wersji $w." echo "Gdy pojawi si&#281; niebieskie okno konfiguracji, kliknij [ENTER] < OK >,  nast&#281;pnie wybierz swoj&#261; kart&#281; d&#378;wi&#281;kow&#261; i wci&#347;nij [ENTER] < OK >, potem znowu [ENTER] < TAK > , [ENTER] < OK >, [ENTER] < TAK >." sleep 15 if [ -d ~/alsa ]; then echo $i sleep 2 instalacja else mkdir ~/alsa echo $i sleep 2 instalacja fi
```

---

### Post by BcRich on 2011-04-13
Off the topic: cherrypie, Your desktop screenshot images are really rather rad :)

---

### Post by cherrypie on 2011-04-13
> **BcRich said:**
> Off the topic: cherrypie, Your desktop screenshot images are really rather rad :)
  umm.. why ?

****update**** 
i used this script [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577) and everything is back to normal. anyway thanks for ur 'support'

---

### Post by BcRich on 2011-04-13
> umm.. why ?
Mainly cause i like the desktop background images you have, did you make them or get them from somewhere else? I just think they are really interesting, didn't mean to stir any paranoia or anything like that.

---

