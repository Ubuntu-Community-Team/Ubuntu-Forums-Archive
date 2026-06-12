---
title: "Flash plugin doens't get webcam image, just a green screen"
date: 2012-07-31
forum: Multimedia Software
---

### Post by iperich on 2012-07-31
Hi, I have a Logitech For Notebook Deluxe webcam working in a HP530 notebook, with Ubuntu 12.04, the webcam works OK in cheese and skype, but in Chrome and Firefox (flash 11.2 plugin) it only shows a green screen, I think it is probably a flash plugin issue... 

Thanks in advice.

---

### Post by iperich on 2012-07-31
I'm answering myself: I've eliminated the flash plugin, installed the adobe flash repo 

```
sudo apt-add-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"

```

and installed the flash-plugin again. 

It worked on Firefox but not on Chrome, because Chrome has its own flash plugin (with also gave me the green screen), so I de-activated the chrome plugin, and it used the correct plugin.

BUT..........................

The new flash plugin don't let me click on the "allow" or "deny" or "whatever" button on the permission dialog (or any other dialog) in Chrome and Firefox, so I went to 

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager08.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager08.html)

to always allow flash to use my webcam. And it finally worked.

As we say in my country "if it's not a sh*t is another", but well... i can stream my webcam.

---

### Post by BonusVitality on 2012-12-20
So I copy and pasted the code into terminal and it doesnt do anything it asks me for my password and then jumps to a new line. I also disabled the Flash Player plugin in chrome and it didnt help. If you could help me alittle more.

---

### Post by iperich on 2012-12-20
> **BonusVitality said:**
> So I copy and pasted the code into terminal and it doesnt do anything it asks me for my password and then jumps to a new line.

The code i wrote only set the adobe repo, did you installed the flash plugin again? 

```
sudo apt-get install adobe-flashplugin
```

---

