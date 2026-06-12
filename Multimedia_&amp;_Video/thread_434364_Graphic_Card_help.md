---
title: "Graphic Card help?"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by looofenixtxoool on 2007-05-05
I just switched over from xp to ubuntu and i love it. the only thing is when ever i try to play a game such as armagentron the screen just turns black. sometimes i can hear the music. i cant seem to figure out the problem i install all the nvidia-glx drivers and made sure 3d acceleration are enabled and i still cant play any of them. the only game that seems to run is neverball and it justs shows the shadows. and help would be appreciated. i tried my best to search for the answer but everything ive come across hasnt fixed the problem. my graphics card is an Nvidia GeForce 4 MX if that helps.

---

### Post by pay on 2007-05-05
Run the game in the terminal i.e.```
armagentron
```and post the output after you quit the game to see if it has any errors.

---

### Post by BRAXS69 on 2007-05-05
have you guys tried reconfiguring the x server?
```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure xserver-xorg

```

the first line makes a backup of the xorg file witch contains all the settings for your devices and such. and so if you ever want to restore that backup you made just enter:
```
cp /etc/X11/xorg.bak /etc/X11/xorg.conf
```

the second line is a tool that reconfigures the xorg just enter the correct information about you system. and when you restart if all goes well you computer will boot without a hitch but if you get a message saying that you x server has crashed, don't panic you should be redirected to the shell and you could restore the backup or go though the configuration tool again.

also if you use a nvidia card you can reconfigure using its tool, and just fiddle around  
```
sudo nvidia-settings
```

remember to see the changes you made with the xorg file you need to restart, or simply restart your x server by holding the keys "ctrl+Alt+Backspace"

well that my ideas at the moment... good luck

---

### Post by looofenixtxoool on 2007-05-06
i tried running armegetron in the terminal and all i get is steve has left the game, no errors. i also tried the reconfigure x server deal. no luck with that either. im out of ideas =/. i dont know why certain games work and others dont run at all.

---

### Post by Cresho on 2007-05-06
try in terminal

sudo apt-get install nvidia-glx nvidia-kernel-common

then

sudo gedit /etc/X11/xorg.conf

go down the list selecting nvidia and then rename to NVIDIA and then just go down the list with defaults.  Then test under terminal by typing glxgears

if you are running beryl, disable it before launching 3d games.

---

### Post by pay on 2007-05-06
Are you running Beryl or Compiz ("Desktop Effects" in Feisty)?

---

### Post by looofenixtxoool on 2007-05-06
im running beryl and ill try the kernel thing now

---

### Post by looofenixtxoool on 2007-05-06
ok so i tried the nvidia kernel idea and it said it was already installed. so i tried disabling beryl and when i start the game i just see differnt colored lines moving on the screen and i can he the music. ill try to print screen it. is there anyway to make armagetron run in a window instead of fullscreen?

---

### Post by looofenixtxoool on 2007-05-06
here are a couple screen shot of what the game looks like when i play it under metacity:
[IMG]http://img354.imageshack.us/img354/9831/screenshotarmagetron1zi2.png[/IMG]
[IMG]http://img375.imageshack.us/img375/4227/screenshotarmagetronnn3.png[/IMG]

---

### Post by pay on 2007-05-06
Are you using Xgl or Aiglx?

---

### Post by looofenixtxoool on 2007-05-07
um how do i tell if im using xgl or aixgl. under settings in beryl it says force xgl if that helps?

---

### Post by pay on 2007-05-07
If you haven't specifically installed xgl, then it is probably aiglx. xgl has problems with games though. thats why i mentioned it.

---

### Post by looofenixtxoool on 2007-05-07
anyone else have any ideas?

---

