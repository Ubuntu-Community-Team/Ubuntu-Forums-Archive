---
title: "players cannot play any video file"
date: 2011-10-31
forum: Multimedia Software
---

### Post by CHAUDHRY07 on 2011-10-31
hello guys
i have recently upgraded to ubuntu 11.10 from 11.04.now i cant watch any video file on it i have tried various players e.g vlc or mplayer but it cant play,though i can watch any video online.whenever i play a video file i just hear sound no video.

i love ubuntu but i want to watch movies too if any of you can help i ll be thankful.

---

### Post by papibe on 2011-10-31
What is you graphic card?
Are you using any proprietary driver?

Could you post the mplayer log while trying to play a video (one that used to work)?

Regards.

---

### Post by CHAUDHRY07 on 2011-11-01
i dont use any 3d card....i have just a built in intel VGA chip(64 MB).and sorry i am a newbee can you tell me how to get that log thing opened.

thanks for your kind reply
regards

---

### Post by little_penguin on 2011-11-01
Try installing ubuntu-restricted-extras and see if it helps:
 
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by CHAUDHRY07 on 2011-11-05
yes i have installed ubuntu restricted extras but of no help....i tried to play with smplayer and it just shows a blue screen and i can hear audio only.Before 11.10 i had 11.04 and with that i had no problem.
i will be thankful if any one can solve my problem.


regards

---

### Post by beew on 2011-11-05
If you could watch videos before but not after the upgrade chances are you have a bad upgrade. In that case you should do a clean install. There is no point trouble shooting a blotched upgrade because even if one issue is resolved other things may still be broken and they will surface later as hard to diagnosed problems. In any case I think a clean install is always preferable because it is so much faster and has a lot less issues.

But whether upgrade or clean install, you should have at least tested with a live usb to make sure major things work with the new release. Now I suggest before you do another clean install again you should test with a live usb to make sure that 11.10 actually works with your hardware.

---

### Post by CHAUDHRY07 on 2011-11-05
i respect your advice.at the moment i am in no position for a clean install please any solution.
regards

---

### Post by beew on 2011-11-05
Well can you at least test with a live usb to see if it is a problem with 11.10 itself so that you can eliminate upgrade as a cause?

---

### Post by CHAUDHRY07 on 2011-11-05
pardon me but i dont have a usb right now.otherwise i could have done that without asking for solution.

---

### Post by papibe on 2011-11-05
You can try, at your own risk, this ppa:
```
ppa:ubuntu-x-swat/x-updates
```
I haven't tried myself, but it has been suggested to people with video problems.

Please visit their page [here]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter="), and do as much as research as possible before going this route.

If that doesn't work, I would follow beew's advice and do a clean install.

Regards.

---

### Post by CHAUDHRY07 on 2011-11-06
i have got some updates on issue....
i use gnome 3 classic on 11.10 yesterday just by the way i started unity 2d and all the players were playing video but as i opened other apps with vlc and memory crossed 50% again there was black screen with audio.and yea it happens some time in gnome too that some how luckily it plays some thing but as soon as other apps are opened no video.
another issue is that whenever my ram usage crosses 50% it gets slows even it is at 51% or 52%.every thing moves slowly in it.
perhaps now you people have a wider view.


regards

---

### Post by little_penguin on 2011-11-06
> **CHAUDHRY07 said:**
> i have got some updates on issue....
i use gnome 3 classic on 11.10 yesterday just by the way i started unity 2d and all the players were playing video but as i opened other apps with vlc and memory crossed 50% again there was black screen with audio.and yea it happens some time in gnome too that some how luckily it plays some thing but as soon as other apps are opened no video.
another issue is that whenever my ram usage crosses 50% it gets slows even it is at 51% or 52%.every thing moves slowly in it.
perhaps now you people have a wider view.

Could you tell us a bit more about your hardware - Is it older equipment? Is this 64mb of onboard video memory on a desktop, laptop or a netbook and if so what kind of CPU processor and how much RAM do you have? All these things can affect performance. Sounds like your system is choking, esp. on graphics/video-intensive tasks, esp. under Ubuntu 11.10, which may possibly have higher hardware requirements than 11.04 did. Your video chip will not be able to handle a 3D desktop environment properly so Unity 2D might be your best bet because compiz on which the default Unity (3D) or Gnome 3 are based is probably causing problems for your hardware; it needs a dedicated 3D graphics card. I was unable to run it on my netbook, for example.

---

### Post by CHAUDHRY07 on 2011-11-06
yeah i m using desktop.....with 64 Mb onboard video memory,512 Mb ram and 2.4 Ghz intel p-iv processor and i am using gnome classic version not shell....does classic version also require compiz i dont think it uses any 3d effects....if my system is choking can you give me any tip how to tweak the programs causing trouble or should i switch completely to xubuntu or unity 2d?

regards

---

### Post by little_penguin on 2011-11-06
> **CHAUDHRY07 said:**
> yeah i m using desktop.....with 64 Mb onboard video memory,512 Mb ram and 2.4 Ghz intel p-iv processor and i am using gnome classic version not shell....does classic version also require compiz i dont think it uses any 3d effects....if my system is choking can you give me any tip how to tweak the programs causing trouble or should i switch completely to xubuntu or unity 2d?

Yes I think you should try installing the desktop environments Xubuntu, Lubuntu (LXDE) or Unity 2D, and see if they give your 64mb onboard graphics chip more "breathing room".

---

### Post by CHAUDHRY07 on 2011-11-06
i am operating from unity now but it dont works so whats my next choice?and should i make a complete switch or what please guide me up.

regards

---

### Post by little_penguin on 2011-11-06
> **CHAUDHRY07 said:**
> i am operating from unity now but it dont works so whats my next choice?and should i make a complete switch or what please guide me up.

Your next step is to try Lubuntu and Xubuntu desktop environments while you're still in 11.10. You do this by entering this in a terminal:

```
sudo apt-get install xubuntu-desktop lubuntu-desktop
```Once they have installed, log out so that you are back at the login screen. There should now be lubuntu and xubuntu as session choices at the bottom of the screen. Try them both out and see if it solves the video problem.

---

### Post by CHAUDHRY07 on 2011-11-08
i tried to make clean install of xubuntu using unetbootin and booting from harddisk.all the steps went well but just after partition management it gave error
cannot unmount following partitions
/cd rom.
and i am not using cdrom to boot in.....any help

---

### Post by little_penguin on 2011-11-08
I can't really help you with that but read the following threads and see if they help:

[http://ubuntuforums.org/showthread.php?t=1237617](http://ubuntuforums.org/showthread.php?t=1237617)

[http://ubuntuforums.org/showthread.php?t=1237721&highlight=the+installer+needs+to+commit+changes](http://ubuntuforums.org/showthread.php?t=1237721&highlight=the+installer+needs+to+commit+changes)

Otherwise, you might want to open a separate thread as the current problem is with installation rather than video playback.

---

### Post by CHAUDHRY07 on 2011-11-19
atlast i have found a work around for the problem i faced.
before starting ubuntu installer just run command "sudo umount -l -r -f /cdrom"  and now the most important part type the next command "sudo mount /dev/sda1  /cdrom" in terminal but dont press enter.when you have selected partition for installation then click  install now and run this command which is already written but make it fast.if it is not fast then ubiquity will  crash.it will surely work if you are booting from harddrive(using harddrive as iso mounted device) using  unetbootin and facing cdrom unmount error.

thanks for your kind help.and yeah i have reinstalled ubuntu 11.10 now i will  migrate to xubuntu found a workaround for that on pshycho cat website.i  was directed their by xubuntu official site.then i ll again test my video on both though ubuntu looks better than before.

regards
 		                   		  		  		  		  		  	   	 		 
	 	 	 		  		 			 			[URL="http://ubuntuforums.org/editpost.php?do=editpost&p=11471720"]
[/URL]

---

### Post by CHAUDHRY07 on 2011-11-21
after i installed ubuntu 11.10 from scratch it was better than before(faster) but video problems are still there.i migrated to xubuntu but of no use and that looked even slower than ubuntu running in unity.some one suggested me to install xubuntu from scratch too and then try it.now i am going to install xubuntu on my pc.can any of you guys predict any thing about my problem from my experiences shared here.i mean isit my pc or 11.10 is not supporting my integrated 64 mb graphics chip.i cannot understand any thing.i mean every thing on 11.04(unity 2d) was working fine even if it was installed with wubi and now its crashing video.
please help me i am getting hopeless and yet i dont have money to upgrade my system or to pay for a genuine window.

regards

---

### Post by CHAUDHRY07 on 2011-11-21
problem is still there.i noticed this much
i have p-iv and 512 MB ram and a 64MB integrated video.i installed xubuntu 11.10 on my pc dual booting with xp.when no process is open my sytem rests at following cpu 4% ram 25% and swap 1%.but with chrome open it rests at 24% ram 40% and swap 5% but the system still gets slow(even if ubunu software center is open) and it donot play any video only audio.its not just with chrome if any normal application opened it starts....like synaptic or firefoxx or chrome :(

---

### Post by CHAUDHRY07 on 2011-11-23
i dont know just got it figured out nbow it has started playing videos but quality is not up to the mark.any tips on how to?

---

### Post by CHAUDHRY07 on 2011-11-30
i dont know its just working now perfectly with vlc.but not with mplayer or sm or parole.....but who cares coz i love vlc :P so its solved now.

---

