---
title: "best&amp;simple to install mp3 player help"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by secondstage on 2008-01-25
I'm looking for the best music player that will **support mp3 and wma files**. I understand that there are tons of different music players with the ability to play these file types. Also, if you could give a link on how to install, and troubleshoot it. I have reid to install amarok but could find where to download the .deb for gutsy.

1. What's it mean to compile a program?
2. How do you get a tar.gz file to work (i can extract it but from that point i have no clue)?

All help would be greatly appreciated! :)

---

### Post by RomeReactor on 2008-01-26
Hi. Note that the "best" player varies from person to person, depending on their taste and needs. Totem, the default media player in Ubuntu, can play MP3 and WMA files by installing the package **ubuntu-restricted-extras**; to install this package, open the Add/Remove application (Applications->Add/Remove); in the **Show:** change the dropdown menu on the top right to "All available applications", then search for **restricted**.

If you want an audio player with more features, then you can use Amarok, also available in Add/Remove.

> What's it mean to compile a program?
It means to create an executable file from source code.

> How do you get a tar.gz file to work (i can extract it but from that point i have no clue)?
Extracting the contents of a program compressed to tar.gz will usually result in a folder; inside that folder there should be a 'readme' or 'install' file with instructions on how to compile it and whether or not you need to install other packages before compiling--these packages are the dependencies. Most of the time the instructions go like this: open a terminal (Applications->Accessories->Terminal), change to the directory where the source code is:
```
cd /PATH/TO/SOURCE
```
and run:
```
./configure
```
then:
```
make
```
and lastly:
```
sudo make install
```

Note that these instructions may vary from program to program. Before compiling, you will need the actual compiler and other libraries; you can get them by searching for **build-essential** in Synaptic (System->Administration->Synaptic) and installing it; or, to install it from the terminal:
```
sudo aptitude install build-essential
```

---

### Post by secondstage on 2008-01-26
thanks a bunch :popcorn:

---

