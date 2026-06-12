---
title: "Keep getting GNU GRUB at each boot"
date: 2012-09-28
forum: Multimedia Software
---

### Post by ubite on 2012-09-28
Hi all,

I'm a Ubuntu 12.04 64bit noob, so please go easy on me. 

I installed Ubuntu 12.04 a while ago and recently I was adjusting some of the graphics settings under: System Settings -> Additional Drivers. I tried activating different NVIDIA accelerated graphics drivers because I was having trouble getting two monitors working well (with the monitor that wasn't the main one having a higher HD resolution). 

The current issue is that after following some instructions that involved the terminal which I'm unable to recall, I get a screen each time I boot the computer which gives me options to start the computer with. I think they're related to the display and say things like:

Ubuntu, with Linux 3.2.0-23 - generic
Ubuntu, with Linux 3.2.0-23 - (recovery mode)

Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

Ubuntu, with Linux 3.2.0-29
" " (recovery mode)

Ubuntu, with Linux 3.2.0-25
" " (recovery mode)

Ubuntu, with Linux 3.2.0-24
" " (recovery mode)

Ubuntu, with Linux 3.2.0-23
" " (recover mode)



I am using Ubuntu to type this and I can get into it but when I try to start nvidia x-server settings (which I'm not knowledgeable about), I get:

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Now whether this issue is a simple fix or not, I'm not sure. I could just do a fresh install and more carefully monitor what I do in the future, but I thought this might be a learning experience too. 


Thanks for any input in advance.

---

### Post by oldfred on 2012-09-29
It will list all installed kernels. Often we houseclean out all but the last two kernels. Current and previous just in case there are issues with current, we have a fall back.

HOWTO: Remove Older Kernels via GUI (or CLI)
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

Above mentions synatic which I use. But it is not installed by default anymore.

sudo apt-get install synaptic

You can see all (or last 500) the commands you have run in terminal with this command:

history

Look in system settings and then additional drivers. It should show the nVidia drivers you have. There was (is) a bug where it said it was not installed when it was.

---

### Post by ubite on 2012-10-01
I remembered a bit more about what has happened and since writing my first post have had new hassles.

I reinstalled ubuntu 12.04 on another partition and that works ok. That is the entry at the top of the GNU GRUB boot loader (I'm not sure what else to call it) with the following:

[LEFT]Ubuntu, with Linux 3.2.0-23 - generic
Ubuntu, with Linux 3.2.0-23 - (recovery mode)
[/LEFT]

 The entries below that are from the old partition which I want to access again. I am having trouble with this partition. I will look at clearing up the other kernels once I can access this partition using an administrators account. Do the oldest kernels have a lower number or is it to do with the ordering of the list?

Current dilemma: Ran some updates when I could get into the old partition/installation and now when I try to get into main account, the screen flickers and comes back to the login screen. I can get into guest account ok. Any ideas what would be causing this? I mucked around with starting the x-server or something like that. Not sure how to control from guest account.

---

### Post by 2F4U on 2012-10-01
> Do the oldest kernels have a lower number or is it to do with the ordering of the list?

Thats correct, older kernels have lower numbers.

> Current dilemma: Ran some updates when I could get into the old  partition/installation and now when I try to get into main account, the  screen flickers and comes back to the login screen. 

Seems as if you did something that makes the desktop environment crash and thats the reason why you are thrown back to the login screen. You could try to press Ctrl-Alt-F1 and see if you can get to a virtual console and logon to the system. This would allow you to access the log files and see what is going wrong. In the home directory of the user account that has login problems there should be a file named ".xsession-errors" which may contain the errors responsible for the failed login.

---

