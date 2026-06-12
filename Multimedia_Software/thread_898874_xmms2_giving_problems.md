---
title: "xmms2 giving problems"
date: 2008-08-23
forum: Multimedia Software
---

### Post by Wickd on 2008-08-23
Hi there

I am relatively new to Ubuntu and have installed it about a week ago. I am struggling to get the right music player and have tried songbird, but struggled to get it installed, because there is not enough disk space on my root drive.

So I switched to the xmms2tray app. I read about it in one of the forums. I installed it completely with alot of plugins and soforth

basically I installed every component of the player. I now get a error message telling me that it cannot connect to the daemon server?

Anybody have any ideas?

---

### Post by kthxbai2u on 2009-03-06
well, if your opening it through the application menu it should ask to start the service... Does it? If it does just click "yes"

I have found the basics on how to use it.

XMMS2 is controlled through console. You may think this sucks, but it actually has its benifits!

1: You can have people code multiple GUI's for it, meaning more client applications

2: You can control it remotley. For example, I have my desktop computer inside my house, and the speakers are there. I am too lazy to take the speakers out to the garage when i go for a smoke. I am also too lazy to come inside to change the songs. So with XMMS2, I also installed an SSH server. Then I took my laptop outside with me, opened the window to my room, and connected to my network. My laptop is windows, so I just ran putty to connect, and now I can change my music from putty on my laptop! HOW CONVENIENT! This has many other useful applications, for example, If you have a swimming pool and a sound system. You just set up a music server, and use a laptop with wireless to chill at the patio and control music!

Here are the shell commads (once you get the server service started)

xmms2 <command> <args>

Command:

list - no args - lists all songs in queue
clear - no args - clears the list
add <path to file> - adds the file to the queue
radd <path to dir> - adds recursivly the specified folder
play - no args - plays the queue
pause - no args - pauses playback
stop - no args - stops playback
shuffle - no args - shuffles the queue
next - no args - next track
prev - no args - previous track
jump <id> - jumps to the id of the song (get it from "list")

help - for anything i didnt mention :)

At first even I too was skeptical. But  now I FREAKIN LOVE IT! I do alot of drinking and smoking in the garage haha

[EDIt] Oops! dead post lol... [/EDIT]

---

