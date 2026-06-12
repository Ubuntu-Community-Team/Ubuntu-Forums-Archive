---
title: "MythTV working on feisty with PVR-150"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by bdogg64 on 2007-03-12
I guess my first thing would be to thank the people who have helped in this forum before.  That being said, I got MythTV working on my PC on feisty herd 5. I have a Hauppauge WinTV PVR-150.  If anyone else has this card, I can try to help you out, even though I am still new to linux myself.  I compiled MythTV from source because the repository for feisty was broken. I will post a guide on what I did if that will help anyone.

---

### Post by xinix on 2007-03-19
Broken in what way?  I installed from the repos and things went well.  Just curious since it's quite possible that things got fixed between your attempt and mine.

---

### Post by bdogg64 on 2007-03-19
Yea, thats what it was. It had been fixed in the repository since then. I ended up reinstalling from the repository and everything is working fine, including my remote after some tinkering with lirc! :)

---

### Post by majoridiot on 2007-03-20
having *literally* installed every possible variation of MythTV package from the feisty repos
in the past few days, i can say for certainty that they work just fine and the metapakages are 
**awesome!**  installing mythtv has never been easier.

add in PVR-150 functionality "out-of-the-box" and Feisty is looking pretty sweet.

EDIT: forgot to mention feisty's "restricted driver manager"... that downloaded and installed 
the proprietary nvidia driver *correctly* in less than a minute.  the entire process, including
reboot, took less than 3 minutes.  gotta love the great work our devs are doing!

---

### Post by Copland Audio on 2007-06-11
wow, I am really having a hard time getting lirc up and running with this card.  Admitedly, I'm a bit of a newbie, but this lirc install is proving to be twice as difficult as the OS/MythTv/PVR-150 install.  
1. (maybe a dumb question) how do you select the module you need to build in the modules-source pages?  I tried to select the pvr-150 module, but was unable to get that little star next to the selection...I know, I'm new, but the enter key just gets me on to the next page (even though 'ok' isn't selected at the time.

2. I'm so new to the command line interface, I don't think I'm copying the lircd.conf file over correctly.  I saved the file from [https://help.ubuntu.com/community/Install_Lirc_Feisty?action=AttachFile&do=get&target=lircd.conf.hauppauge](https://help.ubuntu.com/community/Install_Lirc_Feisty?action=AttachFile&do=get&target=lircd.conf.hauppauge)
but I' can't seem to understand how you copy that using the next command:
sudo cp <name of downloaded.conf> /etc/lirc
I think I copied it over, but don't know how to change the name of the file to remove the '.hauppage' extension so it's just lircd.conf.

Please help where you can.  and thanks for reading!

---

### Post by uputer on 2007-06-14
Can someone give me instructions for installing Mythtv in Feisty?   I only need steps or instructions for now because I am still configuring my drives set up and need to install Feisty somewhere.   I am also considering adding another Hard Drive.    I have another computer with KnoppMyth on it but I want a Linux distro and Mythtv in which I can surf or do other things.   The Fluxbox in that system doesn't allow that easily.

I'll install Feisty anyway but I would be interested in trying Mythtv on it if it wasn't too complicated.   Some people here are saying it's easier than before.   I would rather not have to compile but if the requirement is adding the repositories and installing various packages, then I might be willing to try it out .

---

