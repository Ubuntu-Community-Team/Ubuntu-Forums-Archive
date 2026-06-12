---
title: "loss of wireless connection"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by Paulsandy on 2010-03-11
I have a new Toshiba Satellite L450, and decided to run Ubuntu, which is new to me. I am running a 64 bit Karmic, and there is no driver that works.  So, to make a long story short: a friend helped me get a driver on my Desktop, namely: rtl8192se_linux_2.6.0100.1012.2009_64bit.tar.gz 

We had it working, but when I let in the first large batch up updates, it kicked the driver out.  I found instructions, installed it again.   I let in the next updates, and it kicked out again, and this time the instructions don't work.  So, I have two sets of questions: 

1.  Will updates always undo my wireless?  Are there certain updates I should avoid if I want the wireless to stay up and running?  (I just assumed the thing to do is just get the updates -- though I am guilty of having no idea what they were about.)

2.  Did the updates cause one of my instrucitons to no longer work, or need to be modified?

They were as follows:

sudo apt-get install build-essential
cd ~/Desktop
sudo tar -xvzf rtl8192se_linux_2.6.0100.1012.2009_64bit.tar.gz 


That 'sudo tar -xvzf...' operation is the one that stops me.  Is there something to change in that line?   It goes on:

cd rtl8192se_linux_2.6.0100.1012.2009_64bit
sudo su
make
make install
exit 
sudo reboot


this worked the first time I tried it.  I posted this earlier under 'hardware', and do not know how to get that post off, so I typed it here once I realized.......sorry for cluttering things up with repeats........I'm new

---

### Post by adam814 on 2010-03-11
What is the exact error you're getting from tar?  Have you tried removing the folder and re-extracting it?

If I had to guess I'd say it's kernel updates that are causing it as you'll have to re-build your driver for each kernel.

---

### Post by Paulsandy on 2010-03-12
Thanks for the reply, adam814.  The error message is as follows:

tar:rtl8192.se_linux_2.6.0010.1012.2009_64bit.tar.gz Cannot open: No such file or directory
tar: error is not recoverable: exiting now
tar: child returned status 2
tar: exiting with failure status due to previous errors


What does it mean to 'remove the folder and extract it again'?  Does it mean to delete it off my Desktop and then download it again?

---

### Post by adam814 on 2010-03-12
The error it gives is that it cannot find a file with that name.  One of three things is happening there:
1) You're not typing the correct filename, which isn't hard to do with one that long and complex
2) You're typing the correct filename, but you're not in the directory the file is in when you type it
3) The file has been accidentally deleted.

By removing the folder and re-extracting it I meant if you still have the archive you should delete the folder that came from it when you ran the tar command and then re-run the tar command to get a fresh version of it.  But if you have a working connection it might also be just as easy to download it again (I'm guessing if you select one of the older kernels at the GRUB menu you'll have working wireless with one of them to grab the file).

---

### Post by Paulsandy on 2010-03-12
Thanks so much!  Your first guess was right: the file on my Desktop didn't have the '64bit.tar.gz'.........I was sure I had checked so carefully!!!

I guess I will just count rebuilding the driver as part of getting updates.

Thanks again.
Cheers

---

### Post by adam814 on 2010-03-12
You'll probably only need to do that if the updates contain "linux-image-<something>-generic".  Non-kernel updates shouldn't affect it.

Two other suggestions for making the process a little easier:

1) For the short term you might be interested in making a shell script to do it for you.
```
#!/bin/bash
cd ~/Desktop
sudo tar -xvzf rtl8192se_linux_2.6.0100.1012.2009.tar.gz 
cd rtl8192se_linux_2.6.0100.1012.2009
sudo su
make
make install
exit
```You'd just need to save that as a text file and make it executable.  To make it executable assuming you saved it as rebuild_driver.sh in your ~ directory you'd just run```
chmod +x rebuild_driver.sh
```Then any time you need to re-build it just go to your home directory in the terminal and type: ```
./rebuild_driver.sh
```Then reboot.

2) In the long term once you've learned a little more and are more comfortable with Ubuntu you might want to look into adding the module to dkms so the post-inst scripts will build it for you when a new kernel gets installed.

---

