---
title: "is there *any* way to listen to the BBC with Feisty Fawn?"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by mamadu bwana on 2007-08-13
Dear friends,

I am really becoming frustrated with Ubuntu.  All I am trying to do is listen to the BBC streaming online.  I installed Helix, mplayer, Real audio, the firefox multimedia plugin, I tried opening the stream with VLC and Mplayer,  I tried using the Rythmbox music player and the Stremtuner application but the bloddy thing *never* works!

How can we hope that Ubuntu and Linux will ever be able to provide a free alternative to Windows Vista if something so basic as listening to internet radio does not work.  Grrrrrrrrhhhh!!!

I can't believe that somebody would have to go through all that kind of misery just to listen to what is probably the best known internet radio out there?!

I really would be deeply thankful if somebody could help me out here and give me a step-by-step walkthrough as to how to get this done.

Many thanks in advance from a desperate newbie,

Mamadu

---

### Post by bluenova on 2007-08-13
Strange, works fine for me. I have this package installed:

[mozilla-mplayer]("http://packages.ubuntu.com/feisty/misc/mozilla-mplayer")

which is available in the multiverse repository.

---

### Post by mamadu bwana on 2007-08-13
well, I installed the package and tired playing both the Windows Media Player and the Real Audio stream, but nothing,  Silence.  I tried the option of "playing in stand along player".  Same thing.  Silence.

What browser are you using? What addons do you have installed?

Is there any way at all not to use the damn browsers, but just to capture the stream with Streamtuner or Rythmbox?!

Heeeeeeeeeeeeeeelp!!!!!!!

---

### Post by ravimannan2002 on 2007-08-13
Hi, 
I got the BBC player to work. This is what I did:
Download the real player 10.

Right click on the file and click Properties>Permissions and check the Execute: Allow executing file as program box.

Open a terminal

Copy the paste this command into the terminal, line by line 

chmod +x RealPlayer10GOLD.bin

sudo ./RealPlayer10GOLD.bin

Follow the instructions in the terminal and RealPlayer will be installed.
I chose to install it in "/etc/RealPlayer"


** If you encounter ‘enter the prefix for symbolic links [/usr]’ press enter and the installation will continue**

The part in bold is important because it places shortcuts for  
nphelix.so  , nphelix.xpt 
in 
/etc/RealPlayer/mozilla
to 
/usr/lib/firefox/plugins
so firefox can detect the realplayer plugin, you should go to this dir and double check this

Next, log out, log in.

in firefox, do "about*plugins" (replace the * with a : , it turns into a :p ) you should see 
"Helix DNA Plugin: RealPlayer G2 Plug-In Compatible"
note this isnt the helix plugin, per se, but real player 10.
go to the bbc radio site and test it out. I'm able to do the "open bbc radio player" and listen ok, 
the only problem is that the sound quality is choppy,....

I had problems like you. I had the helix player and i first unistalled that using Synaptic. I had realplayer 10 installed as well, but I botched the part that made the shortcuts to firefox's plugin dir. that was key, so i reinstalled it. I hope this helps!

---

### Post by steveneddy on 2007-08-13
> **mamadu bwana said:**
>  probably the best known internet radio out there?!



So...is BBC a new pop station or something? Maybe I should give it a go myself. Good music, eh?

---

### Post by aidanr on 2007-08-13
Mplayer-plugin for Firefox works for me. Gxine has a load of BBC stations under the media tab, but most of them don't work for me, you might have better luck. I rarely use gxine so i haven't looked into it further.

---

### Post by GeorgeAD on 2007-08-14
This probably isn't going to help, but when you go to e.g.: 

[http://www.bbc.co.uk/radio2/listen/](http://www.bbc.co.uk/radio2/listen/)

and click one of the 'listen to latest show' links, a window appears with buttons for "play", ">>5mins" and ">>15mins". Above those there's a little black box  with what looks like a film strip; click on that.

I spent a long time clicking "play" and wondering why nothing was happening...

---

### Post by rpn on 2007-08-14
I had your frustration, found this thread, installed MPlayer inc Mozilla plug in and it just worked!

I'd been hunting around for an answer and did not want to install RealPlayer if I could avoid doing so; mainly because it is outside the repository system which seemed likely to store problems for the future.

Thanks,

Richard.

---

### Post by mamadu bwana on 2007-08-14
Hi,

Thanks a lot for your help.  I did all the steps you outlined, but when I got to this I felt like an idiot since I could not find any "about plugins" anywhere.

> **ravimannan2002 said:**
> Hi, 
in firefox, do "about*plugins" (replace the * with a : , it turns into a :p ) you should see 
"Helix DNA Plugin: RealPlayer G2 Plug-In Compatible"
note this isnt the helix plugin, per se, but real player 10.
go to the bbc radio site and test it out. I'm able to do the "open bbc radio player" and listen ok, 
the only problem is that the sound quality is choppy,....


However, I still tried listening to the Real Audio stream of the BCC and IT WORKED!!  :cool:

I am very much in your debt for your patience with the noob idiot I am.  Thanks a lot!

---

### Post by ravimannan2002 on 2007-08-14
No problemo.
I meant about<colon>plugins.
Is your sound quality in real player choppy??

---

### Post by acoustibop on 2007-08-14
I just installed mozilla-mplayer and Radio 2 is playing fine - not choppy, either.  However, I do have a fairly fast internet connection.

---

### Post by steveneddy on 2007-08-14
> **mamadu bwana said:**
> 
Thanks a lot for your help.  I did all the steps you outlined, but when I got to this I felt like an idiot since I could not find any "about plugins" anywhere.



It's not "about plugins" - it's

```
about:plugins
```

in the address bar of Firefox.

---

### Post by mamadu bwana on 2007-08-16
> **ravimannan2002 said:**
> No problemo.
I meant about<colon>plugins.
Is your sound quality in real player choppy??

now, the sound is actually very decent, something like 64kbps mp3 I would guess. my network is rather fast though (10mbps)

---

### Post by Orfeo-40 on 2007-08-16
Only just discovered this thread, so am pleased you have it working now.

As a KDE devotee I am streaming wonderful BBC 7, Radio 2 and Radio 4 with Amarok. I can't remember where I found out how to do this, but I installed a Firefox extention called MediaPlayerConnectivity. This allowed me to capture the address of each stream to feed into Amarok (or your player of choice). Like you I'm enjoying decent quality and reliable reception.

My frustration is with the BBC Listen Again stuff. I have to run these in RealPlayer, it seems, and it's what others on this thread would term 'choppy' - it's barely usable and has to be continually paused and played to get it to continue.

Oh well, a task for another day.

---

### Post by johnraff on 2007-08-17
I've installed mplayer and I can listen to the bbc just with that- no browsers or windows. Just type the command ```
mplayer *url/of/stream*
``` and the sound starts coming out: very light on system resources. 

Right now I have to stop it with ```
killall mplayer
``` before opening another url because you otherwise end up with two playing simultaneously. (Probably there's a more elegant way of doing it.)

---

### Post by mamadu bwana on 2007-08-17
BBC on the CLI :-)
thanks for the tip, I really like to stay away from GUIs.
Regards,
Mamadu

---

### Post by nicoblue on 2007-08-20
> **bluenova said:**
> Strange, works fine for me. I have this package installed:

[mozilla-mplayer]("http://packages.ubuntu.com/feisty/misc/mozilla-mplayer")

which is available in the multiverse repository.
Thank you bluenova,I took package mozilla-mplayer from synaptic and had BBC Radio ,including "play it again"working in a minute,a little slow to start but none of the stutering others complain of !much better than having to use automatix to get it !
regards 
                     Nicoblue
p.s. this is on xubuntu 7.04

---

### Post by johnraff on 2007-08-20
> **mamadu bwana said:**
> BBC on the CLI :-)I was a bit vague. You can launch mplayer from a terminal window, but what I'm doing is making a launcher on Xubuntu's panel with that command line and the "run in terminal" box unchecked. The sound comes, but there's not even a terminal window. I suppose this is what they call "running in the background". Unfortunately I haven't yet discovered how to get commands to that mplayer other than "killall"... 
If anyone knows how to control applications running in the background, I'd be very grateful.

-----------------------------------------------------
URLs:
The bbc and a lot of other net radio stations seem to do their best to prevent people from getting hold of the urls of their streaming sources. Maybe there are some legal issues? Is it cool to post up urls that work on a forum like this, or would it get Ubuntu into trouble? I'd be willing to post the few I've found if it's not illegal or anything, and be glad to get a few more...
(The "UnPlug" Firefox extension is sometimes good for getting media source urls.)

---

### Post by ntlam on 2007-08-20
bbc works with my reaplayer

---

### Post by leona on 2007-09-07
Similar problem here also with 64bit Ubuntu using 32bit Firefox, no audio from website.
Also doesn't work in Rhythmbox either :( (it used to with 6.06)
The about plugin thing and it shows that mplayer is installed
File name: mplayerplug-in-wmp.so and mplayerplug-in.so
Movies don't work either on the news.bbc.co.uk :(

---

### Post by theDaveTheRave on 2007-09-21
I was so pleased to find this thread, I thought I may have found the solution to my problem!

Well I seem to have lost ALL INTERNET SOUND!

I've chekced the < about:plugins> page and lots of things are installed and should be running with the various formats.

funny thing is I can download video and it is fine for playback (with sound) through the installed movie player, but I get an error with Real Player, saying it doesn't have the abilities to play MP4 files etc!

I re-installed Real Player 10.5 Gold through synaptic, but still no luck. 

I generally use VLC for DVD's but again it won't play all formats? where can I get "ALL" the required codecs so as VLS / RealPlayer will handle whatever I throw at them.

thanks in advance.

Dave

---

### Post by happy-and-lost on 2007-09-22
Has anyone got the BBC to work in Rhythmbox?

---

### Post by andrew.46 on 2007-09-25
Hi,

 Saw your frustration:

> **mamadu bwana said:**
> well, I installed the package and tired playing both the Windows Media Player and the Real Audio stream, but nothing,  Silence.  I tried the option of "playing in stand along player".  Same thing.  Silence.

What browser are you using? What addons do you have installed?

Is there any way at all not to use the damn browsers, but just to capture the stream with Streamtuner or Rythmbox?!

Heeeeeeeeeeeeeeelp!!!!!!!

 What you are asking for can be fairly easily done but there must be a problem with your setup. Try typing 

```
about:plugins
```

Into the location bar of Firefox and post the list here. This should tell which plugins are allocated to which media format. 

 Have a quick look at this thread as well which may set you on the right path:

[http://ubuntuforums.org/showthread.php?t=540412&highlight=howto+mplayer](http://ubuntuforums.org/showthread.php?t=540412&highlight=howto+mplayer)

  All the very best,

     Andrew

---

### Post by lizzie2 on 2007-09-26
> **rpn said:**
> I had your frustration, found this thread, installed MPlayer inc Mozilla plug in and it just worked!

I'd been hunting around for an answer and did not want to install RealPlayer if I could avoid doing so; mainly because it is outside the repository system which seemed likely to store problems for the future.

Thanks,

Richard.

Hi,
Same here, could not listen to radio. Mozilla plugin went straight to work.
Thanks a lot.
Have fun,
Les

---

### Post by trak87 on 2007-09-26
From the command line:

BBC Radio 2 (music):
```
mplayer -playlist http://www.bbc.co.uk/radio2/realmedia/fmg2.ram
```

BBC Radio 4 (news):
```
mplayer -playlist http://www.bbc.co.uk/radio4/realplayer/media/fmg2.ram
```

Use Ctrl-C to stop playing. The idea is to look at the BBC links and find their .ram URL's. Right click and select "Copy". Then just utilize it (paste it in) as above.

The -playlist option is for .ram or .pls or .m3u files, which are of course playlists and only act as pointers to the actual stream.

---

### Post by pakku on 2007-09-29
Thanks for realplayer installation tips. Also helped me with raaga.com.  Audio is good, not choppy.
I cannot get video to work though.

---

### Post by hums07 on 2007-10-20
Great information. Thanks all!
I just installed mozilla-mplayer with Synaptic.
Now I can play BBC video in my Xubuntu. The sound and video quality is superb.

---

### Post by robc02 on 2008-01-17
I can "Listen Live" to BBC streams using Firefox with mplayer plugin. The method using "mplayer -playlist" in a terminal is really neat and quick to start playing.
I can play "Listen again" using Firefox but the controls "5min", "15min" don't work. I don't have a black box with a film in it above the controls either. Does anyone know how to get this working?
I am using Gutsy.

---

### Post by ubuntu-freak on 2008-01-18
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

### Post by robc02 on 2008-01-18
Thanks, reassuringlyoffensive, I installed realplayer as per your How To and it now works perfectly.

---

### Post by ubuntu-freak on 2008-01-18
> **robc02 said:**
> Thanks, reassuringlyoffensive, I installed realplayer as per your How To and it now works perfectly.

No problem. Everyone else should check it out. There are instructions for encrypted DVD playback too. 
 
Nathan

---

