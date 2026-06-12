---
title: "No Sound Suddenly Ubuntu 10.10"
date: 2011-03-02
forum: Multimedia Software
---

### Post by Singer on 2011-03-02
friends 
till yesterday (March/1/2011) there were no problems with the sound and i was able to watch movies and listen to songs and ya i didn't do anything like updating or so. but there is no sound now
i searched in google and ubuntuforums for a possible solution but was unable to find one please help. this is the outcome of the 
```
sudo lshw -c sound
``` command

```
  *-multimedia            
       description: Multimedia audio controller
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1e.2
       bus info: pci@0000:00:1e.2
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0
       resources: irq:16 ioport:ed00(size=256) ioport:ec40(size=64) memory:dfebfe00-dfebffff memory:dfebfd00-dfebfdff

```
hope this helps.

---

### Post by lidex on 2011-03-02
Interesting. Is this a laptop and did you suspend? 
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by Singer on 2011-03-05
> **lidex said:**
> Interesting. Is this a laptop and did you suspend? 
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

wow thanks Lidex that worked =D>=D>

---

### Post by lidex on 2011-03-06
You're welcome. Please mark the thread solved using 'Thread Tools' up top.

---

### Post by Singer on 2011-03-07
> **lidex said:**
> You're welcome. Please mark the thread solved using 'Thread Tools' up top.

done boss!!!

---

### Post by rockdude_vicky on 2011-05-31
vicky@heaven:~$ rm -r ~/.pulse ~/.asound* ~/.pulse-cookie
rm: cannot remove `/home/vicky/.pulse': No such file or directory
rm: cannot remove `/home/vicky/.asound*': No such file or directory
rm: cannot remove `/home/vicky/.pulse-cookie': No such file or directory

vicky@heaven:~$ sudo rm /etc/sound.conf
rm: cannot remove `/etc/sound.conf': No such file or directory

need help plz!!!:confused::confused:
i tried this and i'm done :p ;)
```


sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload


```

---

### Post by nethero on 2011-05-31
> **rockdude_vicky said:**
> vicky@heaven:~$ rm -r ~/.pulse ~/.asound* ~/.pulse-cookie
rm: cannot remove `/home/vicky/.pulse': No such file or directory
rm: cannot remove `/home/vicky/.asound*': No such file or directory
rm: cannot remove `/home/vicky/.pulse-cookie': No such file or directory

vicky@heaven:~$ sudo rm /etc/sound.conf
rm: cannot remove `/etc/sound.conf': No such file or directory

need help plz!!!:confused::confused:

Hmmmm.  Are the files you are trying to remove actually there?  When you go to your home directory and type Ctrl-H, do the .pulse .asound and .pulse-cookie files show up?

---

### Post by rockdude_vicky on 2011-05-31
Those files where not there i tried to find them using 'locate'

---

### Post by nethero on 2011-05-31
What's happening is you are trying to remove files that were never there to begin with so lidex's solution may not work for you. Try restarting your computer anyway and see if you have sound.  If not, then the problem may be with your sound card driver.  What sound card are you using? 

If your sound card is a pci sound card, type "lspci" in a command prompt and see if your sound card is listed.

---

### Post by marcotl on 2012-01-04
thanks a bunch! worked like a charm, though the .asound dir is not existing on mine, just deleting the .pulse dir seemed to work for me. :KS:KS
now the audio is back! :D

i wonder why it stopped working all of a sudden. maybe due to corrupt files?

---

