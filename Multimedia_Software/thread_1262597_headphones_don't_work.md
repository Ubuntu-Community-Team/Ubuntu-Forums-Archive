---
title: "headphones don't work"
date: 2009-09-10
forum: Multimedia Software
---

### Post by s4mk1ng on 2009-09-10
hello I've a matter with my headphones.I'm french so sorry if I don't speak good but to ubuntu.fr they can't help me.
So I have a Aver aspire 5738G with ubuntu 9.04,and the sound don't work with my headphones I test many solutions but I did'nt succes:(I use Alsamixer.
Please help me:wink:

---

### Post by Lampi on 2009-09-10
could you give us the output of

cat /proc/asound/version
cat /proc/asound/cards

---

### Post by s4mk1ng on 2009-09-10
thank you verry much.
For cat /proc/asound/version:Advanced Linux Sound Architecture Driver Version 1.0.18rc3.
And for cat /proc/asound/cards:0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf3400000 irq 21

Thank you.

---

### Post by Lampi on 2009-09-10
1.0.18rc3 is the version of ALSA - it's pretty recent but you could try the latest stable release (alsa 1.0.21)

There is a script [(link)]("http://ubuntuforums.org/showthread.php?p=6589810") in ubuntuforums.org helping you with the update process. Actually you rebuild the necessary sound modules for your kernel. The script is currently written for alsa 1.0.20, I guess it will be updated to 1.0.21 soon. So you could try 1.0.20 anyway or wait a few days for the script beeing updated or you can follow the howto in the ubuntu help guidlines: [Update to the Latest Version of ALSA]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by s4mk1ng on 2009-09-11
I try to update alsa but I do'nt succes,Ans when I make apt-get upgrade alsa he said to me there are not upgrade.
For this link:[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
I try but I don't see the options for an aspire 5738G.
Thank you verry verry much.

---

### Post by Lampi on 2009-09-11
I don't think there are options for your laptop, so just try to follow the howto in "Update to the Latest Version of ALSA":

Download the source code of alsa-driver,alsa-lib,alsa-utils (version 1.0.21) from the alsa ftp server and follow the commands in the text boxes. It's pretty simple, I never had a problem so far.

---

### Post by s4mk1ng on 2009-09-14
thank you verry much I make evrything and now I have installed the 1.0.20
> fingolfin@OptimusPrime:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on Sep 14 2009 for kernel 2.6.28-15-generic (SMP).
fingolfin@OptimusPrime:~$ 

But I've no sound in the headphones.
Please.
Thank you.

---

### Post by s4mk1ng on 2009-09-15
you know if a reinstall change anything.
Thank you verry much.

---

### Post by s4mk1ng on 2009-09-16
please help me:(

---

### Post by Lampi on 2009-09-16
hello s4mk1ng

well ... I don't understand why it doesn't work. See [http://doc.ubuntu-fr.org/liste_portables_acer_aspire_5xxx](http://doc.ubuntu-fr.org/liste_portables_acer_aspire_5xxx)

They say it works fine without additional options, maybe that's not true, I don't know!

make sure the mixers are all unmuted

---

### Post by s4mk1ng on 2009-09-16
ok I try and I say to you the result..
Thank you verry much:P

---

### Post by s4mk1ng on 2009-09-16
ok I try to touch to the properties in alsa-mixer and I succeeded to have sound in heaphones and in my speakers but I don't succeeded to have sound in one or in onther one.
Thank you.

---

### Post by s4mk1ng on 2009-09-16
ok it's good I just set the sound of speaker off and I've only the sound of headphones.
Thank you verry verry much:)

---

### Post by Lampi on 2009-09-17
glad to hear :)

---

