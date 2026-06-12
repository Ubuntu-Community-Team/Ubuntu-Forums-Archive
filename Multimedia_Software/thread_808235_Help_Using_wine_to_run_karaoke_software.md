---
title: "Help Using wine to run karaoke software"
date: 2008-05-26
forum: Multimedia Software
---

### Post by DesiDishoom on 2008-05-26
I recently installed Ubuntu 8.04 on my mom's old laptop that she managed to completely mess up...somehow. In any case, she's now a happy Ubuntu user except for the fact that she really wants to be able to use her karaoke software to play her Bollywood songs. I believe the database of songs she uses only has files that can be played by the KaraFun player, which is a Windows-only release. 

I attempted to install Wine using the guide in the Ubuntu community docs, and it seemed mostly successful except for a bevy of the same (or similar) error messages during installation of the package, but it didn't affect its completion...

i was able to install the application in the virtual drive C, and made Wine the default for exe files, but once i try to launch the exe, absolutely nothing happens. 

i'm not sure whether it has to do with faulty emulation, or maybe i just missed a step, but to the best of my knowledge, i followed the isntructions carefully. i would greatly appreciate some help with this! thanks everyone.

---

### Post by Koffee Kid on 2008-05-26
Hi, did you update Synaptic Manager first? In synaptic click reload for an update. I'm a Noob myself, so it might be an idea to look at how to upgrade it.
Did you click on the .exe file? Also try "right click" and "open with" then in the use custom command box type "wine". Then "open".

An alternative, Install Virtualbox and load up Windows OS on it. Virtualbox allows any operating system to run on a virtual pc.You choose the memory and hard drive size. Then install your Karaoke app on that, as usual.

Mike

---

### Post by Gunman1982 on 2008-05-26
Could you show what happens if you run the karafun player with wine in a console? There you can see more output and what actually went wrong. Open a console and execute 'wine <path_to_karafun_player>'. In addition did you check the appdb of the wine project if someone already tried to run the karafun player? What file ending do those karaoke songs have or are they stored in one big file which is not accessible?

---

### Post by DesiDishoom on 2008-05-26
thanks for the reply Mike!

yeah it seems to me like the wine version i installed is the most updated version (0.9.59) since i just updated synaptic, and i did follow those instructions to run the exe using wine (the whole "open with" -> wine command thing) but it tries to open it, but nothing happens after that.

i don't have a windows installation cd, so i was looking for an alternative to actually loading up the whole OS on with something like virtualbox, but that might be the only solution if i can't get this resolved. 

thanks again for the reply!

---

### Post by Koffee Kid on 2008-05-26
Dude,I installed aMule. Its interesting what can be downloaded.I wouldn't condone using it to download any iso files or keys to do with Micro$oft.

Mike[-X

---

### Post by DesiDishoom on 2008-05-26
input:

wine /home/[username]/.wine/drive_c/Program Files/KaraFun/KaraFun.exe
(i just copied and pasted the path to the file)

output:
preloader: Warning: failed to reserve range 00000000-60000000
wine: cannot find '/home/[username]/.wine/drive_c/Program'
 
this leads me to believe that it doesn't like the space in the folder name Program Files?

the karaoke files each have the extension .kfn, which by looking at seems like it's proprietary to KaraFun, but i could be wrong.

---

### Post by DesiDishoom on 2008-05-26
@Gunman1982: i just checked the appdb, apparently KaraFun used to work on previous versions of wine, but not on the current one...[Wine appdb:Karafun]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=11479")

@Koffee Kid: haha well i don't have to worry about that necessarily since XP is only 20 bucks at the campus computer store. so i wouldn't have to worry about M$ and their lawyer's wrath.

---

### Post by Koffee Kid on 2008-05-26
DesiDishoom, I've come over from PCLinuxOS, I installed XP yesturday, ran it for 10mins. Then installed ubuntu. I've had enough of M$oft, just some apps people have written can't be replaced easily. I'm using Steinberg's Wavelab 5.0. Audacity is good but....


Mike:guitar:

---

### Post by Gunman1982 on 2008-05-26
> **DesiDishoom said:**
> input:

wine /home/[username]/.wine/drive_c/Program Files/KaraFun/KaraFun.exe
(i just copied and pasted the path to the file)

output:
preloader: Warning: failed to reserve range 00000000-60000000
wine: cannot find '/home/[username]/.wine/drive_c/Program'
 
this leads me to believe that it doesn't like the space in the folder name Program Files?

Right, write a backslash in front of the space '\'.
> **DesiDishoom said:**
> 
the karaoke files each have the extension .kfn, which by looking at seems like it's proprietary to KaraFun, but i could be wrong.
It seems so yes, didn't find any solution to use it with another program or transform it :/

---

### Post by DesiDishoom on 2008-05-26
well, looks like this is going to be chalked up to plain "not gonna work"
here was the output after fixing the space issue:

preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:module:import_dll Library WMVCORE.DLL (which is needed by L"C:\\Program Files\\KaraFun\\KaraFun.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\KaraFun\\KaraFun.exe" failed, status c0000135

going by the response in the appdb and the completely unintelligible (to me at least) errors i just got, i guess a virtual desktop is my next best bet. Thanks for your help!

---

### Post by hchizkool on 2008-12-02
i installed it but then it wont open it does the starting karafun screen but then doesnt open???

---

