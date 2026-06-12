---
title: "Need help with wireless connection"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by Skramer on 2009-04-04
Hi, am brand new to both Linux and Ubuntu.
I am trying to get wireless connection on my computer.
I am useing Ubuntu 8.04
The wireless PCI adapter I am useing is from encore electronics ENLWI-G2.
I tried to put in the CD that it came with but that did not work.
So I went on to my other computer and went on to the encore website and put the driver for for Linux on to my flashdrive.
Then I put my flashdrive into the compputer that I put the Ubuntu on.
When I opened the file and right clicked and hit open it says that there is no application installed for this file type.
Howevere below where it said open it said open with application.
I have no idea what to do.
Can anyone help me?

---

### Post by Sniper.In.The.Darkness on 2009-04-04
Wow. ya think they would include some instructions! I took a look at that package and it looks pretty complex with no instructions!  Maybe its because i'm on my windows partition right now. If you found some i might be able try help, but this looks like you're gonna need to use the command line [terminal]. I'll keep looking.

---

### Post by Sniper.In.The.Darkness on 2009-04-04
Ok. That driver that they gave you is probably too advanced for both of us. [I too am somewhat of a linux n00b] ndiswrapper is a program that lets you use windows drivers in linux. it's kinda complex, but it sure as hell is easier than that other one. 

Here's the stuff that you need: 
ndiswrapper: [http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=655469](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=655469)

How to's: [http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)

[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926) 

Google search is your best friend here. 

Here is a troubleshooting guide: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

If you need any more help, I could provide limited assistance, since I haven't tried this, as my laptop had an atheros card :p so I could use the madwifi package. Good luck :twisted: .

P.S. the zip attached is the xp driver that you can use with ndiswrapper.

---

### Post by wstout on 2009-04-04
Skramer: lets try something a little simplier first. First thing you need to do is enable all the repositories in Synaptec, including third party. Next update Synaptec, then go to System administration, update manager and make sure all updates are installed, then go to system administration hardware drivers and see if you have an option of enabling it through the restricted drivers management. You stand a fairly good chance of that working.

---

### Post by Sniper.In.The.Darkness on 2009-04-04
sorry, i couldnt read the linux text files under windows, i'll post back with better instructions

---

### Post by Skramer on 2009-04-04
> **wstout said:**
> Skramer: lets try something a little simplier first. First thing you need to do is enable all the repositories in Synaptec, including third party. Next update Synaptec, then go to System administration, update manager and make sure all updates are installed, then go to system administration hardware drivers and see if you have an option of enabling it through the restricted drivers management. You stand a fairly good chance of that working.


How do I "enable all the repositories in Synaptec, including third party?"

---

### Post by Sniper.In.The.Darkness on 2009-04-05
I think I've got it now! That driver that you have is a little too confusing, and I got ndiswrapper working with my wireless on my other Ubuntu machine. Here's a step by step guide that's simple enough to follow. 

1. Download the latest stable version of ndiswrapper [attached]

2. Download the XP driver for your device [attached]. Yes, I am fully aware that you are running linux, but you need the xp driver, because ndiswrapper allows you to use it under linux. 

3. un-tar/zip them to your desktop [or other convenient place] 

4. Open up a terminal window [ Applications>Accessories>Terminal]

5.type "cd " with the space without the quotes, then drag the ndiswrapper folder into the terminal window so that it is like  "cd /PATH TO FOLDER" then hit enter and you should be in the ndis folder. 

6. type "make uninstall" [no quotes] in terminal window then hit enter.

7. Next type "make" [no quotes] and press enter [lots of code will run down terminal, wait until it stops and it stops spewing code for about a minute] 

8. Type "sudo make install" [no quotes] and then enter your password when it prompts you. [it doesnt show password dots so just type it then press enter] 

9. again, wait for the code to stop running. 

10. Type "sudo ndiswrapper -i " [no quotes] then drag the .inf file from the xp driver folder to the terminal, then press enter. 

11. now type "sudo depmod -a" *ENTER* "sudo modprobe ndiswrapper" and press enter [no quotes] 

12. type "cd /etc/modprobe.d/" [no quotes] 

13. type "sudo ndiswrapper -m" [no quotes] 

14. type "sudo gedit /etc/modules" [no quotes] 

15. a gedit window should pop up and then add ndiswrapper to the end of the file and click save, then exit. 

16. reboot

17. make sure the wireless device is connected, then click/ double click on the network icon on the top bar, enter your network key, and go! [I dont reccomend entering a password on the prompt, because you have to enter that password every time the computer starts. 

18. open firefox, type in google.com to test 

19. you should see the google homepage ;) if you did everything right. 

Good luck, and I hope that this helps.

---

### Post by Skramer on 2009-04-05
Ok I took those two attachemts that you gave me and put the on my flashdriv then put it into my other computer (the one with the Ubuntu on it). Now when I click open it say that there is no application installed for this file type.
What now?

---

### Post by Sniper.In.The.Darkness on 2009-04-05
which files? if its the archives you need to unzip them first which is built into ubuntu, if you cant unzip them from there then download 7-zip and unzip them on the non-ubuntu computer then copy them over, if you mean the files inside the archive, you aren't supposed to open them, you have to use the command line [terminal] make sure the archives have their file extentions [ndiswrapper = .tar.gz] [XP driver = .zip] if you need screenshot help, i'd be glad to give it. Thats my one complaint about linux: limited/difficult driver support, but I think i'm finally getting better at the UNIX/Linux command line [Terminal]

---

### Post by wstout on 2009-04-05
Skramer go to system-> administration -> software sources be sure that the first four tabs are checked, then go to the third party tab and be sure that all the free and non free options are checked, reload when prompted.
Then go to system-> administration-> update manager and apply all the updates to your system. Chances are you may have to restart due to kernel upgrade or what not, do all of that. then go to system -> administration -> hardware drivers and see if the check box is available to enable your driver. Just be warned the progress meter doesn't always work the best be patient :)

---

### Post by Sniper.In.The.Darkness on 2009-04-05
> **wstout said:**
> Skramer go to system-> administration -> software sources be sure that the first four tabs are checked, then go to the third party tab and be sure that all the free and non free options are checked, reload when prompted.
Then go to system-> administration-> update manager and apply all the updates to your system. Chances are you may have to restart due to kernel upgrade or what not, do all of that. then go to system -> administration -> hardware drivers and see if the check box is available to enable your driver. Just be warned the progress meter doesn't always work the best be patient :)

How will that help? The built in drivers are usually crap, and its not like windows where you just insert a file and expect it to run. why waste your time with this? ~25 lines of terminal code and a few files and it 95% of the time, it works ;) It took me about 15 minutes tops and I'm a still a linux noob, but I know what I'm doing here. [I didn't when I tried it the first time, because I was reading a more complex guide that wasn't well explained.]

---

### Post by wstout on 2009-04-05
sniper: why don't you offer up the correct option to help out here then ?  Ubuntu has the restricted drivers management for a reason, and it works very nicely.

---

### Post by Sniper.In.The.Darkness on 2009-04-06
> **wstout said:**
> sniper: why don't you offer up the correct option to help out here then ?  Ubuntu has the restricted drivers management for a reason, and it works very nicely.

well, just by using ndiswrapper works nicely too, and it has worked for me on various adapters, and it has a high probability of working. I saw the same solution as yours and it did absolutly nothing in my situation, sure, it may work for some, but don't you think the drivers are restricted for a reason? From my experiences with ubuntu, I've found that the built-in/restricted drivers [especially for network adapters] dont do a good job if at all. For someone that's new to linux, sure the command line isn't exactly simple, but in linux the terminal can be your greatest tool, so the sooner the user gets acquainted to it to the better. Also, I thought that synaptic required internet on the linux machine. [correct me if i'm wrong] which he apparently doesnt have. When I first started using linux, the wireless was my main problem [and since I wasnt very good at the command line, I dumped it.] I've recently have tried again, since it brought my data back from an inaccessible laptop hard drive. Next, I tried to get the wireless going using non-command line programs and settings panels. This got me nowhere and I got so frustrated that I was considering dumping it, but i was determined to get it working, so i used the command line with madwifi, and I got my laptop connected to the network. [ndiswraper for my desktops] both of which require some basic commands in the terminal. The whole point of that was to explain that while your method is easier and has a chance of working, if the user gets to know the command line, linux can be so much more powerful for them. [and it makes it easier when you need to deal with more complex commands.] If  ndiswrapper doesnt work for him, i can try to decode the vague instructions for the linux driver provided byh the manufacturer. [many more very complex terminal commands that I dont understand at this point, and i've been using linux for a while now.] Ndiswrapper should work, if not I'll try to simplify the manufacturer's instructions. I like to help get people on linux, because Microsoft is too error prone, and Apples a bitch for making it illegal to put their nice os on their severely overpriced mediocre hardware. Linux runs on almost anything and on top of that its a much more powerful os for FREE!!

---

### Post by Stuart Thomas on 2009-04-06
> **Sniper.In.The.Darkness said:**
> I think I've got it now! That driver that you have is a little too confusing, and I got ndiswrapper working with my wireless on my other Ubuntu machine. Here's a step by step guide that's simple enough to follow. 

1. Download the latest stable version of ndiswrapper [attached]

2. Download the XP driver for your device [attached]. Yes, I am fully aware that you are running linux, but you need the xp driver, because ndiswrapper allows you to use it under linux. 

3. un-tar/zip them to your desktop [or other convenient place] 

4. Open up a terminal window [ Applications>Accessories>Terminal]

5.type "cd " with the space without the quotes, then drag the ndiswrapper folder into the terminal window so that it is like  "cd /PATH TO FOLDER" then hit enter and you should be in the ndis folder. 

6. type "make uninstall" [no quotes] in terminal window then hit enter.

7. Next type "make" [no quotes] and press enter [lots of code will run down terminal, wait until it stops and it stops spewing code for about a minute] 

8. Type "sudo make install" [no quotes] and then enter your password when it prompts you. [it doesnt show password dots so just type it then press enter] 

9. again, wait for the code to stop running. 

10. Type "sudo ndiswrapper -i " [no quotes] then drag the .inf file from the xp driver folder to the terminal, then press enter. 

11. now type "sudo depmod -a" *ENTER* "sudo modprobe ndiswrapper" and press enter [no quotes] 

12. type "cd /etc/modprobe.d/" [no quotes] 

13. type "sudo ndiswrapper -m" [no quotes] 

14. type "sudo gedit /etc/modules" [no quotes] 

15. a gedit window should pop up and then add ndiswrapper to the end of the file and click save, then exit. 

16. reboot

17. make sure the wireless device is connected, then click/ double click on the network icon on the top bar, enter your network key, and go! [I dont reccomend entering a password on the prompt, because you have to enter that password every time the computer starts. 

18. open firefox, type in google.com to test 

19. you should see the google homepage ;) if you did everything right. 

Good luck, and I hope that this helps.

Hi

As a newby that looks like a very easy to follow set of instructions that even I could follow without messing up. I will probably give it a go when I am a bit more familiar with Ubuntu. A question that occurs to me is what happens with the Linux driver that is already installed? Do you have to uninstall it or put it somewhere out of harms way? I know that when I tried to install a wireless card on a laptop running windows I had a lot of trouble because the new driver conflicted with the  generic windows driver that was already installed.

Regards Stuart

---

### Post by Sniper.In.The.Darkness on 2009-04-06
> **Stuart Thomas said:**
> Hi

As a newby that looks like a very easy to follow set of instructions that even I could follow without messing up. I will probably give it a go when I am a bit more familiar with Ubuntu. A question that occurs to me is what happens with the Linux driver that is already installed? Do you have to uninstall it or put it somewhere out of harms way? I know that when I tried to install a wireless card on a laptop running windows I had a lot of trouble because the new driver conflicted with the  generic windows driver that was already installed.

Regards Stuart

you need to find the name of the driver i think its the chipset, and then blacklist the ones that were there before [if any] I'll post back with the command because its late and i dont feel like booting up my desktop that has the bookmark with the code yeah, pretty much I just want to have the follower execute the directions, and then if they say it conflicts or doesnt work, i'll look up their chipset and see if i can come up with the linux generic driver. generic linux drivers are to my knowledge restricted unless you enable tham the blacklist is usually just a precaution. Also in the cryptic instructions for the driver that the manufacturer of Skramer's card had on their site had nothing about blacklisting the ubuntu driver, which probably means that there isnt one. Also, if you do get conflicts just google search [NETWORK CARD NAME/MODEL chipset] then search [CHIPSET ndiswrapper instructions] or just look up [your network card ndiswrapper how to/ instructions] Believe it or not, I'm still a bit of a linux noob. [unfortuneately, vista's fat crapper took up too much space on my tiny 200gb hdd [yeah, tiny], and along with windows7 and my anime + southpark I had to kick off ubuntu until I save up enough money to buy a 500gb internal and a 500gb external Hdd. [If youre wondering oh a HDD isnt that expensive, not for somone with a paying job, but I'm only 13 [Yes, I'm a computer genius for my age. Surprised?] and I have to save up a few weeks of allowance to buy one , and it will be worth every penny! and yes, I kept wretched vista in case something goes wrong with windows 7[though I highly doubt it] But I still have it running on my ultimate compatibility machine with ubuntu as the main, xp, and ME [people that say that ME was the worst pre-xp system should keep their traps shut because its better for usb support and runs better then 95/98] At least windows 7 is a major improvement over [it burns my fingers just to type the evil name] vista. ow. :lolflag:

---

### Post by wstout on 2009-04-06
sniper: you don't know what restricted means. these are drivers that are proprietary that ubuntu can't distribute due to legal reasons. The method I described works very well with broadcom cards, which are generally thought to be some of the worse for linux support. The method also easily installs proprietary video drivers for both nvidia and ati that greatly improve the quality of your system. NDIS wrapper actaully does not work as well as using proprietary drivers made for linux systems.

---

### Post by Sniper.In.The.Darkness on 2009-04-06
ohh. sorry, I guess I got that wrong. and also yes, i see that it is a realtek card which means that your method probably will work better, but I think he sorta got it figured out on his other post. [http://ubuntuforums.org/showthread.php?t=1116119](http://ubuntuforums.org/showthread.php?t=1116119) Thanks, always learning something new. :twisted: at least I know to make sure I avoid the realtek chipsets, cuz all of my computers are / gonna be dual booted with ubuntu.

---

### Post by wstout on 2009-04-06
cool deal, yeah that's been whats hard for me to learn which hardware to buy when i'm lucky enough to purchase it :) still far from having much figured out :D

---

