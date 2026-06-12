---
title: "gsopcast 0.4.0 deb for Gutsy 7.10"
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by chunchengch on 2008-03-19
[SIZE="3"]**[COLOR="Blue"]If you would like to watch sopcast steaming TV in [COLOR="Red"]Full-Screen[/COLOR] mode, you can download Gmlive from my new thread [http://ubuntuforums.org/showthread.php?t=832821](http://ubuntuforums.org/showthread.php?t=832821)[/COLOR]**[/SIZE]


Here is the newest gsopcast 0.4.0, enjoy it!

[COLOR="Red"]It is available in Hardy too![/COLOR]

I build a new [ATTACH]70967[/ATTACH], it will install necessary dependencies and execute file of sopcast, it makes installation more simple


PS: I am using 2M ADSL, I find it takes around 50 seconds to connect selected channel, then more 10-20 seconds to open mplayer, then more 2-3 minutes to display the TV content normally.

[ATTACH]63849[/ATTACH]

---

### Post by MaindotC on 2008-03-25
Thanks a lot for the .deb!  I used the qsopcast guide but I couldn't a channel to play so I tried your gsopcast.  It installed perfectly, but at the bottom it keeps saying its connecting and it never really connects.  I tried several channels just to make sure it wasn't just the NHL channels.  Can you think of why this would happen?  Thanks.

---

### Post by chunchengch on 2008-03-25
> **strAlan said:**
> ... but at the bottom it keeps saying its connecting and it never really connects...

I have modified my thread, please check steps 1 and 2 to fix the problem you mentioned, good luck!

---

### Post by MaindotC on 2008-03-25
Wow thank you - it works now!  Only problem is I'm still experiencing this phenomenon where it gets up to 100% stream and then it slowly starts to degrade eventually reaching like 4%.  This takes place over the course of say 5 minutes, and after about 2 minutes is when it starts to degrade :(  I have another post about this on a similar topic.

Also, it seems to consume an exorbitant  amount of bandwidth and I can't navigate to other websites and Pidgin will sometimes log off and then try and log back on.  Have you experienced anything like this?  Thanks!

---

### Post by nikhil_no_1 on 2008-03-29
You are the MANNN chunchengch...:KS

My qsopcast wud get stuck at connecting...and after reading ur solution...saw that I had 
libstdc++.so.6.
Downloaded so.5 and voila...it started t work..
Thanks a ton...
Nikhil

---

### Post by RamR on 2008-04-19
Worked for me on Hardy.  Not sure if the links are opening qsopcast correctly or not yet but the player runs smoother and clearer than it ever did in Windows XP.  Thanks a bunch.

---

### Post by hkduddu on 2008-04-29
Wow, Thanks a lot man,

I tried this on Hardy Heron and it works perfect.

Cheers.

---

### Post by guga31bb on 2008-05-04
> **chunchengch said:**
> I have modified my thread, please check steps 1 and 2 to fix the problem you mentioned, good luck!

Am I missing something? I'm having the same problems mentioned but I don't see steps 1 and 2...

EDIT: apparently I didn't have Mplayer installed - how embarrassing! 

It works perfectly now, except for not being able to get myp2p to work launch directly from FF3. Thanks a lot!

---

### Post by chunchengch on 2008-05-04
> **guga31bb said:**
> Am I missing something? I'm having the same problems mentioned but I don't see steps 1 and 2...

You need no more to fix the problem manually, just download the deb file from the first post, it will install(fix) everything.

---

### Post by guga31bb on 2008-05-04
Yeah I am happily watching now - thank you very much! 

By any chance, do you know how to make links launch directly from FF3? I tried a fix I saw in other thread but it didn't do the trick.

Thanks again!

---

### Post by iheartubuntu on 2008-05-17
Many many thank you's! Now I can watch the LA Galaxy every week :)

---

### Post by jackschmidt on 2008-05-17
I installed the deb package from this thread and it seems to work.  When I click a channel though, it seems to take forever to play.  The percentages keep going up and down at around 70%.  Is there something I should have done?

---

### Post by chunchengch on 2008-05-18
> **jackschmidt said:**
> I installed the deb package from this thread and it seems to work.  When I click a channel though, it seems to take forever to play.  The percentages keep going up and down at around 70%.  Is there something I should have done?

sometimes you just need to click the [Play] to go.

---

### Post by sungohan on 2008-05-21
Thanks for the wonderful work.
I got it working before. 
But I reinstalled my system(Ubuntu8.0.4), and then reinstalled gsopcast.
This time, it is not working.
Connecting is like forever.
Already 20 minutes gone, nothing happens.

Maybe something with libstdc, it seems I have
both libstdc++5 and libstdc++6, but not something like
libstdc++.so.5
are they the same thing?
Do you know how to solve this?
Thanks.

---

### Post by chunchengch on 2008-05-21
> **sungohan said:**
> Thanks for the wonderful work.
... Connecting is like forever.
Already 20 minutes gone, nothing happens...


1. please download the deb file and install again.

2. sometimes you just need to click the [Play] to go.

---

### Post by sungohan on 2008-05-21
> **chunchengch said:**
> 1. please download the deb file and install again.

2. sometimes you just need to click the [Play] to go.



I reinstalled it, but it still can not connect.
Maybe it is some problem with my network.

---

### Post by chunchengch on 2008-05-21
> **sungohan said:**
> I reinstalled it, but it still can not connect.
Maybe it is some problem with my network.

1. Which channel are you trying to connect?

2. Do you try to click [Play] when something like the following line appears?

[COLOR="SeaGreen"]24%,ur=11K,dr= 75K,us= 4k,ds= 18k,peers=33[/COLOR]

3. If it still does not work, go to [config] and change the [Channels Url:] from [COLOR="Red"]http://**www**.sopcast.com/gchlxml[/COLOR] to [COLOR="Red"]http://**channel**.sopcast.com/gchlxml[/COLOR], save and exit gsopcast.

re-start gsopcast to see if it works.

---

### Post by sungohan on 2008-05-22
Thank you, 

1. I tried to connect CCTV-1 and Shanghai GSport.

2. I clicked play button, nothing happens.
And yes the following lines appear like a second, then disappear and went back to "connecting".

3. Today, I can't get channel list, do not know why.  With either channels url.


Note: I should tell you, my windows sopcast on laptop also can not log in at home, but works fine at office. So I figure that there is something wrong with my router or network. 

But I got it working before using your deb package on ubuntu at home. I connected to cctv.

Thanks again.


> **chunchengch said:**
> 1. Which channel are you trying to connect?

2. Do you try to click [Play] when something like the following line appears?

[COLOR="SeaGreen"]24%,ur=11K,dr= 75K,us= 4k,ds= 18k,peers=33[/COLOR]

3. If it still does not work, go to [config] and change the [Channels Url:] from [COLOR="Red"]http://**www**.sopcast.com/gchlxml[/COLOR] to [COLOR="Red"]http://**channel**.sopcast.com/gchlxml[/COLOR], save and exit gsopcast.

re-start gsopcast to see if it works.

---

### Post by chunchengch on 2008-05-22
> **sungohan said:**
> 
Note: I should tell you, my windows sopcast on laptop also can not log in at home, but works fine at office. So I figure that there is something wrong with my router or network. 


so, I think that is nothing about gsopcast.

---

### Post by pinshome on 2008-05-23
i love ubuntu and linux.
i m a noob and i can do it amazing isn t it?
why did it take me so long to come to linux??

i still learning but i really fanncy this OS

and sopcast is easy too.

i just need to sit, relax and enjoy!!!

Love you all guys!!!!
thx for the great job you're doing for every one .

---

### Post by Dalston on 2008-05-24
Thanks so much for this,  I just did a complete reinstall sopcast was the application I was most dreading reinstalling.

---

### Post by cutOff on 2008-05-24
Thanks chunchengch, works like a charm.

---

### Post by chunchengch on 2008-05-24
> **Dalston said:**
> ...sopcast was the application I was most dreading reinstalling.

That is one of the reasons why I made this deb, and I am appreciated that so many friends unacquainted like it.

---

### Post by rockdude on 2008-05-27
I get this from terminal when trying to connect to a channel:

sp-sc: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by jjgomera on 2008-05-27
you must install libstdc++5, so write in a terminal:

sudo aptitude install libstdc++5

---

### Post by rockdude on 2008-05-27
Thank you. Problem solved.

---

### Post by chunchengch on 2008-05-27
> **rockdude said:**
> I get this from terminal when trying to connect to a channel:

sp-sc: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

use the deb file, it will install libstdc++5 and other necessary dependencies for you.

---

### Post by ariel on 2008-05-27
> **chunchengch said:**
> Here is the newest gsopcast 0.4.0, enjoy it!

[COLOR=Red]It is available in Hardy too![/COLOR]

I build a new [ATTACH]70967[/ATTACH], it will install necessary dependencies and execute file of sopcast, it makes installation more simple


PS: I am using 2M ADSL, I find it takes around 50 seconds to connect selected channel, then more 10-20 seconds to open mplayer, then more 2-3 minutes to display the TV content normally.

[ATTACH]63849[/ATTACH]

Any chance of posting and X86_64 package?

---

### Post by jonno on 2008-05-29
> **ariel said:**
> Any chance of posting and X86_64 package?

I 2nd that motion

---

### Post by chunchengch on 2008-05-30
> **ariel said:**
> Any chance of posting and X86_64 package?

I am not the developer of gsopcat, I just packed it as a deb for easy installation, so I can not give any answer about this.

Please leave your request here [http://code.google.com/p/gsopcast/](http://code.google.com/p/gsopcast/)

---

### Post by RamR on 2008-05-31
> **guga31bb said:**
> Yeah I am happily watching now - thank you very much! 

By any chance, do you know how to make links launch directly from FF3? I tried a fix I saw in other thread but it didn't do the trick.

Thanks again!

Bump

I have the same problem connecting sop links in FF3 to the app.  I've followed the instruction and have this line in my about:config;

```
network.protocol-handler.app.sop; user set; string; gsopcast
```

I can copy the link location into the launch bar of gsopcast and then launch it manually, but it would be good if I could get the launch to work automatically just by clicking a link in FF3.

---

### Post by pluckypigeon on 2008-06-04
> **RamR said:**
> Bump

I can copy the link location into the launch bar of gsopcast and then launch it manually, but it would be good if I could get the launch to work automatically just by clicking a link in FF3.

type ```
about:config
``` in the address bar

right click, create new string

type ```
network.protocol-handler.app.sop
```

then a pop up box will pop up type ```
/usr/local/bin/gsopcast
```

make sure /usr/local/bin is where gsopcast is installed. That's where mine is. I have it loading from Firefox 3 fine

---

### Post by pluckypigeon on 2008-06-04
I have a problem. 

When I try an load a sopcast link from an external source I get the message ```
Restarting Monitoring
```
:confused:

Then it just restarts connecting but never connects 
How do I fix this???:(

---

### Post by pluckypigeon on 2008-06-07
anyone?:(

---

### Post by edisoncm on 2008-06-07
Hello,
I have 100%, ur=ok, dr=10k, us=ok, ds=1k & peers=19
Lots of channels at the window above this info, but when I press play I get no player open.
I have player rm=Kaffeine-ontop -geometry 100%:100%
wmv=Kaffeine-ontop -geometry 100%:100%
what am I missing? 
thx
Solved the problem, I removed the end of the rm and wmv.
now is only vlc and it plays fast and nice

---

### Post by pluckypigeon on 2008-06-09
> **pluckypigeon said:**
> I have a problem. 

When I try an load a sopcast link from an external source I get the message ```
Restarting Monitoring
```
:confused:

Then it just restarts connecting but never connects 
How do I fix this???:(

i still have this problem

---

### Post by tim183 on 2008-06-11
> **chunchengch said:**
> I am not the developer of gsopcat, I just packed it as a deb for easy installation, so I can not give any answer about this.

Please leave your request here [http://code.google.com/p/gsopcast/](http://code.google.com/p/gsopcast/)

bump...

---

### Post by p14u5h on 2008-06-15
> **chunchengch said:**
> Here is the newest gsopcast 0.4.0, enjoy it!

[COLOR="Red"]It is available in Hardy too![/COLOR]

I build a new [ATTACH]70967[/ATTACH], it will install necessary dependencies and execute file of sopcast, it makes installation more simple


PS: I am using 2M ADSL, I find it takes around 50 seconds to connect selected channel, then more 10-20 seconds to open mplayer, then more 2-3 minutes to display the TV content normally.

[ATTACH]63849[/ATTACH]



Hi 
You have done a terrific job by making that easy-to-install file. I used to run sopcast on gutsy but when I switched to Hardy, sopcast no longer worked. I tried the package you provided, Sopcast  runs, but do not show any channels. I tried the way you mentioned somewhere changing channel URL [www.sopcast](www.sopcast).... to channel.sopcast.. but still it doesnot show any channels. What could be the reason. I have all the Libstd files as mentioned by you. I used to watch on gutsy, but on hardy its not working.
The problem is am not an expert in linux and started using just few months back
Please help me out. Would be grateful to you.
thanks
Piyush

---

### Post by chunchengch on 2008-06-15
> **p14u5h said:**
> ... but do not show any channels. I tried the way you mentioned somewhere changing channel URL [www.sopcast](www.sopcast).... to channel.sopcast.. but still it doesnot show any channels...

I got this problem sometimes, and really don't know what happened, I think that should be something about the sopcast server, because few minutes or few hours later, gsopcast worked again.

BTW, it is better to use [COLOR="Green"]http://www.sopcast.com/gchlxml[/COLOR]

---

### Post by p14u5h on 2008-06-16
> **chunchengch said:**
> I got this problem sometimes, and really don't know what happened, I think that should be something about the sopcast server, because few minutes or few hours later, gsopcast worked again.

BTW, it is better to use [COLOR="Green"]http://www.sopcast.com/gchlxml[/COLOR]

Hi 
I think you are right. It could be because of the Sopcast server. I tried opening the sopcast.com site but even that is not opening.It looks like, some problem with the server, site etc...

---

### Post by chunchengch on 2008-06-19
If you would like to watch sopcast steaming TV in **[COLOR="Red"]Full-Screen[/COLOR]** mode, you can download [COLOR="Green"]Gmlive[/COLOR] from my new thread [http://ubuntuforums.org/showthread.php?t=832821](http://ubuntuforums.org/showthread.php?t=832821)

[ATTACH]74605[/ATTACH]

---

### Post by sayantandas on 2008-07-02
hi, i have installed both sopcast and gmlive. they installed fine, with no errors. only thing is when i play any channel, i can only hear, cannot see any video. i cannot figure out why this is happening. pls help.

---

### Post by chunchengch on 2008-07-02
> **sayantandas said:**
> hi, i have installed both sopcast and gmlive. they installed fine, with no errors. only thing is when i play any channel, i can only hear, cannot see any video. i cannot figure out why this is happening. pls help.

In gsopcast, if this happens, try to click the [Play] button again to see if the problem is solved.

---

### Post by sayantandas on 2008-07-02
well, i found out that its the problem with mplayer itself. my mplayer mozilla plugin doesnt have video as well. there's only audio. if i remove mplayer plugin , it plays video with some other plugin(may be real player). is there any fix for mplayer video?

---

### Post by sayantandas on 2008-07-02
> **chunchengch said:**
> In gsopcast, if this happens, try to click the [Play] button again to see if the problem is solved.

thanks , i've fixed the issue by recompiling mplayer from source.  there's a workaround which i found out while trying to fix this.  gsopcast gives an option to choose the default player. u can use any player ranging from vlc, kaffaine,gxine. it works with any player capable of playing streaming video. :). Ubuntu & linux rulez

---

