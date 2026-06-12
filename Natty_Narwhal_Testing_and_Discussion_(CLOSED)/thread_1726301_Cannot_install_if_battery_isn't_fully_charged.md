---
title: "Cannot install if battery isn't fully charged"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by blizzak on 2011-04-10
Hello, You Guys,

Natty Narwhal seems to be unable to get to the loggin page or install properly if the battery pack on a Lenovo Y460 (at least MY Lenovo Y460) is attached, unless it is fully charged. If I take out the battery it will work properly and am able to install Natty normally, though once installed this problem pursues. 

If installed it will hang at the purple screen after selecting nattty from the grub2 menu. From the live cd (if not installed) it will hang at a log screen. Where it hangs is inconsistent though more times than not it will display something about battery pack available.

---

### Post by blizzak on 2011-04-11
Another, unrelated hardware issue. 

After installation (with the battery disconnected) I did a system wide update via apt-get upgrade and on reboot I would be left on the loggin page with neither mouse nor keyboard working. 

Again, think is with the Lenovo IdeaPad Y460.

---

### Post by Lodmot on 2011-04-15
Hi. 
I ran into a similar problem with my laptop, and now it actually wont boot into ubuntu anymore. 

This all happened when I was using ubuntu chatting with someone online. I got a few warnings about the battery life but I didn't do anything about it because I was sidetracked into the convesration with my friend. Then when the battery was dead the whole thing shut off.

So I hooked my laptop into the power supply, and turned it on. After seeing the "ubuntu" screen with the red animated dots, the screen just went to black and the system did nothing else. That's all it will do now. 

So I figured somehow I corrupted my OS, and decided to reinstall it. I put in the cd I burned (which I should mention, worked perfectly before) and tried loading the installer. And guess what? Same thing.  Turned black right after the Ubuntu loading screen with the dots. This same effect was also happening to me when I first tried installing ubuntu 11.04, and I thoughtthe OS wasn't compatible with my laptop, though now I know compatibility obviously wasn't the issue here.

Now I've been hearing people say that their laptops do a similar thing when the terminal output says "Checking battery state" during bootup. Is this related to that? And does this mean that ubuntu will only start working once the battery has gotten a full charge after dying? If so, then this all makes sense.

 It seems strange that an installation cd which I KNOW worked properly doesn't work anymore after my battery died. In addition, my whole OS which was also in a working state on my hard drive wont boot up now after the time my battery died. This issue really needs to get fixed before ubuntu 11.04 is released.

Just for the record, I am using a Toshiba Satellite A660D laptop. Other than this major issue that Im now  trying to solve, Ubuntu 11.04 (beta 2 to be exact) has been working flawlessly. But this situation desparately needs fixing before they release the final version.

---

### Post by Lodmot on 2011-04-15
Update: 
Alright. I did a few tests tonight, and I may have figured out a way to fix the problem with the black screen. But it requires re-installing Ubuntu from scratch again. Also, some of these steps may not be required. I'm not certain what the black screen of death is caused by, so I'm pretty much just reciting everything I did before getting the Ubuntu 11.04 installer to work again. :P

Step 1: If your laptop's battery is still dead, connect it up to the charger and let the battery charge until it is full. Usually a full battery in a laptop will be indicated by a light on the computer itself, but each system is different. On my Toshiba Satellite A660D, my battery indicator is red when it's charging, then turns white when it's full. 

Step 2: Make a USB bootable drive, loaded up with the live CD for Ubuntu 10.04 or something other than version 11.04, then burn a CD of the Ubuntu 11.04 beta 2 live CD image.

Step 3: Boot up the computer using the USB drive (which would be Ubuntu 10.04, just to clarify). Choose to try Ubuntu without installing it from the menu screen.

Step 2: When Ubuntu 10.04 fires up with the desktop, open a terminal and enter this command: "sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1". This will zero-fill the MBR on your laptop's hard drive.

Step 3: Close the terminal window, and open up GPart. Here, you'll want to create a new partition table for the drive. This erases all the information on the drive, and basically starts you out with a fresh slate. Also, you may not have to do this, but I went ahead and formatted the drive with an EXT4 partition while I had GPart still open. 

Step 4: Now we're done working with Ubuntu 10.04/older version, so close GPart and restart your computer from the menu at the top. 

Step 5: If you haven't done so yet, insert the CD you made for Ubuntu 11.04, and choose to boot up from the CD. When you see the purple screen with the little image at the bottom, press a key to bring up the initial menu screen. 

Step 6: Here, press F6 at this menu screen to bring up a sub menu with a few options for the installer. One of these options is "acpi=off". Enable this, and exit out of that sub menu.

Step 7: Now you are prepared to try installing Ubuntu 11.04 again! If it works, you'll know because immediately after the Ubuntu load screen with the red dots, it will switch to the traditional purplish-gradient background, and you'll notice the mouse cursor on the screen. There is no black transition between the Ubuntu loading screen and this purplish screen with the cursor.

Hope this helps a few people out there who might be in my situation! ^_______^

---

