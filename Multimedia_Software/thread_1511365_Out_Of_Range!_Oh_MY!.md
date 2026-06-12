---
title: "Out Of Range! Oh MY!"
date: 2010-06-16
forum: Multimedia Software
---

### Post by wesleybishop on 2010-06-16
Okay so when I try to play some games my screen goes black and says out of range can anyone help me with this PLZ. I switched from windows a while ago and thought there where no good games for Ubuntu but i was wrong there are good games but I just cant get them to work yet. This out of range issue is killing me when ever I try to start certain games it happens and i have to restart the computer.:-({|=

p.s. I LOVE UBUNTU! WOO HOO!!!!!

---

### Post by wesleybishop on 2010-06-16
bump

---

### Post by wesleybishop on 2010-06-16
Someone please help I see this problem a lot in the forums but no one ever answers!

---

### Post by Linuxforall on 2010-06-16
Can you post specifications of your hardware, the video card and if you have enabled video drivers?

---

### Post by wesleybishop on 2010-06-17
> **Linuxforall said:**
> Can you post specifications of your hardware, the video card and if you have enabled video drivers?

I have a n vida video card GeForce 7100 GS and I have the the most current and recommended Ubuntu driver for my card and that is the driver i have enabled.

---

### Post by wesleybishop on 2010-06-17
bump

---

### Post by Linuxforall on 2010-06-17
> **wesleybishop said:**
> bump

Add xswat ppa for latest driver.

In terminal sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update
sudo apt-get upgrade

Tell me how it goes.

---

### Post by wesleybishop on 2010-06-17
It did update the some nvida stuff but it did not solve the problem is there something i need to do to enable the new drivers?

---

### Post by wesleybishop on 2010-06-17
bump

---

### Post by wesleybishop on 2010-06-17
Also it does say out of range 75mhz i do not think that matters because i check the settings on the computer and they matched

---

### Post by wesleybishop on 2010-06-18
bump

---

### Post by sandy8925 on 2010-06-18
When it says out of range I think it means that the horizontal or vertical monitor frequency is out of range. or something like that. used to happen to me before in windows when playing empire earth. are you using a laptop or desktop? if desktop are you using a crt or lcd monitor and how old is it?

---

### Post by wesleybishop on 2010-06-18
I am on a desktop and its a LCD and its about 2 to 3 years old

---

### Post by CharlesA on 2010-06-18
Most LCDs run at 60Hz, if it's trying to push the display at 75Hz, that's the problem.

Ensure that the game is set to run at 60Hz.

---

### Post by konradmb on 2010-06-18
Can you tell what is the name of game you're trying to play and you run it inside wine?

---

### Post by wesleybishop on 2010-06-18
> **CharlesA said:**
> Most LCDs run at 60Hz, if it's trying to push the display at 75Hz, that's the problem.

Ensure that the game is set to run at 60Hz.

I checked my monitor already it runs at 75mhz thanks anyway

---

### Post by wesleybishop on 2010-06-18
> **konradmb said:**
> Can you tell what is the name of game you're trying to play and you run it inside wine?

not trying to run it in wine its aquaria its part of the humble indie bundle

---

### Post by wesleybishop on 2010-06-19
bump

---

### Post by sandy8925 on 2010-06-19
a

---

### Post by wesleybishop on 2010-06-20
bump

---

### Post by wesleybishop on 2010-06-20
SOLUTION: Start game press alt + enter its puts the game into windowed mode. 
Problem: game runs at max resolution of 800x600 my resolution is 1280x1024.

Huge thanks to nhasian for solving this issue for me.

---

