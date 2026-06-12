---
title: "Help with Copy full dvd disk image"
date: 2009-04-18
forum: Multimedia Software
---

### Post by rreyes1316 on 2009-04-18
Hello again. As mentioned in another post I am a week old noob. More history regarding my dvd delema at 

[http://ubuntuforums.org/showthread.php?p=7086926#post7086926](http://ubuntuforums.org/showthread.php?p=7086926#post7086926)

I have an extensive dvd collection mostly purchased from Costco and in order to preserve the disk from my 12 year olds dirty careless hands I have used DVD Shrink and HDDVD decryptor. Well, they ten to wine if I dont have the movie backed up with the menus. They hate it when the movie starts immediately--blah blah blah.

Anyhow, how can I create and iso or exact image to fit onto a standard dvd? I am not sure which program to use? I have installed thoggen and acid rip. 

Also, and mentioned in the above post, when I watch a move it start fine, starts to lag and hesitate during the previews, and jerks durring the main menu screen. Once I get to it, I can click on play and it starts just fine.

Thanks

---

### Post by cariboo on 2009-04-18
Have you tried K9copy? It is available in the repositories. You can use Add/Remove Programs or Synaptic Package Manager to install it. Another way I have had success with is to copy the VIDEO_TS directory to my hard drive, and using k3b to create a working dvd.

Jim

---

### Post by robertc36 on 2009-04-18
K9 works in the same way as dvd shrink. Works very well for me backing uo my own discs of course  *cough*:D

---

### Post by rreyes1316 on 2009-04-18
DOH!!! Had no idea such a program existed in the repository.

Thanks

---

### Post by rreyes1316 on 2009-04-19
I am unable to use K9. After I go through the selection menus and click Finnish I get a windo that reads "Insufficient disk space on /tmp/kde-computer/k9copy/4,400 mb expected."  I should have plenty of room on my hard drive. I have a WD Raptor 150. The partitions on that drive are 40gb for windos and the second partition is dedicated to ubuntu.

Anyone?

---

### Post by JauntyJack on 2010-01-02
I am getting the same error message. I am using a laptop that I can't install Ubuntu on permanently (borrowed), and using a USB key created with the Ubuntu USB Startup Disk Creator. I have a large enough external drive hooked up (160 GB) and tell K9Copy to write an ISO to a folder on that. But I get this message:>  Insufficient disk space on /tmp/kde-ubuntu/k9copy/ 4,400 mb expected.   Is this tmp file on my USB key? I would think so, given that's where my OS is. Trouble is, the USB Startup Disk Creator won't let me allot more than 4Gb as space for non-persistent data (even though my USB key is 16Gb, should have plenty more room on there).  My assumption of what the problem is may be all wrong, though. Any ideas or tips?

---

### Post by SuperSonic4 on 2010-01-02
It would be easier to shift the directory for /tmp to ~ in Settings ---> Paths (the top one)

---

### Post by JauntyJack on 2010-01-02
> **SuperSonic4 said:**
> It would be easier to shift the directory for /tmp to ~ in Settings ---> Paths (the top one)

Thanks. Found that under > K9Copy/Settings/Configure K9Copy/Paths/DVDBut before I do that, where does "~" point to? Is that Home folder? Several of the other paths are marked "/home/ubuntu". Should I select the same from the drop-down menus? Or enter the "~"? Or is that not a reference to Home folder?

---

### Post by SuperSonic4 on 2010-01-02
~ is shorthand for /home/user

Not sure if k9copy recognises the former, but you can use the latter (with your username - not user) or use the icon to select a folder

---

