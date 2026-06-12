---
title: "Audio Drivers,Ubuntu Desktop Issue"
date: 2010-03-27
forum: Multimedia Software
---

### Post by wbee on 2010-03-27
Hello,

My sound stopped working. 

The next logical thing for me to try is to uninstall and reinstall all the sound drivers.

*But the shell warned me it would remove my Gnome desktop.

Please explain this next to me.

If I take out the old drivers,will it not take effect before I reboot? By that logic will it allow me to reinstall the sound drivers AND the gnome desktop BEFORE I reboot the whole thing?

Or will it take out the entire desktop with the drivers?

Will it provide me the opportunity to load 

```
sudo apt-get install gdm ubuntu-desktop
```

at some point and if so,where and when?

--------

Thank you.

((Edit.......Could I accomplish the same thing by uninstalling and reinstalling the gnome desktop before I reboot? Is there a command to do that in one step?))

---

### Post by teejmya on 2010-03-27
Could you let us know what method you used to uninstall/reinstall your sound drivers?
Maybe how it warned you that it would tamper with gdm?
Or even your sound card info?

---

### Post by wbee on 2010-03-27
teejmya.

The sound drivers installed automatically when I loaded the operating system.

I did not reinstall the drivers. I started to,and the shell warned me it would remove gdm,gnome desktop,and kde desktop. It asked me for a yes or no to continue,and I gave it a no.

Allow me to over answer your question with this summary:

--When I booted on this morning,the sound was not working,having worked perfectly last night when I booted off.

--When I rebooted,I got the annoying "pop" I always get from the speakers,so I know the speakers are working. But I did not get the drum sound I usually get when I boot up Ubuntu.

--Next I tried different souces,U Tube,a compact disk,and an FM signal,to confirm that none of those were working.

--The read from the speaker preferences were correct;nothing was muted.

--I use an after market sound card.(More about that in a moment). So I checked the bios and something had caused the bios to default to the onboard AC selection. I changed it to disable it,so that the aftermarket card would work. Still no sound,I confirmed that the bios was still set correctly for the aftermarket card--the idential setting when it was working.

--I ran System>Administration>System testing for "Audio" and got no test sound. So,I attempted to submit the report to Launchpad,which would not connect,though I was able to get into launchpad with my e mail and password.

--Next,I went to one of the trouble shooting stickies above and did these steps,with these readouts:

--Here is the output from ```
aplay -l
```:

```
wbee@wbee-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
wbee@wbee-desktop:~$ 


```

If memory serves me correctly,the last time I ran that,it only showed the card once,so I think something confused the issue,but I can't say that certainly.

--"alsamixer yielded everything green,no mutes,all the levels correct,except for IEC 958 with nothing at all....All the other CE 958s,analog and digital are correct.

--So,the next step was ```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

It yielded this result:```
wbee@wbee-desktop:~$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  alsa-base* alsa-utils* kubuntu-desktop* linux-sound-base* ubuntu-desktop*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 2,712kB disk space will be freed.
Do you want to continue [Y/n]? 


```

I said "n",left the terminal,and posted my question.

--------

The information I have says the command to install the drivers is ```
sudo apt-get install linux-sound-base alsa-base alsa-utils


```

and the code to reinstall what I would have taken out is ```
sudo apt-get install gdm ubuntu-desktop
```

------My original question stands. Can I uninstall,reinstall,put back the desktop,BEFORE I reboot,or will I have to go into a disk operating system to reinstall the desktop,and if so,how.?

---

### Post by wbee on 2010-03-28
bump

---

