---
title: "Mysterious Cinelerra Startup Message"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by AdemoS on 2008-01-20
Ubuntu 7.10 64 bit
Cinelerra [Current Version from Community-Version Repo]
CPU: Intel Core 2 Quad 2.4 GHZ
VPU: Geforce 8800 GTX
Sound: Creative Sound Blaster Audigy 4 Pro
RAM: 8 GB

When starting Cinelerra, I always get this error message:
[img]http://img254.imageshack.us/img254/5933/screenshotcinelerraerrofj4.png[/img]

If I follow the directions (don't worry, I use gksudo) then when restarting the program, the error is gone.

However, after rebooting, the error returns. So my changes aren't being saved.




Before I fix the save-settings issue though, I was wondering ***what this error means***

Laymen's terms would be helpful.



Once I understand what it's speaking of, any help saving my settings in this area, would be appreciated. 

Thanks for reading.

---

### Post by disturbed1 on 2008-01-20
Maximum size of shared memory segment (bytes).

If you make a permenent change, then any program would have the ability to use 2048 MB of shared memory.

^^ the value 0x7fffffff is equal to 2048MB or [SIZE=-1]2147483647 bytes.

You can do a
```
cat /proc/sys/kernel/shmmax
``` to get the value in bytes (divide by 1024, then 1024 again to get MB)

0x2000000 is awfully low.(32mb)
[/SIZE]

---

### Post by kelvin spratt on 2008-01-20
Cinelerra started giving the error message regarding shmmax. This should be the amount of memory shared between process by the kernel. After some work with google I found an easy solution - in the terminal I gave:

    sudo gedit /etc/sysctl.conf

and at the end of this file I added the line

    kernel/shmmax=0x7fffffff

I saved the file and I made

    sudo sysctl -p

Do this and it will then run fine next time you reboot
hope it helps

---

### Post by AdemoS on 2008-01-21
Wow, I heard stories of how helpful the Ubuntu Forums are, but to get two relevant, easy-to-follow responses, in that short a period of time is awesome.

Thanks a lot guys, when I have a chance to try those soultions out I'll post my results.

---

### Post by AdemoS on 2008-01-27
Worked great!

Thanks for the help guys.


One more thing though,

having 8 GB of ram, I could definitely utilize more than 2 GB of RAM.


Would you recommend increasing my limit to 4 GB? Or not?

And if you do, what value should I input?

Thanks again for the continued help.

---

### Post by AdemoS on 2008-03-28
Months later, no response.

So I'm bumping the thread.

---

### Post by disturbed1 on 2008-03-28
Did you at least try it. Or have you honestly sat there for months wondering if it would work :D
[http://www.google.com/search?source=ig&hl=en&rlz=&q=8+gig+ram+set+shmmax&btnG=Google+Search](http://www.google.com/search?source=ig&hl=en&rlz=&q=8+gig+ram+set+shmmax&btnG=Google+Search)
[http://ps-ax.com/shared-mem.html](http://ps-ax.com/shared-mem.html)

---

### Post by AdemoS on 2008-03-28
The second one. :P

I already screwed up Gnome-Panel to the point of losing use of my Volume Manager and Trash. (after trying many ideas from #gnome devs, I decided to reinstall Ubuntu in the future, and try out Ubuntu Studio when I do)

And Splash (which won't even work on the LiveCD) freezes my boot if I try to fix it.




So yes, I like to ask if it's safe before I try things.

Reading through your Google search, and the direct link though, I'm still not sure if it's the best idea.

They seem to say to use 50% of your max RAM, so that would 4 GB for me.


But they didn't mention if it will cause any side effects or not, such as lowering the life of the RAM.


If anyone has advice on Shmmax and Shmall adjustments, let me know.

---

### Post by disturbed1 on 2008-03-28
I'm glad you took my previous post as it was meant :D :D

In all honesty, it seems like you are worried about trying it out. Be smart about it. Try going from 2gig to 3gig, then 3.5...4......4.5.....5 and so on.

You'll have to know exactly what shmmax does. This is the setting, that sets the maxium amount of shared resources any single app can use. It isn't as simple as picking a universal number and going with it. This setting depends on your kernel, your hardware, your applications, and how you use your applications.

Do you think any application you **constantly** use will require more than 2gig memory to work as expected. If the answer is yes, then up the shmmax. If it's "I don't know" then you shouldn't touch the settings. You can use top, htop, free, and even the system monitor to see how much memory a program is using.

If you don't have a 64bit kernel, the settings above 2gig are useless. Yes Ubuntu's 32bit kernel does have the patches in place for *"big mem"* to load and use upto 64gig of RAM, it's just ignorant to use the 32bit kernel with more than 3gig ram, because of the limits with 32bit processing and regesters. Can a 32bit kernel address more than 3gig of ram? Yes. Can it use it? Sort of, but only with ram interaction thrashing. 

Short answer if you don't want to do the research -

Greater than 3gig ram = 64bit kernel.
shmmax = 1/2 total ram.

Understand that if there happens to be a memory leak in a program it will consume upto the shmmax. If you have Firefox, or flash, or java, or wine, you have a memory leak.

Turning on your computer lowers the life of the RAM :D

Seriously, start out with a small number. Test it out. Up the number more, test some more. After upping the shmmax, if you notice no difference, then there is no need to fix what isn't broke.

With Cinelerra, if you are only doing SD, a shmmax of 2gig should be more than enough. For HD, dual Opto's and 16gig ram should get you by. If you're **_serious_** about editing footage on Linux, there are vendors that will build and set up the system for you. [http://www.linuxmovies.org/](http://www.linuxmovies.org/) has some good info.

---

