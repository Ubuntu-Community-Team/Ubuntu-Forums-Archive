---
title: "Boot problem with a new nVidia card"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by Seinfeld on 2007-10-29
Hi..

I have an Intel motherboard with an on board graphics X3100. I have installed Gutsy on this machine and it was working perfectly until I put a new GeForce Asus 7200 GS Video card in the PCI-E.
The machine halts during the boot process and stays forever while reading one of the sequences
"Running boot scripts -- [OK]".. 
This what happens; GRUB loads fine, I can see the Ubuntu logo and the progress line and then, starts reading the boot scripts, screen flickers twice and... halts
The machine boots fine from the live CD with no problem though,. 
I have set the BIOS Video adapter to PCI-E external however, I do not think this is relevant as the same happens if it is set at Auto..

Help... please :confused: ??

---

### Post by dickohead on 2007-10-29
Did you install the graphics card correctly? Most of the newer ones need a second power adapter.

If you're sure you installed the card correctly, try leaving the on-board video turned on at the same time, then when your screen goes black, switch the vga plug from your PCI-E card to your On-Board Video and see if the picture comes back.

---

### Post by tim_wright on 2007-10-29
I had the same problem and it took me about 2 days to figure itout. What you need to do is, when booting press the escape key when GRUB tells you to.

Press "e" once
Go to the second line
Press "e" again
Type in irqpoll
Press "Esc"
Press "b" 

Voila

To make it permentant, when ubuntu loads go to the terminal.
Type:

Sudo gedit /boot/grub/menu/lst

find the line with "nospalsh" in it and add irqpoll to the end, jsut like you did at the start.

Hope this really really quickly typed tutorial helps (I am in a rush to go out and I just seen your problem :))

Tim

---

### Post by Seinfeld on 2007-10-29
Sorry guys.. Both solutions did not work.. I have tried everything, yet I installed all nVidia drivers form the live CD.. it took me at least 3 hours trying and then uhh :???:.. I had to reinstall the root partition again with the card installed. Now works perfect after asking me to reinstall the new nVidia glx drivers,
I know it is a trivial solution but, trust me, it was not working at all.

Thanks anyways for trying to help me...But I wonder what was wrong, should it be just plug and play ??

---

### Post by mrblondeisback on 2007-10-29
I'm having the exact same problem, I got a FX5500 and now my computer won't boot up.  Big bump for finding a solution.  I'll try the solutions posted here and see if that works.  I really do hope we figure this one out, I'd hate to have bought a video card I can't use, or God Forbid, have to go back to windows.

---

### Post by Seinfeld on 2007-10-29
mrblondeisback.. Windows??? :( what ???.. Ohh dear.. do not even think about it.. Right word, God forbids..
Now please install your card in your machine and then go ahead and format and re-install the root partition ONLY. Your settings will all  be conserved as long as your /home is intact. So DO NOT format your home partition.

This is a the only solution for now, so go ahead, I did it and it worked fine, till we find something smarter or the bug is fixed....

Let me know..

Thanks

---

### Post by mrblondeisback on 2007-10-30
hmmm.  but when I installed Ubuntu, my video card was already in place, shouldn't it have got it then?  Well, I'll give it a shot.  I have the alt cd, how exactly do I go about just installing the root partition?

---

### Post by Seinfeld on 2007-10-30
Hi.. Thanks for the question.. yes.. Give it a shot. now, just make sure your card is installed properly. Make sure your DVI connector is connected and no VGA to the display. 
From the BIOS make sure you disable the on board video, just go the main video adapter and make it "external PCI-E". Again. make sure that the on board is disabled to avoid any conflict.
Insert the live CD, reboot again and begin the process normally till  you hit the partitioner phase, 
Go "manual". Then highlight the root partition and edit the partition to /. Similarly  edit the home to /home. 
The software will not install without formatting the root so, ONLY check the box of the root partition for formatting and NOT the /home. Proceed till the end of installation and eject the CD. 
Probably, you will be asked to install the new nVidia drivers so please do so...the machine will ask you to reboot again after the drivers' installation.. Reboot, and then you should be fine..

Let me know . Good luck.

---

### Post by mrblondeisback on 2007-10-31
Well mine's a PCI not express but I set it up in the bios before.  I'm using the Alt cd for install, and when I got to the partitioner, all I had was a big partition and the swap partition.  I know that's probably not really what I have but that's all I'm seeing.  Do I have to get the live cd?  What's the deal here?

---

### Post by Seinfeld on 2007-10-31
OK..
You have to figure out where is your root partition (marked (/)). Is there anything clear on that one big partition indicating where is the home and the root sections ?? Is there any other OS on your machine ?? 

Well, ok, just after the reboot when the computer halts and the problem appears, go to the prompt by pressing ctrl+alt+F1. There you will be on the command line.  You can make sure from there that the nVidia drivers are all installed or you can install them by 

```
sudo apt-get install nvidia-
``` 

press tab to get all the files and pick up the driver and install it or just install them all

logout or reboot and see. If the problem persists
then we will probably format and reinstall the root

but before , show me what you have on the fstab file.. 

type 

```
nano /etc/fstab
```

but please prepare the live CD we will use it after

thanks

---

### Post by mrblondeisback on 2007-11-01
Tried installing the nvidia drivers before installing the card no difference.  Also, when it locks up, I cannot get to the command prompt, ctrl alt F1 does nothing, the thing's frozen.  My computer is in my trunk right now but when I get it back up I'll give you the fstab.  I'll also burn the live cd.  thanks so much for all your help so far.

---

### Post by mrblondeisback on 2007-11-01
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c638db1b-36c3-4ab3-913e-4e91a7261513 /               ext3    defaults,erro$
# /dev/sda5
UUID=332ca498-beb5-4c89-acf6-e861e2605fd3 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       

I don't see anything in there about the vid card maybe that's the problem?

---

### Post by Seinfeld on 2007-11-03
No this is not the problem.

You only have one partition sda1 and a swap sda5
well.. I am not sure.. Please try reinstalling the root ONLY with the card installed as I recommended in my last reply ?? Well my friend, give it a shot, as I told you your /home will be preserved as long you do not format it.. Sorry but if I were you I'd just go that way. I did the same myself.

Let me know..

Thanks

---

### Post by Seinfeld on 2007-11-03
No this is not the problem.

You only have one partition sda1 and a swap sda5
well.. I am not sure.. Please try reinstalling the root ONLY with the card installed as I recommended in my last reply ?? Well my friend, give it a shot, as I told you your /home will be preserved as long you do not format it.. Sorry but if I were you I'd just go that way. I did the same myself.

Let me know what you get..

Thanks

---

### Post by mrblondeisback on 2007-11-03
I got it fixed.  Apparently the problem was my integrated video wasn't shutting off.  [here's]("http://www.albertomilone.com/nvidia_intel_integrated.txt") a link to the way I fixed it.

---

### Post by Seinfeld on 2007-11-04
That's great my friend. Congrats..=D>

---

