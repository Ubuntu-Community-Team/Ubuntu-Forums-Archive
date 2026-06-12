---
title: "Please help, I'm pulling all my hair out!"
date: 2009-01-11
forum: Multimedia Software
---

### Post by korfx04 on 2009-01-11
Ubuntu 8.10

I Installed flashplugin-nonfree 9.0 and when i go to youtube i just get a grey box. I Tried to install the flash player 10 from the adobe website and seems like none of them files work. Another thing is, My Sound is not working!! my graphics card is an ATI HD 2600 Pro. I know in vista that i have to disable the HDMI so my onboard sound (Realtec AC'97) will work.

i already tried /etc/modprode.d/alsa-base and put this at the end of it

options snd_hda_intel index=3

But still nothing.

please help me before i pull the other 3 hairs out of my head.. :lolflag:


  -Linux Newb

---

### Post by Turd Ferguson on 2009-01-12
My suggestion would be to install Ubuntu Tweak and install Ubuntu restricted extras from Add/Remove under applications this package will add flash, java, and other useful packages. 

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by charmaker on 2009-01-12
:confused: you can download a [new program ]("http://www.car-cd-changer.net")from internet and install it again.):P

---

### Post by Turd Ferguson on 2009-01-12
> **charmaker said:**
> *spam post removed*

If that's a question to my answer then yes! Also reviewing my answer you may want to try downloading Adobe Flash Player via the Synaptic Package Manager if your not interested in java and the other packages.

---

### Post by aeronotix on 2009-01-12
Is the sound not working at all or just for the browser?

I remember having to put aoss within the command for the firefox launcher. 

For the grey box issue, have you got multiple flash plugin installed? 

What about this, remove all flash plugins and run this in terminal.

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by korfx04 on 2009-01-12
i got flash to work late lastnight, but my sound isn't working at all.

---

### Post by korfx04 on 2009-01-12
still i have no sound.. someone please help me with this issue, i have completely almost given up.. there's no need for me to continue on with ubuntu linux if sound doesn't work :(

---

### Post by korfx04 on 2009-01-13
no body has a fix?

---

### Post by korfx04 on 2009-01-14
CASE CLOSED:

Figured all of it out

Thanks for all your help!!! (sarcastic)

---

### Post by hazyumps on 2009-01-14
> **korfx04 said:**
> CASE CLOSED:

Figured all of it out

Thanks for all your help!!! (sarcastic)



...thats a bit unnecessary, ya?...i've got the same problem and am currently working on it the deal with mine is however:

sound was working with fresh install (btw...it was like my 5th fresh install to try to find the source of the prob...) i took my pcie ati x2400 card out - sound was great, as soon as i installed the card *not the drivers* the sound quit, installed the drivers for ati and sound still not working...installed the realtek drivers for the biostar mobo, they r recognized as intel chpiset AC97 *if i remember correctly* and when i lspci they read as...ATI R6xx HDMI? and after the install i have an alsa driver for HDA ATI HDMI? 

ill let you kno if i get there = in the mean time what does your lspci say...post it...also do u have a pci card or mobo with integrated parts...more specs help - alot.......

---

### Post by cdwillis on 2009-01-14
> **korfx04 said:**
> CASE CLOSED:

Figured all of it out

Thanks for all your help!!! (sarcastic)

Hey no problem. ):P

---

### Post by hazyumps on 2009-01-14
> **cdwillis said:**
> hey no problem. ):p

\\:d/

---

