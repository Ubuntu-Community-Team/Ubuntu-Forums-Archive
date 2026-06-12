---
title: "how can I install the driver another way?"
date: 2011-02-16
forum: Multimedia Software
---

### Post by debd on 2011-02-16
I have been for some time now trying to manually install an nvidia driver with the .run 

file I dloaded from their website.   since it requires to stop the default gdm X 

server before i can install it, I start a new tty session using ctrl+alt+f1

the problem is , when am dropped in the new session it asks me to log in and 

when I enter my username and pw it says Login incorrect. I  have multi-checked 

that am entering the right credentials..but it refuses to log me in.

anyone else who faced this kinda problem??

pls help.

---

### Post by bloodorange on 2011-02-16
I don't know why your login isn't being accepted in tty1.  However, I'm pretty sure that even if you managed to log into tty1, you still wouldn't be able to install the driver because you're still running X server.  The best way I know of doing this, is to boot into Recovery Mode and do it from there.

If you're dual booting, you'll get the Grub menu when you boot up your PC.  If you're not dual booting, you'll need to hold down Shift (as the PC boots, almost as soon as you've switch on; during POST should do it) until you see the Grub menu.  Either way, at the Grub menu, choose the (usually) second kernel entry from the top (using up/down arrows on your keyboard), which should say "recovery mode" at the end in brackets.

You should then get to the Recovery Menu.  Using your keyboard arrows again, move down to where it says "root" (or you could press "r" on your keyboard).  Press Enter.

You should now be a root command prompt.

Type "telinit 3", without the quotes, and press Enter.

You should now get a prompt asking for your normal username, and then your password.

When you've logged in, navigate to where your "NVIDIA*******.run" file is stored.

Once there, type "sudo sh ./NVIDIA*******.run" (without quotes), obviously typing in the proper name of the file.

That should start the install process, so just follow the instructions from there on.

I can't remember if, at the end of the installation, you are returned to a command prompt, or whether the installation itself reboots your PC.  If you end up at a command prompt, just type "sudo reboot".

I haven't felt the need to install an NVIDIA driver this way for a while, but I'm pretty sure this should work for you.

---

### Post by hsoulen on 2011-02-16
Good reply bloodorange.

Alternative to recovery mode is simply to kill gdm...

Login normally in X, open a terminal and type:

```
sudo service gdm stop
```

Then just hit ctrl+alt+F2 to get a login prompt.

Also, remember you may have to chmod the .run file to make it executable, and you will need to run it as root (sudo).

Edit: This thread has some info for installing Nvidia drivers: [http://ubuntuforums.org/showthread.php?t=1559254]("http://ubuntuforums.org/showthread.php?t=1559254")

Hank

---

### Post by debd on 2011-02-16
actually i was gonna stop x server using 
sudo /etc/init.d/gdm stop

wont that have worked??

anyway m going to try the way you suggested.

thanks.

---

### Post by hsoulen on 2011-02-16
> **debd said:**
> actually i was gonna stop x server using 
sudo /etc/init.d/gdm stop

wont that have worked??

anyway m going to try the way you suggested.

thanks.

Yes, that works sometimes (for some folks and not others, don't ask me why it's Linux!) but the solution I gave works 100% of the time.

Good luck and post your results!

Hank

---

### Post by debd on 2011-02-16
hey bloodorange,  thanks man. it worked. but I had to stop the nouveau kernel driver and try again.
but worked well.

before now I had 1366x768 res display. now, with that res the display goes outta screen. and at a lower res i.e. 1280x800 (set now) the texts are diplaying a bit hazy.
any idea what to do?

---

### Post by hsoulen on 2011-02-16
> **debd said:**
> hey bloodorange,  thanks man. it worked. but I had to stop the nouveau kernel driver and try again.
but worked well.

before now I had 1366x768 res display. now, with that res the display goes outta screen. and at a lower res i.e. 1280x800 (set now) the texts are diplaying a bit hazy.
any idea what to do?

Well if your drivers installed correctly you should have the NVidia control app available "System->Administration->NVIDIA X Server Settings".

Load that up and look under "X Server Display Configuration" and you should be able to set the resolution there.

Hank

---

### Post by bloodorange on 2011-02-16
> **hsoulen said:**
> 
Alternative to recovery mode is simply to kill gdm...

Login normally in X, open a terminal and type:

```
sudo service gdm stop
```

Then just hit ctrl+alt+F2 to get a login prompt.


Hsoulen, thanks for that, I thought there must be a better way than the convoluted method I described.

Debd, you're welcome.  Sorry I didn't know about the nouveau kernel bit.

---

### Post by debd on 2011-02-16
the thing is there is no 1366x768 option in the X Server Display Configuration's res. list.
instead there is 1360x768. which is going out of the screen.

further, when I reboot it rolls back to 'auto' res. mode which is cumbersome.

what should I do?

---

### Post by hsoulen on 2011-02-16
> **debd said:**
> the thing is there is no 1366x768 option in the X Server Display Configuration's res. list.
instead there is 1360x768. which is going out of the screen.

further, when I reboot it rolls back to 'auto' res. mode which is cumbersome.

what should I do?

Sounds to me like the nouveau driver is still conflicting with the NVIDIA proprietary driver, I could be wrong but you can try blacklisting the nouveau driver and any older NVIDIA Drivers:

Add the following to

```
/etc/modprobe.d/nvidia-graphics-drivers.conf:

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
alias nvidia nvidia-current
```


EDIT: You will need to reboot after editing the file...

Hope this works for ya.

Cheers,

Hank

---

### Post by debd on 2011-02-16
well, the 'roll back to auto' has been solved after I saved the nvidia x server display settings in the conf file.

but still clueless about how to make the texts appear prominent. :|

..but thanks for all your replies. :)

---

