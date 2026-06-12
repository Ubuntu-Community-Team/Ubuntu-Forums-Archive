---
title: "Ubuntu 13.04 Sound from both headphones and speakers"
date: 2013-09-17
forum: Multimedia Software
---

### Post by Amaazaoui on 2013-09-17
Hello Guys,

I hope that everybody are ok.

I have an issue, since I installed ubuntu 13.04 on Laptop HP nc6120, related to the sound output. I hear sound from both  headphones and speakers. would someone give a support to resolve this problem?

Thanks in Advance

here is some details:

amaazaoui@amaazaoui-HP-Compaq-nc6120-PN936AV:~$ **uname -a**
[COLOR=#0000ff]**Linux amaazaoui-HP-Compaq-nc6120-PN936AV 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:54:42 UTC 2013 i686 i686 i686 GNU/Linux**[/COLOR]
amaazaoui@amaazaoui-HP-Compaq-nc6120-PN936AV:~$ **aplay -l**
[COLOR=#0000ff][B]**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: ICH6 [Intel ICH6], périphérique 0: Intel ICH [Intel ICH6]
  Sous-périphériques: 0/1
  Sous-périphérique #0: subdevice #0
carte 0: ICH6 [Intel ICH6], périphérique 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0[/B][/COLOR]
amaazaoui@amaazaoui-HP-Compaq-nc6120-PN936AV:~$ **cat /proc/asound/version**
[COLOR=#0000ff]**Advanced Linux Sound Architecture Driver Version k3.8.0-30-generic.**[/COLOR]
amaazaoui@amaazaoui-HP-Compaq-nc6120-PN936AV:~$[B] head -n 1 /proc/asound/card0/codec97#0/ac97#0-0
[COLOR=#0000ff]0-0/0: Analog Devices AD1981B[/COLOR][/B]
amaazaoui@amaazaoui-HP-Compaq-nc6120-PN936AV:~$ [B]head -n 1 /proc/asound/card0/codec97#0/ac97#0-0+regs 
[COLOR=#0000ff]0:00 = 0090[/COLOR][/B]

---

### Post by Amaazaoui on 2013-09-18
Finally it works, without reboot needed.
Install xfce4-mixer

1- sudo apt-get install xfce4-mixer
2- launch the program: from terminal, type:  xfce4-mixer
3- go to "switches" Tab
4- select "Headphone Jack Sense"
---> the sound is switched to headphone only

---

### Post by Yellow Pasque on 2013-09-18
Do you have to do that every time you reboot?

---

### Post by Amaazaoui on 2013-10-07
no
you do it once

---

### Post by Amaazaoui on 2013-10-07
Install qfce4-mixer:  sudo apt-get install xfce4-mixer
launch xfce4-mixer from Terminal: /usr/bin/xfce4-mixer
go the tab "Switches"
Check the option "headphone jack sense"

and Enjoy

---

### Post by Kristian_Iversen on 2013-11-01
Tried this on 13.10 but with no luck..got a HP nc6120 as well with the same problem

---

### Post by olli-sylvanne on 2013-11-07
Well, I have ASUS eeePC and had also the same problem with sound. I removed Rhythmbox audio player and instantly my several problems related to videos and the loudspreaker/headphones disappeared. My music and videos all come now thru SMPlayer.

---

### Post by boeingx37 on 2014-02-06
Thank you so much. :) Your advice with xfce4-mixer helped me too for my Compaq-nc6120 on Lubuntu 13.10.

---

