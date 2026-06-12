---
title: "No sound in ubuntu 8.10"
date: 2009-04-08
forum: Multimedia Software
---

### Post by Kishcage on 2009-04-08
Hi
        I am very much new to linux environment and i have been having trouble in getting sound properly in ubuntu. I installed the new ubuntu 8.10 3 days ago and still looking at the forums for finding out, how to get sounds working in my system. I am having HP pavilion Dv4 1041-TX. I have installed gstream patch and plugins and still couldn't able to get the sound working properly although i can hear beeping sound continuously. I have installed 32 bit Ubuntu OS. I am really tired in searching for the answer. Can anyone please help me?????

---

### Post by Jakey_TheSnake on 2009-04-08
What happens when you double-click the volume icon on your panel (taskbar)? 

If a volume control appears, make sure the PCM slider is high up. 

If you're trying to play .mp3's, you'll need to run this in a terminal first: 

```
sudo apt-get install lame
```

OR I believe

```
sudo apt-get install ubuntu-restricted-extras
```

would do it too.

---

### Post by Kishcage on 2009-04-08
Hi Jakey

              Thanks for such a quick reply. As you suggested in the last message that to install the restricted package or to install lame package, i did so and got them installed successfully but i am still getting the same problem which is only the beep sound. And i also checked the PCM level in sound properties and they were on high. I restarted my system then to take changes but it still resulted in same. 

              Now when i open any mp3 file using totem, it gives a new error message as "Could not get/set settings from/on resource". I am very much stuck now. i have installed all the updates for linux and everything is working well except the sound. And also i can play movies but cant hear anything other than beep sound. I was able to play when i installed all the gstream package but no sound again. And now its giving the above error which i cant figure it out.

Please help.

---

### Post by Kishcage on 2009-04-09
Hi Jakey

I have managed to play both mp3 and video files without any problem but its the sound i am not able to get it. All i can hear is only a beep sounds continuously. I have tried these links but could not able to manage to get sounds properly. I am using HDA Intel on board sound. I tried removing pulse audio and could managed to play and i can see them playing but with only a beep sound. Can u please help?

Thanks

---

### Post by reahjw6 on 2009-04-09
Have you checked preferences>sound to see what the settings are there.

---

### Post by markbuntu on 2009-04-09
This sort of problem can be very hardware specific. There is some listings for HP dv4 here along with directions. This works for a lot of dv4s but not all. There are also a couple of running threads on the dv4 here in this forum.

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

