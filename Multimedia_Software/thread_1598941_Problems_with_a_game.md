---
title: "Problems with a game"
date: 2010-10-17
forum: Multimedia Software
---

### Post by Mr.Sykkoh on 2010-10-17
Hi everybody ! :)
I have ubuntu for very long time and now my little sister wanted to give it try, after having too many problems with MS Windows.
So i helped her install it and teach her how to use it, but then i met a problem with the game "The Sims 3".
I installed drivers for nvidia and it works fine, after that i installed PlayOnLinux, and installed the game from there. That also worked until i started up the game. The game starts up fine and starts loading when its done loading it just closes, without any prompt or anything.
What can i do please help ! :)

Sorry for maybe writing in a wrong forum section

Thankes

---

### Post by Lazaruss on 2010-10-17
Try going through this troubleshooting list:
[http://www.playonlinux.com/en/topic-2530-Solutions_for_frequent_problems.html]("http://www.playonlinux.com/en/topic-2530-Solutions_for_frequent_problems.html")

---

### Post by Mr.Sykkoh on 2010-10-20
> **Lazaruss said:**
> Try going through this troubleshooting list:
[http://www.playonlinux.com/en/topic-2530-Solutions_for_frequent_problems.html]("http://www.playonlinux.com/en/topic-2530-Solutions_for_frequent_problems.html")

Thanke you i will try that tomorrow :)

---

### Post by Mr.Sykkoh on 2010-10-21
Hmm i tried everything on that list now and nothing works, i been wondering it maybe could be the no-cd crack theres something wrong with. Because it's starts up with fine graphic and starts loading when done loading it just closes without any error ?

Bug 18991 (crash loading a town) fix: 
env WINEPREFIX="/home/pablo/.wine-sims" TZ="America/Bahia" wine "C:\Archivos de programa\Electronic Arts\The Sims 3\Game\Bin\TS3.exe" 
The newest Mono fixes this error. 

This could be it i guess it's loading town at the start of the game. Never played it though, but i will try update Mono that should fix the bug right?

---

### Post by directhex on 2010-10-21
> **Mr.Sykkoh said:**
> This could be it i guess it's loading town at the start of the game. Never played it though, but i will try update Mono that should fix the bug right?

No. That's the problem none of the Wine devs were capable of understanding.

It's not your system Mono, it's the version of Mono built into TS3 - TS3 is programmed in Mono. The built-in version is old and buggy - but you cannot update it.

---

### Post by Mr.Sykkoh on 2010-10-22
> **directhex said:**
> No. That's the problem none of the Wine devs were capable of understanding.

It's not your system Mono, it's the version of Mono built into TS3 - TS3 is programmed in Mono. The built-in version is old and buggy - but you cannot update it.

Hmm okay what can i do then ?

---

