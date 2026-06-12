---
title: "black screen with flashing curser xps_630I graphics card issue?"
date: 2012-03-14
forum: Multimedia Software
---

### Post by wavebreak on 2012-03-14
Hello,

At first I thought I had an installation problem but now I believe it is a graphics card problem.

I have installed wubi 11.10 after the first reboot it goes to a complete black screen with a flashing cursor. If I then turn off my computer manually by holding the off button and turn it back on the grub menu loads perfectly I can then choose windows visa (64bit) or ubuntu, vista works as normal however when I try ubuntu it goes to the black screen with flashing cursor. This happens even if I open windows first and shut it down correctly and reboot and try opening ubuntu so its nothing to do with not shutting windows down correctly. Which leads me to thinking it may be linked to hardware, most likely graphics card. 

I have a xps_630i:
op = windows vista 64 bit[COLOR=Red]
gc = NVIDIA GeForce 9800 GT - chip type = NVIDIA GeForce 9800 GT - Dac type = Integrated RAMDac - Total memory = 1647mb[/COLOR] (glad I checked this because I thought I had one of the 8800 dual graphics card range).

Trying to get the latest version of wubi to work 11.10.

Is there a driver I need to install if so which one and how do I install it/use it. If not any other advice please make it a newbie friendly as possible.

If you need any other info let me know and thank you to all that help/try to help in advance although I will thank you again if you help me to fix/get round the problem that I am having. ):P

ps
Sorry if this has been covered please link to the topic if it has been. I am new to the forums and have been trying to get wubi to work for some time now and am starting to loose patience with it.

---

### Post by bcbc on 2012-03-14
You'll need 'nomodeset': [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Check post #8, it sounds like you have the install with the wubildr-disk.cfg so I'd start there. Then install the driver once it boots.

Good luck

---

### Post by wavebreak on 2012-03-15
Thanks bcbc completely forgot there was a method 2 as I went to bed after reading the first one... However problem not solved :/ 

[COLOR=Gray]Can ignore this bit in () if you want:
(Had a bit of a struggle with this, first time I tried and saved it as txt without noticing then thought ow I will try again to reinstall wubi and change the file, again I saved it as a txt file without noticing unsurprisingly it didn't work so then I reinstalled wubi and edited the file in notepad instead of wordpad as I knew how to change the file type... didn't work. Then I read about having to use wordpad due to the line spacing so I figured out how to change the file type in wordpad (not that hard lol) and followed the whole process correctly for the first time by reinstalling wubi editing the file it wordpad saving in the correct format.)[/COLOR]

I rebooted to see if it had worked and same old story of the screen coming up black with a flashing cursor before the grub menu. With each reinstall of wubi taking 20 min and the slowish speed of my computer booting up/down I have spent quite a bit more time on this. Hopefully I will get there in the end with a little help ;) .

Note - When editing the file in the txt editor I deleted it all and copied and pasted what was given in your guide. I then pressed backspace 1 time to get rid of the space after the last word "boot" as I presumed this was a copy/paste error if this isn't a copy/paste error and will affect the results I will give it another go but its 4:30am now and I have to get some sleep.

Another thing that I thought of is doing something in the menu before the grub menu the one that says dell and press f something for boot options never tried it but if someone reading this thinks it will help then i will give it ago. Think it gives options like safe mode but have never used it so don't know for sure.

Look forward to your reply and/or anyone else. Sorry for the wall of txt tried to break it up with paragraphs.

edit:
If there is no solution its possible I have a instillation error and not [862003]("https://bugs.launchpad.net/bugs/862003") which I am pretty sure it is if some one would like to check this here I would be happy to dig up the file that the error points me to for someone to check tomorrow. If this is the wrong place for that then I can make a new topic in the correct forum as well, let me know.

---

### Post by bcbc on 2012-03-15
> **wavebreak said:**
> edit:
If there is no solution its possible I have a instillation error and not [862003]("https://bugs.launchpad.net/bugs/862003") which I am pretty sure it is if some one would like to check this here I would be happy to dig up the file that the error points me to for someone to check tomorrow. If this is the wrong place for that then I can make a new topic in the correct forum as well, let me know.

Are you saying you get an error within windows as well? If so, post the log file (find it in the %TEMP% directory).

At this point, it might be simpler to download the desktop CD ISO yourself (every time you try to install it's downloading the 500MB preinstalled diskimage). And the nice thing about using the ISO is that you can also use it to create an Ubuntu CD or USB.

So what you'd do, is download the desktop CD from here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
Then save it in the same directory as wubi.exe (that you have already). Then run wubi and it should find and use the ISO. In this case, you'd use the other method in post #8 to override the boot options.

---

### Post by wavebreak on 2012-03-15
Thank you again bcbc (I really do appreciate your help) but again I think something is not working. 

After downloading that file I no longer get an error message although I still have to keep clicking continue during the instillation process of wubi due to drives not being found/understood by it.

After following the instructions for stage 1 of post 8 completely I end up at a page that says "[COLOR=Red]Booting a command list[/COLOR]" with the rest of the screen in black with a flashing cursor. After a few tries of this I noticed that my number lock flashed on my keyboard a few times (tried pressing a few things such as Esc and Ctrl+x but had no noticeable affect) and then went completely off and would not let me turn it back on manually by pressing the Num Lock key on my keyboard. 

The ending of the example of what you put it should look like is   slightly different with mine it mentions a keyboard... I could write it   all down by hand and type it up for you if it is relevant? <- could be a keyboard related problem?

Note - first attempts I tried with the 64 bit version in the same folder as the wubi.exe as I have a 64 bit vista version... after that didn't work I downloaded the 32 bit version of the file you pointed me to and moved the 64 bit out of the folder and put the 32 bit version in the same folder as the wubi.exe.

Before each attempt of method 1 I reinstalled wubi as admin which was allot quicker to do since downloading the file you pointed me to (thanks for that :D).

Any suggestions? 

I would just do a dual boot system but my backups of windows op and ms office are at home and I am currently at uni and will not risk being without a computer while studying. (would get it mailed to me but after such things as phone chargers being lost in the mailing service were I live I will not risk it.)

---

### Post by bcbc on 2012-03-15
I found this: [http://erl1.wordpress.com/2012/02/28/ubuntu-11-10-on-xps-630i-with-logitech-dinovo-keyboard/](http://erl1.wordpress.com/2012/02/28/ubuntu-11-10-on-xps-630i-with-logitech-dinovo-keyboard/)

Does that help?

Alternatively you could try 11.10 in a VM.

---

### Post by wavebreak on 2012-03-15
Thanks for your reply bcbc

I did stumble across that link myself however it is talking about ubuntu not wubi so do not know how to apply the first bit and my keyboard is the standard keyboard that came with the computer : Dell L2ou not a Logitech so could not find the files that person was talking about. 

vm = virtual machine? 
I just tried mounting the image file that you linked me to in post 4 using Virtual CloneDrive (the sheep one) the only difference through out the entire process was that it gave an extra menu before uninstalling the previous instillation entitled Ubuntu menu that gave 3 options:

Demo and full instillation
Installing inside windows (this is the option I went for as it sounds like wubi).
Learn more

They all came with descriptions as well.

Not sure if that is even related it may just be a wubi update or a result of myself trying to reinstall wubi so many times. I can take a screen shot of it if you would like?

Thanks again for all your help hopefully we will get there in the end but its not the end of the world if I can't use ubuntu would just like to try it out. I want to learn more about computers and how they work and was told ubuntu is a good op to have for fiddling about/learning.

---

### Post by bcbc on 2012-03-15
The link mentioned the keyboard specifically, but it wasn't clear which bits were keyboard related, and which weren't.

Wubi == Ubuntu. Apart from the bit than runs on windows (wubi) it boots Ubuntu natively on your machine (just using a virtual disk). So if there is a hardware incompatibility it will affect both normal and wubi installs. So the noacpi and noapic are not going to be keyboard related, or the nomodeset. I'm not sure about the mem= one.

When you open the ISO with virtual clonedrive it makes it look like you have it in a CDROM drive as a CD. This then gives you the --cdmenu which includes a cd boot helper (3rd option) and the option to simply reboot so you can boot the computer from the CD. Obviously this won't work since when you reboot the virtual CD drive will no longer exist.

By VM I meant, install Ubuntu with VMWare or VirtualBox. I've got a couple of virtual installs and they work well with the benefit that a) you can use both OSes at the same time and b) you don't have to worry about hardware compatibility.
Downside is it's slower and the graphics isn't as good.

---

### Post by wavebreak on 2012-03-15
Thank you so much got the vm working :D shame about wubi in this instance but doing it through a vm is the next best thing.

Learned quite a bit through this process but still have lots to learn thanks you once again for the help.

---

### Post by wavebreak on 2012-03-15
Quick questions:

How does doing ubuntu via vm affect secruity of windows I understand ubuntu is quite safe (still going to look into getting security solutions for it) but could some one who hacked there way into my ubuntu get into windows easily or would they have to go through the firewalls setup on my widows op aswell?

This is a inception sort of question could I have a vm within a vm within a vm? lol presuming ram is limitless.

---

### Post by bcbc on 2012-03-15
I suppose a vm-aware virus (do any of these exist?) might be able to attack the host OS but it seems unlikely.

Most viruses go through windows anyway - so you'd have to make Ubuntu vulnerable somehow and then get infected by what would be an incredibly rare virus (affects Ubuntu looking for windows host OS).

---

### Post by wavebreak on 2012-03-15
Interesting (Google search) apparently vm aware virus/malware do exist, they detect whether they have infected a vm and if they have they act differently as programmed so they could infect the host os however quite a few vm aware viruses are programed to basically stop on a vm. Also another thing to add is that ubuntu is a different op to windows so the vm command would have to take that into account if it wanted to work. <- I don't think I have much to worry about unless I am specifically targeted by a individual/group after taking the security precautions that I do as well as the security installations. 

Regarding the inception question I asked a vm within a vm it is difficult as a vm does not have the same access to the hardware that is needed to create a vm however some software's/programers seem to have found ways around it as people claim they have done it.

Anyways thanks again for all your help bcbc :D.

---

