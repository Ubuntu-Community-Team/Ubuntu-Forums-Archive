---
title: "MCEUSB IR Blaster problem after upgrade to Mythbuntu 11.04 and Kernel"
date: 2011-08-19
forum: Mythbuntu
---

### Post by Tim L on 2011-08-19
Up to last Saturday had a perfectly working Mythbuntu 10.10. In a moment of insanity I decided to upgrade to 11.04.

 

From that point on the MCEUSB IR Blaster stopped working. After trying a number of solutions I finally did a fresh installation of Mythbuntu 11.04 - still no luck.

 

irsend -d /dev/lircd SEND_ONCE sky 1  works perfectly (Note this is a New Zealand Sky box)

/usr/share/lirc/extras/transmitters/sky/general.conf 01 does not work and produces a page of errors saying that says in part:

 

… line 13: begin: command not found

… Line 15: name: Command not found

… Line 16: bit command not found

… Line 17: CONST_LENGTH: command not found

 

After many hours of reading it seems like the MCEUSB is now part of the Kernel and that there are two instances running at the same time. And because the two are running it is causing a conflict.

 

This seems evident by entering the following in the terminal:

 

$ irsend LIST “” “”

            Sky

            mceusb

 

I have found some information on turning off one [http://ubuntuforums.org/archive/index.php/t-1594799.html](http://ubuntuforums.org/archive/index.php/t-1594799.html) but it is too complex for me to follow all of the steps, and I do not want to try something and have to install everything again. Or even go back to Ubuntu 10.10.

 

My questions are:

 

Does it look like I have correctly identified the problem?

Has anyone got basic instructions on turning one off?

If I keep the Kernel mceusb where do I put the general.conf? (This is necessary for the New Zealand Box)

---

### Post by rileyp on 2011-08-19
Id like to resolve this as well  irsend in natty not working for me either
Did you actually get it to send something in natty?
If you did could I please see your hardware.conf
cheers rileyp

---

### Post by PatrickD-52761 on 2011-09-04
> **Tim L said:**
> Up to last Saturday had a perfectly working Mythbuntu 10.10. In a moment of insanity I decided to upgrade to 11.04.

 

From that point on the MCEUSB IR Blaster stopped working. After trying a number of solutions I finally did a fresh installation of Mythbuntu 11.04 - still no luck.

 

irsend -d /dev/lircd SEND_ONCE sky 1  works perfectly (Note this is a New Zealand Sky box)

/usr/share/lirc/extras/transmitters/sky/general.conf 01 does not work and produces a page of errors saying that says in part:

 

… line 13: begin: command not found

… Line 15: name: Command not found

… Line 16: bit command not found

… Line 17: CONST_LENGTH: command not found

 

After many hours of reading it seems like the MCEUSB is now part of the Kernel and that there are two instances running at the same time. And because the two are running it is causing a conflict.

 

This seems evident by entering the following in the terminal:

 

$ irsend LIST “” “”

            Sky

            mceusb

 

I have found some information on turning off one [http://ubuntuforums.org/archive/index.php/t-1594799.html](http://ubuntuforums.org/archive/index.php/t-1594799.html) but it is too complex for me to follow all of the steps, and I do not want to try something and have to install everything again. Or even go back to Ubuntu 10.10.

 

My questions are:

 

Does it look like I have correctly identified the problem?

Has anyone got basic instructions on turning one off?

If I keep the Kernel mceusb where do I put the general.conf? (This is necessary for the New Zealand Box)

From the thread you quoted, it seems that Post #4 (Option 2) is the way to go.  Here's what he posted:

2. Blacklist the kernel source drivers and use the old dkms built drivers.
-Well you already have lirc-sources-modules install and probably had this working on 10.04 or older version of ubuntu.
A. Edit /etc/modprobe.d/blacklist.conf , create it if it doesn't exist.
Add> 
blacklist mceusb
line to the file and save it.
B. Update initrmafs, #sudo update-initramfs -u -k all
C. reboot
D. Reconfigure lirc if its not already working.
#sudo dpkg-reconfigure lirc
On the Remote, Select "Windows Media Center Transceiver/Remote (All)
E. Thats it. 
This is the method I chose after wrestling with button repeats on option 1. I use XBMC and could not figure out how to disable Ubuntu treating the remote as a keyboard device.

Also for others having issues with lirc and Maverick but using a different remote than the microsoft media center type, something similar approach will more than likely be needed as well.

Essentially the steps work out to this:

1. Install lirc-sources-modules if it's not already present.

```
$ sudo apt-get install lirc-sources-modules 
```

2. Create or edit /etc/modprobe.d/blacklist.conf

```
$ sudo vi /etc/modprobe.d/blacklist.conf 
``` (you can use whatever editor you want in place of vi--I typically use nano, myself)

3. Add the following line to the end of the /etc/modprobe.d/blacklist.conf file (or add it as the only line if you create the file)

blacklist mceusb

4. Save the file.

5.  Update initrmafs (this essentially tells all versions of your kernel to follow the instructions in the blacklist file, along with any other changes that the kernel needs to make). 

```
$ sudo update-initramfs -u -k all 
```

6. Reboot the computer.

7. D. Reconfigure lirc if its not already working.

```
$sudo dpkg-reconfigure lirc 
```

For your Remote, Select "Windows Media Center Transceiver/Remote (All)


I didn't go into how to edit the file in vi (or save) because I'm not that familiar with it. I've ran into problems with vi, so I prefer to use nano instead. It's more like notepad or "edit" from the old MS-DOS days.

Hopefully this helps, and have a great weekend :)
Patrick.

---

