---
title: "Yahoo video issues"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by new2linux411 on 2007-10-21
I'm having some minor issues with the quality of video playback when watching music videos on Yahoo Music. The sound and video are there, but the picture is choppy and not smooth whatsoever. I would almost say it seems like its lagging. Am I the only one who is having this issue? I seem to recall that I tried another distro and it acted the same way. I'm using dapper on my laptop and edgy on my desktop. Same results on both machines. I've tried changing the connection speed that they offer in a configuration menu, but still no luck. Any ideas? This happens on both wired and wireless connections. Thanks in advance for any help or feedback.

---

### Post by SeePU on 2007-10-21
I will suggest something to you but don't take my word for it.  I'm no expert. 

My guess is that it may be video drivers.  What video card do you use and which drivers do you have installed?  

What happens if you play youtube videos?  Same thing?  

If you have both sound and video, it would suggest to me you have the plugins and/or codecs installed but lack the proper video drivers.   But, perhaps someone else with more experience with those issues can confirm if my guess is even close to being accurate or applicable.

These threads might help?:

[http://ubuntuforums.org/showthread.php?t=513120&highlight=choppy+video](http://ubuntuforums.org/showthread.php?t=513120&highlight=choppy+video)

[http://ubuntuforums.org/showthread.php?t=458090&highlight=choppy+video](http://ubuntuforums.org/showthread.php?t=458090&highlight=choppy+video)

I found them by entering 'choppy video' in the search box.

---

### Post by new2linux411 on 2007-10-21
Well, on this machine(laptop) it uses:

0000:01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05), not sure which driver, it was configured automatically. My laptop is a IBM Thinkpad T23.

On the desktop machine it is an Nvidia geforce fx 5200, that one is using the nvidia-glx driver.

I don't know what the deal is, it does the same thing on every machine I test with. Most other videos, including You Tube, play a lot better(not perfect) than Yahoo Music. I used Automatix to install all my codecs and plugins, which is better than what I was able to do on my own. I just cant get those Yahoo videos to play smoothly. If I recall correctly, Xandros and Mandriva were the other distros I tried which both did the same thing. Have you personally tried to watch any of your favorite music videos with Yahoo Music? If not, watch a few and get back to me so I can see what your experience was. Thanks for you feedback.

---

### Post by SeePU on 2007-10-22
I'm looking for a laptop and probably a Thinkpad (maybe even same model as yours!) so I hope you can solve the issue!

I just tried it on my desktop.   It started out choppy like it was lagging so I went to the 'Video Quality' link and got the preferences screen and chose the top connection speed.   Now, the video quality is fine and smooth.   There is the odd delay but I'm sure that's related to the connection. 

That might not help you but I think it is probably due to your graphics drivers.  These are especially problematic in Linux (imho!) in laptops.  

I suggest trying to fix the problem on the desktop first since you have an Nvidia card in there.  

I am guessing you will have to configure the Thinkpad's drivers manually.   I'm not sure, though.  You might google your Thinkpad and the 'S3 Inc. SuperSavage IX/C SDR' to see  what comes up.  

I have not optimized my video drivers yet.   The video quality when using media players on my Kubuntu partition is not as good as the video quality in Windows's VLC.  So, you should be able to get Yahoo videos working with smooth video quality on your desktop even if you need to go to a bit of trouble to do the same on the laptop.  I'm using an ATI video card and Linux usually has better support with Nvidia cards.

---

