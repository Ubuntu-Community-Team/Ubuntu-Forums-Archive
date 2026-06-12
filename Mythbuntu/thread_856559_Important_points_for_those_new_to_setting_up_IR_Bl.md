---
title: "Important points for those new to setting up IR Blaster MCEUSB"
date: 2008-07-11
forum: Mythbuntu
---

### Post by Tim L on 2008-07-11
After many many hours I have found a few points that for people new to Linux and Mythbuntu are very hard to understand. This relates specifically to using an MCE remote with the IR Blaster connected through the end jack plug on the USB. These comments relate to Mythbuntu 8.04.

First find the instructions for setting up the IR Blaster and the Channel Change Script. All the instructions have to be done in the Terminal.  [https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer)


1.Use the Alternative Channel Change Script
2.The first thing you are told to enter in the Terminal is “ $ gedit change-channel-lirc.sh”. First you do not enter the dollar sign, it indicates that you are using the terminal. Second gedit which is a simple text editor, is not installed with the basic installation so this must be installed first. There are several ways to do this - the easiest is to type just “gedit” in the terminal and press the enter key and you will get instructions to install gedit. Third unless you put the word “sudo” before gedit you will not be able to save the changes. So once you have installed gedit enter  “sudo gedit change-channel-lirc.sh”.
3.In the text it says “Modify the 2nd line to match the name of your remote per /etc/lirc/lircd.conf”. Be very careful, logic would suggest that the word remote means the name of the remote controller you are tying to setup, in my case a MCEUSB remote and so the modified script should be “REMOTE_NAME=MCEUSB” but that is not correct. REMOTE in this case means the box that is remote from the computer that you are working on that you are trying to control. In my case it is SKY satellite box, therefore in my case it should be “REMOTE_NAME=sky”.
4.At the end of the instructions it says “When configuring your tuner in mythtv-setup, be sure to set the external channel change script to change-channel-lirc.sh”. To do this you need to get to the mythtv configuration and “4. Input connections”, and select the input device you have previously set up, in my case the satellite receiver is connected to the composite plug on the TV tuner. Then find the “External channel change command:” field and enter “/usr/local/bin/change-channel-lirc.sh”.
5.On that same page of the mythtv configuration two fields down it says “Starting channel:” when you move to the field using the up down keys additional instructions are displayed saying “Starting LiveTV channel. This is updated on every successful channel change.” What you are not told is that although logic would suggest that you type the starting channel into that field you cannot actually type anything in the box. To get a starting channel number in this field you must press the left or right arrow keys but before that you must set up the channels in the Channel Editor. If you do not do this correctly when you try to come out of the configuration you will get a message saying that the start channel has not been set correctly. If you get this message the IR Blaster will not work. This one thing took hours to get to work.

Mythbuntu is very good, but for new people it is very hard if you want to do anything other than use the basic setup as it comes out of the box. Many of the instructions are written for experienced Linux users often in a sort of short hand and new people just do not know what to do. And on the web there is so much contradictory information. Someone, and I am happy to help, should write some instruction in a clear way so that anyone can actually get it to work. Alternatively make the whole process automated so that new people to not have to try and find simple things like the terminal. But I must also say I have learnt such a lot about Linux through the process.

I would like to thank those who have helped with advice.

---

### Post by tgm4883 on 2008-07-12
You may be the first person i've seen having these problems.

The whole process cannot be automated without making everyone have the same hardware.  If you truly need a simple setup I suggest purchasing a preconfigured system from a Mythbuntu vendor.

---

