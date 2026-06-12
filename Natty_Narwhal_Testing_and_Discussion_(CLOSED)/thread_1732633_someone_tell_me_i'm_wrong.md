---
title: "someone tell me i'm wrong"
date: 2011-04-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cheesekiller on 2011-04-18
I recently tried the 11.04 beta 2 (infact i'm still on it)

Now maybe this is because its a beta but holy crap it seems to eat cpu like crazy. just playing music in banshee eats up 50 to 100 cpu couple that with the 30min to import music from rhythmbox (because it only found 13 songs on its own).  rhythmbox finds my music in about 1 min if i clear stuff out of it     when in expo mode when i click to go to another workspace it makes my wobbly windows mess up like crazy. I have to use classic mode because unity is just waaaaaaaaaay too buggy.   it seemed twice as stable when i tried it in beta 1 the only problem i had with beta 1 was that i wasn't used to unity, but now with beta 2 its like holy crap my computer is dieing..........   someone tell me this isn't gonna be like this come the 28th...


also its eating up all my ram now, back in 10.10 it only ate up half unless i was running virtualbox windows.

I know its not ready yet but just want to be reassured that the world isn't going to explode....

---

### Post by uRock on 2011-04-18
Moved to Natty Narwhal Testing & Discussion.

I have not experienced any of these issues on my Natty system.

---

### Post by hornedfiend on 2011-04-18
I'm not seeing this issue either. On my core 2 duo, with firefox and banshee running, I get about 30% load/core.

---

### Post by TBABill on 2011-04-18
+1 Unity is running pretty well on my machine now and since beta 2 release it's a huge improvement over beta 1. I have managed to only crash it one time in about 18 hours of usage and I also crashed Chromium at the same time (with heavy video, many tabs open/closed, lots of back/forward/reload). My RAM usage is higher than in 10.10, but that's expected when running Natty in 3D. CPU usage is normal and with 4GB RAM I am still not hitting swap even under pretty heavy load.

---

### Post by gnomeuser on 2011-04-18
I would be most interested in seeing that performance bug filed.

[http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/](http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/)

---

### Post by cheesekiller on 2011-04-18
well i was running it on an acer aspire one with 1 gig of ram and a dual core atom 1.6ghz.      on meerkat it runs great but with natty everything gets buggy and i kept getting python.sh(or something close to that) error and i kept trying to report it but it would never open to report so finally i clicked ignore.  and as i said wobbly windows does horribly funny things so i guess i'm going to wait till the 28th and just revert to maverick. I'll see if i can file these bugs manually i guess. it just seems slower generally... meh i was hopeing it would run even faster then maverick. I'm glad noone else is getting these errors it gives me hope for the rest of my computers....  perhaps i should just do a format and install when it comes out on the 28th instead of upgrading. everythings backed up to ubuntu one anyway.

if anyone has any ideas on how to possibly make this less buggy tell me if i get any info before 4 hours from now then i'll definatly try it but in about 4 hours in installing maverick lol

---

### Post by keithpeter on 2011-04-18
> **hornedfiend said:**
> I'm not seeing this issue either. On my core 2 duo, with firefox and banshee running, I get about 30% load/core.

Hello All

EeePC 1000 (atom processor that shows as two cores in system monitor) with Firefox, dropbox syncing and banshee playing a podcast results in around 60% to 70% cpu on both 'cores' and 500Mb of ram.

Drops to around 45% when I quit banshee. Will probably use mpg321 when running on battery!

Cheers

---

### Post by cheesekiller on 2011-04-18
hmmm   yours has less resources then mine and seems to be running fine. perhaps there is some incompatibility with the acer?   i dont see why their would be.  It might be worth me just installing 11.04 from a format and trying it before i install maverick. did you upgrade or reformat?  I upgraded with update-manager -d

---

### Post by uRock on 2011-04-18
> **cheesekiller said:**
> I upgraded with update-manager -d

My money says that is the cause of the problems. I only do clean installs.

---

### Post by keithpeter on 2011-04-18
> **cheesekiller said:**
> hmmm   yours has less resources then mine and seems to be running fine. perhaps there is some incompatibility with the acer?   i dont see why their would be.  It might be worth me just installing 11.04 from a format and trying it before i install maverick. did you upgrade or reformat?  I upgraded with update-manager -d

This is my messing about machine, and its a fresh install from a USB made from my desktop PC running 10.10 using the System | Startup Disk Creator.

Atom 1.6 GHz processor, 1 Gb ram (first time I've ever gone into swap on this machine by the way), Intel chipset. Its not too laggy with the Unity interface.

---

### Post by cheesekiller on 2011-04-18
> **uRock said:**
> My money says that is the cause of the problems. I only do clean installs.


then i shall copy my videos (the only thing not on ubuntu one) and do a clean install! let the unity love begin?

---

### Post by cheesekiller on 2011-04-18
I'm writeing these down as i think of them so please don't hate me for this.


a clean install got rid of most of the crashing problems however me and unity are still far from being friends because it seems much slower it still seems glitchy as far as wobbley windows goes. 
you have to know what your looking for and type it in to get to it which makes opening programs slower also the limit to 4 workspaces annoys the hell out of me. I use ubuntu at work so i usually have ALOT of stuff open at once and the lack of a window list makes it much harder to keep track of my windows and thus makes it where i basically only have one window to a workspace.....  not to mention on a netbook that tanslates to even less space. if by the 28th it gets faster and wobbley windows is fixed then I'll definatly give it a try but even classic in natty is slower and the right click menu on some things look messed up. Also currently hplip isn't compatible with 11.04(i know compatibility is coming just saying...)

can i even install ut99 on natty?  it has to have some old stuff so i'm unsure.

i tried to install system moniter applet with the .deb from omg ubuntu but ultimatly failed, also cpu freq failed, also meh

unity would just make me trying to work in a hurry almost impossible... however i can see how if i had a huge moniter with lots of space that it could be usable on a desktop

did i mention unity doesn't seem to enjoy allowing you to actually have icons on your desktop.

I am really tying to enjoy unity i REALLY REALLY am i really am trying not to just complain..... a simple window bar at the bottom would go a long way seriously a looooooong way. unity just feels like theres alot of code behind an auto hiding panel with lenses that pop out. I'm not a programmer but it just seems like its missing ease of use. unity feels like i was made for a phone. gnome 3 also looks like it falls prey to alot of the same things i dislike about unity, i dont particularly care for kde. so it looks like by 10.10 ill have to be converted to unity. 

am i just asking a crappy computer to do too much? it didn't seem like it on 10.10. most of the people that i got to "convert" also feel as though unity sucks for the same reason 10.10 was good "ease of use" as in unity has alot less and 10.10 had tons and tons of it. in 10.10 you basically drag something and it goes there no matter what it is to where its going. in 11.04 if i try to drag from a lens to the desktop i get no icon.. lenses are a great idea just not all the way to fruition yet i think.

also the tomboy applet sucks... its just the regular one from the program, the one from the add to panel in 10.10 allows you to stick notes to the list and looks prettier.

also i feel as though i have to choose carefully what to put in my launcher because if i dont have it there then i'm going to have to go through a long complicated process just to open something.   before i could open any program in 3 clicks or less and no long list. my only issue on 10.10 was that sometimes the icons took a second to load not a big deal though a it certainly didnt cut down on speed. i love ubuntu and i started useing ubuntu because it was fast a reliable and seems to just be "put together well" but unity feels half done. I know theres classic but it even feels weird on 11.04(probably because it runs slower)

also everytime i change a setting in compiz it DIEZ! i love the fact 11.04 still uses compiz and i think it really improves unity but its not stable at all and playing with the settings proves that also wobbley windows why do you mess up when i click to change workspaces in expo?

unity just scares me because it seems to cut down on efficiency.

I really dont mean to be a complainer and i'm sorry if i have offended anyone. i really am looking for advice (not any advice that says oh use this different distro because im KEEPING ubuntu even if i hate unity) someone please tell me theres light at the end of this tunnel!  if worse comes to worse i'll probably stick with 10.10 until 11.10 hopefully stuff will be worked out completely then.... meh i hope so. i'm also scared that if i stick with 10.10 that i will lose compatibility with new stuff that comes out. meh i wish there was like ubuntu 11.04 without the unity or that they fixed unity to still let you get to places and apps quickly. meh.  still any advice please i welcome it as i want to stay updated with the newest ubuntu but i still want to be productive at work and also i dont want to think angry unity thoughts everytime i see a narwhal!

---

### Post by stragierk on 2011-04-19
Have you checked the System Monitor? Syndaemon ran crazy for a time on my end, so that might be one cause. (I killed it without any further problems.)

---

### Post by cheesekiller on 2011-04-19
it was a fresh install and anticipating such i never connected my ubuntu one account. the above experiences come from a fresh install on an acer aspire one. I hope it gets better and screw fresh installs i hate having to reload all my crap so im gonna use the crappy laptop i got as a guinea pig so i'll know when i can upgrade my main comps because fresh installing all these pcs would just be rediclous because i dont have time to just sit infront of a comp and install software and data all day and then wait for the rest to redl from ubuntu one on like 5 comps

---

### Post by cheesekiller on 2011-04-19
i  really hate not having a window list. someone needs to make a unity window list mod.....  meh

---

