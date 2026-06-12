---
title: "No sound at all; it doesn't recognize my audio card"
date: 2010-12-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Nuker90 on 2010-12-19
Hello, I am Nuker90, a newbie with Ubuntu and Linux (have it for almost 2  months) and I'll try to explain my problem in the most clear way  possible so you could hopefully help me.

DESCRIPTION:

Currently I am using Ubuntu 11.04.

Ok, so I had Ubuntu 10.04 before, running perfect; almost perfect - I  had a problem with a strange beep (coming from my motherboard I think),  when I restarted the system. Also, I have to say that I had a problem  with my sound in the headphones: when I was plugging the headphones in,  the sound from the speakers was going off but I was still not getting  sound on the headphones; I figured it out in the end and it worked  perfectly (updating some alsa drivers and things like these, if I  remember well - also editing some cfg files).

Ok, now what is the problem: I updated, as stated, to Ubuntu 11.04,  hoping to get rid of the strange beep. Everything went well, the beep  went off but the alsa drivers got replaced. And the problem with the  headphones appeared again.
Therefore, I tried to fix it again, by updating alsa drivers but ended up destroying everything :sad:.  There was no more sound from the speakers and, when I went to the Sound  options -> Output, there was a DUMMY OUTPUT (or SPEAKERS) option  checked.

WHAT I HAVE TRIED:

I have tried to use this guide  ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449))  to reinstall everything but I encountered an error when I was compiling  the drivers (sudo module-assistant a-i   alsa-source   - in this  point). Therefore, I am currently in that stage of "fixing" the problem.  Also, I have to tell you that I have the   hda-intel   module for my  sound card (that's what it says and what I remember from when it  worked).


So, this is my problem. Hopefully someone will have the time to read  everything and try to assist me in fixing it.I'd really appreciate that.  

Thank you,
Nuker90



PS: There's one more little thing that I want to ask whoever reads and  is willing to help me - whenever I start Ubuntu / shut it down, I get  some lines of "code" or lines of messages that prompt on my screen - is  it normal for 11.04? 

Thank you again!

---

### Post by cariboo on 2010-12-19
It would help if you let us know what make/model/type of sound card you are using. Could you paste the output of:

```
lspci | grep Audio
```

in your next post.

> PS: There's one more little thing that I want to ask whoever reads and is willing to help me - whenever I start Ubuntu / shut it down, I get some lines of "code" or lines of messages that prompt on my screen - is it normal for 11.04? 

It could be depnding on the state of your installation. Remember this is **Alpha** software, things are frequently broken and probably will be until the RC release. If you don't want to be constantly fixing things that are broken, I would suggest you go back to a released version.

---

### Post by Nuker90 on 2010-12-24
```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
02:00.1 Audio device: ATI Technologies Inc RV710/730
```




Sorry for the late reply, but I was travelling...

Thank you again and have a nice Holiday.

Nuker90

---

### Post by efflandt on 2010-12-24
What do you get for **dmesg | grep -i hda** (that is hyphen, small i for case insensitive).  I have i5 cpu, but NVidia instead of ATI and my ACL audio device on the motherboard might be different.  Example:

```
**lspci | grep Audio**
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)

**dmesg | grep -i hda**
[    9.112547] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.112595] HDA Intel 0000:00:1b.0: irq 42 for MSI/MSI-X
[    9.112634] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.233048] hda_codec: ALC887: BIOS auto-probing.
[    9.248585] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    9.248757] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.248760] hda_intel: Disable MSI for Nvidia chipset
[    9.248800] HDA Intel 0000:01:00.1: setting latency timer to 64
[   15.644971] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
```But if you removed or have been tampering with alsa, not sure what state your sound drivers are in.

In a terminal, does **aplay -l** (small L) hang (if it does hit Ctrl+C) and does **alsamixer** show any sound devices (MM would indicate an input or output is muted, m to unmute).  In some cases aplay -l may hang, but alsamixer might still show audio devices.

My system is configured to use analog sound on the internal device, and I had to add a line to /etc/pulse/default.pa to enable HDMI audio, so I could select and control main volume of either Output from Sound Preferences (pulse).

---

### Post by Nuker90 on 2010-12-24
```
vlad@vlad-laptop:~$ dmesg | grep -i hda
vlad@vlad-laptop:~$ aplay -l
aplay: device_list:235: no soundcards found...
vlad@vlad-laptop:~$ alsamixer
cannot open mixer: No such file or directory
vlad@vlad-laptop:~$ 
```


So, the GREP thing doesn't give anything...

---

### Post by ronacc on 2010-12-24
it looks like you don't have alsamixer installed ,use synaptic or apt-get to install either alsamixergui and/or gnome-alsaamixer .

---

### Post by Nuker90 on 2010-12-24
```
vlad@vlad-laptop:~$ alsamixer
cannot open mixer: No such file or directory
vlad@vlad-laptop:~$ sudo apt-get install alsamixergui
[sudo] password for vlad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsamixergui is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
vlad@vlad-laptop:~$ sudo apt-get install gnome-alsamixer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-alsamixer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
vlad@vlad-laptop:~$ alsamixer
cannot open mixer: No such file or directory

```

So I installed alsamixergui (using the shown command) and then restarted; after the reboot, I did it again just to be sure, and that's what I got, but I can't get into alsamixer still...

---

### Post by ronacc on 2010-12-24
I think the command you want to start it with is alsamixergui  not alsamixer ,also you should be able to launch it from applications>sound&video  if in classic or just applications if in unity .

edit , gnome-alsamixer gives more things you can twiddle with

---

### Post by mc4man on 2010-12-24
just a small observation - if you were following that guide, at the point you say you're at you would have re-installed several packages inc. alsa-utils which has alasmixer.
Maybe you skipped that step and possibly others?

---

### Post by Nuker90 on 2010-12-24
> **mc4man said:**
> just a small observation - if you were following that guide, at the point you say you're at you would have re-installed several packages inc. alsa-utils which has alasmixer.
Maybe you skipped that step and possibly others?

Well, I tried that tutorial (with uninstalling everything, reinstalling, etc.) three times, and I got the errors / problems in the same place - when I try to compile the drivers for my sound card... So I think I did it the right way but the problem may be somewhere else.

Also, I forgot to mention that the little speaker from the toolbar is no longer there (it disappeared before I posted on the forums, while I was trying to update the drivers and so on, by myself).


> **ronacc said:**
> I think the command you want to start it with is alsamixergui  not alsamixer ,also you should be able to launch it from applications>sound&video  if in classic or just applications if in unity .

edit , gnome-alsamixer gives more things you can twiddle with


Ok, indeed my command was wrong. I used the ones you told me and I get the following behaviors:
1.
```
vlad@vlad-laptop:~$  alsamixergui

```
pops out a window that states:
```

alsamixer: function snd_ctl_open failed for default: No such file or directory
```
with only the option to CLOSE it.

2.
```

vlad@vlad-laptop:~$ gnome-alsamixer

```
opens a window that is blank - it only has the header, with the File Edit Help  buttons; File -> Exit,  Edit -> {Sound Card Properties, Program Preferences},  Help -> About;    if I click on Edit -> Sound Card Properties, here is what I get:
```

vlad@vlad-laptop:~$ gnome-alsamixer

(gnome-alsamixer:2582): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault

```


Hope this is helpful in an way to determine what the problem is... :(

Thank you.

---

### Post by lidex on 2010-12-25
You probably borked your alsa and/or pulse install trying to upgrade. More info would be useful. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Oh yes, and Merry Christmas.

---

### Post by Nuker90 on 2010-12-25
```

Your ALSA information is located at http://www.alsa-project.org/db/?f=dcc8ed8f155cd5b531695c9c4a02925c14cb5533  
```


Thanks and Merry Christmas :) *sorry for bothering you with this... :< *

---

### Post by lidex on 2010-12-25
Yeah, alsa is borked. A re-install should get you back to default.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

Haha, this is no bother. I'm glad I now have the off time to spend here.

---

### Post by Nuker90 on 2010-12-28
Ok guys, thank you for your help and sorry for my late feedback, but here is what happened:

lidex, I did what you said (I think I did at least), because, after you posted the steps, I went to sleep because I was too tired. The next day, when I opened my laptop with ubuntu, I tried to do the steps but, after 5 mins, the whole system froze (I was able to complete just the 1st thing). I restarted, I did the rest of it, and it froze again after. And now I think I was able to do everything, but there is still no sound and ubuntu freezes after 5 minutes, every time I run it.

Do you have any other ideas now, besides reinstalling to 10.10? :-/

Thank you very very much and sorry for the late reply.

Nuker90

---

### Post by lidex on 2010-12-28
At this point you're probably better off with a re-install. It would be less work and time. Just back up your data first.

> **cariboo907 said:**
> 
It could be depnding on the state of your installation. Remember this is **Alpha** software, things are frequently broken and probably will be until the RC release. If you don't want to be constantly fixing things that are broken, I would suggest you go back to a released version.

---

### Post by Nuker90 on 2010-12-28
Ok... and is there a way of reinstalling with keeping part of my settings or something similar? Or how should I reinstall it :D

EDIT: I installed ubuntu via wubi.exe, but I don't have it in Add/Remove Programs... So, how should I properly do it?

---

### Post by cariboo on 2010-12-28
I've never done a wubi install, but I assume there is a partitioning step, once you get to it choose manual partitioning, and select the partition you want to use, but don't mark it for formatting, then continue on with the installation. I won't guarantee that it will work, but it's worth a try.

---

### Post by lidex on 2010-12-29
> **Nuker90 said:**
> Ok... and is there a way of reinstalling with keeping part of my settings or something similar? Or how should I reinstall it :D

EDIT: I installed ubuntu via wubi.exe, but I don't have it in Add/Remove Programs... So, how should I properly do it?

Have a look here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by shre7as on 2011-01-14
you might want to check out this link.. it worked for me on 11.04 [http://www.webupd8.org/2010/11/fix-hda-intel-realtek-alc887-no-sound.html]("http://www.webupd8.org/2010/11/fix-hda-intel-realtek-alc887-no-sound.html")

---

