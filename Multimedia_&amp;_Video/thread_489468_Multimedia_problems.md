---
title: "Multimedia problems"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by Belgatom on 2007-07-01
Hi Folks,

Recently decided to give Ubuntu another chance on my VAIO. I have tried before with Edgy but had a lot of problems just getting the sound to work and screen resolution to go wide. I gave up. When Feisty came out, I thought I'd give it another try. Same thing happened  but I did not put much effort in to trying to get it to work. A friend helped me thishttp://ubuntuforums.org/newthread.php?do=newthread&f=138# time and yes, it worked. I now have a Vaio TR5 with Ubuntu Feisty Fawn. So last night, I tried to install the multimedia so I can get some music and movies on the laptop (one of the main funcitons). I used automatix2 to do this. NO errors were seen so I assumed it worked. But no such luck. 

Current symptoms: when I copy a divx file to my Home folder, I can see a preview for an icon. Which looked promising, but when I double click on it, I first just got the sound and blue screen. After restarting, what happens is that the player starts up, I get a fraction of a second some sound and then the player disappears. Same thing happens with MP3 playback. within VLC but not when I use Rythmbox.  

I am not running Compiz Beryl or anything fancy. I did however try the new option, desktop effects but I think this is now turned off as the button still shows "enable desktop effects".  I assume after looking through the forum that the videodriver is probably at fault. . As I didn't insall it myself, I will need some guidance to find out which one is installed and how to adjust it. 

Let me finish by saying that I am not a virgin a Ubuntu but to keep the metafor going, I've just touched first base so be patient with me.

---

### Post by baldercm on 2007-07-01
I think Automatix doesn't install ALL the codecs you may need, so try this:
check out the Ubuntu Guide ([http://ubuntuguide.org/wiki/Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")), make sure you read the section "How to add extra repositories" and then look for "How to install multimedia codecs". Make sure you copy all the installation code, because it's shown quite weird.

I encourage you to use xine video player, you will find instructions to install it in the Ubuntu Guide, so keep the quite next to you!!  :D

---

### Post by baldercm on 2007-07-01
It's obvious I wanted to say "keep the guide next to you". Fast typing errors...

---

### Post by baldercm on 2007-07-01
I've just realized you use Dapper, so I think you should this this link fot the Ubuntu Guide [http://ubuntuguide.org/wiki/Ubuntu_dapper]("http://ubuntuguide.org/wiki/Ubuntu_dapper").

---

### Post by Belgatom on 2007-07-03
Adjusted my Profile: definately using Feisty right now. 

I did follow the complete guide over here: [http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)
But did not do anything. Problem stays. Clearly Automatix2 had already installed the W32 codecs as well as te libdvdcss. 

I also uses add/remove software manager to first remove the GSstreamer entries, restarted and added them again. Still no succes.

After removing the GSStreamer entries, I tried to play an mp3 file and although I expected it not to play, it did. But movies, nothing's happening there. Anything I try to play, I get a little shot of a blue screen followed by the application closing down by itself. 

It's either codec connected or videodriver connected. Any commandline actions I can run to determine what the problem is exactly?


***edit***

Just thought I would have a look if the Experience ubunutu.ogg file in the examples plays. And same problem there, a fraction of sound and application closes.

---

### Post by RomeReactor on 2007-07-03
Hi. Maybe [this]("http://ubuntuforums.org/showthread.php?p=2947630#post2947630") can help. Seeing as you already have the Medibuntu repositories, skip that and go to **sudo apt-get update** and the rest of the commands. It would also help if you launch the video player (**totem, vlc, mplayer, kaffeine**, etc) from the terminal (just write one of the previous words and press enter) and open a file from it's menu; if it crashes, it'll leave messages regarding the errors it encountered, which might be useful to figure out what's wrong.

---

### Post by Belgatom on 2007-07-03
This is what I got back after launching VLC via the command line: 

> VLC media player 0.8.6 Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82


---

### Post by RomeReactor on 2007-07-03
Are you running Beryl or Compiz? If so, try disabling them and try again:
> X Error of failed request: BadAlloc (insufficient resources for operation)
I've seen this very frequently related to desktop effects.

---

### Post by Belgatom on 2007-07-03
I am sure I am not using Beryl or Compiz as I didn't install them. I did however touch the Desktop Effects dialogue and can't seem to figure out if they are on or not. What I do see, is that when I maximize a window, I do get some kind of animation. Alt+TAB does also give me preview of different windows. So if these functions are hoggin' too much resources, how do I get rid of the eye candy?

---

### Post by RomeReactor on 2007-07-03
Yes, that's Compiz (System->Preferences->Desktop Effects) running; most likely that is what's taxing your system. To disable the effects, you can go to it and click "Disable Desktop Effects"; or, to manage it better, install **gnome-compiz-manager** through Add/Remove, Synaptic, or from the terminal:
```
sudo apt-get install gnome-compiz-manager
```
Once it's installed, you'll find it in "System->Preferences->GL Desktop". Open it and uncheck "Enable GL Desktop". Also do a search for ** black screen compiz** on this section of the forums; many people are having the same problem as you, I think.

---

### Post by Belgatom on 2007-07-03
We are definately getting closer. What happens now, is the following:

I now start up VLC via terminal. I open an AVI file and get a blue screen, but this time the sound does keep playing and the application does not close down. 

I have tried up to now two divx files of my own and the ogg file in examples, all with the same effect. When I close VLC, there is no error message. Where to now?

---

### Post by Belgatom on 2007-07-03
Thankx for the tipps, I did find this and it works. I now have video playback. 


> VLC (VLC is not installed by default; you need to search in the package manager, then install)
o Start VLC and click on Settings, then Preferences.
o Expand Video and then expand Output modules. You will notice several options for output device.
o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.
o Pick X11 video output
o Click on Save and you are set! 

---

### Post by RomeReactor on 2007-07-03
Glad to hear you got it working! Sorry for the late reply, I was searching and it seem we came across that same thread, which I was about to suggest. Anyway it's good you sorted it out!

---

