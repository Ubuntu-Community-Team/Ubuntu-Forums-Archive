---
title: "Problems with Divx"
date: 2010-03-13
forum: Multimedia Software
---

### Post by werdo1998 on 2010-03-13
Ok I am trying to get my videos to pause and rewind from [www.stagevu.com]("http://www.stagevu.com"). Right now if I pause it just starts over.  Also is there a program like Yahoo messenger that will let me send SMS messages to friends?  This is a screen shot of what my player looks like.  I should also tell you that others have tried to help me and no luck. I have  a post under general help. DVD Problems. So  check that out if it will help.

---

### Post by werdo1998 on 2010-03-13
Ok I have this now. SOMEONE SAVE ME!

---

### Post by 2hot6ft2 on 2010-03-13
For the sms try kopete (pic attached).
```
sudo apt-get install kopete
```
For the other I don't know it's so slow I can't stand to wait for it to even get started, but you're right it does go back to the beginning. You could right click on it and select play in vlc player at least I could but it's still like it's not even downloading so perhaps it's a server problem there.

---

### Post by jocko on 2010-03-13
The videos on that site works fine with gecko media player (a browser plugin that uses gnome mplayer and mplayer).
To install it, remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc):
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
Install gecko media player:
```
sudo apt-get install gecko-mediaplayer
```
Then restart firefox and try it out.

---

### Post by 2hot6ft2 on 2010-03-13
> **jocko said:**
> The videos on that site works fine with gecko media player (a browser plugin that uses gnome mplayer and mplayer).
To install it, remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc):
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
Install gecko media player:
```
sudo apt-get install gecko-mediaplayer
```
Then restart firefox and try it out.
I had already removed mplayer and installed gecko but apparently there was some plugin left causing a conflict so using the remove part of your instructions did the trick. Now pause works like it should and the downloading to cache can be seen.

Thanks

Looks like the OP has logged off so it may be a while before we find out if it works for them.

---

### Post by werdo1998 on 2010-03-13
It's getting better . I can pause it now. I still can't rewind with the slide bar.

---

### Post by 2hot6ft2 on 2010-03-13
> **werdo1998 said:**
> It's getting better . I can pause it now. I still can't rewind with the slide bar.
I'm just downloading the ones I want to watch from there and I'll play them in vlc when their done. Since it's streaming I doubt you can go back like you want to.
 Just a minute I'll post how to download the movie.

---

### Post by 2hot6ft2 on 2010-03-13
In firefox click on Tools > Add-ons
Then Get Add-ons
Search for DownThemAll and install it
Then after restarting firefox and going to the movie click on
Tools > DownThemAll! Tools > DownThemAll!
A box will open go down to the bottom and find the one that is a .avi and select it (most will be .jpg).
Right click and select Invert Selection
Move your mouse to the others that are now selected and right click
Choose Uncheck selected items

Right under the window you can choose where to download it to.
Then you can click on Start to start downloading it.

That's it you'll have the movie on your drive when it finishes to watch at your leisure and you can pause/play/rewind all you want.

---

### Post by werdo1998 on 2010-03-13
That helps, but it's not a fix. I don't really want to fill up my disk. I would rather have it just download the part file and write over it every time I watch a new video. So how is that done. That is what the Divx web player does on widows. I need a player that will do that.

---

### Post by 2hot6ft2 on 2010-03-13
That way I just delete it after watching it and poof it's gone. I don't know how to fix the player so you can rewind. I tried Opera and Epiphany browsers but it wasn't any better. Couldn't rewind.

---

### Post by werdo1998 on 2010-03-13
I seems to me it would be a simple fix. There has to be somebody out there who knows what to do . I only have a 20gig drive. So I have very little room to work with on this computer.

---

### Post by werdo1998 on 2010-04-26
Okay here is the deal. I am having trouble with Divx movies.  I watch videos on [www.stagevu.com]("http://www.stagevu.com")  a lot.  However, I've had trouble with the videos, they stop and start over as soon as he buffer runs out.  Also, I can't rewind videos. Can anyone help? I'm new to Ubuntu, I need help.

---

### Post by llamabr on 2010-04-26
Did you:

```
sudo apt-get install ubuntu-restricted-extras
```

?

---

### Post by werdo1998 on 2010-04-26
That's all up to date.
I'm trying to get it so I can pause the video and let it load. Like the divx player for windows will do. I think that one just writes the AVI. as a part file to the drive which is why you can rewind and and skip ahead with it.   Is there a player for Ubuntu that can do that?

---

### Post by werdo1998 on 2010-04-26
Here is what's up. I watch videos at [www.stagevu.com]("http://www.stagevu.com") pretty often.  When I do this, the videos sometimes stop and start over when the buffer runs out.  This really sucks!! It always does it like half or two thirds of the way into it.  I can't even pause and let it load. Also, I am not able to rewind or skip ahead.  
         I have used the Divx player for Windows before. That program makes a part file on the drive with the streaming video. Then it reads from the part file. So I am able to skip ahead and rewind with that program.  So is there a player for Ubuntu that can do that? 
   Oh, and my browser has been crashing  a lot too. I don't know if one has anything to do with the other, but I thought I would throw that out there for you guys too.:( anyone out there have an idea what to do?

---

### Post by djrobthaman on 2010-04-27
Why not try vlc? One of the better players I would say (some might tell you mplayer is better and they might be right but vlc's pretty good as well).  Just install it through synaptic.

---

### Post by werdo1998 on 2010-04-27
I have problems with Divx files. I like to watch videos at stagevu.com.  These videos are Divx, or AVI files that stream. When I was using Windows I had Divx web player.  So I'm used to that one.  
    So anyway, when I watch a divx video I can't rewind or skip ahead. Not only that, but when the buffer runs out the video will start over. This sucks when the video is long. 
   I know that with the Divx web player on Windows that the program would take the streaming AVi/Divx fires and write them to the drive as a pert file. Then it would read from that file. I'm pretty sure that is why I was able to rewind and skip ahead with that program.   
   So do any of you people know what program I need so I am able to watch my videos without these problems? I am pretty new to this Ubuntu thing, so please cut me some slack.  

... one more thing. I like to use Veoh player too. Is there a Ununtu version of it?

---

### Post by carl4926 on 2010-04-27
Are you using the gecko-mediaplayer plugin?

---

### Post by werdo1998 on 2010-04-27
I am.

---

### Post by elliotn on 2010-04-27
vlc is more than better

---

### Post by carl4926 on 2010-04-27
It seems to work OK for me. But I'm on my openSUSE laptop ATM.
I'll check Ub* later.

Remember that most of these sites give no time to supporting Linux, they are all M$ focused.

---

### Post by werdo1998 on 2010-04-27
I know, but it seems to me that this would be a common problem. Divx is a really widely used video format, just about as common as Mp3 audo files these days.  I would think there would be an easy fix for this one. Maybe I'm wrong....

---

### Post by 2hot6ft2 on 2010-04-27
Remove any conflicting browser media player plugins you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc):
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```

The videos on that site works fine with gecko media player. I know since I've uploaded about a hundred there.

---

### Post by werdo1998 on 2010-04-27
2shot that fixed the stop and restart problem I think, but I still can't rewind or skip ahead.

---

### Post by carl4926 on 2010-04-27
You could also use the FF extension 'DownloadHelper'

---

### Post by 2hot6ft2 on 2010-04-27
> **werdo1998 said:**
> 2hot that didn't change anyting for me.

Did you restart firefox?
I have 154 there right now. I just checked.

---

### Post by carl4926 on 2010-04-27
> **carl4926 said:**
> You could also use the FF extension 'DownloadHelper'
Also. I'm back on Ubuntu now and it works fine.

---

### Post by werdo1998 on 2010-04-27
I did that, yup.

---

### Post by werdo1998 on 2010-04-27
> **carl4926 said:**
> Also. I'm back on Ubuntu now and it works fine.
I did.

---

### Post by carl4926 on 2010-04-27
> **werdo1998 said:**
> I did.
You did what?

---

### Post by 2hot6ft2 on 2010-04-27
> **werdo1998 said:**
> 2shot that fixed the stop and restart problem I think, but I still can't rewind or skip ahead.
You wont be able to skip ahead unless you wait for it to download at least as far as you're wanting to skip.
I'm loading one now to check the skip backwards since I don't usually back up in a movie.

---

### Post by werdo1998 on 2010-04-27
GRRR!!!! Okay guys, I still can't rewind or fast forward. Is there a program that works just like Divx player for Windows?

---

### Post by werdo1998 on 2010-04-27
Sorry carl the "i did" was for 2hot from before. my bad

---

### Post by 2hot6ft2 on 2010-04-27
> **carl4926 said:**
> You could also use the FF extension 'DownloadHelper'
I use Down them all for that site.

I just tried skipping forward and backwards and it worked fine so lets just start from scratch.

Here's my cookie cutter fix for multimedia.
Let's just cut to the end and install it all at once so you can play pretty much everything.

I could spend a half hour saying go here click this open that  yada yada yada instead do this.

Open a terminal
Applications > Accessories > Terminal
and run these commands one at a time and your password wont be shown when you type it in just type it in and hit enter.
This first one enables the medibuntu repository for restricted codecs and such
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) like this:
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
then for all the multimedia, mp3's, divx web player, and dvd playback
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer vlc
```
Oracle Java is part of the ubuntu-restricted-extras package so use your arrow keys and Tab key to select and Enter to accept the Java terms of use since Oracle now owns Sun.
And to get rid of one package in the restricted extras that causes problems:
```
sudo apt-get purge ttf-mscorefonts-installer
```
ttf-mscorefonts-installer bug report
[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

[And to install Flash (the same as going to the adobe website) just click this link if using 9.04 or up, then on OK]("apt:adobe-flashplugin?channel=$distro-partner")

And you're done.
Close and reopen firefox and try it now.

---

### Post by 2hot6ft2 on 2010-04-27
> **werdo1998 said:**
> GRRR!!!! Okay guys, I still can't rewind or fast forward. Is there a program that works just like Divx player for Windows?
Yes gecko for the web player and vlc is my player of choice for all the movies I've ripped and encoded to DivX.

---

### Post by clhsharky on 2010-04-27
Hi werdo1998

I have the default player with ubuntu-restricted-extras, Firefox's Download Helper plugin. That it and every thing works fine at [www.stagevu.com](www.stagevu.com) , sure you run into slow URLs but thats there fault.

Sharky

Disclaimer - your hardware may very

---

### Post by lucasta on 2010-04-27
vlc is definitely the best option, you may want to look at some guides on tweaking it to your needs though. and of course you may need extra codecs to play specific files. but the restricted extras seemed to do enough for me

---

### Post by 2hot6ft2 on 2010-04-27
And keep in mind that people upload videos in a lot of formats to that site so after they re-encode them to divx some wont work like they should like skipping forward and backwards.

If they were encoded to divx or xvid first then they work like they should so it may be the video that you're trying to play that is causing problems.
Looks like the OP logged off so I'm calling it a night.

---

### Post by 3rdalbum on 2010-04-27
You can make a larger buffer in VLC and Totem.

---

### Post by siretfel on 2010-04-27
I was looking for a way to play streaming video from web in firefox under linux Coala and also play divx videos online through firefox and after i installed gecko-mediaplayer everything works like a charm.
BUT the only thing i cannot do is this:the video buffers but i cannot move to a specific time frame.Say for example i watch a video and i'm in the 10 minutes and 32 seconds.If i want to go back to 9 minutes to re-watch this part again i cannot.(i'd appreciate any workaround if there's any.)

---

### Post by werdo1998 on 2010-04-27
I can't rewind or fast forward my videos.  I used to use Divx Player for Windows. That program would take the streaming .Avi or Divx file and write a temp file to the disk with it. Then it would read from the temp file. Is there a program that will do that?
I have posted on this problem before, but no luck fixing it.
 I know one of you nerds can do it .... HELP!!!!! I am just not nerdy enough.
    I like to watch videos at [www.stagevu.com]("http://www.stagevu.com"). Most of the videos on that site (if not all) are DIvx, or .AVI files. 
I am having trouble with Veoh video as well. Veoh's web page only lets you watch a 5 minute clup if you don't have the Veoh web player installed.  However Veoh only works on Windows. I have tried to run it with Wine, but I need direct x....So.....
....Also to all of you people who say use Gecko player. I am, and it's not working very well.
...that's nerd in a good way lol

   I should log on and off all night tonight. So  if anyone responds. I will get back to you soon.
UM?

---

### Post by werdo1998 on 2010-04-27
I used to use Divx player on Windows to watch videos from sites like [www.stagevu.com](www.stagevu.com).  I can still do that with gecko, but there are a few things that are buggy. For example I can't rewind or fast forward the videos. I know that this site streams .AVI or Divx files. 
    Anyway, I want a player that can write the video file as a temp file. So the player can read from that. That is what the Divx Web Player does. Is there anything that works like that? 

   I am have problems with Veoh video too. The Veoh site only lets you watch a 5 min clip of the video unless you have their player installed on your computer. SInce I can't get their player to work with wine because of a direct x issue. That seems hopeless. 
    Any help you guys can give would be great!  I will be poping on and off of this stite to check replys, so if I'm offline., I'll be back really soon.

---

### Post by werdo1998 on 2010-04-27
[COLOR=black]  Okay, so when I was hooked on Windows, I would use Divx Web player and Veoh web player.
Right now I'm using Gecko(for avi, and divx files).. That hasn't been working too good. I cant rewind or fast forward the videos, and since Veoh's site makes you use their player, i can only watch 5 min clips on that site. That sucks! They have some cool stuff on there.
    Anyway, Divx player on Windows always wrote a temp file to the drive, then it  would read from that. Is there a player that works like that for Ununtu? It's nice to be able to let a video load then skip back and forth. I can't do that right now.
   Also I have tried the Veoh player with wine...I need direct X for that. So..... you know.....
I'm lost. What do I do?
     My nerd skills are not so great... HELPPPPPPPPPPPPPPPPPP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
   I really like the videos at  [www.stagevu.com]("http://www.stagevu.com"). They are divx, or avi.  Anyway...I have used vlc. It's a good player, but not for what I'm trying to do.
[/COLOR]

---

### Post by hopstah on 2010-04-28
I'm not familiar with Veoh, but VLC is an amazing player that can play pretty much anything you throw at it.

---

### Post by lisati on 2010-04-28
Multiple threads merged

---

### Post by blanksean on 2010-06-14
> **werdo1998 said:**
> Ok I am trying to get my videos to pause and rewind from [www.stagevu.com]("http://www.stagevu.com"). Right now if I pause it just starts over.  Also is there a program like Yahoo messenger that will let me send SMS messages to friends?  This is a screen shot of what my player looks like.  I should also tell you that others have tried to help me and no luck. I have  a post under general help. DVD Problems. So  check that out if it will help.


textem.net is the sms for your needs

---

### Post by blanksean on 2010-06-14
Let me start by saying please excuse my frustration.

I am having trouble watching anything on stagevu the buffering is insufferable,
every 2 sec it buffers to play for 2seci use mplayer and am trying xine wich seems to
have the same issue it does however play a little longer. i am really interested in ubuntu
and not much could change that but not being able to use stage vu is a big issue.
please help me i don't want to go back to windows but im getting that frustrated.
i know it can work i've seen it i  have searched and searched and searched myself sick
and im so discusted with totem please help me resolve this. 

this is my first ever help post i mostly find the issue on google if i have one
and although i have seen many post of people complaining about this i have yet to see 
a fix please help 

i have tried adjusting buffer in totem seems to have no effect at all
why is this even an issue there has to be a way to fix it

---

### Post by wesleybishop on 2010-06-14
Pidgin is a good program for sending SMS

---

### Post by blanksean on 2010-06-14
> **wesleybishop said:**
> Pidgin is a good program for sending SMS


agreed but can you help me?

Textem is web based 
it can sends and receive texts.


but really please help or poin tme in the right direction.

---

### Post by rebelDNS on 2010-07-20
There seems to be a lot of miscommunication on this thread, so I'd thought I'd just clear the main issue up.

To those of you who are saying "open it with VLC" and things like that:

The issue is with the WEB player (i.e. through the browser.)  If you don't know what I'm talking about, try installing and using the Divx Web Player on Windows or Mac.  It is a really awesome plugin which allows you to watch Divx as it is being downloaded (gives the impression of streaming) but at the same time allows you to treat it like it was already just a file on your computer (because it is.)  This means that while you're still buffering, you can pause, skip to any time backwards or forwards, skim through, etc. within the part you already downloaded without having to rebuffer and restream.

Downloading the file and then opening it after is easy.  But the cool thing about the Divx Web Player is that you don't have to wait until the entire file is downloaded.

And to those of you asking the question - say "Divx **Web** Player" since you're talking about the one on the browser.  The Divx Player is just a program to open files that are already fully downloaded.

And as someone who loves Linux but watches a lot of DivX content, I too feel the frustration of not having a decent web player for avi files.

---

### Post by =CrAzYG33K= on 2011-03-20
Bumping this thread up to see if the DivX web player's issues have been resolved yet (under Ubuntu).

Some quirks that still remain:
1) The buffer progress bar that's shown with divx web player is not seen with the 'movie player' plugin on FF.
2) I cannot seem to pause and replay it. It just stops if I do that in ubuntu, whereas in windows with divx web player plugin (on FF), I could pause and then resume as and when I need it.

My config for FF : Totem 2.30.2 plugin + DivX web player version 1.4.0.233

PS : I've tried the gecko media plugin for FF and it's actually worser.

**EDIT:**

I just tried out in Google Chrome and the 'Pause/Resume' issue seems to work perfect there. Maybe there's a contradicting plugin in Firefox. Maybe it's recommended to go the Chrome route for streaming DivX videos on Ubuntu. I've checked and there doesn't seem to be a particular plugin for this on my Chrome install.

**EDIT 2:**

Upgraded Firefox and Ubuntu and the 'Pause/Resume' thing is actually fine! :)

---

