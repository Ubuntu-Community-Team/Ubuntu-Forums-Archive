---
title: "My World of Warcraft login screen is blank!"
date: 2008-08-16
forum: Multimedia Software
---

### Post by gluonman on 2008-08-16
Greetings.
   I installed World of Warcraft: Burning Crusade on my laptop. It seemed to be working just fine, login-screen included, up through installing all the latest patches. When the most recent patch was finished installing, however, I attempted running launcher.exe with wine and the login screen is blank. The animation is in the background, but the username and password bars are missing as well as any of the other elements that should normally display on the screen. There is nothing apparently wrong with my wine configuration or installation or even the installation of World of Warcraft itself. I have it installed on my desktop and it works just fine, but it just doesn't work on my laptop. Maybe it's a hardware issue?
   Any help would be much appreciated.

---

### Post by Beshaba on 2008-10-16
I solved the problem by going into the WTF file. 
How to go to the WTF. file: 
In the applications menu-> Wine -> Browse drive C-> Program Files-> World of Warcraft -> WTF (it's a folder) then open Config.wtf

I changed 
SET gxApi "opengl"
with: 
SET gxApi "direct3d"

Let us know if that works for you.

Beshaba

---

