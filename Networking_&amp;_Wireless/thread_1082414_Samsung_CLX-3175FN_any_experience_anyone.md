---
title: "Samsung CLX-3175FN: any experience anyone?"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by DiabolusItalicus on 2009-02-27
Hi guys,

does anyone have any experience to report in installing and using a CLX-3175FN over a network?
I find it appealing and I'm actually considering buying one to hook up to my home network for our three PCs (XP, Vista and my beloved Ubuntu 8.10), but would like to hear from other users before wasting my money.

If not the CLX-3175, what other network color MFPs below EUR 500 would you suggest?

Thanks and regards!

---

### Post by KEYofR on 2009-04-27
I don't remember every detail required but I do have the printer working on an opensuse 10.2 box and just now on Jaunty as well. Before Jaunty, all I did was pull up the printer from the Samsung web site and follow support links to some rpm's. But I do remember discovering that the driver install scripts are TERRIBLE. I don't mean merely inelegant or broken, I mean outrageous. They actually replace parts of your system they have no business touching, without even asking if it's ok or warning you, basically breaking the system in order to make this printer & scanner work, and the uninstall doesn't undo it all either. One really outrageous example was replacing a basic binary like lpstat that is supposed to be only a commandline and background tool, with a QT gui version, which then of course fails to run in any situation other than when run by an interactive users from an X session! I don't remember if it was lpstat specifically or some other(s) but it was like that, and it BROKE the system because the binary is used in all manner of situations as part of printing and has nothing to do with desktop/gui! Horrible horrible install that was clearly written by someone who writes for the Windows world where there is no such thing as running without a gui and all machines have the same files in the same place and all work exactly the same way and there is only one user at a time and they are always an interactive user and a gui user.

However at least for the printer part, you can skip that mess. Jaunty supports it natively. (via foo2zjs used by foomatic used by cups). Just go to system, printing, add, it searches the network and finds the samsung, then says searching for drivers for a minute or so, then prompts you to OK the driver it pre-selected and for me that worked fine just now on xubuntu-jaunty.

I haven't even tried to scan in linux from this thing so no help there, except this: Given the the train wreck that is the manufacturer-supplied printer driver, I would avoid the scanner drivers supplied by Samsung like the plague and hope that there is similar built-in support, and if you HAD to try the manufacturer-supplied driver, find out everything it does and clean up after it. None of the bad things the Samsung printer driver did were actually necessary to make the printer work and I was able to clean things up afterwards and still have the printer work fine, so perhaps the same will be true of the scanner driver.

---

### Post by rrinaudo on 2010-04-11
I have the CLX-3175 and I installed the linux drivers from Samsung's support site. When installing them be sure to pick Samsung CLX-3170 Series (SPL-C) driver for the printer, and it works great!.

Good luck

---

### Post by Kermit524 on 2010-04-24
Hi, after reading [KEYofR]("http://ubuntuforums.org/member.php?u=369201") I have decided to avoid using the install.sh script, and set the device using the system printer manager. This worked out fine, so thanks for the tip!
However, I still at a loss on how to set the scanner to work on Karmic.
Is there a way I can set a scanner using the system tools, by having it scan for the driver and install it? Or is there a way to find the right driver myself? 
Thanks in advance for any help at that,
Michal

---

### Post by Kermit524 on 2010-04-24
Ok I came across this:
[http://www-personal.umich.edu/~tjwatt/suldr/index.html]("http://www-personal.umich.edu/%7Etjwatt/suldr/index.html")
Everything now is up and running.
Hope it can help other people.
Cheers,
Michal

---

### Post by plh on 2010-12-20
hello kermit,

this libk is not active anymore :(
do you remember what you had to do to make the scanner work with the network (and not with USB, which already works fine but is boring to use), or do you know were I can now find the info ?

thx in advance!

---

### Post by Kermit524 on 2010-12-20
> **plh said:**
> hello kermit,

this libk is not active anymore :(
do you remember what you had to do to make the scanner work with the network (and not with USB, which already works fine but is boring to use), or do you know were I can now find the info ?

thx in advance!

I am so sorry - but I have no solution :-(. Even worse - after upgrading my system to lucid - the scanner stopped working.

In the meantime I gave up, and scan by the USB interface. 

If you find anything - maybe you want to post it here.

Good luck!
Michal

---

### Post by Kermit524 on 2010-12-20
> **Kermit524 said:**
> I am so sorry - but I have no solution :-(. Even worse - after upgrading my system to lucid - the scanner stopped working.

In the meantime I gave up, and scan by the USB interface. 

If you find anything - maybe you want to post it here.

Good luck!
Michal

This may help:
[http://ohioloco.ubuntuforums.org/showthread.php?t=341621&page=49](http://ohioloco.ubuntuforums.org/showthread.php?t=341621&page=49)

---

### Post by scooper77515 on 2011-03-05
I know, old thread...Maybe someone will come along and ask the same question.

I just bought this printer and it literally installed itself on my ubuntu 10.10. It found it's own drivers, etc. I just pointed it to the IP address of the printer.

---

### Post by Flanmaster on 2012-10-15
This is specific to scanning

Disclaimer:
This information assumes you have assigned a static ip address to your samsung clx-317x printer, AND that you sane and xsane installed on your flavor of linux/ubuntu/etc.

If you can't get your scanner working then here are Specific instructions for the computer illiterates here both in command line and graphical formats :

From the command line:
type:
```
sudo gedit /etc/sane.d/xerox_mfp.conf
```enter your password

either search or browse for the following lines

> #Samsung CLX-3170fn & CLX-3175FW
usb 0x04e8 0x342aModify the file so that the above will look something like this:

> #Samsung CLX-3170fn & CLX-3175FW
#usb 0x04e8 0x342a
192.168.x.x <NOTE: put the actual ip address of YOUR printer here>
save the file and close.

FROM THE GUI (graphical user interface)
Click open whatever file manager YOUR variant of ubuntu possesses that you use (mine uses nautilus)
open up the root directory (assuming everything has been automatically installed or you manually installed everything to the root directory), also shown as "system"
from here RIGHT click on the "etc" folder and select "open as administrator"
when prompted enter your password. 
double click (open) the "sane.d" folder
right click on the "xerox_mfp.conf" file and select to open with whichever editor you prefer (I use gedit)
search or browse for the following lines:


> #Samsung CLX-3170fn & CLX-3175FW
usb 0x04e8 0x342aModify the file so that the above will look something like this:

> #Samsung CLX-3170fn & CLX-3175FW
#usb 0x04e8 0x342a
192.168.x.x<NOTE: put the actual ip address of YOUR printer here>
Save the file and close.

when I performed the above edits to the noted file I was immediately aboe to open gimp and scan a picture into gimp.  Hope this helps.  

while this is probably tmi for many, perhaps it is just enough for others.

Credits/kudos:
Here is a link to the (original) short version that I found first that assumes you know how to do all the above without needing step by step instructions:

[http://www.pclinuxos.com/forum/index.php?topic=101096.0](http://www.pclinuxos.com/forum/index.php?topic=101096.0)

---

