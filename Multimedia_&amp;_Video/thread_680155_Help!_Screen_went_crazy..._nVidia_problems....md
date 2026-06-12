---
title: "Help! Screen went crazy... nVidia problems..."
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by Prinssimikko on 2008-01-27
oh my... 

i somehow managed to screw my display settings and now i need a way to reset them! please help! i really wouldnt like to do another clean reinstall. and i really did try to find similar issues from these forums...:confused:

I am running Linux Mint (i believe its based on Ubuntu 7.10?), and i am a total newbie with this Linux thing... so please be patient :(

SITUATION:
When i start Linux, my screen flickers, then it's full of stripes and every item (folder, shortcut, whatever) is multiplied by three. so the screen is totally unreadable mess! i cant go to Terminal to write some stuff, because i can't see what i am writing!

I have dual boot system. I went to Windows XP, installed the FS-Driver program in order to reach the config-file and ask here if there is something wrong... BUT the FS-driver wont let me see my Linux-partitions (ext3), because there seems to be something funny going on and it only asks me to format it (which i won't do!)...

things started to go wrong when i tried to load the nVidia drivers in order to get fancier desktop effects... after reboot it all went wrong... 

I have an old AMD Sempron 2500+ PC (1,75ghz) with integrated graphics card (NVIDIA Vanta/Vanta LT), if that helps. My monitor is Samtron 71S LCD, which can give me 1280x1024 resolution. 

BTW, is it even possible for this configuration to have any of those desktop eye candy things? 

Please help! I'll try to give you more info if needed. I guess the main problem is that i cant really start Linux to access the Terminal in order to write some commands...

Thank you!

- Mikko

---

### Post by Prinssimikko on 2008-01-28
bumb...

anyone?
 i have spend hours to try to find solution, but with no luck...

---

### Post by Prinssimikko on 2008-01-28
hmm... i just found this page:
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)
which lists supported nVidia cards. my card seems to be on the very bottom of the list, on the section "Below are the legacy GPUs that are no longer supported in the unified driver. These GPUs will continue to be maintained through the special legacy NVIDIA GPU driver releases." and it states "1.0-71xx driver" for my integrated "Vanta/Vanta LT 	0x002C" card.

could some tell me what this means? and above all - how can i fix my issue? how can i access the command prompt (terminal) if my screen is totally messed up? can it be accessed before GUI boots up? and most importantly: what should i write there to reset my settings?

Thanks! i am a total newbie here, but very willing to learn!

- Mikko

---

### Post by djIMP on 2008-01-29
Hey, I feel your pain. Hope this helps. 

To get out of the crazy X session, use the key combination ctrl-alt-F1. You can also do things from the command line in single-user mode, which you may be able to choose when you boot. To install the correct driver down load the package from

[http://www.nvidia.com/object/linux_display_x86_71.86.04.html](http://www.nvidia.com/object/linux_display_x86_71.86.04.html)

and follow the instructions. You may have to do a few Ubuntu specific things first, described here

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

Good luck.

---

