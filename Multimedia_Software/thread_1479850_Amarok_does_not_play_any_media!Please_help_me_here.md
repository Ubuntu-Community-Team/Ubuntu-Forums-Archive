---
title: "Amarok does not play any media!Please help me here!"
date: 2010-05-11
forum: Multimedia Software
---

### Post by raks1991 on 2010-05-11
I've been a  Ubuntu user for the last 7 days and just switched from Vista.I've been  loving it so far except for this tiny problem.
Amarok does not play media files at all.The pre-installed Rhythmbox with  10.04 works great.In Amarok,it isn't that I don't get sound. It just  won't *play*. If I click  a file, then click *play* it quickly  goes through an amount of  songs and then it tries to play all the  songs in the playlist unsuccessfully.
I'm using Ubuntu 10.04 Lucid Lynx and Amarok 2.3.0(KDE 4.4.2) in a 32  bit system.

---

### Post by NightwishFan on 2010-05-11
Try installing libxine1-ffmpeg. Click here: [Install libxine1-ffmpeg]("apt://libxine1-ffmpeg")
or type this into a terminal:
```
sudo aptitude install libxine1-ffmpeg
```

---

### Post by brallan on 2010-05-11
I always just install 

ubuntu-restricted-extras

after the vanilla install to get mp3 support for vlc and other apps... but for some reason, there is a different package for kde apps like Amarok, which is 

kubuntu-restricted-extras

Once I install this, i have no problems with amarok... 

i suppose that xfce users should install xubuntu-restricted-extras

---

### Post by Spitting Crows on 2010-05-11
I installed the restricted extras and still (in 10.04) can't play audio files.  It sees my library and will load them to now playing but won't actually play the files.  Ideas?

---

### Post by raks1991 on 2010-05-12
> **NightwishFan said:**
> Try installing libxine1-ffmpeg. Click here: [Install libxine1-ffmpeg]("apt://libxine1-ffmpeg")
or type this into a terminal:
```
sudo aptitude install libxine1-ffmpeg
```

I installed this but still can't get it to work.

---

### Post by raks1991 on 2010-05-12
I figured it out.I hadn't installed Ubuntu  restricted extras.That's why Amarok wasn't playing any files.The  restricted extras can be found here.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Just run the installed,it downloads all the files in the package(17) and  after you're done,restart Amarok and it should work just fine.Thanks for helping everyone.Wonderful community.:)
:guitar:

 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=9285017") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=9285017")

---

