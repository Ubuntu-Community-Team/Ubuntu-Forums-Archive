---
title: "Need help with display issue!!!"
date: 2008-02-20
forum: Multimedia &amp; Video
---

### Post by Kamicowzi on 2008-02-20
Hello

I had installed Ubuntu on my Asus G1S laptop and when I first installed it everything was fine and I could set my desktop res to 1680x1050 (my monitors native resolution). Then I downloaded the restricted drivers for nvidia and a large batch of updates. When I restarted my pc, I was greeted with the login screen looking like a totally unreadable rainbow. I tried to reboot and it did the same thing. i then reset my xconfig thingie through the recovery and ran Envy and got the same results. Ubuntu would not let me go above 800x600 res or pick my 8600MGT card. I have since unstalled Ubuntu. I really enjoyed it but it was driving me crazy that I could not get my screen o the res I wanted or activate the desktop effects. I really hope someone can give me some help with this because I really want to run Ubuntu, but that problem drove me crazy enough to uninstall it.

Thanks

---

### Post by jonathanmotes on 2008-02-20
There is a line near the top in your xorg.conf file that has a command to you can run in a terminal to reconfigure it. This has almost always fixed my problems. I'm not on Linux at the moment, but I think you can access that file using this command```
sudo gedit /ect/X11/xorg.conf
```

Or, if your running in recovery mode, you need to use a command line editor, like this:
```
sudo nano /ect/X11/xorg.conf
```
Before running that command or following any of the steps below, you may want to preserve a backup of your xorg.conf file:```
sudo cp /ect/X11/xorg.conf /ect/X11/xorg.conf.backup
```

If that doesn't work, the restricted nvidia driver comes with a pretty nice settings tool that usually allows high resolution settings that your screen resolution settings won't include. It also allows dual screen layout configurations. You can run it with this command in a terminal:```
sudo nvidia-settings
```

If anyone asks you, it is important to run nvidia-settings using sudo (as the command above shows) so that nvidia-settings has permissions to reconfigure your xorg.conf file.

Remember you must have the restricted nvidia driver installed before you can run the settings tool.

Hope this helps!

---

