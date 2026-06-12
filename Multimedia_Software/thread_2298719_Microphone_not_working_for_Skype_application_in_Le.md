---
title: "Microphone not working for Skype application in Lenovo G40-80"
date: 2015-10-13
forum: Multimedia Software
---

### Post by Nilanjan_Sircar on 2015-10-13
Hi, I recently bought a Lenovo G40-80. I have installed Ubuntu 14.04 LTS. Initially the internal microphone was not working (nothing was muted).
Then I followed the steps in [http://ubuntuforums.org/showthread.php?t=2270010](http://ubuntuforums.org/showthread.php?t=2270010) by kuba6.
> [COLOR=#000000][INDENT]Type in Terminal
Sudo apt-get install pavucontrol
pavucontrol
In opened window go to input devices, click lock icon and then move left-right sliders to different positions. I put 45% and 60%.
It seams that stereo channels cancel each other[/INDENT]


[/COLOR]
[COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]

Now the microphone is working. But I am facing two problem:
1) I am trying to use Skype, the microphone seem to catch faint sound, which cannot be increased.
2)Once I close pavucontrol and open again, the setting seems to be reverted to original setting, and the microphone stops working.

Can anyone help to resolve this issues.

---

### Post by Nilanjan_Sircar on 2015-10-13
I have been  able to solve both of the issues. I have to switch off the option in Skype that allows Skype to alter mixer levels. You have unmark this option in Sound Devices setting of Skype.

---

