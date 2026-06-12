---
title: "Hey !! its very urgent.Plz help me out...!!"
date: 2009-10-22
forum: Multimedia Software
---

### Post by pandeylavakesh on 2009-10-22
I've installed Ubuntu 9.04 yesterday.But the real issue is that I have not been able to watch movies and play songs(audio or video).When I started "Movie Player" it was showing an error with a message saying "Install multimedia plugins".After searching for two plugins that were there in the list namely [1.MPEG-1 Layer 3 (MP3) decoder & 2.DivX MPEG-4 Version 5 decoder].So how can I fix this problem?Please help me.
Similar is the problem with Rythmbox Music Player an error showing "Install Multimedia Plugins" came.After that it searched for the plugin & showed "No packages with requested plugin is found".
Name of the plugin was " MPEG-1 Layer 3 (MP3) decoder".
Point to be noted here is that in both of the cases(while playing movies & MP3 songs) name of the plugin was varying with the extension of the file.

I have tried my level best to make the issue more clear but still if u wanna know something about the error or whatever u can contact me.But its realy urgent please do help me.


Thanx a tonnnn......:P

---

### Post by utnubuuser on 2009-10-22
are your universe/multiverse repositories enabled?
System>>Synaptic Package Manager>>Repositories>>Third Party software


Used to be one had to add the medibunto repo to get proper codec for DVD etc, though I thought that that was no longer necessary.  Google for Add "Medibunto repository ubuntu".

---

### Post by Paul41 on 2009-10-22
Have you installed the restricted extras package?
```

sudo apt-get install ubuntu-restricted-extras
```

---

### Post by guriinii on 2009-10-22
get mplayer, it plays everything.

---

### Post by hanzomon4 on 2009-10-22
Are you connected to the internet? if so it should work

---

### Post by vinutux on 2009-10-22
1. Connect internet 

2. open terminal | Applications > Accessories > Terminal 

3. Type this in terminal ```
sudo apt-get install ubuntu-restricted-extras
```

give password and wait to complete installation..... it auto install plugins for you

---

### Post by pandeylavakesh on 2009-10-23
thanx for the support ....
actually i m newbie for linux esp. Ubuntu....
thanxxxxx.......again...[:)]

---

### Post by vinutux on 2009-10-23
> **pandeylavakesh said:**
> thanx for the support ....
actually i m newbie for linux esp. Ubuntu....
thanxxxxx.......again...[:)]

Welcom..........

plz.....mark thread SOLVED:)

---

