---
title: "Scrolling graphics error - Artifacting - Acer Aspire 3053"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by DBAlex on 2007-11-16
[SIZE="2"]Hi,

I have an error with the graphics on my Acer Aspire 3053WXCi, when I scroll in Firefox or gEdit (or probably any application with a large file/slow scrolling) it produced the following graphics errors shown in the pictures, I just wanted to know if this is because of a hardware fault or a software problem?

[IMG]http://img3.freeimagehosting.net/uploads/53d4000ae9.jpg[/IMG]

[IMG]http://img3.freeimagehosting.net/uploads/ad35d08912.jpg[/IMG]

[IMG]http://img3.freeimagehosting.net/uploads/295f04944c.jpg[/IMG]

Also, it has only happened since I installed OpenArena, so could it be the integrated graphics overheating? It does specifically ONLY happen when I scroll with the large files though.

Anyway, any help, information or guidance is greatly appreciated...! :)

Alex.[/SIZE]

---

### Post by DBAlex on 2007-11-17
* * * Bump * * *

---

### Post by DBAlex on 2007-11-17
[SIZE="3"]Please, I really need to know whats happening here...

If anyone has **ANY** clue then **PLEASE HELP!** :(:(:(:(:(:(:(:(

Alex.

[I really hate bumping threads, but im scared my laptop is broke and need to know if its a hardware or software problem so I know if I need to contact Acer or not][/SIZE]

---

### Post by DBAlex on 2007-11-18
Still haven't found any help? 
:confused: , any helo is still appreciated... 

Please [SIZE="5"]**--don't--**[/SIZE] ignore me!

:-(

---

### Post by hispanico87 on 2007-12-04
Same problem for me with Ati Mobility Radeon X700, fglrx 8.43 and AIGLX enabled...

---

### Post by DBAlex on 2007-12-06
hispanico87:

Ahh, could you post some more details, possibly with a screenshot/photo? :)

I'm glad that someone else has the problem, it must be an ubuntu or a gutsy issue.

---

### Post by DBAlex on 2007-12-06
I'm also thinking of sudo apt-get upgrading' my xserver-xorg...

could this have a good effect on the problem? I'm just assuming that its some problem in the current version of the xserver with specfic hardware (intergrated ATI cards)

Thanks for any help.

---

### Post by DBAlex on 2007-12-08
[center]< - - - - -   - - - - -   - - - - -   - - - - -  - - - - -  - - - - -B U M P - - - - -  - - - - -  - - - - - - - - - -  - - - - -  - - - - - >[/center]

---

### Post by hispanico87 on 2007-12-08
I've this problem only sometime with firefox! but only sometime! after 2-3 minutes it fix! i don't know if the problem with "apt-get upgrade xserver-xorg" can be solved. 
I use openbox that WM and DE...
Sorry for my bad english...

---

### Post by Dubra on 2007-12-08
I have the exact issue with an ATI x600 pci-E card...
   I'm using the 8.42 proprietary drivers running aiglx, no glx installed, running compiz-fusion, etc..

      Restarting xserver usually clears the problem but this is bad.  I also notice some artifacting when the cursor passes over dark lines or text while scrolling.  It seems to grab onto the image and stretch it.  Moving the cursor around usually makes it go away.   Very odd that it only seems to happen when scrolling up....  anyone else notice that?

   When are the new and improved ati drivers going to be released?  I'm willing to experiment!

---

### Post by DBAlex on 2007-12-12
[IMG]http://img406.imageshack.us/img406/8899/dsc0019td3.jpg[/IMG]

Heres a newer picture of the problem, as you can see it also occurs on the mouse too, that corruption disappears when I move the cursor though... The screen corruption still stays though... I had to scroll up/down very quickly continously to produce the error again, so It seems its more an issue of general scrolling - not just with large files...

Should I file a bug report for this?

If not ill just re-install XP... Its not *really* annoying but I don't really like it occuring, even if it does disappear if I restart the XServer.

---

