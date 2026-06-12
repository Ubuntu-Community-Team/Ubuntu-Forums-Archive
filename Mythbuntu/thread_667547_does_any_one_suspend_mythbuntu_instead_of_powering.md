---
title: "does any one suspend mythbuntu instead of powering it off?"
date: 2008-01-14
forum: Mythbuntu
---

### Post by onesojourner on 2008-01-14
I don't need my media center to run 24-7 so I power it down when I am done. Right now I do that but walking over and pushing the power button on the machine and it goes through the shut down process. I Would prefer to just suspend the machine so it does not have such a long boot up  time. I would like to be able so suspend/unsuspend it with the power button on the mce remote. is that possible? If it is not I would like to change the behaviour so that pressing the power button on the machine will cause it to suspend instead of shutting down. I also need it to auto log in when it resumes. as it is now I have to enter my user name and password.

---

### Post by anand on 2008-01-16
I haven't tried this yet but it might work...

In the directory /etc/acpi are several scripts that get executed when various ACPI events are triggered.

There is a script there called "powerbtn.sh" that I assume is what is called when the power button is pressed.  There is another script called "sleepbtn.sh" which I assume is used if your PC has a "sleep" button.  My laptop does (using one of the FN keys) but my desktop doesn't.

You might try making a backup copy of "powerbtn.sh" and then copying "sleepbtn.sh" over the original "powerbtn.sh" and see what happens.

Like I said, I haven't tried this so try at your own risk :)

---

### Post by Glenhawk on 2008-01-16
I don't think you even have to go that technical. You should be able to go into power management and select what happens when you press the power button (eg, ask me, suspend, shutdown, hibernate).

However I think there have been issues with making sure that mythbackend is running when you resume from a suspend (when you boot your PC it starts up mythbackend but when you resume from suspend it may or may not be running).
On top of that there have been lots of trouble suspending and hibernating with Gutsy where you can get it to suspend ok but on resume all you get is a blank screen (I haven't been able to get a successful resume during my testing)

That said, you CAN get it to power off using the remote. When you exit from Myth you usually get an option to either just exit or exit and shutdown. To get the shutdown to work you have to input a shutdown command in the MythTV General settings and also allow the shutdown command to execute without password (sudo visudo). Try googling shutting down MythTV or something like that. I switch my box on using the power button but can switch it off via the remote.

With respect to automatically logging in you should be able to set that in the ubuntu login window settings.

You should be able to find more information about all this using google but if you get stuck reply to this post again and if I get a moment, I'll point you in the right direction.

PS: another really cool feature is to use ACPI to automatically turn your PC on when it needs to record and then shutdown when it is finished!
[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

---

### Post by onesojourner on 2008-01-17
I have looked through my menus and I don't see any power management tools. what package do I need to install?

---

