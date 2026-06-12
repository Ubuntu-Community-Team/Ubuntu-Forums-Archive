---
title: "External monitor having a resolution higher than native."
date: 2010-01-02
forum: Multimedia Software
---

### Post by Jarige on 2010-01-02
I've got a little problem with my 9" netbook. It came preinstalled with Ubuntu (factory install), but I reinstalled it to get a fresh karmic as it was a second hand.
The problem is, whenever I plug in an external monitor, rightclick on the display icon and click "Configure Display Settings..." both monitors go black and nothing responds. Weird thing though, is that sometimes the mouse appears on the second monitor. I need a solution for this, either creating a xorg file (I have no clue on how to do that) or some other solution that works.
My netbook resolution is 1024*600, the external monitor resolution is 1024*768. It should be noted that I had a similar problem on another Ubuntu laptop (NVIDIA drivers), but it had to do with the resolution height. My laptop had 1440*900 and my external monitor needed to have the height lower then 900.
For further information, this is what the system profiler says about my graphics card:
Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller

I hope you guys can help me, as plugging in a netbook to an external monitor (or TV) is not uncommon to me :) I like doing that, even if there's no point in it :P
I hope I gave enough information on this, I'm willing to give more if needed of course :)

Thanks in advantage :D

---

### Post by Jarige on 2010-01-02
I figured out that executing xrandr in the terminal does the same thing as opening the display manager settings. I also found out that if I plugged in the cable (I don't know what kind, but its blue and its not HDMI :P ) before booting it would boot in 800x600 on the netbook display and nothing on the second monitor. At that moment I unplugged the cable, and wanted to change the settings to 1024x600. Then I saw the Detect Monitor button, and thought I could give it a go since it was booting in 800x600 anyway. Plugged in the cable, clicked the button. Black screen. This time I had a mouse that I could move between the monitors, and some green stuff in the topleft side of the netbook screen. Pressing ALT-CTRL-1 or some other number worked this time, although I didn't know any commands to fix this. Reboot without cable showed me the 1024x600 desktop again.

What should I do?

---

### Post by Jarige on 2010-01-02
Apparently, there's no way you can edit the title of the topic.

Ontopic:
I probably need to create an xorg.conf file from scratch. I need help in doing so. What does the default file need to have? What things do I need to change for my specific gpu? (if there's any, it might be build-in the motherboard)

---

### Post by Mr. Matt on 2010-01-02
Hey Jarige,

I just solved my problem ([http://ubuntuforums.org/showthread.php?t=1370648](http://ubuntuforums.org/showthread.php?t=1370648)) with an external monitor displaying low resolution.

It seems you are having a different problem though.  If you start the computer with the external monitor plugged in, do you get a blank screen after logging in?

This guy came up with an interesting solution to make an xorg.conf file - run the LiveCD for Ubuntu 8.04 and he says it will make a full xorg.conf file for you to use.  I didn't need to try this but it might help you:

[http://ubuntuforums.org/showthread.php?t=1320785](http://ubuntuforums.org/showthread.php?t=1320785)

I also found this information helpful:

- [http://ubuntuforums.org/showthread.php?t=1364460](http://ubuntuforums.org/showthread.php?t=1364460)
- [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by Jarige on 2010-01-03
Hey :)

Thanks for your reply, I've seen most of these links already in search for an answer. When you replied, I decided to go for Ubuntu 8.04. I downloaded it, burned it to an USB device (as I don't have a cd drive in my netbook), and booted. It gave me some fatal error, I don't know why. So I'm back using 9.10 again, with an empty xorg.conf file.
I don't know how to create that file, but I'll keep on searching. Your links weren't useless though, its just that they do not apply to my problems. I'm not even able of running xrandr with my external monitor plugged in.
About your question, asking me whether both screens go blank after login with external monitor, they do not. What does happen, is that my netbook resolution will change to 800x600 instead of 1024x600. The external monitor does nothing.

---

### Post by Jarige on 2010-01-03
I have found out that the problems I have are due to a known bug in Karmic:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/438000/](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/438000/)

I partially solved my problem by turning off Compiz, then plugging in the external monitor, and then setting up both monitors. That does mean that Compiz is off, which is a big loss for me, thats why its partially solved.

To turn off Compiz, you'll need to turn on Metacity by executing this:

```
metacity --replace
```

There are alternative ways in turning on Metacity though. You can execute this command by pressing ALT-F2 typing it over and press enter, if you want to now :)

Whenever I try to turn on Compiz after setting up the monitors, both screens go black again, and I need to do a hard reset.

Hope this solves any problems, and I hope you won't miss Compiz :)

This bug will be fixed though. It seems that the problem is Compiz, which cannot handle resolutions higher then 2048x2048 on my videocard.
"The problem is that those tools are not aware that compiz is running (which reduces the hardware limit to 2048x2048), and so try to create the too large frame buffer (which is legal without compiz)."
Compiz will be changed to support higher resolutions though, so there is hope :D

---

