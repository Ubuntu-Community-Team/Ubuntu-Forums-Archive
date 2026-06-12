---
title: "Help With Fixing My HP dv2000's audio!!!!!!!"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by Watchtow3r on 2007-12-21
I have been trying using various techniques for the longest time to try to fix my audio using various techniques to no avail. I have no audio at all dual booting Ubuntu on my HP laptop, even though it works fine in Windows. This is supposedly a common problem, and I can't seem to fix it. PLEASE HELP! I have been trying to get it to work almost forever now and I'm about to give up with Ubuntu. I tried [this]("http://ubuntuforums.org/showthread.php?t=455147") guide, but it gets confusing in the very first step. First off, am I suppose to put uname -r in apostrophes like in the instructions? Because when I do that, my (myname)@ubuntu:~$ symbl on the left side of the terminal goes away and is replaced by a > symbol. This symbol seems to make the terminal do nothing, no matter what commands I type. Also, if I don't put the apostrophes there in the first step, I get this: 2.6.22-14-generic. What do I use that for? Do I put that in place of where it says (uname -r) in step 2? Also, do I put 2.6.22-14-generic inside of the parentheses, or just leave out the parentheses?

Here's a copy of everything I tried: 

jake@ubuntu:~$ uname -r
2.6.22-14-generic
jake@ubuntu:~$ sudo apt-get install linux-headers-$(uname -r) build-essential libncurses5-dev libncursesw5-dev ncurses-term alsa-tools-gui gettext po-debconf debhelper quilt alsa-base libc6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsa-tools-gui
jake@ubuntu:~$ sudo apt-get install linux-headers-$(2.6.22-14-generic) build-essential libncurses5-dev libncursesw5-dev ncurses-term alsa-tools-gui gettext po-debconf debhelper quilt alsa-base libc6-dev
bash: 2.6.22-14-generic: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is not installed, so not removed
E: Couldn't find package alsa-tools-gui
jake@ubuntu:~$ sudo apt-get install linux-headers-$2.6.22-14-generic build-essential libncurses5-dev libncursesw5-dev ncurses-term alsa-tools-gui gettext po-debconf debhelper quilt alsa-base libc6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-.6.22-14-generic
jake@ubuntu:~$ 

No matter which way I do it, I keep getting error messages (the "couldn't find package..." message. Am I suppose to be getting this message?

Also, later on in step 2, it looks like this:

jake@ubuntu:~$  sudo apt-get remove --purge alsa-base alsa-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsa-tools
jake@ubuntu:~$ 

Which looks to me like another error message.

Also, on the next step, it looks like this (step 4) (for the first part of it):

jake@ubuntu:~$ mkdir /home/user/alsa
mkdir: cannot create directory `/home/user/alsa': No such file or directory

Am I suppose to put my username (jake) in place of where it says user?



I'm sure I will have questions later on, but if someone could lay out very simply how to fix these problem, it would be much appreciated. Sorry if I sounded rude, I'm just very frustrated now.

---

### Post by anubhavrocks on 2007-12-21
Use this command
jake@ubuntu:~$ sudo apt-get install linux-headers-2.6.22-14-generic build-essential libncurses5-dev libncursesw5-dev ncurses-term alsa-tools-gui gettext po-debconf debhelper quilt alsa-base libc6-dev

---

### Post by Watchtow3r on 2007-12-21
I tried that and I'm still getting the "E: Couldn't find package alsa-tools-gui"
 message

---

### Post by anubhavrocks on 2007-12-22
Enable Universe,Multiverse repositories through Synaptic Package Manager and then try.

---

### Post by Watchtow3r on 2007-12-22
Thanks, that helped with the first parts. With the next parts though, I have some more questions.On the next part, I kept doing this and got this error message:

jake@ubuntu:~$ mkdir /home/user/alsa
mkdir: cannot create directory `/home/user/alsa': No such file or directory

So I changed it to mkdir /home/jake/alsa and it seemed to work (it didn't display any notifications, just gave me a new command prompt), so I assume that's fixed.

But, my biggest problem is this: on step 7, I kept getting this message: 

root@ubuntu:/home/ubuntu# cd alsa-driver-1.0.15rc3/
bash: cd: alsa-driver-1.0.15rc3/: No such file or directory

How can I fix this? Because I get this same message when trying to install the:
 cd alsa-lib-1.0.15rc3 , cd alsa-utils-1.0.15rc1 and cd alsa-firmware-1.0.15rc1 files.

Also, in step 14, I don't even see a Recording tab.

Lastly, this may just be a result of steps 7-11 not working, but on step 17, heres what I get when I type in the command:

root@ubuntu:/home/ubuntu# /usr/sbin/alsaconf
bash: /usr/sbin/alsaconf: No such file or directory

Again, I don't know what's wrong here.

Sorry for all the lengthy questions, but I really want to get this working. Thanks a lot to everyone that helps!

---

### Post by Watchtow3r on 2007-12-22
Can someone help me out?

---

### Post by Watchtow3r on 2007-12-24
bump

---

### Post by quik366 on 2008-01-02
be carefull when looking at commands lots of commands require you to use sudo before hand... try sudo mkdir ... btw i am having this same issue looking for 3 days i am about to downgrade to 7.04 from what I understand this is a glitch in gutsy (7.10) and (7.04) works fine with our sound card...goodluck!

---

### Post by christrucker on 2008-01-29
Heres something I found.  I have a pavilion dv2000 with duel boot 7.10 and vista.  Sound works fine in vista and sometimes works fine in ubuntu 7.10.  I have been trying to find a pattern to why it works sometimes and not others.  I have tried hibernating windows and doing a full shutdown doesn't seem to make a difference.  It just seems to work sometimes.  Another interesting thing is my buttons for mute and play and volume control work without me having to do anything.  It even mutes and turns up and down the volume.  Just no sounds come out!  Its weird how it works perfectly fine some times and not others?!?  Does anyone have any suggestions??  Thanks

-Chris-

---

### Post by Desiree on 2008-01-31
Chris,

I am having the same problem with my newly installed Ubuntu 7.10 on my HP dv6000, but was aware of the problem before I went ahead.  Sound works on the Vista partition, as do the audio controls on Ubuntu, just no sound.  Sounds familiar doesn't it?  I'm still working on getting my repositories up and running as I still am rather slow at re-figuring out what has to be done to make things tick again, but the linked thread below may be of some help to you as it seems to have helped others in a similar situation.  

Post #6 by holodad:
[http://ubuntuforums.org/showthread.php?t=582825](http://ubuntuforums.org/showthread.php?t=582825)
> 
* sudo apt-get install module-assistant
* sudo m-a update
* sudo m-a prepare
* sudo m-a a-i alsa
* Reboot and setup your sound settings

I get stuck on the first terminal line, but maybe you won't. I have to investigate further, but feel free to post if you have better luck.

---

### Post by christrucker on 2008-02-01
Desiree, I have had my laptop sound work in linux the past 3 times I started it.  Seems to make no difference if I hibernate vista or shut it down.  I have also tried muting and un muting before I start linux.  Right now I know my vista is unmuted and I hibernated it and it worked in linux.  But I have tried that combo before, so I don't know.  Its maddening how it works fine sometimes and not other.  I will try what you suggested and let you know.
-Chris-

---

### Post by hp_dv2k_guy on 2008-02-15
same exact problemo here: it works rarely, usually it doesnt
did u have any luck?

I tried doing the same stuff but doesnt compile on my machine...

---

