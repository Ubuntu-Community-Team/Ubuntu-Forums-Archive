---
title: "IMON Pad Problems"
date: 2008-06-30
forum: Mythbuntu
---

### Post by iamian727 on 2008-06-30
I have been trying to install an IMON PAD remote control for my mythbuntu setup for the last two days. Although the forums have been very helpful with the setup and patching steps, most users seem to be fixing problems for already functioning remotes. (fyi I am running Hardy 8.04 with an AMD 64x2)
I have run LIRC several times, including recompiling with the pad2keys patch, there is still no response for the remote.
I also tried running mode2 in root, and it returns 
"mode2: error opening /dev/lirc
mode2: No such file or directory"
At this point, I'm a bit lost as to where to go with this thing (other than to the store to return it). Any ideas why LIRC wouldn't have created the dev/lirc file, and why it won't run?

---

### Post by netslacker on 2008-06-30
try running "irw" from the command line, and press buttons on the remote.  If that works then you are almost there.  If that does not work then there are definite setup/configuration problems that need to be resolved.  Check your lircd.conf file (/etc/lircd.conf) and make sure you have the correct remote control setup.  You can also check the hardware.conf file (/etc/lirc/hardware.conf) and see if the proper driver is being loaded.

If "irw" does not yield results then you can try mode2.  The main difference here is that irw is using the configuration/setup and is an easy way to validate that everything is configged properly where mode2 just reads raw IR commands from the device and prints them to the screen, bypassing the setup.  This is helpful to see if the device was recognized and loaded, but that's about it.

"sudo mode2 -d /dev/lirc0" is the command for imon, since the imon driver loads the device to /dev/lirc0 not /dev/lirc.

---

### Post by sebrock on 2008-06-30
probably you need to create a symlink to /dev/lirc0 (that's lirc-zero).

try:

```

ln -s /dev/lirc /dev/lirc0

```

---

### Post by iamian727 on 2008-07-01
Thanks for the help - I have tried irw, and all it give me is connect:connection refused.

Here is what I got when trying to create the ln:

]root@Ian-Ubuntu:/home/ian# ln -s /dev/lirc /dev/lirc0
ln: creating symbolic link `/dev/lirc0': File exists
root@Ian-Ubuntu:/home/ian# mode2
mode2: error opening /dev/lirc
mode2: No such file or directory
root@Ian-Ubuntu:/home/ian# 

I'm wondering if there is some problem with my daemon configuration - it seems like it doesn't want to load it at all. I also tried to follow the installation found [here]("http://ubuntuforums.org/showthread.php?t=814294"), but when I ran the "./configure" line, it returned:
ian@Ian-Ubuntu:~/Desktop/lirc-0.8.3$ ./configure --with-moduledir=/lib/modules/`uname -r`/kernel/drivers/input/misc --prefix=/usr --with-x --with-driver=<imon_pad>
bash: syntax error near unexpected token `newline'

I have a feeling I am messing up something really basic, and have no idea what that is. Thanks much for the help so far. Any further clues as to what might be going on?

---

### Post by netslacker on 2008-07-01
it sounds like the driver is not being loaded...

what do you get when you do:

ls /dev/l*

You should see something like this:
/dev/lirc0
/dev/lircd
/dev/loop0
/dev/loop1
....

if you don't see /dev/lirc or /dev/lirc0 then the driver is not loading.  /dev/lircd is the daemon.

Also, have you gone into mythbuntu control center and selected the IR remote there?  This utility goes a long way to setup the remote for you.  If you haven't (or even if you have) do it again and make sure to check the box "generate button mappings" or something like that and click apply.

---

### Post by Trollslayer on 2008-07-02
> **iamian727 said:**
> Thanks for the help - I have tried irw, and all it give me is connect:connection refused.

Here is what I got when trying to create the ln:

]root@Ian-Ubuntu:/home/ian# ln -s /dev/lirc /dev/lirc0
ln: creating symbolic link `/dev/lirc0': File exists
root@Ian-Ubuntu:/home/ian# mode2
mode2: error opening /dev/lirc
mode2: No such file or directory
root@Ian-Ubuntu:/home/ian# 

I'm wondering if there is some problem with my daemon configuration - it seems like it doesn't want to load it at all. I also tried to follow the installation found [here]("http://ubuntuforums.org/showthread.php?t=814294"), but when I ran the "./configure" line, it returned:
ian@Ian-Ubuntu:~/Desktop/lirc-0.8.3$ ./configure --with-moduledir=/lib/modules/`uname -r`/kernel/drivers/input/misc --prefix=/usr --with-x --with-driver=<imon_pad>
bash: syntax error near unexpected token `newline'

I have a feeling I am messing up something really basic, and have no idea what that is. Thanks much for the help so far. Any further clues as to what might be going on?

/dev/lirc is the driver, /dev/lirc0 is the interface. DO NOT create a symlink.
Do 'ls /dev/' and see if /dev/lirc0 is present. If not then the receiver has not been found.
If so, try the Mythbuntu control centre to select the remote and genereate dynamic mappings again.
If that doesn't work then it sounds like a hardware problem.

---

