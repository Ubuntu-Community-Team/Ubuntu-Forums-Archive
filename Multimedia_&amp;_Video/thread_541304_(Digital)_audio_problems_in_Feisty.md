---
title: "(Digital) audio problems in Feisty"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by G-forze on 2007-09-02
So, my audio is giving me a hard time. I have a MSI K8N Neo Platinum with integrated 7.1 audio, and I am using the digital output which has worked fine in Windows and on my previous Ubuntu installs (after some tweaking). Now it only partially works. The gnome media players like totem and rythmbox work just fine (every single time I boot up), but Amarok and the system sounds (login/out sounds for example) work only every second boot, on average. For instance, yesterday I turned the computer off with working sounds, but today on boot the sounds were missing (but only from Amarok and the system sounds, mind you). Reboot three times and surprise - they are suddenly back.

I've had to adjust Amarok (and VLC, which I don't use anyway) by specifying the output device to hw:0,2 (the digital out) in order to get any sound at all, but to me it seems the problem is not in any of the apps but rather in the way alsa is loaded or something like that. I really don't know that much about the inner workings of the Ubuntu sound system.

All other sounds worked just fine by choosing the right device in System -> Preferences -> Sound and have given me no trouble since.

Does this sound familiar to anyone? I would very much appreciate a solution.

Thanks!
Nicklas

My system specs:
AMD Athlon 64 2800+
MSI K8N Neo Platinum motherboard
1 Gb RAM
ATI Radeon 9800 Pro 256 Mb
Dual boot Ubuntu 7.04 x86 / Win XP 64 on different HDD:s

---

### Post by G-forze on 2007-09-06
So it seems noone has any solution to offer. No surprise, this problem is a mystery to me as well. It's just sad that stupid errors like these spoil the whole nice experience I am having using Ubuntu.

---

### Post by ldegryse on 2007-09-14
Make sure that all users needing access to the Sound Device are members of the audio group (System->Administration->Users and Groups) 
Test different "Sound Servers": Go to System > Preferences > Sound ("Multimedia Systems Selector" in earlier editions of Ubuntu). From there, you can test the different options. In some scenarios several different sound servers may be installed, and only one may work. This is probably the origin of the problem if you cannot play audio with xine or rhythmbox, but you can with xmms or helix/realplayer. 
[B][B][B]If you application sounds works, but your system sounds does not (login, logout, error sounds...) try removing the .asoundrc* files from your own directory (e.g. with 'rm .asoundrc*'). It should make the system sounds work without a reboot. 
[/B][/B][/B]If you can get absolutely no sound and you have an onboard sound chip you can try to disable it in the BIOS. This solves the problem is some cases. 
If you have no sound and you have a regular sound card type "lsmod | grep snd" in the terminal and see if there is more than one card listed. It's possible that you have a motherboard sound chip that is interfering. Add it to the bottom of the blacklist file. For example, sudo nano /etc/modprobe.d/blacklist then add "blacklist snd_via82xx" to the bottom. 


Found the answer here. 
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

Hope it will help. It did for me (bold part)

Regards

---

