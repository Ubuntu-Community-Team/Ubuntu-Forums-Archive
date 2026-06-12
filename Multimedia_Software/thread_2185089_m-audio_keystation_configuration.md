---
title: "m-audio keystation configuration"
date: 2013-10-31
forum: Multimedia Software
---

### Post by fred-lorrain on 2013-10-31
Hello kind forum members,
I am trying to migrate completely to my Ubuntu 13.10 xfce (Voyager fork) for everything I do with my PC. I am having trouble getting my sound system to behave in a stable fashion with my midi keyboard controller (m-audio keystation). If i fire up an application that can use midi, then fire up qjackctl, i can connect using the Alsa tab in some cases and not in others. Then upon quiting my sound doesnt work at all for other applications (like Firefox for example) till i reboot. In other cases i can see that the controller is doing something (piano booster shows activity but no sound) but i cant hear anything. I have read and read but feel no closer to understanding what i'm doing. Is qjackctl the right tool to connect my hardware to software in xfce? It seems that the system sound preferences once showed whether to use jack/alsa as a input driver, but now i dont see it among my choices. I am plugging the USB cable directly to the computer, without the dongle that is necessary with windows and the Avid software that came with the controller. HELP!!
Thanks in advance for any help you can offer!:confused:

---

### Post by fred-lorrain on 2013-11-01
*****Update*****
I have made some progress, I get better results if i first open a program that can interpret midi signals THEN plug in the keyboard THEN use Qjackctl to connect the m-audio to the program within the ALSA tab without connecting anything else in jack. Some volume levels are very low, even with the vol controls i can find cranked up all the way, but at least i'm getting a little closer. I have been watching midi/linux tutorials on youtube, while they are for different distros and some details are different i am learning a bit. I also installed a bunch of programs from the ubuntu studio packages per ([https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)) which organized my menu nicely and included some tools that will help me figure out what to do I'm hoping. If anyone has a firm grip on best practices to use a midi controller with any of the most popular audio production programs, a noob friendly tutorial would be very appreciated by many, I'm sure. Thanks for reading, and please add any tips you can think of!

---

### Post by fred-lorrain on 2013-11-03
For any of you who are following this thread here is where I am. I have got zynaddsubfx working by just starting it, then qjackctl, then connecting zynaddsubfx to system in the audio tab (qjackctl), and the keystudio to zynaddsubfx in the ALSA tab (also qjackctl) I then select an instrument in zynaddsubfx and have SOUND!!. For some reason this setup does NOT work with qsynth, (although i did once see the meters bounce when i hit a key without sound, but can't reproduce that now??) I have tried adding connections to system in both tabs, (audio and alsa) the keystation never shows up in the midi tab, I guess because it is a usb device (?) I have a "midi through" entry in the alsa tab, but I haven't figured out how to get output from there to any of the programs i have tried. I would like to figure out how to connect this keyboard to any of the sound generator programs that are part of the ubuntustudio-audio package, to find the best sounds, and to record the output to Ardour, any of you who have experience with usb keyboards and these programs please share your experiences, there are alot of threads that discuss problems with audio and midi but none that present clear "best practices" to pull all the pieces together. 
In earlier attempts I had tried to use the Timidity driver that came automatically with some package (I forget which) but have since removed it, as I thought I might be uneccesarily complicating my set-up. It did show up in qjackctl but I had trouble getting sound out when i connected to it, and realized that ALSA seems to be working to a degree. Thanks for reading, and have a great day!

---

