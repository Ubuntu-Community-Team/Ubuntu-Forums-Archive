---
title: "Critical Error in Ubuntu Hardy heron?"
date: 2008-06-21
forum: Multimedia Software
---

### Post by nightwolf2k5 on 2008-06-21
Dear all,

I just installed the flash plugin for my laptop. Now the tabs in mozilla disappeared, the google search option in the right hand corner of the browser does not work! If i goto tools and choose downloads or add ins, the browser crashes!.. To make matters worse, the shut down does not happen. If i click on the right hand corner button, instead of getting a nice pop up showing me the different options (shutdown, restart etc), I have the two panels disappearing and my desktop visible!.. I have to then click the power of button on the laptop for a successful shutdown.
THis is the second time I am facing this error, I formatted and reinstalled my previous ubuntu installation. But now, I have removed the flash plugin to be able to use my browser and post this here. The shut down problem is still present..
Help me.. Oh ubuntu Guru's! My impression of this Linux has fallen thanks to this!

---

### Post by LunatikOwl on 2008-06-21
I'm in not way a Linux guru but I know that you won't get much replies to you post unless you provide more details about the issue. You got to understand that problems like this one are not common. In-fact most users probably won't experience something like this ever(unless they do some no-no like compiling and installing a random source-code from the 'net on a production machine).

I suggest that you provide you're hardware specs, ubuntu version and the package you installed for starters. But since I'm not a guru that might not be enough. Also, try to google the the package name with some other keywords like bug or shutdown to see if this bug is documented.

---

### Post by nightwolf2k5 on 2008-06-22
hi LunatikOwl.. I have an Acer 5004NWLMi. Amd trion 64ML-34 processor, 60gb hdd, DVD-writer, 608 mb of available ram.
THe steps of recreating the error i mentioned was as follows.
1) Install ubuntu
2) Try and play and mp3 file, then it asks to download the plugins and after which it says updates are available.
3) Update the packages (by running the bright orange thingy on the top right corner).
4) goto youtube.com. It asks for plugins, so, install the flash plugin.
5) THe flash plugin works for a while. Then suddenly, when you are updating ur packages (I couldn't update all at one go cuz of the net connection speed), the browser hangs (Firefox).
6)When I reopen the browser, the tabs go missing. When I try to use the google search tool on the top right corner, it becomes non responsive (i.e. I type what i want to search and press enter and nothing happens. Even when i manually click on the search icon, nothing happens thus ruling out a hardware problem).
7) If i go to tools->add ins or downloads, the browser disappears.

Now it might be rare and all that, but, its happened to me twice! THe first time, I had added the extra mediabuntu repositories. I figured that maybe thats what caused the whole problem, so the scond time (After the format) I did NOT add the mediabuntu repositories.

Btw, the second time, I was also installing a power management tool called kpower, that also hanged and did not open.
As of now, both kpower and flash have been removed. (Kpower was removed first to check if that was giving the problem, then when the problem still remained, the flash was removed). Now the tabs are back and the shutdown works perfectly.
I have now installed a different flash plugin (Swflash or something like that). Everything works ok, for now. But, the instability after installing the maromedia flash plugin is pretty scary windows like!

EDIT: I still have the error. The browser crashes everytime I goto tools-> addon or download.
I am also unable to download files!

Edit: The back button also does not work.

---

### Post by cariboo on 2008-06-22
There is probably something corrupted in you default directory. open up Places-->Home Folder and hit Ctrl-h this will show all the hidden files and folder. The first thing to do before you do anything else is try to export your bookmarks. If you are using Firefox 3 there is a choice to backup or export html. the choice is yours to do either. Now that you have safely backed up  your book marks, the default folder is in .mozilla/firefox. Double click on .mozilla then double click firefox, you should see a folder named xxxxx.default. Delete this folder and profile.ini. the file and folder will be recreated when you start Firefox again. The only other thing to do is to restore or import your bookmarks, and then you can redo the addins

Jim

---

### Post by nightwolf2k5 on 2008-06-22
i think there is a bigger problem.. now the synatic package manager does not work.. i'll do what you said.. but.. i'm guessing there is a pretty big issue with ubuntu. I haven't done anything to actually cause such a big failure of the OS.
It almost feels like its hanging by a thread before it crashes completely..

Edit: WOW.. syanptic package manager and firefox are back to normal!! awesome.. let me check the flash plugin now and see what happens..

---

