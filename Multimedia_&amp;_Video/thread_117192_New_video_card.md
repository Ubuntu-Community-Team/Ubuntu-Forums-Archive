---
title: "New video card"
date: 2006-01-14
forum: Multimedia &amp; Video
---

### Post by Christopher999999 on 2006-01-14
Recently I have bought a new AGP 64 MB Video Card. It seems that new new card has been giving me nothing but problems. When I start up ubuntu, just before the login screen, it shows me a error alert. It can not intalize soemthing. It has been messing up windows too. What should I do here? I got the card from tigerdirect.com and it was only $5 (after rebate).

---

### Post by kiddo on 2006-01-14
First, describe the card name, manufacturer, model. Then, the errors you get...

---

### Post by Teroedni on 2006-01-14
[FONT="Impact"]Open Terminal and write[/FONT]

```
lshw -class display

```

Post the result here.

---

### Post by Christopher999999 on 2006-01-16
I fixed the problem by reinstalling ubuntu.

---

### Post by Omnios on 2006-01-16
Just so you know you probably could have fixed the problem by pressint CTRL-Alt_F1 and running 
```
sudo dpkg-reconfigure xserver-xorg 
``` 
in comand like and going through the praphical config program

---

### Post by az on 2006-01-16
[QUOTE=Omnios]Just so you know you probably could have fixed the problem by pressint CTRL-Alt_F1 and running 
```
sudo dpkg-reconfigure xserver-xorg 
``` 
in comand like and going through the praphical config program[/QUOTE]


..or

sudo dpkg-reconfigure -phigh xserver-xorg

for it to re-run autodetection without asking you any annoying questions.  Use this with no X server running, since it often cannot autodetect hardware with an X session running.

It would be great if it could run that automagically every time it thinks you install a new card.

---

### Post by Omnios on 2006-01-16
Kewl im bookmarking that one lol. :"Tips Hat"

---

### Post by DirtDawg on 2006-01-17
[QUOTE=azz]
sudo dpkg-reconfigure -phigh xserver-xorg

for it to re-run autodetection without asking you any annoying questions.  Use this with no X server running, since it often cannot autodetect hardware with an X session running.[/QUOTE]

Good God this trick saved me a headache. I've said it before and I'll say it again: 
 "I like Azz!"

---

### Post by jorge_f_gonzalez on 2006-01-18
Well, that'll come in handy!!  That command should be documented somewhere in the easily accessible Ubuntu documentation pages.  Too often critical information like that is missing from there.

---

