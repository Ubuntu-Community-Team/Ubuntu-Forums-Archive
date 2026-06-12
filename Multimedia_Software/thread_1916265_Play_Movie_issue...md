---
title: "Play Movie issue.."
date: 2012-01-27
forum: Multimedia Software
---

### Post by sschevy010 on 2012-01-27
Doesn't matter what format of movie i try playing and which player... it always blacks out after trying to play movie and takes me back to login. What is missing to this and what do i need to look for of which log file and to see why this is?

---

### Post by WasMeHere on 2012-01-27
Hi sschevy010,

You need to tell more about your system:

- computer specs: CPU , RAM, graphics driver
- OS: Ubuntu version, way to install it
- video player(s)

Did you read and tweak according to the following link?
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=766683_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

Have fun finding out about Ubuntu :-)
Olle

---

### Post by goldshirt9 on 2012-01-27
have you loaded the restricted drivers and the extra dvd drivers from the repository

---

### Post by sschevy010 on 2012-01-27
Yeah sorry about not having specs... Ubuntu 11.10 AMD64 ..  running Gateway Laptop NV53 series .. AMD Athlon X2 M300 with 4gb Memory, ATI Radeon HD 4200.

I am currently looking at some restricted updates but I swear i Have done those already and it got to point where it flashes to a screen with something said in black screen and i cant figure out how to get the screen to freeze so i can write it down lol. And it goes back to login like i just turned it on.

---

### Post by sschevy010 on 2012-01-27
> **Olle Wiklund said:**
> Hi sschevy010,

You need to tell more about your system:

- computer specs: CPU , RAM, graphics driver
- OS: Ubuntu version, way to install it
- video player(s)

Did you read and tweak according to the following link?
[[COLOR=RoyalBlue]_http://ubuntuforums.org/showthread.php?t=766683_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

Have fun finding out about Ubuntu :-)
Olle


Just did this link and still no go. Everytime it tries to start the movie, it just goes to black screen then back to login like it was just starting up from time you turn computer on.

---

### Post by WasMeHere on 2012-01-28
I don't think the codecs and such software cause the problems. You have an ATI Radeon graphics card. Often there are problems to make them run properly in Ubuntu. What happens (happened) when the proprietary driver is (was) not used? Did you get graphics but slow, or nothing?

I have nvidia, so I don't know how to make the ATI cards work. Let us hope someone else starts writing in your thread, someone who knows about ATI cards and Ubuntu.

---

### Post by sschevy010 on 2012-01-28
Well I didnt have this problem in 10.10 64bit but soon as i got 11.10 on.. 3d actually works in ATI Graphics but now I cant play any movies.. i can play a couple 3d games but they are choppy... Everytime i play any type of movies of any type of players it just kicks out of desktop into black screen with some letterings and back to my login screen. And this is not an upgrade to 11.10... its a clean install of 11.10 64bit

---

### Post by WasMeHere on 2012-01-28
Unfortunately 11.10 needs quite a lot more computing and graphics power to perform compared to 10.04 LTS and 10.10. At least when we are talking about 'vanilla' Ubuntu. It is partly due to the graphics drivers, that are not quite as efficient as the corresponding drivers for Windows, but it is partly due to the more complicated desktop environment.

One alternative is to try ***Xubuntu*** with a light-weight desktop environment, XFCE, and another one is ***Lubuntu*** with an ultra-light desktop environment, LXDE. Try them live: download the iso files and make boot CD or USB drives to try them before deciding if they are worth installing. I have read many positive posts about these two flavours of Ubuntu.

---

### Post by MoreOrLess on 2012-01-28
> **Olle Wiklund said:**
> Try them live
It would be far easier to install them in the existing installation and they don't take much disk space (especially lxde), and yes, the fglrx/Catalyst driver is known for having issues with Unity/Gnome 3. Catalyat 12-1 supposedly fixes some of these issues, but I wouldn't try that (yet).

As for getting kicked out of X, the error message should be in ~/.xsession-errors

---

### Post by sschevy010 on 2012-01-28
> **MoreOrLess said:**
> As for getting kicked out of X, the error message should be in ~/.xsession-errors

Where am i looking for this? I will keep lookin but Directory is confusing me for which I understand it would be under my account folder etc..

---

### Post by Rodney9 on 2012-01-29
> **sschevy010 said:**
> Where am i looking for this? I will keep lookin but Directory is confusing me for which I understand it would be under my account folder etc..
 .xsession-errors will be in your Home Directory.

You will have to turn on 'Show Hidden' under 'View' in PCMan.

 
For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

