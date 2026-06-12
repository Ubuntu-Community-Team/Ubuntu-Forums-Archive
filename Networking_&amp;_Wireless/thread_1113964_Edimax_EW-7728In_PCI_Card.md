---
title: "Edimax EW-7728In PCI Card"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by gmcm1979 on 2009-04-02
I have recently installed ubuntu 8.10 on a secondary pc, the install went fine but i have no network connection. i am using an edimax EW-7728In wireless card [(link here)]("http://www.edimax.co.uk/en/produce_detail.php?pd_id=225&pl1_id=1&pl2_id=44"). I have downloaded a tarball for Ralink 2860 based cards but was unable to get it to work. Does anyone know if there is a debian file available for my wireless card or any help would be appreciated.

---

### Post by chili555 on 2009-04-02
Check here: [http://ubuntuforums.org/showthread.php?t=966185&highlight=2860](http://ubuntuforums.org/showthread.php?t=966185&highlight=2860)

I just ran 'sudo make' and it produces a few minor warnings, but no errors.

---

### Post by gmcm1979 on 2009-04-02
thanks i'll give a it try and let you know if it works.

---

### Post by gmcm1979 on 2009-04-02
i couldn't get that to work, i was able to do some of the steps but when i tried to edit the read only files from a terminal using sudo such as those in step 9 i either couldn't or it was really difficult to type in the changes. this is so frustrating i am now beginning to remember why i left linux the first time, everthing is just way to fiddly and to get the simplest thing to work takes ages and then breaks something else.

---

### Post by chili555 on 2009-04-02
I just noticed they ask you to edit these files with *vi.* That ***is*** fiddly! Please try:```
sudo gedit /whatever/file
```gedit is a simple text editor that will look a bit like an office kind of document creator. Then you should be able to easily edit your file by plopping your cursor behind whatever you want to change, backspacing and typing in your new text. Proofread, save and close. Done!

Have patience. A few minutes work and we can be all set!!!

---

