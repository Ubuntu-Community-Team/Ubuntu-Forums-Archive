---
title: "How to get effective display brightness magement under Unity/Gnome Shell"
date: 2012-04-07
forum: Multimedia Software
---

### Post by thaelim on 2012-04-07
As many of you will be aware, the transition from Gnome 2 to Gnome 3 brought with it a number of simplifications in the power management configuration applet. Some of these simplifications are fine, but as a laptop user it lacks two things I cannot live without:

[LIST]
[*]Set my preferred brightness level after boot (might be a bug, on my laptop it always defaults to 100% no matter what I do).
[*]Define different brightness settings for battery and AC modes
[/LIST]
So I set about writing a very simple daemon script that would manage these two functions for me. I am posting it here in the hope that it might be useful to some people. In fact, if there were sufficient interest, I would consider developing a Gnome Control Center panel for it as well as proper packaging etc.


To use the script, simply download it and customise your preferences using the ALL_CAPS variables at the start of the script. The variable names are fairly self-explanatory - brightness values are expressed in percentages, and times are in seconds. Then give the script executable permissions and configure it to start using the Startup Applications config panel. Log out and back in and you are done.

---

### Post by dinutu on 2012-06-02
Thank you for the script, can you tell me where to copy it? as i have the same issue.

---

### Post by DGINSD on 2012-06-03
Great idea, wish it worked for me. I hate that basic functionality like brightness control and memory of the last brightness setting has seemingly been removed. Unfortunately for me this script didn't work. 

I've been searching for weeks now for a solution to "100% brightness at startup", I've found quite a few solutions but none yet have worked for me. I'm no computer expert but I think it has something to do with the fglrx proprietary graphics driver taking over and overriding even the simplest of solutions.

Any suggestions?

---

### Post by DGINSD on 2012-06-03
I found my missing piece of info and got your script working correctly. Thank you, thank you, thank you, for this script.

I found the solution here [http://blog.ishans.info/2011/09/25/set-brightness-automatically-at-the-startup-in-linux/]("http://blog.ishans.info/2011/09/25/set-brightness-automatically-at-the-startup-in-linux/") which point to yet another script (not as full featured and useful as yours) for lowering brightness upon startup.

The key I was missing was to add "python " in front of the path to the script in startup applications, now it works like a charm. Why this basic functionality is not included by default with Ubuntu is beyond me, I still have to deal with 100% brightness prior to login, but I'm very happy to have some functionality. 

Just out of curiosity how hard would it be to make a script that took the backlight settings when changed manually and input those values to the pertinent parts of the script

---

### Post by in8sworld on 2012-10-23
> **dinutu said:**
> Thank you for the script, can you tell me where to copy it? as i have the same issue.

You can put the script anywhere you have permissions to put it.  Then make sure you set it executable: ```
chmod 755 /path/to/script
```  Then in the startup applications, call the script by adding ```
python /path/to/script
``` in the command field.  Works great!  Thanks for the great script.

---

### Post by Dink444 on 2013-02-24
Thanks so so much , I am a bit new to all this Unity Dash , had tried all the mods to the rc.local file with no luck.
 
Every reboot I got a very very dim display , I could always bring it up with the brightness keys , but this was a pain every boot.
 
Was a bit weary to add a .py file for the python interface , but having got to my wits end , I thought hey WTF lets give this a go.
 
You have been a saviour , I have done a Dual Boot , Win 7 Pro and Ubuntu 12.04 on my Daughters HP Envy 3277nr , which is ATI / Intel Hybrid video cards and 4 speakers + a Sub Woofer onboard , have had loads of fun with getting that to all work and this forum has been a God send :)
 
This was the last piece to the puzzle , please please make this available to the newbies like me on Ubuntu 12.04 via a ppa or a more readable A to Z description :) 
This is now plain to me what you were getting at but it did take me a bit to understand , unfortunately when you understand like you do it's hard to understand why people like me can't :)
 
All I can say is you are the wizard , 
 
Dave.
 
P.S. Took abit to find as the title is " magement "

---

### Post by DGINSD on 2014-02-16
I know this is a rather old thread but hopefully the OP'er keeps up on their old topics. First off I'd like to say thank you for your script, it's served me very well for a few years now. I just upgraded to 13.10 and it does seem that it no longer works though, due to the regression of gconf being replaced by dconf.  I'm just curious if you happen to have written another script that works in the newest version of Ubuntu, and if so would you be willing to share it?

---

