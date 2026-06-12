---
title: "No sound!"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by fenixfox on 2008-01-03
So fresh install. I have a yamaha sound card. I had to reinstall ubuntu the first time I had no net connection, but I had sound. Now I have the net but no sound.

---

### Post by pietjanjaap on 2008-01-03
Maybe this can hekp you:

1 asoundconf-gtk           
 choose soundcard to play



2

uname -r

aplay -l

lspci -v

cat /proc/asound/cards

cat /proc/asound/modules

cat /etc/modprobe.d/alsa-base



3

sudo asoundconf list
sudo asoundconf set default-card "name cardt"

4
asoundconf list
wat soundcards you have

---

### Post by fenixfox on 2008-01-03
heres what it says when i type asounconf (I'm very very new to ubuntu so I dont know what to type into terminal usually.) 

asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card PARAMETER
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio

---

### Post by fenixfox on 2008-01-03
sudo asnoudconf set default-card "YMF748C
> 
> 

now im here

---

### Post by Yellow Pasque on 2008-01-03
This thread is pretty confusing. Do you need additional assistance?

---

### Post by Kzin on 2008-01-03
I would try the volume before anything ;-)

---

