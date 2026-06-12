---
title: "Wireless &amp; Keyboard problems"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by jenna7033 on 2009-09-28
Hi everyone, 
So I really have two problems and I'm hoping someone out there knows an easy fix for both of them because they are driving me insane!

About a month ago I reformatted my dell inspiron 1520 laptop and installed Ubuntu 9.04.  Everything worked great, except two things:  

1.  Every time someone calls into or from our house, I lose my wireless internet connection.  We have Verizon FIOS, so it's not a dial up or dsl.  The only work around I've found so far is to restart the computer.  If I try to simply click on the wireless option to reconnect, it doesn't work.  

2.  I want to disable my touchpad because every time I type a few words or sentences, I must be bumping the touchpad and it sends my cursor to a different part of the page and/or erases whole paragraphs, sentences, etc.  The only thing is that I have watched myself type and I swear I am NOT hitting the touchpad!  

Anyone have any ideas?  Thanks!

---

### Post by Iowan on 2009-09-28
The touchpad on my laptop can be, well... touchy. On occasion, I've been hovering over it and had it select something (or move cursor). There is a sensitivity control, but if I turn it down, then I need to hammer on the pad to "click". 
Have you tried adjusting sensitivity?

---

### Post by t0mppa on 2009-09-28
> **jenna7033 said:**
> 2.  I want to disable my touchpad because every time I type a few words or sentences, I must be bumping the touchpad and it sends my cursor to a different part of the page and/or erases whole paragraphs, sentences, etc.  The only thing is that I have watched myself type and I swear I am NOT hitting the touchpad!

Know what you mean, it drove me nuts at first as well. But there's a brilliant solution for that and that's called *syndaemon*. In all simplicity, it disables the touchpad for *n* seconds (personally I prefer 3, but you could find some other number more to your liking) after each key press.

If you want to test it, just open up a terminal and run **syndaemon -i <number_of_seconds> -d**. And if you like it, you can automatize its use by creating a shell script. Personally I put it to *~/scripts/touchpad-fix.sh*, but again you can pick another location as well, that's not important. Contents of said file would be (feel free to replace 3 with any other number): ```
#! /bin/bash
syndaemon -i 3 -d
 

```

After that you just need to open System / Preferences / Startup Applications and choose *Add*, then give it a name and comment describing it, so you won't later forget why it's there and finally choose *Browse...* and point it to the script file you made and click *Add*.

EDIT: Ironically enough, you posted on the networking forum and got two keyboard answers, but I'm not familiar with the FIOS and the behavior you described sounds (to me) like something you should take up with Verizon. But instead of restarting whole computer, you could try running **sudo /etc/init.d/networking restart** from a terminal the next time and see if that helps.

---

### Post by duanedesign on 2009-09-28
Under System > Preferences > Mouse you can turn of the 'Enable Mouse Clicks' option.

If that is unacceptable their is a script that turns clicking off while you type.

Just add the following command to System > Preferences > Startup Applications

Click the 'Add' button.
Name : touchpad syndaemon
Command :  syndaemon -i 4 -d -t -K
Comment : Disables touchpad while typing

When finished Click 'Add' and exit the 'Startup Applications' menu. 
(The number 4 in the command is the number of seconds clicking is suspended on the touchpad after you are done typing. you mat find a number that works better for you.)

Now you need to enable SHMConfig
Open a Terminal (Applications > Accesories > Terminal) and issue the following command.

for Ubuntu:
gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi

place the following text in that document and save it.

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>
</deviceinfo>


Reboot, and SHMConfig should be enabled. With SHMConfig enabled you can also install Touchpad configuration tools like 'gsynaptics'

---

