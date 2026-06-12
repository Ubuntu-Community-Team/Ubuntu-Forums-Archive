---
title: "how to fix  low graphic mode"
date: 2011-03-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-03-05
i was messing around trying to increase my display res and pouched my system. i get the ubuntu is running in low graphic mode error and just wont start x. tried to update run backups and no avail. i think if i could set my nvidia to current it would fix the issue but have no idea how to do

---

### Post by rburkartjo on 2011-03-05
can boot into recovery mode no problem

---

### Post by Harry33 on 2011-03-05
> **rburkartjo said:**
> i was messing around trying to increase my display res and pouched my system. i get the ubuntu is running in low graphic mode error and just wont start x. tried to update run backups and no avail. i think if i could set my nvidia to current it would fix the issue but have no idea how to do

Start Natty with recovery mode (choose form grub).
That works even without gdm and X.
Then from the menu (whiptail) choose "drop to shell with net".
Now you have a console and you can install packages.
If you want to start X, choose from the menu "failsafe" boot. You need to have xserver-xorg-video-vesa installed.

I did not quite understand the words about nvidia nor what do you want to do.
How did you try to increase the res?

---

### Post by rburkartjo on 2011-03-05
harry what i did was i increased the res to high for 11.04 a3 to read just really need to set display res to 800 X 600 as default and that should fix problem. it think or if you have any other ideas great. thought that trying to do an update from the console would fix but didnt tks

---

### Post by rburkartjo on 2011-03-05
still stuck only can get to the 11.04 splash screen and then it shows trying to load but doesnt

---

### Post by rburkartjo on 2011-03-05
think i fixed will reboot and find out. i just had to reinstall the ubuntu-desktop

---

### Post by rburkartjo on 2011-03-05
well that didnt work i can now boot up in safe graphic mode though. which gives me a desktop about 1/3 the normal size everything stills work. using nvidia driver as mentioned before. again i am open to suggestion; there has to be a way to fix. tks

---

### Post by plun on 2011-03-05
The first step which must be done is to check what graphic card you are using.

```
lspci | grep VGA
```

If it is a **nVidia 6xxx or above** (otherwise you must use Nouveau).

```

sudo apt-get install --reinstall nvidia-current

sudo nvidia-xconfig
```

Restart !

---

### Post by rburkartjo on 2011-03-05
pun tks copied it down and will reboot into my linux hard drive. one question if it is Nouveau what would i do. tks

---

### Post by plun on 2011-03-05
> **rburkartjo said:**
> pun tks copied it down and will reboot into my linux hard drive. one question if it is Nouveau what would i do. tks

Well what gives this ?


```
lspci | grep VGA
```

?

---

### Post by rburkartjo on 2011-03-05
plun here is out put note i cant copy and paste 

i bad a forgot i update by graphic card
here is output

01:06.0 VGA compatible controller: ATI Tech inc M9+5c63[radion mobility 9200 (AGP)]rev 0 1)

---

### Post by plun on 2011-03-05
> **rburkartjo said:**
> 
01:06.0 VGA compatible controller: ATI Tech inc M9+5c63[radion mobility 9200 (AGP)]rev 0 1)

As you can see you are running an ATI graphic card.

This card is too old for running a proprietary ATI driver.

Maybe this can give you some clues ?

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by rburkartjo on 2011-03-05
tks pun cant figure out why it was working great until i messed with x.org. i will figure it out. tks again

---

### Post by plun on 2011-03-05
> **rburkartjo said:**
> tks pun cant figure out why it was working great until i messed with x.org. i will figure it out. tks again

Ok..... the first step is maybe to remove nVidias driver

```
sudo apt-get remove nvidia-current
```

---

### Post by rburkartjo on 2011-03-05
okay i got it to start in full graphic mode. how can i save this current xconfig.(what would be the command) because i know if i restart without saving it will not reboot correctly/tks

---

### Post by plun on 2011-03-05
Well... it will be "automagic" take care of.....

But remember what graphic card you are running !

---

### Post by rburkartjo on 2011-03-05
plun working great

---

