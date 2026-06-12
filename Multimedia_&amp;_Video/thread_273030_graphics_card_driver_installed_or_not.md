---
title: "graphics card driver installed or not?"
date: 2006-10-07
forum: Multimedia &amp; Video
---

### Post by yuliang on 2006-10-07
I have xubuntu 6.06 installed on my ThinkPad R60e with Mobil e intel 945GM graphics card. But I don't know whether the driver for this card is installed automatically or not. The image quality seems not as good as in the Windows XP. Anyone knows how to check this. If it is not installed, how to install it?

---

### Post by RudolfMDLT on 2006-10-07
What Graphics card are you using? Ati or Nvidia?

open the terminal and type in the following:

fglrxinfo
and press enter.

It should display something like:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)

---

### Post by RudolfMDLT on 2006-10-08
I don't know where you got to.... If your graphics acceleration does work but the images are crap then:

1) get a higher resolution
system => prefrences => resolution
2) [http://en.wikipedia.org/wiki/Compiz](http://en.wikipedia.org/wiki/Compiz)

Compiz is a third party app that really makes your desktop come to life.
3) Ditch gnome for KDE, again searching the forum and google will really give much more advice than i can ever do. In short, KDE has a lot more eye candy, but, it's also a little more complicated to use.

---

### Post by yuliang on 2006-10-08
The graphis card is mobile intel(R) 945GM. The resolution is correct, but the image and font seems less clearer than in Windows.
By the way, I typed fglrxinfo, but 'command not found'.

---

### Post by RudolfMDLT on 2006-10-08
Sorry about that. fglrx seems to requier you running an ati card. Nvidia and intell cards are usaully installed without any hicups at all. To know whether you're drivers are installed see if you have rd acceleration:

glxgears -printfps

Let this run for about 10sec. If the fps number is below 500 then you have a problem. If it is above 500 then the card is working and then you may have to play arounf with diffrent contrass and brightness settings.

---

### Post by RudolfMDLT on 2006-10-09
If you ever do come back and read this... :)

Gnome does have uglier fonts than Windows, but you can fix this, just search for fonts on the forum.

CHeers!

---

### Post by yuliang on 2006-10-14
I runned the command in the Terminal. A window showing running gears poped up and the fps displayed in the terminal is above 1000. But this number droped below 200 the after I maximize the window showing animations. That was the first time. The second time I maximized the window, the screen went blank, and the system broke down. How do you think about those? And how to change contrast and brightness, by the way?

---

