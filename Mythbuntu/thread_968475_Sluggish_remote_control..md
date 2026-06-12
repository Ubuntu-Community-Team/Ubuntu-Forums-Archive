---
title: "Sluggish remote control."
date: 2008-11-02
forum: Mythbuntu
---

### Post by scweston on 2008-11-02
Hi,

I hope someone could help me! After having a perfectly working and smooth operating mythtv setup on hardy I was very silly in deciding to fix what wasn't broken and wipe the system and install the new intrepid then add mythtv on to it following the instructions on the mythbuntu website.

At the moment I'm having problems with a sluggish remote control. It's the grey/silver one that comes with the Hauppauge Nova-T 500. I've managed to set the device up and get all the buttons to work the way I want them to, except for the fact that the response in mythtv is very sluggish. It also causes the tv playback to become choppy when used to change the volume for example during playback (I don't find this when I use the keyboard in place of the remote).

I followed the suggestion in this thread [http://ubuntuforums.org/showthread.php?t=835809](http://ubuntuforums.org/showthread.php?t=835809) to add Option "UseEvents" "on" to xorg.conf. This has improved things, but not completely resolved the issue. So I'm guessing that there is something else going on too.

Please, any suggestions would be welcome.

Stephen

---

### Post by SiHa on 2008-11-03
See rtrevors post in this thread:
[http://ubuntuforums.org/showthread.php?t=787218&highlight=exclusive+access](http://ubuntuforums.org/showthread.php?t=787218&highlight=exclusive+access)
There's a link to a bug and a manual fix that may help:

---

### Post by scweston on 2008-11-03
Hi,

Thanks SiHa fro your suggestion. I had already found that fix myself and had to use it to get the remote control working at all when I was first setting up the remote. However, it is not what I believe is causing the choppy tv playback the moment any remote button is pressed (note that using the equivalent keyboard controls doesn't have the same issue, so is definitely a remote problem). I have also used the remote in other applications such as totem movie player and have no issues there. I think this is a specifically a MythTV problem I have got.

Any more suggestion are welcome.

Stephen

---

### Post by ajhtiredwolf on 2008-11-03
I feel your pain, i have the same problem. I have a thought though, do you have virtualbox installed? And does the remote go through USB? I am thinking that the problem is with a USB conflict caused by the tuner, but virtualbox has given me usb problems in the passed as well. So thought i might ask

---

### Post by scweston on 2008-11-03
> **ajhtiredwolf said:**
> I feel your pain, i have the same problem. I have a thought though, do you have virtualbox installed? And does the remote go through USB? I am thinking that the problem is with a USB conflict caused by the tuner, but virtualbox has given me usb problems in the passed as well. So thought i might ask

Hi,

ajhtiredwolf I think you may be on to something with the USB thing. I have also 'just' discovered I'm having issues with USB devices (I've just tried copying stuff from a usb drive and its copying at USB1.1 speeds). And from what I understand about the Hauppauge Nova-T 500 is that it's basically a USB device as the PCI card boasts an onboard USB controller (see the information about the device ([http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)). So my remote control is going through USB.

Unfortunately I don't know any more about how to check that my USB devices are using USB2 over USB1.1, nor how to fix the problem if it is.

Here's a link to another thread that shows someone with similar slow speeds from their USB devices.. [http://ubuntuforums.org/showthread.php?t=968547](http://ubuntuforums.org/showthread.php?t=968547) Although no solution yet.

Also, to answer your question I don not have VirtualBox installed.

Stephen

---

### Post by ajhtiredwolf on 2008-11-04
Welp it looks like most people have this issued solved by following the instructions in this thread.
[http://ubuntuforums.org/showthread.php?t=835809&highlight=lirc+lag&page=2](http://ubuntuforums.org/showthread.php?t=835809&highlight=lirc+lag&page=2)
you have to add 
	Option "UseEvents" "on"
to the device section of your xorg.conf. 
Unfortunately this didn't solve my issue, for me, the cpu doesnt continue to jump to 100% when using the remote, the cpu load stays fine. But I continue to have this issue. Give it a try, maye it will help you.

---

### Post by scweston on 2008-11-05
Hi ajhtiredwolf,

Thanks for the suggestion, although as you can see from my first post I had already noticed that thread and attempted their suggestions. It did improve things slightly, but didn't completely resolve the issue as I still occasionally get a sluggish remote and choppy video when I use the remote control.

I did however stop the jumping CPU usage as you suggested.

I have to admit defeat with Intrepid now. I'de had too many problems getting my hardware to run as smoothly as it did in Hardy. I've just done a fresh install of hardy and everthyings all good again.

Stephen

---

