---
title: "Dell 1018 wireless inoperative"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by Sargatana on 2012-01-26
I have a Dell 1018 netbook, running ubuntu 10.10.  Around 2 weeks ago the wireless stopped working.  I was running 11.10 but did not care for the unity dashboard feature.  I had my friend install 10.10 because it is more pleasing to me being an inexperienced user.  I have read that the netbook I have has had  this problem across the board, from windows 7, to all versions of ubuntu.  Being very inexperienced with non windows platforms, all I have been able to figure out is that using the terminal and the RFKILL LIST command this is what I see.  

root@wedge-Inspiron-1018:/home/wedge# rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@wedge-Inspiron-1018:/home/wedge# 

Using this information I found on another forum (can't remember which one) I then tried rfkill unblock 0 this is what shows up in the terminal
root@wedge-Inspiron-1018:/home/wedge# rfkill unblock 0
root@wedge-Inspiron-1018:/home/wedge#



I am not sure what the problem would be, and the command to unblock doesn't seem to work.


Please help this helpless n00b   

              Thank you in advance,
                             Brian

---

### Post by chili555 on 2012-01-26
Please press the F2 button and run and post:```
rfkill list all
```Now run:```
lsmod | grep dell
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

You will find a dell module is loaded and running, named dell-laptop or dell-wmi. We are going to remove it temporarily and see if it helps. If it does, we will make it premanent. Whatever you found will be substituted here:```
sudo rmmod -f dell-[COLOR="Red"]whatyoufound[/COLOR]
sudo rfkill unblock all
rfkill list all
```Any improvements?

---

### Post by Sargatana on 2012-01-26
I'm not sure if I'm doing something wrong here, but this is what I've got so far


> root@wedge-Inspiron-1018:/home/wedge# rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@wedge-Inspiron-1018:/home/wedge# lsmod | grep dell
dell_laptop             5730  0 
dcdbas                  5402  1 dell_laptop
root@wedge-Inspiron-1018:/home/wedge# rmmod -f dell-dcdbas
ERROR: Removing 'dell_dcdbas': No such file or directory
root@wedge-Inspiron-1018:/home/wedge# rmmod -f dell-dell_laptop
ERROR: Removing 'dell_dell_laptop': No such file or directory

Did I enter something wrong in the terminal, or is this worse than I thought?

Apologies in advance, still pretty new at this...

---

### Post by chili555 on 2012-01-26
You were close! Please try this:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
rfkill list all
```What does it say now?

---

### Post by Sargatana on 2012-01-26
Ok, that gave me this:
 Code:
root@wedge-Inspiron-1018:/home/wedge# rmmod -f dell-laptop
root@wedge-Inspiron-1018:/home/wedge# rfkill unblock all
root@wedge-Inspiron-1018:/home/wedge# rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@wedge-Inspiron-1018:/home/wedge# 
 

When I disconnect the laptop from my wired connection, there is no change.

---

### Post by Sargatana on 2012-01-28
I found a bug report on another forum (can't remember, bad memory) but they are text files of code and I'm pretty confused on what to do with them.  Do I have to put them in the terminal line by line?  Or do I have to get something to compile them and make something else to install?  I will post the files when I get home from work.

---

### Post by chili555 on 2012-01-28
> **Sargatana said:**
> I found a bug report on another forum (can't remember, bad memory) but they are text files of code and I'm pretty confused on what to do with them.  Do I have to put them in the terminal line by line?  Or do I have to get something to compile them and make something else to install?  I will post the files when I get home from work.It depends on what they are. Can you post the link here and we can look at it together?

---

### Post by Sargatana on 2012-01-28
Here is the link for the first bug report I found
 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/697520](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/697520)

Here is the "drivers" that I found
 [http://people.canonical.com/~lexical/bugs/lp697520/](http://people.canonical.com/~lexical/bugs/lp697520/)


I haven't been able to figure out what to do with these.  Sorry about not posting this earlier, but I found these this morning and had to leave for work quicker than I expected.

---

### Post by chili555 on 2012-01-28
> **Sargatana said:**
> Here is the link for the first bug report I found
 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/697520](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/697520)

Here is the "drivers" that I found
 [http://people.canonical.com/~lexical/bugs/lp697520/](http://people.canonical.com/~lexical/bugs/lp697520/)


I haven't been able to figure out what to do with these.  Sorry about not posting this earlier, but I found these this morning and had to leave for work quicker than I expected.The bug report says:> Fixed in linux (2.6.38-5.32) natty.What kernel version are you running?```
uname -r
```I think it would be easier and permanent to update your kernel if not done so far.

If you are already running a kernel equal or later than 2.6.38-5.32, you need to reopen the bug report. 

If upgrading the kernel doesn't do it, we'll attack the files linked.

---

### Post by Sargatana on 2012-01-28
It says that I am running 2.6.35-32-generic.


How would I go about updating the kernel?  I looked in the help, and online, but didn't want to go and update and install a "custom" one without being told to do so.

---

### Post by Sargatana on 2012-01-28
UPDATE:
  It works now.  I really wish I knew what exactly I did, but it now works.  I tried resetting the bios settings to factory, but that didn't work.  I tried the System Testing program thingy as a last ditch effort, and while it was testing the network connections, it connected.  I will attach the results of the tests if someone can tell me how to upload an .xml.html file .  Can anyone tell me what happened for it to start working again?  Thank you for all your help, especially you chili555.

---

### Post by chili555 on 2012-01-28
You could download it here: [http://packages.ubuntu.com/natty/linux-image-2.6.38-10-generic](http://packages.ubuntu.com/natty/linux-image-2.6.38-10-generic)

I am not at all sure you can install a package from 11.04 on your 10.10 system, but you can download it and try:```
sudo dpkg -i linux-image*
```If it doesn't work or there are errors, we'll try the files referenced above.

---

