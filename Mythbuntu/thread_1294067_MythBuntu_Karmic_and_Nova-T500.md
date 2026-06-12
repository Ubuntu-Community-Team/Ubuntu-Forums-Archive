---
title: "MythBuntu Karmic and Nova-T500"
date: 2009-10-17
forum: Mythbuntu
---

### Post by GuiGuy on 2009-10-17
After installing (clean) I had some issues with the NOVA-T500 dual digital PCI tuner. 

Conventional wisdom says [*turn on the onboard amplifier or you will get very poor signal strength. It is possible that this will cause you to receive no signal at all due to the amplification of signal noise regardless of signal quality.* ]("http://mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI")

> 
sudo gedit /etc/modprobe.d/options
Add: options dvb-usb-dib0700 force_lna_activation=1 


... to turn on the onboard signal amplifier. This didn't work for me initially. With a bit of help form [http://xpmediacenter.com.au](http://xpmediacenter.com.au) the following steps resolved the issue:

[LIST]
[*]If you have "/etc/modprobe.d/options" rename it to "/etc/modprobe.d/options.conf" (without the double quotes, of course); 
[/LIST]
Then, in a terminal
[LIST]
[*]sudo mousepad /etc/modprobe.d/options.conf
[*]Add the line "options dvb-usb-dib0700 force_lna_activation=1"
[*]Save and close mousepad 
[*]sudo modprobe dvb-usb-dib700
[/LIST]

If modprobe doesn't complain the Nova-T500 signal levels should be up again. 

NB: It would seem the move to use the suffix .conf for configuration files is taking hold and will catch some of us out. 

Cheers

---

### Post by SiHa on 2009-10-18
This is with 9.10 beta?

I've got the same card, and I've been putting off upgrading due to the infamous I2C errors that seems to have come back with more recent kernels. How's your card performing?

---

### Post by Steve Goodey on 2009-10-24
Then, in a terminal
sudo mousepad /etc/modprobe.d/options.conf
Add the line "options dvb-usb-dib0700 force_lna_activation=1"
Save and close mousepad
sudo modprobe dvb-usb-dib700

I believe the above line should read:-

sudo modprobe dvb-usb-dib0700

Regards, Steve.

---

### Post by Zeedok on 2009-10-27
> **GuiGuy said:**
> After installing (clean) I had some issues with the NOVA-T500 dual digital PCI tuner. 

Conventional wisdom says [*turn on the onboard amplifier or you will get very poor signal strength. It is possible that this will cause you to receive no signal at all due to the amplification of signal noise regardless of signal quality.* ]("http://mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI")

I think I had this issue with 9.10RC.  All of my channels were reading bit error rates of >65k and some of them could not get a lock (despite reported signal strength of ~99%).

I tried following your instructions (I had seen your posts elsewhere) but I had no success.  I regressed to 9.04, which does not have this problem, for the time being.

---

### Post by idrisdraig on 2009-11-10
As an uber noobie, please can I get some clarification please?

> If you have "/etc/modprobe.d/options" rename it to "/etc/modprobe.d/options.conf" (without the double quotes, of course);How do you find out and how do you change it?

> Then, in a terminal[INDENT]sudo mousepad /etc/modprobe.d/options.conf[/INDENT]Does this open a file that can be edited?

> Add the line "options dvb-usb-dib0700 force_lna_activation=1"Assuming a file is opened to edit, does it matter where within the file this line is added?

> Save and close mousepadIs this just a case of clicking on Save from a menu or do commands need to be typed ... and if so what?

> sudo modprobe dvb-usb-dib700Presumably this is just typed in a tereminal after saving the above file?

> If modprobe doesn't complain ...Where would it complain and what message would you get?

> sudo modprobe dvb-usb-dib700
...
sudo modprobe dvb-usb-dib0700Is it possible to confirm which is correct please?

---

### Post by SiHa on 2009-11-11
OK, a quick linux lesson first:

Linux is Case Sensitive.

Linux has permissions. To do anything that might adversely affect your system (like editing the contents of /etc) you need Superuser access. sudo = Superuser Do (...the following command), you will be prompted for the password, which is the login password for the current user. 
This password is 'remembered' for a while (15 Mins, I think), so after typing it once, you shouldn't be prompted again within this time.

**cd /path/** = change directory to /path/
**ls **= list contents of a directory. 
**ls -l** = list contents and their attributes (-a will also show hidden files)
**cp** = copy
**mv** = move
**rm** = remove. Should be used with caution, especially with the -r switch, which will recursively remove directories and their contents.

> **idrisdraig said:**
> As an uber noobie, please can I get some clarification please?
> If you have "/etc/modprobe.d/options" rename it to "/etc/modprobe.d/options.conf" (without the double quotes, of course); 
How do you find out and how do you change it?
```
cd /etc/modprobe.d
sudo mv options options.conf
```
In a fresh install of 9.10, it is unlikely you will have an 'options', so this command will probably error (file not found). If the file existed, you've just renamed it. If not, it doesn't matter as you will create it in the next step

> [QUOTE]Then, in a terminal
sudo mousepad /etc/modprobe.d/options.conf
Does this open a file that can be edited?
[/QUOTE]
Yes. Mousepad will warn you that you are root (from the sudo) and may do damage. Ignore this, you know what you're doing don't you?;)

> [QUOTE]Add the line "options dvb-usb-dib0700 force_lna_activation=1" 
Assuming a file is opened to edit, does it matter where within the file this line is added?
[/QUOTE]
No, and you should leave the quotes out.

> [QUOTE]Save and close mousepad  

Is this just a case of clicking on Save...?
[/QUOTE]
Yes

> [QUOTE]sudo modprobe dvb-usb-dib700  

Presumably this is just typed in a tereminal after saving the above file?
[/QUOTE]
Yes

> [QUOTE]If modprobe doesn't complain ... 
Where would it complain and what message would you get?
[/QUOTE]
In the terminal window directly below the command. Not sure what error you'd get, but it's usually pretty obvious that an error is an error. If the modprobe is successful, though, you should get no output to the terminal.

> [QUOTE]sudo modprobe dvb-usb-dib700
...
sudo modprobe dvb-usb-dib0700 
Is it possible to confirm which is correct please?[/QUOTE]
The second one (...0700)

---

### Post by idrisdraig on 2009-11-11
Thanks very much SiHa.
I'll give it a go as soon as I can get ANYTHING at all back on the screen. [http://ubuntuforums.org/showthread.php?t=1319582](http://ubuntuforums.org/showthread.php?t=1319582)

---

