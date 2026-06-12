---
title: "[SOLVED] N00B going from ATI to Nvidia...correct way?"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by b3y0nd on 2007-08-01
Not having any luck with my ati card so i want to install a nvidia (TI4200), what is the best way to go about that?

I actually just tries switching, but of course linux didnt like that much. I downloaded the driver to a local folder, just need to know how to properly uninstall ati driver and reinstall the nvidia smoothly.

thanks again all

---

### Post by b3y0nd on 2007-08-02
In case it may help someone in simular situation I will post what I did to solve my problem. I had a ATI radeon 9600 pro graphics card and  the default ATI drivers installed and upon upgrading to the newest driver games quit working.

ATI sucks, 9 hours of hell over a driver. I was stuck with ATI drivers installed and I wanted to install a Nvidia TI4200 desktop card because there is better support & functionality with Nvidia.

 Of course I could not just switch cards like I could do in Windows (point for windows). I wasnt sure how to install the nvidia card/drivers properly so I posted earlier asking for help. Impatient as I am I couldnt wait. I found this guide: [HERE]("http://albertomilone.com/guides.html")


I downloaded the following script to automate the downloading & setup of the correct Nvidia drivers: [HERE]("http://albertomilone.com/nvidia_scripts1.html")

Download the script to a famliar folder and open up the first link (guide). Follow the instructions to ensure you have the correct library's/dependencies before you run the script or go any further. Before you start the installation process you will need to uninstall the ATI drivers. I found an ATI folder in " /etc/ati" with a uninstall script.

 Run it in terminal. Do NOT restart Xserver yet.

I used "Method 2" in the guide to fix my problem, your needs may be different. read.


Follow the instruction in the guide to update sources & libraries. Step 4 of this  guide is for backing up your xorg file. Do this  and  then complete step 5 

~STOP~

Now run script, should be self expainitory from here. After its complete restart your computer. Your Nvidia card should now be working.

"" I really dont know what the hell im doing WARNING""

This worked for me, by accident or some show of mercy from the tux gods, i dunno...but it worked. My reasoning was that I had to force the old driver to uninstall without reseting xserver, so I could then install the correct driver enabling me to simply shut down my computer and swap adapters. Im using Ubuntu Ultimate (fiesty), but by following the guides at the above link it may work on others. The ATI card I was using was Radeon 9600 Pro, I swapped it out for an Nvidia TI4200.

Some will likely shake their heads at the barbaric nature of my procedure, but not "knowing" how to get around in linux very well I had to try something...and it happened to work. Hope this helps someone. 

B3y0nd

---

