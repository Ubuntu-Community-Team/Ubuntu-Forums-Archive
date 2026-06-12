---
title: "Dvd can't be played in Jaunty"
date: 2009-04-26
forum: Multimedia Software
---

### Post by StarryFlag on 2009-04-26
I've newly installed Jaunty onto my computer. But I can't get the dvd playable. I've installed restricted extra pack, run the CSS script file, I also try VLC instead of the default MoviePlayer, but it just blow up with no trace whatsoever. Using the MoviePlayer, it give a error of permission...

---

### Post by leonardo_neo on 2009-04-26
OK, I am not sure if this is going to help, but you can sure give it a try. Have you installed the medibuntu repository? Go to this link.....

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

From this repository you would like to add the following two codecs

1. libdvdcss2
2. w32codecs

Try this, and see now if you can play DVD?

---

### Post by axel206 on 2009-04-26
Take a look at the DVD playback section of the following guide and you should be fine.

[Ubuntu 9.04 Post Installation Guide](http://www.my-guides.net/en/content/view/158/26/)

---

### Post by jeshasgoodstinky on 2009-04-26
i am having a similar issue.  totem will no longer play any form of video.  

i completed the upgrade over night, and this morning when i went to watch some wake up music vids, they would not play.  so most of my day has been spent uninstalling and reinstalling, applications, codecs, plug ins, and reading posts here at ubuntu forums.  this is my first post because i have yet to find the info i need.   


any help? thanks.

---

### Post by VMC on 2009-04-26
> **StarryFlag said:**
> I've newly installed Jaunty onto my computer. But I can't get the dvd playable. I've installed restricted extra pack, run the CSS script file, I also try VLC instead of the default MoviePlayer, but it just blow up with no trace whatsoever. Using the MoviePlayer, it give a error of permission...
What do you mean by "blows up". If you mean that you tried mplayer and it opens and then quickly closes, then it could be your video driver. If you have an Intel video chip, it surely is your video driver. 

type form a Terminal this and post output:

```
lspci | grep VGA
```

---

### Post by Kevbert on 2009-04-26
I had a similar problem to this. I found that the standard version of totem would not play DVDs if they had a fancy front-end menu. totem-xine with the libxine1 plug-in solved this and can be found via Synaptic.

---

### Post by jeshasgoodstinky on 2009-04-26
fathead@fathead-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
fathead@fathead-laptop:~$ 
fathead@fathead-laptop:~$ 


i hope what he means is crashes.... im not sure if the vid card is  having issues.  im running dual mon.  on at 1280x1024 and the other 1024x600  with no issues.   and i get the same problem when the 2nd mon is dissabled

edit/ where in synaptic?  i must be blind...

---

### Post by Kevbert on 2009-04-27
You may need to set up the Medibuntu repo, if you haven't already. See [[COLOR="Red"]this[/COLOR]]("https://help.ubuntu.com/community/Medibuntu").
This [[COLOR="Red"]link[/COLOR]]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-904-jaunty.html") may also be of use.

---

### Post by Gunbullet on 2009-04-27
I've gone through every suggestion listed in this thread and others on the web but I still get the message "you may not have permission to..." when I try to play a DVD in Totem. If I try VLC then a window pops up with the error message "couldn't play format". Any other suggestions, feels really pointless to not be able to watch DVD:s in Jaunty. :(

---

### Post by stoobers on 2009-04-30
wow!  I've gone through all the steps with enabling the medibuntu repositories, installing restricted blah blah.

Nothing seems to work.  I can't get my dvd's to play.  I also can't play back my .iso dvd images, which played back just fine in ubuntu 7.10.

I someone figures out how to get dvd's to play back from a CLEAN install of ubuntu 9.04, post it somewhere.  Every post out there describes what "ought" to work, but leaves out some pretty critical steps!

help!

---

### Post by stefanjcarney on 2009-05-01
I'm getting the same problem.  Worked for me with the previous version of Ubuntu but now just get that error message. Followed all of the advice so far but most of the updates etc. were already installed.  Anyone worked out how to fix this problem yet?

---

### Post by Gunbullet on 2009-05-03
All quiet on the western front. :(

---

### Post by gijello on 2009-05-03
I am having the same problem playing DVDs. Not sure what I'm doing wrong as I have installed all of the required packages.

---

### Post by ticket on 2009-05-03
Don't know if this helps, but as the error sounds like access permissions, make sure you're in the following groups:

[ ]Capture video from TV or Webcams and use 3d acceleration
[ ]Use audio devices
[ ]Use CD-ROM drives

These are found in 

  System->Administration-> Users and Groups
  ->Properties -> User Privileges

You should also make sure you are members of the pulse, pulse-access and pulse-rt groups if you have sound problems (these groups are in the 'Manage Groups' section)

I assume these menus are the same in Jaunty - I am still on 8.1.

---

### Post by stefanjcarney on 2009-05-03
Thankyou for that.  Interestingly it says that access for these things is turned off however it will not let me edit permissions.  Is there a way to do this in the terminal?

---

### Post by xc3RnbFO8P on 2009-05-03
Did you not see the unlock button?

---

### Post by matthekc on 2009-05-03
> This post talks about a region that is set in the drive's firmware.

[http://bbs.archlinux.org/viewtopic.php?id=68280](http://bbs.archlinux.org/viewtopic.php?id=68280)

Be careful, it warns that:

"Most drives only allow you to change the region code 5 times before it is locked forever, so be cautious when changing your region code."


jdb

This worked for me my region code got removed somehow...

---

### Post by hellibombelli on 2009-05-03
Thanks Kevbert! totem-xine is the right (longtime?) workaround:
```
sudo apt-get install totem-xine
sudo apt-get remove totem-gstreamer
```
IMHO many of you have the same problem and should try this.

---

### Post by morrie on 2009-05-03
I tried all that, and still my Blade Runner Box Set would not play.  Finally, I decided to do what I used to do on PC; make sure I have XVid, and DivX codecs.  Apparently DivX is taken care care of by (at least) Mediabuntu full, but I found XVid right there in the Synaptic.   Installed it, and BINGO! worked like a charm with VLC.  I am sure that will help some of you, because I was truly in the same boat...(also, I restarted my computer after all those installs)...

---

### Post by Gunbullet on 2009-05-21
This is getting really frustrating, the only "sucess" I've had is that VLC loads the Menu screen of a DVD such as Select language etc. But after that the player freezes the image and the time indicator stops. That's it, to not be able to play DVD:s in Jaunty is mind boggling.

---

