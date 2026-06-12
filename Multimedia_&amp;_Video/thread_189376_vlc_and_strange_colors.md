---
title: "vlc and strange colors"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by tonny on 2006-06-05
Hi

I have som problems playing video in vlc. When playing high definition .ts mpeg2 video files and other mpeg2 video clips, the color somehow gets distorted. It looks as the color is displaced compared to the contrasts (black / white image).

This does not ocure in mplayer, but mplayer cannot handle .ts files and plays theese in a framerate of 3 - 4 frames per second and eventualle crashes with some erroe saying "to many packets in videoframe" or something like that.

please take a look at the attached screenshot.

I run the newest nvidia driver, and uses the xgl server and compiz composite manager. Keep in mind vlc plays divx / xvid clips fine without theese color distortions.

---

### Post by tonny on 2006-06-10
is there anybody outhere with some reflections on this issue ?

---

### Post by E-Jey on 2006-07-06
*kick! 

I have the same problem. I guess the problem is a combination of libmpeg2 and Xgl/compiz. I've tried to play it without compiz/xgl running and it don't help :/ Did you already solve it?

---

### Post by nevin on 2006-07-06
i have the same problem.  it's gotta be xgl/compiz i think, but it does it even when i dont have compiz up.  soooo, i dont know... mplayer gets it to where there is no discolor, but i cant get the audio and the video to line up or the video to zoom to fit the window size... if only i could use mplayer better....

---

### Post by E-Jey on 2006-07-06
I tried to play it in my windows XP virtual machine (vmware) and the colors are good! It's lags a little bit but it's better than native under Linux. I have a problem with movies encoded in x264. Under VLCplayer the color are bat. With other players there is lag or no sound. I hate the bad support for movies under linux. Now I have to boot windows to see my movies :/

mayby it's something with the driver ?

---

### Post by nevin on 2006-07-06
yeah, but everything worked fine in 5.10... its only when i "upgraded" to 6.04 that everything started going crappy.  like i said before, mplayer plays it without the video getting messed up, its just the audio that i cant get to line up with the video right.  i dont know what changed, but i wish it would change back... ive tried reinstalling the stuff.  totem used to play everything right, but it has the scan lines (discoloration at the top of the video) too.  so i tried uninstalling it (totem-xine) and i also tried totem-gstream, but that didnt work either... i dont know whats up, but i hope someone can enlighten me as to what's up and if there is a fix.  i just want to watch some movies.

---

### Post by nevin on 2006-07-06
well, wait, i just played an .avi video encoded with xvid and there is no discoloration... but with the divx, i get the discoloration.. im going to try to reinstall the codecs... maybe that will work...

---

### Post by E-Jey on 2006-07-06
I have it only with High definition movies. Mayby it's something with the resolution. The HD movie has a higher resolution than my screen. Let's try to play it on my LCD TV :)

---

### Post by E-Jey on 2006-07-07
I have tried to play it on my LCD tv, but I still have the problems with the colors. I think the problem is with the codecs and not XGL/compiz. If I try to play the .TS files with Totem I get this error: 

Totem cannot play the file. You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

edit: I have tried to update vlc player to version 0.8.5 but that also didn't help

---

### Post by Deus42 on 2006-09-05
I have this problem on two systems when playing XVID, both of which are running XGL and Compiz

One system is running AMD64 with an NVIDIA card(using nvidia drivers), the other is an intel laptop with a ATI firegl (using fglrx drivers) card.

on the ATI card all I did was uncheck the "Deinterlace" option and it was fine, but I have yet to fix the problem on my AMD64 system.

One other thing that I thought was very interesting was that if I disabled the extmod xorg module, it also fixed the problem on the computer with the firegl card.
Edit/Delete Message

---

### Post by Deus42 on 2006-09-07
Ok, try this:

Install Totem-xine

Change the video driver totem uses from auto to opengl (see [http://ubuntuforums.org/showthread.php?t=217064&highlight=totem+opengl](http://ubuntuforums.org/showthread.php?t=217064&highlight=totem+opengl) for istructions) this fixed the entire problem for me.

---

