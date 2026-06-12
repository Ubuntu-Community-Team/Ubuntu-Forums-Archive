---
title: "glc-play won't play - &quot;invalid argument&quot; error"
date: 2012-07-22
forum: Multimedia Software
---

### Post by mtdewd on 2012-07-22
I'm running Ubuntu 12.04.

I want to capture some video from a game. From what I found, glc is the way to go, and all the instructions and tutorials I've read are pretty much the same. Real simple.

So, I installed the latest version, and tried it on Nexuiz to keep things simple. 

glc-capture /usr/games/nexuiz

I ran that command, started the game, hit SHIFT+F8, played for a minute or two, hit SHIFT+F8, and exited the game. Got a file called "darkplaces-21827-0.glc" that looks to be over 800MB in size! I just want to see if the video works, so I typed in:

glc-play darkplaces-21827-0.glc

This is the entirety of the output I got:

[   0.49s glc_thread error ] Invalid argument (22)
[   0.49s        rgb error ] Invalid argument (22)
[   0.49s glc_thread error ] Invalid argument (22)
[   0.49s glc_thread error ] Invalid argument (22)
[   0.49s      scale error ] Invalid argument (22)
[   0.50s      color error ] Invalid argument (22)

I tried this same procedure with a windows game run through PlayOnLinux, and got the exact same results - large glc file and error in glc-play. I also tried using PlayOnLinux's "Capture" plugin (which uses glc), and got absolutely no response from that whatsoever - i.e. no capture file that I could find. 

I can't seem to get this simple process to work! Any ideas? Suggestions? Help??

---

### Post by Paddy Landau on 2012-07-24
I have not tried glc; I do not find it in the repositories.

I have found [Record My Desktop]("apt:gtk-recordmydesktop") to work well. I suggest you try it. You may need to experiment with the performance settings, depending on your hardware.

You could also try [Istanbul Desktop Session Recorder]("apt:istanbul"), but I have not tested it.

---

