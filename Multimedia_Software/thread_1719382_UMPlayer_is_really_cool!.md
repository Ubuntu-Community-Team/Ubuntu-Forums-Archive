---
title: "UMPlayer is really cool!"
date: 2011-04-01
forum: Multimedia Software
---

### Post by nrundy on 2011-04-01
I like it so much I've made it my default Multimedia player.

[http://www.umplayer.com/](http://www.umplayer.com/)


EDIT:
I changed my mind. I've uninstalled UMPlayer and won't use it any longer. I've learned every time I start UMPlayer it makes connections to the internet. I hate it when applications make unneeded and unexplained connections to the internet. Especially every single time I start the app.

VLC is much preferable.

---

### Post by Aquix on 2011-04-11
How did you find that out?

This post is the first hit in google with the term "ubuntu UMPlayer"

---

### Post by wolfen69 on 2011-04-11
> **nrundy said:**
> I like it so much I've made it my default Multimedia player.

[http://www.umplayer.com/](http://www.umplayer.com/)


EDIT:
I changed my mind. I've uninstalled UMPlayer and won't use it any longer. I've learned every time I start UMPlayer it makes connections to the internet. I hate it when applications make unneeded and unexplained connections to the internet. Especially every single time I start the app.

VLC is much preferable.

UMPlayer gets a net connection so it can retrieve video lists from youtube. No big deal. Firefox connects to the internet every time, but no one minds that.

Anyway, I think UMPlayer is really good.

---

### Post by nrundy on 2011-04-11
> **Aquix said:**
> How did you find that out?

This post is the first hit in google with the term "ubuntu UMPlayer"

using MS Windows with an application firewall. Linux makes it hard to find this stuff out because it has no application firewalls. Hopefully this will change. See here: [http://brainstorm.ubuntu.com/idea/26902/](http://brainstorm.ubuntu.com/idea/26902/)


> **wolfen69 said:**
> UMPlayer gets a net connection so it can retrieve video lists from youtube. No big deal. Firefox connects to the internet every time, but no one minds that.

Anyway, I think UMPlayer is really good.

When I'm playing a video off my hard drive, I don't want the player making internet connections. Numerous reasons exist, for example maybe I have broadband usage caps. VLC doesn't do this behavior. I'll stick with VLC, more trust worthy.

---

### Post by IT2870 on 2011-04-13
that's too bad because I came to this thread just to mention how much I'm loving UMplayer. I've been a tried and true VLC guy except for just a few complaints,like settings not remaining from track to track, etc. I recently had a bad audio issue with vlc playing downloaded music videos on ubuntu 10.10. I tried every option and nothing. I installed umplayer a while ago and just decided to try playing the music video downloads with it. PERFECTION! and the video quality and eq are great. 

Uninstalled VLC last night. And umplayer plays all my DVDs which was my main love of vlc so i'm not even missing it.

---

### Post by beew on 2011-04-14
If you use Umplayer to play youtube videos how do you choose the resolution (360p, 480p etc)?

Thanks.

---

### Post by KegHead on 2011-04-14
Hi!

I'm using also.

One problem, it plays video's I already have, but won't play any that I download.

Anyone?

---

### Post by KegHead on 2011-04-14
You tube resolution;

tools,, performance...Youtube.

KegHead

---

### Post by beew on 2011-04-14
> **KegHead said:**
> You tube resolution;

tools,, performance...Youtube.

KegHead


Found it. Actually it is Preference > Performance > Youtube.

Thanks.

---

### Post by Zendon on 2011-04-14
> **wolfen69 said:**
> UMPlayer gets a net connection so it can retrieve video lists from youtube. No big deal. Firefox connects to the internet every time, but no one minds that.

Anyway, I think UMPlayer is really good.
Sorry I found that very funny.

---

### Post by Broker on 2011-08-04
I can not run youtube in UMPlayer.
[IMG]http://img694.imageshack.us/img694/9919/umplayer.jpg[/IMG]

I install all gstreamer packages.


Any suggestions.

---

### Post by beew on 2011-08-04
It stopped working maybe yesterday. It seems that Youtube has changed something and broke all third party Youtube viewers as a result. Minitube also stopped working at the same time. The only thing that still works is the flashvideoreplacer plugin for Firefox (that stopped working on Youtube as well a few days ago but it was later fixed)

There is nothing you can do as it is not caused by problems on your end. Just be patient and check for Umplayer updates from the ppa.

---

### Post by andrew.46 on 2011-08-04
The fix is out already for UMPlayer so those who build from source should be alright. Not sure about PPAs though..... The screenshot shows my crazy daughter tandem skydiving BTW :).

---

### Post by Broker on 2011-08-05
I have PPA 
```
ppa:nilarimogard/webupd8
```

---

### Post by andrew.46 on 2011-08-05
Hmmmm.... PPAs need to incorporate [rev 174]("http://umplayer.svn.sourceforge.net/viewvc/umplayer?view=revision&revision=174"). Has the webupd8 PPA added this one in?

---

### Post by beew on 2011-08-05
> **andrew.46 said:**
> Hmmmm.... PPAs need to incorporate [rev 174]("http://umplayer.svn.sourceforge.net/viewvc/umplayer?view=revision&revision=174"). Has the webupd8 PPA added this one in?

Not yet, but I suppose it will be updated soon.

On the other hand I don't mind trying to compile Umplayer from source just as a learning experience, except I am not able to find any instruction.

Can you give me some help? Thanks.

---

### Post by andrew.46 on 2011-08-05
> **beew said:**
> On the other hand I don't mind trying to compile Umplayer from source just as a learning experience, except I am not able to find any instruction.

I have not had a look at it for a while but the following guide should still build the latest UMPlayer as well as MPlayer:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

---

### Post by beew on 2011-08-05
> **andrew.46 said:**
> I have not had a look at it for a while but the following guide should still build the latest UMPlayer as well as MPlayer:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

Thanks. But why do you need to cd into the ~/mplayer-build? Can you build Umplayer in a separate place? ( In my case it would be !~/mplayer2-build )

---

### Post by andrew.46 on 2011-08-06
> **beew said:**
> Thanks. But why do you need to cd into the ~/mplayer-build? Can you build Umplayer in a separate place? ( In my case it would be !~/mplayer2-build )

This can be changed to whatever location you prefer, it is just a matter of 'housekeeping' really :)

---

### Post by Broker on 2011-08-23
Solved problem.
Update UMPlayer with PPA nilarimogard/webupd8 to version 0.95 and youtube work fine.:D

---

