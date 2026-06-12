---
title: "Newbie - Installation Problem"
date: 2008-12-16
forum: Mythbuntu
---

### Post by mr-vain on 2008-12-16
I am running the installation of 8.10 from the CD and when running the mythtv setup I get a message about shutting down the backend then the next message is about running mthyfilldatabase.  I do not get any of the installation setup screens as shown in the guides.

I am trying to perform the install without a caputure card, is this the problem?

Please help. Thnaks

---

### Post by uMuppet on 2008-12-16
Do you mean you are only running a live CD session?  

You will still be able to access the backend without a video card.

---

### Post by mr-vain on 2008-12-17
I ran the Live CD and clicked on the install icon from the desktop and ran through the installation steps until step 15 of 15 where I clicked on the "Launch MythTV setup" button.

At this point instead of getting the setup screens I get nothing.

If I then click on finish and then open a terminal window and run the command mythtv-setup all I get is a message asking to shut down the backend and the next message I see is asking to run mythfilldatabase but still no setup screens.

Hope this is a little clearer.

---

### Post by EasyRiderOnTheStorm on 2008-12-18
I'm not sure this is the case here, but be advised that mythbackend-setup has a lovely habit of launching a console-based tool like mythfilldatabase in the setup's console (there are always two windows running for the backend setup, the setup GUI and a console window behind it/minimized) and then not bringing said terminal window in the foreground. 

The result is usually that you are staring at a "message box" waiting for setup to finish whatever it just told you it's doing, while the setup is actually waiting for the console-based tool that it just launched to do it's job, which said tool is in turn waiting for your input in the console that you do not see.

Try do an ALT-TAB or otherwise bring up the taskbar/the console running in the background when you get to the critical step, and make sure there is nothing waiting for you input there...

---

