---
title: "Need help switching video cards/drivers"
date: 2006-02-27
forum: Multimedia &amp; Video
---

### Post by josiahgould on 2006-02-27
I currently have a S3 ProSavage8 32M Integrated Video on my computer, it's set up and working fine, but I just obtained a 64M Nvidia GeForce MX440-T AGP video card and I have no idea how to switch from my Savage drivers to the Nvidia drivers.  I have to swap the card out whenever I want to boot into Ubuntu, and it's getting to be a pain, anyone that could help would be greatly appreciated.  I'll try to provide any additional information you need, but I'm still pretty new at Linux so detailed instructions will be needed.

---

### Post by theob88 on 2006-02-28
Wow...I have almost the exact same problem.  I am brand new to Ubuntu and originally installed it with a really old S3 Virge video card.  I recently purchased an nVidia MX 440 card and installed it in my machine, assuming Ubuntu was like Win**** and would automatically detect the new card and ask for drivers :???: .  When I booted, I found this is not the case. I get a bunch of errors regarding X and then the computer just locks.  I already chucked the old S3 card out :( 

I have read the Ubuntu starter's guide and printed off instructions for installing the nVidia drivers.  Since I can't book to X (is that what the main desktop is called?), is there anyway to boot to a prompt or something so I can run all the apt-get commands, etc. and update the necessary files for the new card?  I really need the help.  Thanks guys

- Brian

---

### Post by FSO on 2006-02-28
theob88: run sudo dpkg-reconfigure xserver-xorg, it could help.

---

### Post by theob88 on 2006-02-28
Thanks for the response.  The only thing I don't understand is where to type this command.  As mentioned, when Ubuntu starts up, it tries to load Xserver but can't load the video driver because it's expecting the old card still.  It gives me a bunch of error messages and then goes back to the black screen that lists all the steps it's taking while it's booting up.  It is locked on this screen with no command prompt so I can't actually enter any commands or anything.  All I can do is restart.  What I need to know is how to start Ubuntu into a non-graphical state so I can run the commands to update the nVidia driver.

Thanks again for any help,
- Brian

---

### Post by BeatBoxRocker on 2006-02-28
Are you sure you can't introduce in console your user name and password after X crashes? If you cant just press control + alt + F2 and it should allow you to access the Console and login. After that use the command that FSO told you sudo dpkg-reconfigure xserver-xorg and reconfigure X.

Saludos!

---

