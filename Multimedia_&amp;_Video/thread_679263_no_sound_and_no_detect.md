---
title: "no sound and no detect"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by niteklub79 on 2008-01-26
Hello,

I installed 7.10 on my hp pavilion 7950 with no problems however I cannot access sound functions and a dialog box pops up saying there are no g streamer plugins

can anyone help?

---

### Post by Metaljaz on 2008-01-26
To install every plugin of Gstreamer do this in Terminal

    sudo apt-get install gstreamer*

---

### Post by niteklub79 on 2008-01-26
I attempted terminal however it came up that it "couldn't find package" are there any other fixes?

---

### Post by niteklub79 on 2008-01-26
I attemted terminal and it came up that I have all of my gstreamer plugins installed... any other suggestions?

---

### Post by niteklub79 on 2008-01-27
how do I configure my sound card...etc. so I can activate sound

---

### Post by Metaljaz on 2008-01-27
Lets see what sound card you are using and go from there:
From the terminal type: 
lscpi

Look for multimedia audio controller. Should look something like this: (Post the results)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) A

Right click on the volume button in the top right hand corner. Open volume control and make sure that PCM is not muted.  Mute PC speaker and Line in to start with.
Then again right click on the volume control button and select preferences. try selecting alsa mixer and then scroll down to PCM. Give that a try.

---

### Post by caseyg on 2008-01-27
Your sound card config is located in /proc/asound 

You can also type #sudo asoundconf list
this will show what card is active.

You should be able to go to your <System>  <Preferences>  <Default Sound Card> from the tool bar. Good Luck

---

### Post by Metaljaz on 2008-01-27
if all else fails try these troubleshooting threads/wiki:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by fridgemagnet on 2008-01-27
> **Metaljaz said:**
> Right click on the volume button in the top right hand corner. Open volume control and make sure that PCM is not muted.  Mute PC speaker and Line in to start with.
Then again right click on the volume control button and select preferences. try selecting alsa mixer and then scroll down to PCM. Give that a try.

I've been struggling to get ALSA to work with my Shuttle SN25P card for *ages*, and this has just let me play sound - at least, for the moment, though I expect it to go back to silence when I next boot, knowing my luck.

---

### Post by niteklub79 on 2008-01-27
after attempting a reboot , i cannot access my system bios - FOR THE RECORD: I have a very limited knowledge of computers and this operating system in general.

I need alot of tech support help

---

### Post by Metaljaz on 2008-01-27
We are here to help you so don't get discouraged. I knew nothing about Ubuntu until I installed it and started reading about it. The more I read the more I learn. I have learned most by having some hardware conflicts and working them out with the help of this forum. I have a very stable Dell XPS running nothing but Ubuntu.

Tell us what you have done to your installed version of Ubuntu since you started this thread so that we can maybe figure out whats going wrong.Have you installed any other programs? if so did you use synaptic or add/remove? Why did you have to do a reboot and how are you trying to access your system bios?

---

