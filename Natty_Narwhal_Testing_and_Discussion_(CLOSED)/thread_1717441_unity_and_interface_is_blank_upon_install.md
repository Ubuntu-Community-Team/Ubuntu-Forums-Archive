---
title: "unity and interface is blank upon install"
date: 2011-03-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by thelastfoiter on 2011-03-29
I just updated to ubuntu 11.04 and theres no unity, no nothing. I downloaded it OTA so no disc was used. I know I can use the old gnome-shell but I don't want to. I'm running on a Dell dxp051 2ghz dual core, a crappy card, but it ran all 3d compiz stuff no problem, so I'm not sure what it is. Any help? PS. I have terminal open so thats really all I can do.

---

### Post by thelastfoiter on 2011-03-29
Oh and I'm lovin the aero snap, really a nice feature;) I also have unity installed so thats not it I'm pretty sure

---

### Post by cariboo on 2011-03-29
You can do all sorts of repairs from a terminal, first type:

```
sudo apt-get -f install
```

to make sure you are missing any packages, then try:

```
unity --reset
```

if that doesn't work install ccsm:

```
sudo apt-get install compizconfig-settings-manager
```

and make sure unity is enabled. You can also start synaptic from the terminal to see if you have any broken packages.

Keep in mind we are still using alpha 3, so make sure you do all the updates.

---

### Post by thelastfoiter on 2011-03-29
ok none of that worked but i dont know how to get to synaptics w/o a menu and i dont know how to enable unity. thanks in advance!

---

### Post by thelastfoiter on 2011-03-29
I need help cuz the only thing I have is Terminal!

---

### Post by cariboo on 2011-03-29
To start synaptic in a terminal type:

```
sudo synaptic
```

to check if Unity is enabled type:

```
ccsm
```

in the terminal. The above command will start compizconfig-settings-manager

I'd suggest if you are planning on using a testing release, that you sharpen up your command line skills, as these types of situations come up fairly often.

---

### Post by cariboo on 2011-03-29
Please don't create multiple threads on the same subject. I have merged your two threads.

As a new user, I would really suggest you install a stable version, or wait until Natty is released.

---

### Post by thelastfoiter on 2011-03-29
KK thanks bro but now that its working by graphics are all weird and fuzzy, I'm ganna try to solve it myself though.

---

### Post by cariboo on 2011-03-30
If you have an ATI graphics card, **don't** install the restricted drivers, if you've got an nVIdia graphics card just click the application icon and type [b]add[/] and select additional drivers from the menu if you are running Unity. 

If you are running the Classic desktop, click the Ubuntu icon and go to Administration->Additional drivers.

---

