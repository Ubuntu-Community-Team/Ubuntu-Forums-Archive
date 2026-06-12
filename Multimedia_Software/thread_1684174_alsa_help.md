---
title: "alsa help"
date: 2011-02-08
forum: Multimedia Software
---

### Post by l3lhsl3 on 2011-02-08
after trying so hard last night to get my mic working on skype now my laptop doesnt recognize my sound card 



i cant remember what i did but i was messing around with alsa and trying to get it upgraded.  

i dont know if trying to update alsa again is the key ?  


im running 10.10



i currently am installing all the alsa backports listed in synaptic

---

### Post by lidex on 2011-02-09
Don't do anything just yet. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by l3lhsl3 on 2011-02-10
> **lidex said:**
> Don't do anything just yet. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]


will do as soon as the fresh install of ubuntu is complete.    



will fixing this drive problem also fix the reason why my headphone jack doesnt work on my laptop.?

---

### Post by l3lhsl3 on 2011-02-10
> **lidex said:**
> Don't do anything just yet. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]


Your ALSA information is located at [http://www.alsa-project.org/db/?f=66128bdc4aa5a5798fa1b522de5295b56121e959](http://www.alsa-project.org/db/?f=66128bdc4aa5a5798fa1b522de5295b56121e959)

---

### Post by l3lhsl3 on 2011-02-13
bump

---

### Post by lidex on 2011-02-15
Sorry for the delay. Try adding a model switch for alsa. Using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by l3lhsl3 on 2011-02-16
> **lidex said:**
> Sorry for the delay. Try adding a model switch for alsa. Using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

i tired that in terminal it asked for my password and then nothing else happend i also reset and it was still the same.  


the sound works now after i reinstalled ubuntu i just really would like the headphone jack to work/

---

### Post by l3lhsl3 on 2011-03-04
bump

---

### Post by lidex on 2011-03-06
Can you post your latest alsa-info?

---

### Post by Yellow Pasque on 2011-03-06
'ideapad' may be the keyword needed: 
> Main speakers work out of the box, headphone jack doesn't. This includes on-screen display of the sound, and pulseaudio's ability to set the volume greater then 100%. Adding 'options snd-hda-intel model=ideapad' to the end of /etc/modprobe.d/alsa-base.conf allowed the headphone jack to work (i.e., all sound outputs to the headphones if they are plugged in). It's not an ideapad, but setting model=toshiba made no difference. This works on all versions of the C655D, and is highly recommended.
[http://www.linlap.com/wiki/toshiba+satellite+c655d](http://www.linlap.com/wiki/toshiba+satellite+c655d)

---

### Post by lidex on 2011-03-06
Nice find T.

@l3lhsl3
Let us know how that works for you.

---

### Post by l3lhsl3 on 2011-03-31
ok guys sorry for the delay

i just wanna say thanks for all the help with this. 

what i had to do was 

add-apt-repository ppa:ubuntu-audio-dev/ppa
apt-get update
apt-get install linux-alsa-driver-modules-$(uname -r)

gedit /etc/modprobe.d/alsa-base.conf

then add options snd-hda-intel model=ideapad 

and it fricking works man !!!!!! 

:D
woooooooo [COLOR=Red]**thanks so much for the time guys**[/COLOR]

---

