---
title: "MythTV and the Plextor ConvertX PX-TV402U"
date: 2009-07-10
forum: Multimedia Software
---

### Post by bakelitedoorbell on 2009-07-10
I was using my ConvertX box with Elgato EyeTV software to watch cable TV on my MacBook.  I recently upgraded to a System76 Serval laptop running 64-bit Ubuntu.  Now I am trying to get this converter box working with MythTV.  Goal is to be able to watch live TV, and also record TV shows to watch later.

Installed MythTV using Synaptic Package Manager.  I followed the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=791842&page=5") to download the driver (sadly no longer supported), compile and install.

Tested the driver using the included "gorecord" app as recommended in the driver's README file.  It captured 60 seconds of a black screen.  I figured it was black because I couldn't tune to a specific channel.

I went through the Myth backend setup, and on section #4 Input connections - there is a button to scan for channels.  I select it and get the message "failed to open the card".

In the Myth frontend program, when I select "Watch TV" the screen blinks and then it goes back to the menu.

I suspect that there is something not working with the driver, that I don't understand.  Any hints on how I can troubleshoot this?

---

### Post by bakelitedoorbell on 2009-07-11
I'm not familiar with the CLI commands to test the driver.  What commands can I type in the terminal to see what is working with this setup?

---

### Post by xmrkite on 2009-11-12
Hello, did you ever get this working with mythtv? I have the same device and would like to get it working with my mythtv setup too.

-Thanks

---

### Post by bakelitedoorbell on 2009-11-23
Unfortunately, no.

I'm thinking about buying another tuner device, but not clear on which one.  There are other USB video capture cards on [this list]("http://www.mythtv.org/wiki/Tuner_Card"), but the Plextor is on the same list and it's not working for me.  So it seems like it would be an expensive gamble to buy one that "might" work.

Of course if I could get the Plextor working it would be awesome, still willing to try if anyone has a suggestion.  Still running Jaunty 64-bit.

---

### Post by xmrkite on 2009-11-23
I'm in the same boat as you. I have the plextor and kinda got hosed buying that since it doesn't work with Ubuntu. I don't want to buy another usb tuner either unless I'm 100% sure it'll work.

I did hear that people have it working with the old fedora core 4, and i've thought of running that in a virtual machine as a slave backend just to get this tuner usable. But I am not sure when i'll have the time to set that all up, and besides, my mythbackend only has 1gb of ram in it which i don't think is enough.

But if you have the chance to try it out, let me know if it works.

---

