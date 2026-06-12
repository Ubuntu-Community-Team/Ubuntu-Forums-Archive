---
title: "Help for amarok"
date: 2008-08-19
forum: Multimedia Software
---

### Post by ultimate_aektzis on 2008-08-19
Hello everybody!I want to use amarok to listen to my music and my streams but when I load my playlist a message apperas from the bottom-left window side saying

> Audio output unavailable; the device is busy.
xine parameters: 

Can I do something to fix this.I like it very much and I dont want to change it.
I would appreciate any kind of help.
Thanks in advance

---

### Post by bbq^ on 2008-08-19
Perhaps go to System->Preferences->Sound and make sure things are correct. Use the test options there to help with this :)

---

### Post by ultimate_aektzis on 2008-08-19
No ,unfortunately nothing happened.I change prefs from auto to something else considering test button's result.I think that a bug exists.what do you think?

---

### Post by ultimate_aektzis on 2008-08-19
Is there anybody here?

---

### Post by bbq^ on 2008-08-21
Are you using onboard sound ? (motherboard) or a pci sound card. 

lspci in console see if it shows your sound card

---

### Post by rossjman1 on 2008-08-21
In order to use Amarok while another app is outputting sound you need to change Amaroks sound engine from 'Autodetect' to Alsa.
In Amarok:
Settings > Configure Amarok > Engine
Change output plugin from Autodetect to Alsa.
You may need to restart Amarok.

---

### Post by rossjman1 on 2008-08-21
In order to use Amarok while another app is outputting sound you need to change Amaroks sound engine from 'Autodetect' to Alsa.
In Amarok:
Settings > Configure Amarok > Engine
Change output plugin from Autodetect to Alsa.
You may need to restart Amarok.

---

### Post by ultimate_aektzis on 2008-08-21
> **rossjman1 said:**
> In order to use Amarok while another app is outputting sound you need to change Amaroks sound engine from 'Autodetect' to Alsa.
In Amarok:
Settings > Configure Amarok > Engine
Change output plugin from Autodetect to Alsa.
You may need to restart Amarok.


Thank you so much my friend rossjman1.It worked at last.Thank you all for your help:)

---

