---
title: "Volume on top right does not work after running/configuring mumble"
date: 2023-02-07
forum: Multimedia Software
---

### Post by Hankbonk on 2023-02-07
[SIZE=2][/SIZE]Hello to all of you       :guitar:.

I am running Ubuntu 20.04.5 LTS with the Gnome Desktop environment on an older HP Compaq-Pro-4300 64-bit.

I am one of the very few people on the globe that have encountered and embraced the game Linux Air Combat,
the first Combat Flight Simulator for Linux, where you can (dog-)fight and fly with WWII planes .

see [https://askmisterwizard.com/2019/LinuxAirCombat/LinuxAirCombat.htm](https://askmisterwizard.com/2019/LinuxAirCombat/LinuxAirCombat.htm)

The voice communication between players is handled by Mumble, and there I have a big problem with :

After configuring Mumble to work with input and output both set to 'JACK' all Pulseaudio output stops .
So I changed the input and output to 'Pulseaudio', which worked for the Linux Air Combat game BUT :

Now my volume handle on the top right does NOT have any effect anymore on all sound output !
Then I got some help from one of the LAC players : I installed Pulsemixer to see which output DOES change by the speaker button .

Here is what I discovered :

screenshot BEFORE  increasing speaker volume :


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291720&stc=1[/IMG]


screenshot AFTER increasing speaker volume :


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291721&stc=1[/IMG]


In these two screenshots you can see that the volume button on the top right does NOT work correct :

In the Pulsemixer window the value of *PulseEffects(mic) is showing a longer green line !

Normally it should be the top 2 lines that should be effected by the volume button : 

The line called

```
Built-in Audio Analog Stereo
```


Can anyone explain how that is possible ?

Thanks in advance to read and post your thoughts on this .

---

