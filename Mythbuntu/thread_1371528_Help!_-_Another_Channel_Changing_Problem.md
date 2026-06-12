---
title: "Help! - Another Channel Changing Problem"
date: 2010-01-03
forum: Mythbuntu
---

### Post by tracyandskye on 2010-01-03
I have a new install of 9.10 with a PVR-150 capture card, MCE v2 remote & blaster, and a Pioneer digital cable box. 

When setting up I chose the MCE remote & blaster with the Pioneer external changer & was very excited, assuming that what I needed was already there & I wouldn't end up in ubuntu-terminal script hell, but alas, I was mistaken again.  The OSD indicates that the channel is changing but the blaster is not changing the cable box.  I did find a thread about a bug that cause files to point to the wrong place or something here:
[http://http://ubuntuforums.org/showthread.php?p=8464899]("http://http://ubuntuforums.org/showthread.php?p=8464899")

Indeed, my system had the problem of the two files pointing to the same place, & patching the file seemed to have fixed it, except that it didn't result in channels changing.  I currently have nothing in the external channel change command in the backend input setup.  I tried many variations of chan_change.sh, channel-change.pl, etc.  None have worked.  I have also seen references to the location of the channel changer files, but I don't see the files there.

It would seem that the Mythbuntu software had what I needed in it and, assuming I chose properly with the "MCE v.2 remote/blaster & Pioneer stb external channel changer" options during setup, that all that is left to do is reference the script in the external channel changer dialog so that it uses it.  That seems too easy though.  I mean, if the setup let me choose my components and created the proper script, why didn't it also insert the proper value in the back end external channel changer window for me, or why isn't it somewhere obvious in the wiki?

Is there a simple string I can enter in that window that will make this thing work?

Thx-

---

### Post by Chewiesw on 2010-01-04
Hi 

I had a similar problem. This is what I did




Channel Setup
For each channel make sure to fill in the following when setting them up in the backend setup -> Edit Channels ( I use Arena channel as the example).

Page 1
Channel Name ARENA, Channel Number 105, Callsign ARENA.
Page 3
Frequency or channel 105 - this is the number that myth will send to lirc to change the box with, so make sure it's correct (ie. the actual channel number on your box).  

Make sure Frequency/Channel is set on page 3. This is the number that myth sends to LIRC, LIRC then sends it via the transmitter to you STB.

Try this for a couple of channels if this resolves your problem you can edit the remaining channels (freqid)in mythweb it will be much quicker and easier.

---

### Post by tracyandskye on 2010-01-04
Thanks.  I'm in the US and I used Schedules Direct.  When I look at the channel edit pages they look just like you describe so I don't think that's the problem.

---

### Post by tracyandskye on 2010-01-04
Since it asked me during install for the remote & set top box, am I wrong in thinking the script is there and I just need to point to it in the external channel change window?

So where is it?  I've seen "/usr/local/bin/change_chan.sh" referenced but there's nothing there.  I looked in the wiki and there is even a section for IR blasting in the wiki 

[http://www.mythtv.org/wiki/MCE_Remote#IR_Blasting]("http://www.mythtv.org/wiki/MCE_Remote#IR_Blasting")

but it's for older versions of Mythbuntu and I don't want to make things worse.  Should I be following those instructions?

---

### Post by Chewiesw on 2010-01-05
I understand your frustration. I battled with getting my transmitter/blaster to work for weeks. You can follow some of the advice in the link you posted with a few tweaks.  I not sure if you have tried any of this yet. OR I might be telling you how to suck eggs.

The first thing to determine is the name of your remote. Having a quick look at my 9.10 setup the remote name for the Pioneer STB should be TWC_UR4-P360.

To check this is true for your setup.

gedit /etc/lirc/hardware.conf

Look under  

#Chosen IR Transmitter

 For TRANSMITTER_LIRCD_CONF="pioneer/general.conf"

 Then confirm your lircd.conf

gedit etc/lirc/lircd.conf


look for something like 

include "/usr/share/lirc/extras/transmitters/dish/general.conf" (this is on my setup your might say /pioneer/general.conf)


This should tell you what config file your transmitter is using.

Finally we are going to confirm the remote name from the config file we determined above 

gedit /usr/share/lirc/extras/transmitters/pioneer/general.conf

you should see something like

begin Remote

name TWC_UR4-P360

We now have the remote name and you can start at step 4 on the link.


irsend LIST TWC_UR4-P360 ""

See if you get any  output

If you do then try (step 5)
 
irsend SEND_ONCE TWC_UR4-P360 button (buttton=channel number)

if this works you are on your way..

---

### Post by tracyandskye on 2010-01-05
Thank you so much!  The files all checked out and the channel changed so I'm just missing the script?  I'm such a noob that I'm not sure if I'm entering in the script language in the terminal window and that makes the script for me, or I'm actually creating a file & saving it somewhere?

From step 5 in the wiki, this is what I came up with;

#!/bin/sh
 REMOTE_NAME="TWC_UR4-P360"
 irsend SET_TRANSMITTERS 1
 for digit in $(echo $1 | sed -e 's/./& /g'); do
         irsend SEND_ONCE $TWC_UR4-P360 $digit
         sleep 0.4  
 done
 irsend SEND_ONCE $"TWC_UR4-P360" Enter
 exit 0

Does that look right?  Now, what do I do with it?  I tried just entering it into the terminal window but it didn't work.

---

### Post by Chewiesw on 2010-01-06
No problem, I am also new to this game.  You will need to create and save the script.  Unfortunately the script you have created in your last post is wrong.  Try the one below

```
#!/bin/sh
 REMOTE_NAME=TWC_UR4-P360
 irsend SET_TRANSMITTERS 1
 for digit in $(echo $1 | sed -e 's/./& /g'); do
         irsend SEND_ONCE $REMOTE_NAME $digit
         sleep 0.4  # note, you may have to tweak the interdigit delay up a bit, depending on your STB model
 done
 irsend SEND_ONCE $REMOTE_NAME Enter
 exit 0
```

What you need to do is open up your text editor (gedit) and copy and paste the script above.  You can save it to any location you want (just remember where).  I initially saved it to my Desktop. 

You call also it anything you want, but it must end as a .sh  (dot sh) eg changescript.sh

Once you have saved the file you must make it executable, to do this  open up your terminal and change the directory to the directory  that you saved the script to

 (in my case  cd /home/pvrbox/Desktop )to and then use this command

chmod +x changescript.sh

now  hold your breath  – test the script
still in the same directory try :  channelscript.sh  404 (any channel number ..in my case 404)

if this changes the channel you are now cooking on gas and the only thing left to do is add the script to the external channel change command in the backend setup. (again in my case /home/pvrbox/Desktop/changescript.sh)
good luck !!

---

### Post by tracyandskye on 2010-01-06
That's what I figured.  I figured out how the script thing worked but still had no success.

So here is where I'm at: The script works from the command line, except that it adds the number 9 to to any one or two digit inputs, so 5 becomes 59.  I removed the Enter command from the end of the script because my remote doesn't need that I think, and the channel changing works without the extra 9, but I get an irsend error that there aren't enough arguments (I think - not enough something anyway).

I saved the file to the /usr/local/bin directory since that's what I see everywhere and I don't want to have to try and remember the arcane spot I chose to locate it later.  I enter that full path (/usr/local/bin/channel_change.sh)in the external channel changer command box in the back end & when I go to LiveTV on the front end, it says to please wait & then just returns to the menu.  I tried leaving the path out & just having the file name but it's the same.  If I teake all the text out of that box, live TV works (just can't change channels).

A couple more questions:  Do I have to run the mythfilldatabase thing every time I try something with this?  When I get this working, will the channel up & channel down commands work?

---

### Post by tracyandskye on 2010-01-06
Got it working!  I had the external tuner preset channel to 4 and that was keeping LiveTV from working.  I removed the Enter command from the end of the script again & it changes channels correctly.

I did notice that channel up/channel down don't work. I suppose I need another command in that script for that, but I'll deal later.  For now I'm just happy to get back to my life!

Chewiesw, THANK YOU!  Really, could not have done it without that help...

---

### Post by tracyandskye on 2010-08-15
Reviving this thread.  I'm setting up a new installation & I have this problem again:

> So here is where I'm at: The script works from the command line, except that it adds the number 9 to to any one or two digit inputs, so 5 becomes 59. I removed the Enter command from the end of the script because my remote doesn't need that I think, and the channel changing works without the extra 9, but I get an irsend error that there aren't enough arguments.

Last time I wrote this:

> Got it working! I had the external tuner preset channel to 4 and that was keeping LiveTV from working. I removed the Enter command from the end of the script again & it changes channels correctly.

but there is no number in the channel preset this time & when I remove "Enter" from the end of the script I get the "Not Enough Arguments" error in the terminal.

---

