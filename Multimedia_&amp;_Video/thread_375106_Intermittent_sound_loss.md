---
title: "Intermittent sound loss"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by gewitty on 2007-03-03
I'm a new Linux user (Ubuntu 6.1.1/Gnome) and have so far been getting on pretty well, but I have an odd problem with sound that is baffling me. Every so often, when I start up my PC, I find that there is no sound working in any app. To cure this often takes several reboots (the record is six so far).

Can anyone suggest why this might be happening and how it could be cured?

---

### Post by Old Jimma on 2007-03-03
No kidding on this one! 

I have held out for months over this problem!

Intermittant sound, and now no sound at all. Somthing about sound in Dapper is fragile. 

Will somebody PLEASE post a permanent solution.

Dapper 6.06
Phil Smith
Duluth, GA

---

### Post by gewitty on 2007-03-04
Look as if we're on our own on this one Phil. Can you tell me if you have success in restoring sound when you do a warm restart, or do you have to power down completely?

---

### Post by Old Jimma on 2007-03-04
HI gewitty:

I got my immediate problem corrected, but not in a satisfactory or permanent manner. 

Here is what I did. I may not work for you...

I have an internet phone plugged into one of my USB ports. Under system > sound I noticed that Ubuntu had chosen the generic usb device (ie, my USB phone that I use for Skype) instead of my sound card... so I manually chose my sound card and rebooted. After rebooting, ubuntu kept choosing my generic usb devise, no matter what.... so I unplugged the usb phone, and rebooted so that ubuntu wouldn't have any choices in choosing a sound device. It worked,... sort of... there was sound thru realplayer, etc. However, when I use xine for sound, close it, then try using realplayer, ubuntu thinks my sound card is still being used by xine and won't let me use realplayer. Go figure!

There is a page on the forums called "comprehensive solution to sound problems" at [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449) . If you can understand it, you may be ahead of the game. I'm not a software engineer, so I can't. I'm only a PhD mathematician.

While I'm quite sold on Ubuntu (over Windows) for many, many reasons, there is a price for the freedom of linux.

After looking over the forums, I feel that we are not alone in our sound problems. There is something that our Ubuntu experts are not articulating to us in a language that we can understand, in my opinion.


Here is something funny and a little interesting... sometimes when I have no sound thru my speakers, it is actually coming thru my phone. I'm not sure I wanna listen to either streaming audio or my jazz collection using my phone.

Sorry I can't be more help. If you have a breakthru, please let me know!

All the best,
Phil Smith
Duluth, GA

---

### Post by gewitty on 2007-03-04
Hi Phil (I'm Dave by the way),

It's pretty late here, so I'll check this out tomorrow. I too have a USB phone hooked up for Skype, so there does seem to be a common element. What still baffles me though is the seemingly random nature of the sound failure. Why should it refuse to work through several reboots and then suddenly come to life?

I'll try unplugging the phone and checking the sound set-up tomorrow and let you know what I find.

---

### Post by gewitty on 2007-03-06
Looks as if the USB phone used with Skype was the cause of the problem, or to be more precise, the item of hardware that triggered the bug. I've had it unplugged for twenty four hours now, during which time I've done several restarts. Sound has worked fine afetr every one.

So who do we tell about this?

---

### Post by TheBigJimbrowski on 2007-03-06
Hi you two,

If it makes you feel any better, you are not alone - and it is the USB phone which grabs the sound first on my system intermittently too. It is fixable through your sound settings though - similar to the way you do it in windows. It is a pain, still, but at least it saves all that rebooting, and you can still leave your phone connected.

I too am one of those disappointed, regularly flamed, nOObs, who doesn't understand the Ubuntu tagline - surely it should be 'Linux for software engineers who already know linux'?

Still no cigar in my opinion, Windows wins for those of us who just want to use a PC, not programme it, but i'm still persevering as I hate the idea of buying a new PC so I can use Vista.

Cheers,
Jim

---

### Post by gewitty on 2007-03-06
Hi Jim,

A bit harsh I'd say. Since switching to Ubuntu I've had a huge amount of help from all sorts of people and have now got a pretty good set-up that works very well.

I agree that at times you do encounter people who only speak Tharg, but usually if you ask nicely they will translate into idiot language for the likes of us.

I don't see myself ever going back to Windows now, although having said that, I do have to run it inside Ubuntu in a Virtual Machine for some MS apps that I just have to use occasionally.

All in all though, it's a huge change for the better.

---

### Post by gewitty on 2007-03-06
Egg all over face.

The problem returned today. After quite a few successful starts, I did a reboot this afternoon and had no sound. It took four attempts to get it working again. So back to square one.

The thing that really bugs me is the apparently random nature of this fault.

---

### Post by jlachovsky on 2007-03-06
I am having a similar issue, except I have a pair of Logitech USB headphones that messes up my sound.  Usually I just have to choose my sound card in the sound options and it fixes it, but now that isn't working.  I don't have the head phones plugged in right now either.  It is very strange, because sound will work in movie player, but I won't hear my log in noise when I log in and when I use XMMS it says my sound card my not be configured properly or a program might be blocking it.

---

### Post by gewitty on 2007-03-07
Well this thread has been running for a while now and none of the gurus have waded in with any ideas. So I guess they're as baffled as we are.

It seems like something that affects a number of people though. So perhaps it should be followed up as a bug.

---

### Post by jlachovsky on 2007-03-08
I tried doing what they recommended in the previous thread and all it dead was kill my desktop and I had to reinstall it.  Really wish we could get some help.

---

### Post by 900donuts on 2007-03-08
i'm no expert but i think i have a idea

* make sure that your computers bios isn't set to boot from usb
*move all files that have to do with your usb phones to an external storage device (you know flash drives)
*reinstall anything you think nessesary is to make this work(drivers, audio players, codecs stuff like that)
* if you have a 4 year old sound card try geting a new one (one newer that your phone)
*and finally if you have a lot spare parts try swiching things around until something works

i hope this helps

---

### Post by jlachovsky on 2007-03-08
900donuts I thank you for the reply, but I fail to see how having my computer set to boot from a usb drive would effect me not having sound.  My usb headphones used to work fine and have only just recently ran into this issue.  I would've just uninstalled and reinstalled the program if it was just one program, but I also don't have any system sounds (i.e. log in, log out) and sound also doesn't work in XMMS (it reports that a program might be blocking my soundcard or it might not be configured properly).  I do have sound though when I play music through Movie Player.  I have already checked my sound options and I know I have the right thing chosen so I know that isn't an issue either.

---

### Post by Aellus on 2007-03-13
Hey Guys,

I've actually been having this problem on my laptop since last fall when i first put Ubuntu on it. However, i have no USB phone attached. Unless there is something else going on in my laptop hardware that i am unaware of, i have had no luck at all figuring it out.

The reason i'm posting this is to maybe steer you guys away from assuming its the phones. It could be a coincidence...

The reboots are very annoying, though! I'm just getting used to it since i dont need sound much on my laptop.

---

### Post by Old Jimma on 2007-03-20
I found a nice web page on how to tweek Dapper: 

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

then look for   "**How to stop default sound card from changing**".


I'm going to try this to see whether it works... it will take a few weeks of using it (making phone calls, and listening to streaming audio) to know whether this is a good solution.

Phil Smith
Duluth, GA

---

### Post by leodp on 2007-03-31
Hi,
same problem here. I noticed two things:

1) On the taskbar I have the kmix applet. When I have the sound problem, if I open the mixer the "current mixer" pull-down menu is not set at the "SiS SI7012" sound card, but  to "SAA7134" (the internal TV card).

2) Mplayer works if I set the audio output with the flag "-ao sdl" .


Does this help in discovering the problem or the eventual process blocking alsa/oss?
By the way, I tried "sudo /etc/init.d/alsa-utils restart", but it has no effect.

Ciao, Leo

---

### Post by leodp on 2007-03-31
The module saa7134_alsa is in use. I closed kmix, then

sudo rmmod saa7134_alsa  
sudo rmmod saa7134
sudo /etc/init.d/alsa-utils restart 

now if I restart kmix it shows the 'correct' mixer menu, but xmms still not working.
We have to find which process is blocking the alsa output. But I have to go now, it's saturday evening 	\\:D/

Leo

> **leodp said:**
> 
1) On the taskbar I have the kmix applet. When I have the sound problem, if I open the mixer the "current mixer" pull-down menu is not set at the "SiS SI7012" sound card, but  to "SAA7134" (the internal TV card).


Ciao, Leo

---

### Post by rwe_linux on 2007-06-14
Hi everyone,

Sorry I am not posting any solutions, just more problems.

My sound problem sounds similar but it is unique... I'll be listening to music or surfing the web and the system will lock. Followed by vertical lines that totally distort my screen. I have to power off the workstation several times before my sound will return. Its almost like something is stuck in memory somewhere that just wont release.

I have reinstalled apps and stuff but I have not been able to track it down to any thing specific. Im running Ubuntu 7.04. I thinking its a bug or a driver.

Any help would be great!

---

### Post by johnmuir on 2008-01-11
I too have this problem with the newest 7.10 with the variation that intermittently SOME sound apps do not work, specifically

always worK:
    totem movie player
    banshee

intermittently don't work:
    system sounds
    real player
    mplayer
    amarok
    audacity
    kaffeine

It must be some component common to the "don't work' apps. 

Do any gurus see the common element?

---

