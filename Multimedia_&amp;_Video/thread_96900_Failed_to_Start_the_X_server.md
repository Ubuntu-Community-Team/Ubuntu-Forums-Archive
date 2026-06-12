---
title: "Failed to Start the X server"
date: 2005-11-29
forum: Multimedia &amp; Video
---

### Post by hot.box on 2005-11-29
New to Linux (you gotta start sometime, right?)

get the error, "Failed to Start the X server"

told to use 
apt-get remove xserver-xorg
apt-get install xserver-xfree86

but where do i input this?  I don't know any commands

or, something about 'vesa'?  but how do I open it to edit it?  Anyways, if anyone can help, it would be great.  Thanks.

---

### Post by Xian on 2005-11-29
[QUOTE=hot.box]told to use 
apt-get remove xserver-xorg
apt-get install xserver-xfree86[/QUOTE]
That would be a long shot. 

Basically, when the computer boots and fails to start X it will drop you back to a command prompt. Here is your chance to manually configure the hardware that is on your system for use in Linux. It's not complicated at all, and only requires that you know the specs of your box.

At the command prompt enter this:

$ sudo dpkg-reconfigure xserver-xorg

---

### Post by kairu0 on 2005-11-29
[QUOTE=hot.box]New to Linux (you gotta start sometime, right?)
told to use 
apt-get remove xserver-xorg
apt-get install xserver-xfree86
[/QUOTE]

That's like the "reformat your hard drive" of the Linux world; it's very general and too drastic.

You have to reconfigure X and at worst install a video driver.

---

### Post by DUNC4N on 2005-11-30
Hi I'm having the same issue after an update, that my buddy helped me with. During the update, It downloaded 500 plus updates, and after it was done, It said that I needed to restart. After restart, same message. I tried sudo dpkg-reconfigure xserver-xorg about 10 times before I went to bed with no luck. I figure I'm not doing somthing right.

I'm using a HP-4540us laptop with ATI MOBILITY RADEON 4X AGP. Weird that I didn't have any problems during initial install. Help.......And thanks in advance.

---

### Post by qx48 on 2007-02-08
Hello. 
I am currently having the same problem with the X server not being configured. 
I am actually attempting to install Beryl on a fresh install of Ubuntu 6.10 Edgy (via the directions here: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)) , and in attempting to do this I didn't realize i had to configure my graphics card. After I followed the directions following the graphics card configuration, i realized i had to do this. When i finally realized this needed to be done, i installed the ATI graphics card drivers, (though i'm not positive thats what i have; i'll check now) and when i restarted, this error came up. However, when asked if i want to view the error report or something, i say no, and then it comes up with a blank, black screen with a cursor in the upper left hand corner (which i don't think is a command prompt). so basically i need to get to the command prompt where i  can enter the "$ sudo dpkg-reconfigure xserver-xorg" command line. 
thanks.

---

### Post by ddurant on 2007-02-09
My problem turned out to be a bad rewrite cd. I kept burning cd rw's but it just wouldn't take. Then I tried it on a cd write only and success.

Note you can tell if it's your cd by either testing it or hit F6 and change the boot option ( delete "splash quiet --" and put as others have mentioned break=bottom. Then during the install if you get any errors such as hdd my cd drive you will know that the problem lies with your cd.

Good luck

---

### Post by randydueck@mts.net on 2007-03-07
I have the same situation as qx48, but I don't get a black screen...i get a shell and i did the whole "$ sudo dpkg-reconfigure xserver-xorg" thing. After doing the configuration, do you still have to activate x server somehow? I'm running Ubuntu 6.10 AMD64 and an NVIDIA 7600 GT OC. I followed the same instructions to install beryl. I tried uninstalling it via command-line, and restarted, but that didn't work either. I still have no x server.

---

### Post by mcsuperhouse on 2008-06-02
HI there - I am having the same x server errors

I tried entering the code: $ sudo dpkg-reconfigure xserver-xorg (as suggested by Xian)in the comand prompt after the error but nothing happened -what I am I meant do -how am i supposed to fix it



> **Xian said:**
> That would be a long shot. 

Basically, when the computer boots and fails to start X it will drop you back to a command prompt. Here is your chance to manually configure the hardware that is on your system for use in Linux. It's not complicated at all, and only requires that you know the specs of your box.

At the command prompt enter this:

$ sudo dpkg-reconfigure xserver-xorg

I tried this

---

