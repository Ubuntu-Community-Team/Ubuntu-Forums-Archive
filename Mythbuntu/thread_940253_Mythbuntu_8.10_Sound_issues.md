---
title: "Mythbuntu 8.10 Sound issues"
date: 2008-10-06
forum: Mythbuntu
---

### Post by DemonBob on 2008-10-06
Here is the deal, i have a pvr-150 

8.04.1 - Sound works fine...

Upgrade to 8.10 -> with kernel 2.6.27-4 - Sound works fine

Upgrade to 8.10 -> with kernel 2.6.27-5 - No Sound 
Spent half a night trying to figure it out. 

Install from disk 8.10 beta -> with kernel 2.6.27-4 - No Sound.
Now i'm baffled. 

Install from disk 8.04.1 -> Sound works fine

There is deffentially a configuration change going on during the upgrade that is affecting the pvr-150. All new recordings/and live tv have no sound, i know my sound works fine, since i can play back ANY previous recordings from before this mess and the sound works fine.

---

### Post by damnick on 2008-11-02
Same problem here.
I just upgrade to 8.10 and only in mythtv i have no sound.

---

### Post by agamotto on 2008-11-03
Drop into XFCE, open the Sound preference, and make sure that you have the control for both the PCM and Master activated, and raise to near 100%.  Solved the problem for me.  This seems to happen with various *buntus with each upgrade.

---

### Post by mjezell on 2008-11-05
Also check your alsamixer settings (open a shell window and enter "alsamixer" to activate it) and adjust levels accordingly. Make sure to activate all needed funtions by toggling them with the M key on your keyboard. ("00" is on "MM" in disabled in small box under volume levels). When I did a clean install of 8.10 alternate amd64 I found most of the volume levels at "0" and most functions disabled. Hope this helps.

---

### Post by lmclaren on 2008-11-06
Hi,

I am using an ATV as a front end and are seeing the same problem, I use analog out and can't get a peep out of it, Has anyone with an ATV had any success? If so can you please advise on what devices etc you are using on the "General" page.

thanks

Lee McLaren

---

### Post by lmclaren on 2008-11-09
I have fixed my sound problem, after the update I needed to re-add an option under modprob.d that is needed for the ATV.

regards

Lee McLaren

---

### Post by f-win on 2008-11-13
Hi,

I used mythbuntu 8.04.1 for a while and everything worked beautifully. On Sunday I upgraded my distribution to 8.10. Here is what I found out:

- Installing the proprietary Nvidia GRAPHICS driver breaks sound on my machine!!!
- It does not matter which driver version I install (173.x or 177.x)
- If I revert back to the nv driver everything works fine!!!
- No the mixer levels are not the problem
- I first thought it might be an incompatibility between the Nvidia driver and the ALC888 chip on my motherboard. So I tried 2 different Soundblaster cards (Audigy and Audigy 2) and guess what exactly the same thing - sound with nv and no sound with the proprietary drivers
- I did not notice any errors in syslog or anywhere else
- I am using a GIGABYTE GA-EP35-DS3L motherboard
- Not using pulseaudio or any other sound server...
- I guess I not the only one having this issue but it seems like it is not very common either since I did not find a solution / bug acknowledgment anywhere [http://ubuntuforums.org/showthread.php?p=6046886](http://ubuntuforums.org/showthread.php?p=6046886)

I am happy to provide more information about the system if you have any questions.
Hopefully somebody is smarter than I am so I don't have to reinstall my system using 8.04 this weekend?

Thanks a lot,
-Florian

---

### Post by raptorjr on 2008-11-14
I have a Abit N73HD motherboard with ALC888. I also lost the sound with the upgrade to 8.10. But for me it was enough to install the 173 Nvidia drivers again to get it back. But it would be nice to find a real solution so i can use the latest drivers.
On the other hand it could have been somthing else i've done also. I think i tried everything before i downgraded the graphics driver. So now alsamixer dont report ALC888 anymore for soundchip, insted generic something. But atleast i have my sound back.

---

