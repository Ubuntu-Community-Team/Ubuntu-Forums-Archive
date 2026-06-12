---
title: "NVIDIA driver install - Error: Unable to find the kernel source tree"
date: 2008-06-28
forum: Multimedia Software
---

### Post by moonwalk on 2008-06-28
After following the very helpful guide from Starcannon in [http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia) I managed to get the installer working. 

Unfortunately the installer is having problems of its own. It had a warning along the lines of 'couldn't find kernel compiler' and attempted to download something to do with the kernel. This didn't work either and I'm currently looking at:

"Error: unable to find the kernel source tree for the currently running kernel. Please make sure you have installed the kernal source files for your kernel and that they are properly configured..."

This Leads to:

"Error: installation has failed. Please see the file '/var/log/nvidia-installer.log' for details

I've attached this file.

Any ideas on what I need to do to get this working?  Thanks

---

### Post by sim-value on 2008-06-29
Install your kernel sources ?

---

### Post by ceedub7 on 2008-12-05
I just want to update this thread to try and save someone some time. I was getting the same message as moonwalk and spent many frustrating hours trying to fix it before figuring out that I had a very simple problem:

/boot/grub/menu.lst wasn't updated properly and I was booting into the wrong kernel! I was booting into 2.6.24-19-generic when I should have been in 2.6.27-9-generic. Once I fixed this installing the Nvidia drivers was completely painless. 

'sudo update-grub' didn't fix the file initially, so I backed it up and deleted it and then re-ran 'update-grub'. This time it worked, so I just copied the WindowsXP section from the backup file into the new one and everything was peachy.

---

### Post by hdog on 2009-01-05
I had this problem after my kernel got upgraded.  I had to do a 
sudo apt-get install linux-headers-`uname -r`
then run the Nvidia installer.

---

### Post by tuket on 2010-01-30
>               **Re: NVIDIA driver install - Error: Unable to find the kernel source tree**
         I had this problem after my kernel got upgraded.  I had to do a 
sudo apt-get install linux-headers-`uname -r`
then run the Nvidia installer.     tank you very helpfull :KS:KS:KS:p:KS:KS:KS

---

### Post by Cincinnatux on 2010-06-23
Thank goodness for this thread!  I've been struggling with nVidia driver issues for the past few days, burning precious hours trying to fix something that appeared to have spontaneously broken without my help.  There are dozens of nVidia problem-solution threads, but none of the others I checked helped me make any progress.  It turns out that my problem was the kernel source tree thing (which I only discovered by trying to manually install the latest nVidia driver), and this thread solved my problem!  Woohoo!

---

### Post by mister.zee.man on 2010-07-04
Sorted for me also. Shouldn't kernel sources automatically download with the update? This should be stickied :KS

---

### Post by rennau80 on 2011-05-20
thanks for this thread. problem solved on my desktop too when i got graphics problems switching to natty narwhal.

---

### Post by frosty555 on 2011-07-04
> **hdog said:**
> I had this problem after my kernel got upgraded.  I had to do a 
sudo apt-get install linux-headers-`uname -r`
then run the Nvidia installer.

This thread was a lifesaver for me as well! I was having a hard time figuring out what package to install to get the kernel source tree. This helped a lot.

(I was actually running Debian Lenny, but it works exactly the same way)

---

### Post by _glook on 2011-10-11
hdog, you sir are a gentleman and a scholar.

After spending hours on this, getting nowhere, your simple solution worked miracles, even on Natty Kubuntu.

This needs to be better indexed by google so it saves more people time.

---

### Post by spleach on 2011-10-16
Yep, still just as relevant today, upgrading to Kubuntu Oneiric Ocelet (11.10). The uprade process should blatantly have upgraded these kernel headers too!

---

### Post by hallgeir on 2012-02-24
Worked like a charm for me as well. Trying to install nvidia driver on my ion 330 chipset on a Debian system.

---

### Post by blueicewater on 2013-02-12
Can someone please explain how to do these solutions in detailed newb instructions?

Running into this same issue too and can't figure out how to fix this from the vague comments :/

---

### Post by blueicewater on 2013-02-12
> **hdog said:**
> I had this problem after my kernel got upgraded.  I had to do a 
sudo apt-get install linux-headers-`uname -r`
then run the Nvidia installer.

What does it mean when it shows this error?

E: Unable to locate package linux-headers-uname-r

---

### Post by bogan on 2013-02-12
Hi!, **blueicewater**,
What: "sudo apt-get install linux-headers-`uname -r`" means, is that you should run: 'uname-' [ without the quotes] and add the output of that command to the 'linuxheaders-' in place of "`uname -r`"; for example: ```
uname -r 
3.5.0-24-generic
sudo apt-get install linux-headers-3.5.0-24-generic
```You can get the same effect by running:```
sudo apt-get install linux-headers-generic
```And then removing the existing video driver and re-installing it. [ Which you must also do after the other command]

Chao!, **bogan**.

---

### Post by lrohr on 2013-02-20
> **blueicewater said:**
> Can someone please explain how to do these solutions in detailed newb instructions?

Running into this same issue too and can't figure out how to fix this from the vague comments :/

Hi, as bogan already described a bit, which can be done easier and I explain more precisely so Linux newbees should be able to do this.

(things in capital letters have to be replaced with the name that is correct for you, like YOUR_NAME is your login name ;) )

1.) Download the driver from Nvidia to a location you can easily find, I suggest your home directory, the path should look like "/home/YOUR_NAME/".

2.) Log off (don't restart or turn off just log off)

3.) press strg + alt + F1 (german layout in english it's ctrl + alt + F1)

4.) the screen gets black and you can log in on the consol by typing YOUR_NAME enter YOUR_PASSWORD enter

5.) you write the following
```
sudo apt-get install linux-headers-`uname -r`
``` with **all** characters even the ` have to be there. And of course hit enter and confirm the questions with yes. Now the missing sources of the kernel will be installed.

6.) you have to shut down the grafix system by typing ```
sudo service lightdm stop
``` Note that lightdm is the standart used in Ubuntu, it maybe, that you have kdm or gdm so if you get an error telling you you don't have lightdm running (or installed) try ```
sudo service kdm stop
``` and/or ```
sudo service gdm stop
```

7.) you start the downloaded Nvidia driver. How? Well change to the directory you downloaded it to, if it is the directory I suggested nothing has to be done if it's not you have to use the change dicertory command i.e. "cd DIRECTORYPATH". Once you're there you simple type```
chmod +x NVIDIA-Linux-VERSION_NAME
sudo ./NVIDIA-Linux-VERSION_NAME
``` and follow the instructions. It may be that you have to reboot after nvidia did some things, this can be done be typing ```
 sudo shutdown -r now
``` after a reboot you have to repeat the steps 3-7 of course befor you log in. (Good advice for linux newbees you don't really have to type in the full name after typing the first characters of the name you can hit the tab key and linux will pull in the rest for you, of course this only works if there is only one file starting with the typed characters otherwise how is linux suppose to know which one you want... and by the way this also works for any other command like the pre mentioned cd DIRECTORYPATH)

8.) when it is installed you can restart the graphics system by typing```
sudo service lightdm start
``` once again if you don't have lightdm try using gdm or kdm instead.

9.) the graphical login screen should appear and everything is fine =)

One last notice, if you want to change the resolution or multi monitor settings you can do this by using the nvidia-settings tool, which you should start with admin/root rights to save the changes permanently, this can be done by starting a terminal and typing in ```
sudo nvidia-settings
``` after the changes don't forget to hit the "Save to X Configuration File" Button.

Thanks again to hdog you really made my day :KS

---

### Post by Yellow Pasque on 2013-02-20
> **blueicewater said:**
> What does it mean when it shows this error?

E: Unable to locate package linux-headers-uname-r
It means you should copy/paste commands when possible to avoid typos. It also probably means you have a key on your keyboard that you rarely/never took notice of: the back tick/quote: [http://www.computerhope.com/jargon/b/backquot.htm](http://www.computerhope.com/jargon/b/backquot.htm)

---

### Post by bogan on 2013-02-20
> **Temüjin said:**
> It means you should copy/paste commands when possible to avoid typos. It also probably means you have a key on your keyboard that you rarely/never took notice of: the back tick/quote: [http://www.computerhope.com/jargon/b/backquot.htm](http://www.computerhope.com/jargon/b/backquot.htm)This is not incorrect, but is is not the right answer to the question.

> What does it mean when it shows this error?

E: Unable to locate package linux-headers-uname-rIt means exactly what it says. The package does not exist because the instruction is wrong: "linux-headers-uname-r" should have been: " linux-headers-'uname-r'", or "linux-headers-<uname-r>" .

Which in turn both mean: replace "<uname -r> with the output from running 'uname -r' [ without quotes ] in a terminal; for example:```
:~$ uname -r
3.5.0-25-generic
sudo apt-get install linux-headers-3.5.0-25-generic
:~$ 
``` The first: 'uname -r' is supposed to do that for you, but in my experience it does not always work, so I prefer to be certain it is right and do it myself.

Chao!,** bogan**.

---

