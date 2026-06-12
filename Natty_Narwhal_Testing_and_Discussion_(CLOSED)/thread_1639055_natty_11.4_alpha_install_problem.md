---
title: "natty 11.4 alpha install problem"
date: 2010-12-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Amroozy on 2010-12-06
Hello there..
spent 3 days trying to install Ubuntu 11.4 alpha and i totally failed.. 
started with Ubuntu 10.10 clean install and upgrade to 11.4 but i got too many bugs "too many applications didn't start the most annoying one for me was the software center" .. also  installed google chrome and it didn't start as well. 

after all i started to download Ubuntu 11.4 desktop CD and make fresh install.. sadly i didn't get any luck to make it work.. wubi didn't work cuz it was 10.10 version not 11.4.. tried to make startable USB from the iso i downloaded and it didn't work.. 

next day i downloaded another version of Ubuntu alpha 11.4 "for whom who don't know it's updated daily" .. so i downloaded 05-December one.. i was lucky to find that the wubi version working BUT.. it kept giving me "wubildr" error.. so i tried again to make a startable USB to setup Ubuntu and it stuck somewhere after booting.. so i decided to burn this iso on DVD and try .. but no luck again i got some screens for it...
[http://yfrog.com/jdubuntu20101206124804p](http://yfrog.com/jdubuntu20101206124804p)   
then it stuck at this screen 
[http://yfrog.com/66ubuntu20101206125038p](http://yfrog.com/66ubuntu20101206125038p)

i tried everything to make it work.. i tried two different PCs 
AMD/Intel-- external/internal VGA card.. also i tried on VMware..
as i mentioned before "Totally failed"
i looked at forums and googled my problems to fined out if anyone else facing them.. n luck.. i tried to copy/paste "wubildr" from working "10.10 Ubuntu iso" i passed the error then the install kept auto restarting.. 

well.. i will download the 06-December version and this will be my last try till the final release.. i hope it will work.. i really like the Unity desktop.. and i like to help "testing/bug reporting"...

before you start to flame on me "if you planning to :P".. I am MCSE/MCITP/CCNA... and i have good knowledge of linux.. was using OpenSuse for a year or more.. before it i was trying redhat/fedora as well.. 

at last i saw a video on Youtube for 11.4 running.. good to know that someone on earth has it running on his machine..

---

### Post by bcbc on 2010-12-06
You should post Natty inquiries in the [Natty forum]("http://ubuntuforums.org/forumdisplay.php?f=394") 

There's still some work to be done for wubi... See this [http://ubuntuforums.org/showthread.php?t=1636138](http://ubuntuforums.org/showthread.php?t=1636138)

I previously had a wubi 10.10 that I upgraded to Natty a while ago, but it was pre Alpha1 and worked fine but was uninteresting.

---

### Post by popeblack on 2011-01-11
Hi,

I am new to Ubuntu and this forum and I would be very grateful for a bit of advice. 

[I] just tried to upgrade to 10.04 and somehow managed to upgrade to 11.4. It seems to be working ok except for the fact I can't upgrade, open the Ubuntu Software Center, and when I try and do upgrades through the terminal, I can't type my password in. It just won't let me. 


I'm not really a computer geek but instead of going through the hassle of reinstalling 10.04, I've decided to stick it out.

Anyone had the above problems or have any advice?

SLÄCK/LÜCK,
PopeBlack
[/I]

---

### Post by bcbc on 2011-01-11
EDIT: @popeblack
There is a bug - someone updated the wrong repository so Maverick says it's Natty 11.04, but it's not. 

You can check by doing this from terminal (CTRL+ALT+t):
```
lsb_release -a
```

It will tell you Release: 10.10
Codename: maverick

Unless you really upgraded to 11.04, but this is unlikely. 

I believe it's just that About text that says it's Natty - nothing material in 10.10 is effected.

Not really sure what the cause of your inability to update or open Software centre is: what is the error you are getting?

---

### Post by amjjawad on 2011-01-11
I'm sorry if this will sound VERY negative but if I were you, I would never bother with 11.4 because:

1) it's alpha version so bugs/errors are so much expected.

2) 11.4 uses Unity and if they will confirm that and will drop GNOME then I'm looking for a better alternative from now. I don't need to use that kind of Desktop Manager.

> Yeah, I know I might be able to change Unity to whatever I like but why would I even bother with that while there are tons of other alternatives? However, that's my personal opinion.

My advice: Use it from LiveUSB. Or perhaps install it using Virtual Box?

---

### Post by cariboo on 2011-01-11
> **amjjawad said:**
> I'm sorry if this will sound VERY negative but if I were you, I would never bother with 11.4 because:

1) it's alpha version so bugs/errors are so much expected.

2) 11.4 uses Unity and if they will confirm that and will drop GNOME then I'm looking for a better alternative from now. I don't need to use that kind of Desktop Manager.

> Yeah, I know I might be able to change Unity to whatever I like but why would I even bother with that while there are tons of other alternatives? However, that's my personal opinion.

My advice: Use it from LiveUSB. Or perhaps install it using Virtual Box?

Please quit spreading mis-information, Unity works on top of Gnome, and the classic interface is still available, at the login screen.

---

### Post by amjjawad on 2011-01-11
> **cariboo907 said:**
> Please quit spreading mis-information, Unity works on top of Gnome, and the classic interface is still available, at the login screen.

That was NOT mis-information, that was my own personal opinion, period. Sorry if that sounded too negative.

I already posted my suggestion to the OP.

:)

---

### Post by tokyobadger on 2011-01-11
I think cheese smells funny = opinion

Cheese is made of carrots and superglue = misinformation

You posted both opinion and misinformation.

---

### Post by cariboo on 2011-01-11
> 2) 11.4 uses Unity and if they will confirm that and will drop GNOME then I'm looking for a better alternative from now. I don't need to use that kind of Desktop Manager.

This looks like mis-information to me.

---

### Post by amjjawad on 2011-01-11
Again, I did not mean that but if that sounds "mis-information", feel free to use your admin-tools to delete it or anything you want :)

Sorry, perhaps I'm totally out of mode today :(

Shall I remove it or what? I don't want to mislead anyone!!!

---

### Post by cariboo on 2011-01-11
You are entitled to your opinions, I won't delete anything. It's just that we see some many people saying that gnome will be dropped, when it isn't true. All your favorite gnome applications will still work just like they did in earlier versions. 

If you really want to see what how Natty works, I would suggest installing virtualbox 4.0 and try Natty out, that way you can post informed opinions. :)

---

### Post by amjjawad on 2011-01-11
> **cariboo907 said:**
> If you really want to see what how Natty works, I would suggest installing virtualbox 4.0 and try Natty out, that way you can post informed opinions. :)

That what I already suggested to the OP in Post#5

> **amjjawad said:**
> My advice: Use it from LiveUSB. Or perhaps install it using Virtual Box?

Again, sorry if I caused any issue. Just ignore my posts. I'm totally out of my mind and mood today.

Logging off :)

---

### Post by popeblack on 2011-01-12
AHA! This is what it is. It is 10.10 and not 11.4. 


> **bcbc said:**
> EDIT: @popeblack
There is a bug - someone updated the wrong repository so Maverick says it's Natty 11.04, but it's not. 

You can check by doing this from terminal (CTRL+ALT+t):
```
lsb_release -a
```It will tell you Release: 10.10
Codename: maverick

Unless you really upgraded to 11.04, but this is unlikely. 

I believe it's just that About text that says it's Natty - nothing material in 10.10 is effected.

Not really sure what the cause of your inability to update or open Software centre is: what is the error you are getting?

---

### Post by Nebutron on 2011-01-21
> **popeblack said:**
> Hi,


[I] just tried to upgrade to 10.04 and somehow managed to upgrade to 11.4. It seems to be working ok except for the fact I can't upgrade, open the Ubuntu Software Center, 

SLÄCK/LÜCK,
PopeBlack
[/I]

I have a similar issue right now and am unable to use the software center.  However, I am able to install anything normally using symaptic.  You may be able to also.

---

### Post by cariboo on 2011-01-21
> **Nebutron said:**
> I have a similar issue right now and am unable to use the software center.  However, I am able to install anything normally using symaptic.  You may be able to also.

Are you sure you're running Natty, open a terminal and type:

> cat /etc/lsb-release

and paste the results in your next post.

the output should look like this:

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"

```

if you are running Natty.

---

### Post by Blackleker on 2011-03-01
Hello your download on a daily basis an update with zsync and avoid you  you can download the iso again I have to try sooner or later will be an  update that will allow you to install it

---

### Post by jerrylamos on 2011-03-01
> **Blackleker said:**
> Hello your download on a daily basis an update with zsync and avoid you  you can download the iso again I have to try sooner or later will be an  update that will allow you to install it

As of second update to Natty Build on 28 Feb install is working again with ubiquity update 2.5.19

[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)

I think there's a 1 March update in process will try that too when it is ready.  Images are oversized so I use a USB stick.

Note, still LOTS of Alpha type bugs in Unity 3D.  I don't like Unity 3D at all but I'm testing looking for bugs so I'm trying to use it anyway (ugh. Obviously I'm not an Apple fan).

Good luck, Jerry

---

