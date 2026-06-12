---
title: "LIRC works for everything but MythTV"
date: 2010-01-23
forum: Mythbuntu
---

### Post by Matkyne on 2010-01-23
I am a long time Linux user and have been using MythTV since 2003. I am having the strangest problem. I have 2 nearly identical machines, (only differences are HDD Size, and One puts out 720P and the other one puts out 1080P). The have been working Myth Boxes for 2 years without any complaints. I recently upgraded and switched from Knoppmyth to Mythbuntu; because Knoppmyth turned into LinHES, based on Arch and I prefer Debian. 

Anyhow, the 720p box was upgraded with only minor problems, but it is working 100% now. 

The 1080p box is another story. I use a home-brew serial receiver (made myself) and it has worked flawlessly for years. During setup I picked an RCA generic remote, and after setup was complete, I:

sudo dpkg-reconfigure lirc 

and selected the correct settings for Home-Brew serial report receiver. I the copied my known good lircd.conf to /etc/lirc/ and copied my known good lircrc to /home/USER/.lircrc & /home/USER/.mythtv/lircrc .

I kill restart lirc, and start the frontend, and it does not respond to the remote. 

So I exit out of the front end , Kill lirc, run mode2, and the terminal lights up whenever a button is presses. So I Kknow my hardware is good and that my /etc/lirc/hardware.conf file is good. 

Next I re-check my lircd.conf and lircrc files to make sure they are intact. and they are. 

So next I launch Xine, and aim the remote at the sensor, and it responds like it should. Great. That means that the lircd.conf and lircrc files are working. So I re-launch the front end and, still no response from button presses. I can navigate fine from a keyboard, but the remote does not work  for the front end. 

Now I know that it can work because I have an identical machine, that uses identical hardware and even uses the same remote! What am I doing wrong? It is so weird.

---

### Post by azmyth on 2010-01-23
what happens with

ircat mythtv

then start pressing remote buttons.

Also, I'm sure this is okay but just to be on the safe side check

mythfrontend --version | grep lirc

You should see using_lirc in the list

Lastly, the FE log should say connected to /dev/lircd. Does it say this or give you an error?

You may need to set this to something different in 

Utilities/Setup -> Setup -> General (9th Screen in)

---

### Post by Matkyne on 2010-01-27
I figured it out. I opened up a remote terminal on for each box, the one working and the one that was not. I compared the two, file by file until i found the error. On the machine that the remote did not work on, I forgot to replace the .lircrc file in the ~/mythtv/ directory. The .lircrc file in there was still pointing to the .lircrc/ folder and the lirc config file in there. I replaced the incorrect file with my known working one, and restarted lirc (sudo /etc/init.d/lirc restart) and re-opened the frontend and it worked as it should. I just goes to show, double and triple check things that you "know" that you have done correctly. Thanks for the suggestions though.

---

