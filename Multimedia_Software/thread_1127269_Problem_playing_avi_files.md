---
title: "Problem playing avi files"
date: 2009-04-16
forum: Multimedia Software
---

### Post by lazy_bones1987 on 2009-04-16
I have been researching about this problem for quite a long time now and strangely theres not a single valid solution (even though this problem has been there for quite some time now)

I'm using Ubuntu 8.10.I'm unable to play any sort of video file (say .avi,divx) in any media player. (VLC,Mplayer,etc)
These players just keep crashing if i try to watch any sort of video file.

After going through the other threads I have installed all sorts of codecs, plugins and performed steps I dont even know of and yet I'm not able to play avi files

However I did find an alternate solution after going through this thread.
[http://ubuntuforums.org/showthread.p...play+avi+files](http://ubuntuforums.org/showthread.p...play+avi+files)

This solution however leaves you with a very pixelated and crappy video quality.

And I have to say that Ubuntu sucks big time because I cant even watch a movie on it!!!

With every version of the distro you guys release, you fix one problem and you create a problem which was not there in the previous version!!!

My specs:
Intel centrino duo 2.0 Ghz
ATI HD Radeon 2300 128 Mb
Ubuntu 8.10 32 bit
160 Gb HDD

---

### Post by lazy_bones1987 on 2009-04-16
I have been researching about this problem for quite a long time now and strangely theres not a single valid solution (even though this problem has been there for quite some time now)

I'm using Ubuntu 8.10.I'm unable to play any sort of video file (say .avi,divx) in any media player. (VLC,Mplayer,etc)

After going through the other threads I have installed all sorts of codecs, plugins and performed steps I dont even know of and yet I'm not able to play avi files

However I did find an alternate ( so called "solution") after going through this thread.
[http://ubuntuforums.org/showthread.p...play+avi+files](http://ubuntuforums.org/showthread.p...play+avi+files)

This solution however leaves you with a very pixelated and crappy video quality.

And I have to say that Ubuntu sucks big time because I cant even watch a movie on it!!!

With every version of the distro you guys release, you fix one problem and you create a problem which was not there in the previous version!!!

---

### Post by _Purple_ on 2009-04-16
Have you tried Totem Movie Player?

---

### Post by gali98 on 2009-04-16
First, not the best title you could have chosen.
Second the simple command
```
sudo apt-get install ubuntu-restricted-extras
```
will install most all codecs you will ever need.
Third, if the video plays, but is pixelated, then it is more than likely pixelated video in the first place.
Fourth, and finally, we don't make ubuntu. We help users. Most devs never even come here. 
Kory

---

### Post by sadicote on 2009-04-16
If you have Intrepid, "sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2". I got this from Ubuntu unleashed, i think...

---

### Post by Simian Man on 2009-04-16
I can play .avis flawlessly and I don't even remember doing anything special for that.  Did you install Ubuntu's restricted formats package?  I forget the name?  What is the error Totem and/or VLC give you?

---

### Post by Dougie187 on 2009-04-16
> **lazy_bones1987 said:**
> And I have to say that Ubuntu sucks big time because I cant even watch a movie on it!!!

With every version of the distro you guys release, you fix one problem and you create a problem which was not there in the previous version!!!

What you are describing here is typical user error. Don't blame the system for what you don't know.

---

### Post by kpkeerthi on 2009-04-16
> **lazy_bones1987 said:**
> I have been researching about this problem for quite a long time now and strangely theres not a single valid solution (even though this problem has been there for quite some time now)

I'm using Ubuntu 8.10.I'm unable to play any sort of video file (say .avi,divx) in any media player. (VLC,Mplayer,etc)

After going through the other threads I have installed all sorts of codecs, plugins and performed steps I dont even know of and yet I'm not able to play avi files

However I did find an alternate ( so called "solution") after going through this thread.
[http://ubuntuforums.org/showthread.p...play+avi+files](http://ubuntuforums.org/showthread.p...play+avi+files)

This solution however leaves you with a very pixelated and crappy video quality.

And I have to say that Ubuntu sucks big time because I cant even watch a movie on it!!!

With every version of the distro you guys release, you fix one problem and you create a problem which was not there in the previous version!!!

This is not going to help you in any way. If you are looking for some help, post the problem detail and we'll be glad to assist you (People offer help in their free time here; so pls be gentle). Otherwise, use what works for you.

---

### Post by riza hylviu on 2009-04-16
ubuntu is great, you need just some patience 
if you want there is a release -superubuntu- it is just ubuntu but with the most restricted extras and plug ins installed. When i first installed ubuntu i had your same problems and i didn even know what synaptic was.
Install it instead of official ubuntu and you can learn ubuntu whithout going mad. the only extra plug in i installed is libdvdcss, couse i couldn't watch dvd. there is wine preinstalled too

---

### Post by Sef on 2009-04-16
Merged threads.  Do not double post, please.   Double posting can result in a warning or infraction being given.

---

### Post by caperpc on 2009-04-16
Ubuntu is the bomb....u just really need to give it a chance...step back and breathe...then continue.

Been away from it for years, actually used Solaris for a while, but am a hard core Ubuntu fan now and I myself am still learning.

anyhow I experienced the same issue...dld the latest greatest codecs and still came in choppy and pixild (totem).....Installed vlc and movies come in great.

o btw...u can use Ubuntu for more than watchin movies.lol
I have it running a web server, ftp server, cctv server, NAS, MySQL db, Blogs, mail servers as well as a personal os which my son is now growing on.
If you keep having issues try linux mce...out of the box works well if you are only interested in media. [http://linuxmce.com/](http://linuxmce.com/)

cheers :popcorn:

---

### Post by lazy_bones1987 on 2009-04-16
> **_Purple_ said:**
> Have you tried Totem Movie Player?

yup I have...and it doesnt work

---

### Post by gali98 on 2009-04-16
Did you try
```
 sudo apt-get install ubuntu-restricted-extras
```
And what kind of video are you trying to play?
Kory

---

### Post by lazy_bones1987 on 2009-04-16
> **gali98 said:**
> First, not the best title you could have chosen.
Second the simple command
```
sudo apt-get install ubuntu-restricted-extras
```
will install most all codecs you will ever need.
Third, if the video plays, but is pixelated, then it is more than likely pixelated video in the first place.
Fourth, and finally, we don't make ubuntu. We help users. Most devs never even come here. 
Kory

Yup...did that..and it doesnt work as well

theres no problem whatsoever with the video...all the videos work fine in windows..

and my frustration is not at you guys...its rather at the developers..why cant they just leave things as it was in the previous version??

if you do a google search on "cant play avi files in ubuntu" you will understand that there are loads of ppl out there who share the same problem and theres no solution for it (even though the problem has been there since the release)

---

### Post by lazy_bones1987 on 2009-04-16
> **Dougie187 said:**
> What you are describing here is typical user error. Don't blame the system for what you don't know.

I'm a complete newbie. (With a bit of unix experience at uni and have used to work with ubuntu 7.10 previously)

I'm not blaming my system. I just expect my system to play a video (avi file??) without having to go through all the trouble of installing codecs and plugins and performing steps that the user would not know of.

This is where windows is still preferred by most of the users out there (I'm not saying windows is good!). Its just that for new users, you expect (basic) things(like watching a movie) to work with minimal effort

---

### Post by SuperSonic4 on 2009-04-16
(If applicable), do you have the proprietary video drivers installed? Also, some videos are stuttery if desktop effects are turned in. In my case the video flashes red unless I turn desktop effects off

A lot of new users tend to blame ubuntu for their hardware compatibility, I was lucky in that most of my stuff works without much effort at all

---

### Post by lazy_bones1987 on 2009-04-16
> **kpkeerthi said:**
> This is not going to help you in any way. If you are looking for some help, post the problem detail and we'll be glad to assist you (People offer help in their free time here; so pls be gentle). Otherwise, use what works for you.

I'm sorry...i have posted this problem loads of times! and not often than not I havent had any replies to my threads and no solution to the problem

and the only way to catch the attention of the forum users is to have this heading for the topic

---

### Post by gali98 on 2009-04-16
Tell you what.
Do you have any videos that are short clips that you could upload somewhere so we could test? We might figure out the problem.
Kory

---

### Post by lazy_bones1987 on 2009-04-16
> **SuperSonic4 said:**
> (If applicable), do you have the propiertry video drivers installed? Also, some videos are stuttery if desktop effects are turned in. In my case the video flashes red unless I turn desktop effects off

havent tried that...but i did see someone else suggesting the same method to a different user for the same problem, but it didnt work out

---

### Post by JohnFH on 2009-04-16
> **lazy_bones1987 said:**
> I'm sorry...i have posted this problem loads of times! and not often than not I havent had any replies to my threads and no solution to the problem


That might have something to do with your attitude along with the complete lack of information you give about your problem.

---

### Post by lazy_bones1987 on 2009-04-16
> **gali98 said:**
> Tell you what.
Do you have any videos that are short clips that you could upload somewhere so we could test? We might figure out the problem.
Kory

they are normal avi files. Put in any video file (even a dvd) and all the media players will just crash if you try to play it

and as i mentioned before you can watch the video if you change the output to x11 and its rather bad quality

---

### Post by Ericyzfr1 on 2009-04-16
> **lazy_bones1987 said:**
> I'm a complete newbie. (With a bit of unix experience at uni and have used to work with ubuntu 7.10 previously)

I'm not blaming my system. I just expect my system to play a video (avi file??) without having to go through all the trouble of installing codecs and plugins and performing steps that the user would not know of.

This is where windows is still preferred by most of the users out there (I'm not saying windows is good!). Its just that for new users, you expect (basic) things(like watching a movie) to work with minimal effort

I never watched a movie with media player on Windows, I always installed a different player so there is also additional work to be done.
I may be wrong, but I do not think Win Media Player is the prefered media player for the majority of MS users.

---

### Post by lazy_bones1987 on 2009-04-16
> **JohnFH said:**
> That might have something to do with your attitude along with the complete lack of information you give about your problem.

pardon me if i have a bad attitude, but only if you do go through the pain and trouble which i'm going through, you would understand the situation!

---

### Post by lazy_bones1987 on 2009-04-16
> **Ericyzfr1 said:**
> I never watched a movie with media player on Windows, I always installed a different player so there is also additional work to be done.
I may be wrong, but I do not think Win Media Player is the prefered media player for the majority of MS users.

yupp I know..I use vlc and k-lite...but atleast i can watch videos in windows without doing anything

In ubuntu the media players just keep crashing if i try to play a video file (.avi,divx,etc)

---

### Post by JohnFH on 2009-04-16
> **lazy_bones1987 said:**
> they are normal avi files. Put in any video file (even a dvd) and all the media players will just crash if you try to play it

and as i mentioned before you can watch the video if you change the output to x11 and its rather bad quality

I can tell you now that your problem has nothing to do with the media players you are using.  It's to do with your graphics setup.  What graphics card or chipset do you have and what drivers are you using for them?

---

### Post by gali98 on 2009-04-16
Well don't put the flak on us. We're just trying to help. :)
This sounds like a video issue. First, tell us what video card you have.
```
lshw -c Video
```
Next, confirm that you have gone to 
System-Administration->Hardware Drivers
(It may be named restricted drivers depending on what version you have)
And see if there are any video drivers you are can enable.
Also for future reference what version are you on?
(Intrepid, Hardy, Jaunty?)
Kory

---

### Post by kazuya on 2009-04-16
Hey lazy, I would not say you are not a little correct to be frustrated. I do sometimes too as I do with all other OSes. expectation for Ubuntu from me and I am sure you are very high. So I agree with your complaint, but not the approach. 
I think more should be done to make this media issue easier for new users. Even I a somewhat expereinced user having played with linx in general for about 6 years now, still nod my head sometimes.

We know the alternative is worse. I think you are just venting. However, by understanding why sometimes things happen, you form a better grasp of what happens in your system.

I am having similar issue as you at the moment. One question I would ask, Are you using Ubuntu 64 bit or just Ubuntu 32 bit.?

---

### Post by lazy_bones1987 on 2009-04-16
> **JohnFH said:**
> I can tell you now that your problem has nothing to do with the media players you are using.  It's to do with your graphics setup.  What graphics card or chipset do you have and what drivers are you using for them?

oh...

I have ATI HD Radeon 2300 128Mb

and the drivers...i'm not really sure...I might be using the restricted drivers...I didnt install any drivers specifically

---

### Post by caperpc on 2009-04-16
> **gali98 said:**
> Tell you what.
Do you have any videos that are short clips that you could upload somewhere so we could test? We might figure out the problem.
Kory

great idea...using istanbul right?

---

### Post by kazuya on 2009-04-16
Thanks JohnFH, Yo and Lazy may have pointed me to my earlier suspicion. On my other laptop with nvidia videocard, everything works awesomely. The laptop I have my issue on has an ATI videocard. So does installing proper ati driver via restricted solve the problem wi the media player.

I have desktop effects turned on. Maybe I need to reinstall ati driver? Is envy a better alternative?

---

### Post by lazy_bones1987 on 2009-04-16
> **gali98 said:**
> Well don't put the flak on us. We're just trying to help. :)
This sounds like a video issue. First, tell us what video card you have.
```
lshw -c Video
```
Next, confirm that you have gone to 
System-Administration->Hardware Drivers
(It may be named restricted drivers depending on what version you have)
And see if there are any video drivers you are can enable.
Also for future reference what version are you on?
(Intrepid, Hardy, Jaunty?)
Kory

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: M71 [Mobility Radeon X2100]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: ce
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

and theres a proprietary driver which I have not activated and I dont want to activate it because the last time I activated it in 8.04 I ended up with some daemon failure and I dont want to go through the trouble again

---

### Post by lazy_bones1987 on 2009-04-16
> **kazuya said:**
> Thanks JohnFH, Yo and Lazy may have pointed me to my earlier suspicion. On my other laptop with nvidia videocard, everything works awesomely. The laptop I have my issue on has an ATI videocard. So does installing proper ati driver via restricted solve the problem wi the media player.

I have desktop effects turned on. Maybe I need to reinstall ati driver? Is envy a better alternative?

can you let me know if it works if you install the proprietary driver? I dont know if its supposed to be activated though...

---

### Post by lazy_bones1987 on 2009-04-16
> **kazuya said:**
> Hey lazy, I would not say you are not a little correct to be frustrated. I do sometimes too as I do with all other OSes. expectation for Ubuntu from me and I am sure you are very high. So I agree with your complaint, but not the approach. 
I think more should be done to make this media issue easier for new users. Even I a somewhat expereinced user having played with linx in general for about 6 years now, still nod my head sometimes.

We know the alternative is worse. I think you are just venting. However, by understanding why sometimes things happen, you form a better grasp of what happens in your system.

I am having similar issue as you at the moment. One question I would ask, Are you using Ubuntu 64 bit or just Ubuntu 32 bit.?

hey I totally understand what you mean...and yes I'm just venting out my frustration..just cant solve this stupid issue

I'm using ubuntu 8.10 on a 32 bit machine

---

### Post by bobmatino17 on 2009-04-16
did you try the open source equivalent? plus AVI's are microsoft, they dont have to play well on Linux.

---

### Post by lazy_bones1987 on 2009-04-16
> **bobmatino17 said:**
> did you try the open source equivalent? plus AVI's are microsoft, they dont have to play well on Linux.

hmm havent tried any...all the files which i have are of .avi, divx, xvid

yeah i do know that avi is ms based...but arent there tons of videos (atleast thats what i think) in avi formats??

---

### Post by digitalmonk on 2009-04-16
@lazy_bones : 
i am also new to ubuntu, have been using ubuntu since a couple of months,i have upgraded from intrepid to jaunty beta recently, all i can tell u my experience has been better with the new release.i have also faced issues,but could solve them by doing some google search and posting my queries on this forum but i think it is not justified in blaming the OS. i use ubuntu as i cannot afford a genuine copy of windows vista. why are you sticking to ubuntu,go ahead and use microsoft xp/vista or say osx if u are on a mac platform.
please understand this a effort of developers who act as a community developing and upgrading various softwares just out of passion and people like us who visit this forum and help our fellow ubuntoids ;).if u are using a free open source os, be thankful instead of bad mouthing.

---

### Post by lazy_bones1987 on 2009-04-16
> **SuperSonic4 said:**
> (If applicable), do you have the proprietary video drivers installed? Also, some videos are stuttery if desktop effects are turned in. In my case the video flashes red unless I turn desktop effects off

A lot of new users tend to blame ubuntu for their hardware compatibility, I was lucky in that most of my stuff works without much effort at all

oh wow..it works if i disable the desktop effects...so now i have to disable the effects every time i want to watch a movie?

and no i havent activated the proprietary drivers...scared of doing it as i have had some pretty bad experiences after doing it in 7.10

---

### Post by SuperSonic4 on 2009-04-16
It's possible, It's surprisingly how quickly one gets used to it, I don't bother turning them on any more. However, installing the proprietary drivers may solve this as ATI's driver is likely to be better than the Open Source one.

If it goes wrong you can either back up xorg.conf and use a terminal to bring it back which should work ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` and ```
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
``` to restore it.

You can also use xfix from the recovery menu (via grub) which should reset x

---

### Post by lazy_bones1987 on 2009-04-16
> **digitalmonk said:**
> @lazy_bones : 
i am also new to ubuntu, have been using ubuntu since a couple of months,i have upgraded from intrepid to jaunty beta recently, all i can tell u my experience has been better with the new release.i have also faced issues,but could solve them by doing some google search and posting my queries on this forum but i think it is not justified in blaming the OS. i use ubuntu as i cannot afford a genuine copy of windows vista. why are you sticking to ubuntu,go ahead and use microsoft xp/vista or say osx if u are on a mac platform.
please understand this a effort of developers who act as a community developing and upgrading various softwares just out of passion and people like us who visit this forum and help our fellow ubuntoids ;).if u are using a free open source os, be thankful instead of bad mouthing.

hey there,
ok before you judge me on my topic heading, please have a look at this link:
[http://bash.org/?152037](http://bash.org/?152037)
it was on reddit

and NO I DONT LIKE MS! I have been using (or atleast TRYING) to use some version of ubuntu so far. I had graphic problems in 7.10, wireless problems in 8.04 and now video issues with 8.10

But the thing is, I have been trying to use it!

---

### Post by lazy_bones1987 on 2009-04-16
> **SuperSonic4 said:**
> It's possible, It's surprisingly how quickly one gets used to it, I don't bother turning them on any more. However, installing the proprietary drivers may solve this as ATI's driver is likely to be better than the Open Source one.

If it goes wrong you can either back up xorg.conf and use a terminal to bring it back which should work ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` and ```
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
``` to restore it.

You can also use xfix from the recovery menu (via grub) which should reset x

OH NO! No way I'm going to do that! I faced loads of issues coz of that and I had the black screen error while installing 8.10. Had two sleepless nights in trying to find a solution. I dont know if i can do that again!

---

### Post by lazy_bones1987 on 2009-04-16
to everyone who is angry at me for having such a harsh topic heading

please have a look at this link

[http://bash.org/?152037](http://bash.org/?152037)

I just hope you guys dont stop replying now that I have told you why!

---

### Post by SuperSonic4 on 2009-04-16
Fair enough I suppose and what you put is largely true even if nobody will admit it ;)

---

### Post by lazy_bones1987 on 2009-04-16
> **SuperSonic4 said:**
> Fair enough I suppose and what you put is largely true even if nobody will admit it ;)

hehe...well i'm sure if i had created a normal thread posting my problem (which i did twice!) I might not have had even 10 replies!

btw..
as i mentioned before, I'm a newbie in linux...

with the backup and copy method you have mentioned, you want me to perform both the copy and move and then enable the proprietary graphics?

what if i cant get into terminal after enabling them. How do i restore my settings in that case?

---

### Post by JohnFH on 2009-04-16
> **lazy_bones1987 said:**
> oh wow..it works if i disable the desktop effects...so now i have to disable the effects every time i want to watch a movie?

and no i havent activated the proprietary drivers...scared of doing it as i have had some pretty bad experiences after doing it in 7.10

so now it's up to you to fix it (install proprietary drivers) or workaround it (turn off desktop effects).  Personally my desktop effects are always turned off anyway because I don't like them, even though my graphics setup can easily handle it.  

Also please note that ATI graphics cards always seem to cause trouble on linux, but NVidia have better support for linux and that's why their cards are preferred.

---

### Post by JohnFH on 2009-04-16
> **lazy_bones1987 said:**
> 
with the backup and copy method you have mentioned, you want me to perform both the copy and move and then enable the proprietary graphics?

what if i cant get into terminal after enabling them. How do i restore my settings in that case?

As mentioned before, this is the backup command, so do this and then try enabling the proprietary drivers:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```

This is the restore command to use if anything goes wrong:
```

sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

```

If the worst happens you will not be able to start X and you will have a console prompt instead.  That's ok too because you can just type in the restore command above and then reboot.  You will always have access to a terminal/console.

---

### Post by kazuya on 2009-04-16
lazy has some valid points. I am still having issues with palying videos after enabling proprietary restricted ati driver. I  start vlc or totem-player and they simply exit without warning.

To the folk that say go to Microsoft.. are you kidding.? No way I'm I going that route again. I use windows xp/vista for only one thing, .....gaming...

For my day to day use, video watching, editing, social networking ,.  etc., its linux and real life. lol

This issue is a major one for many users with laptops or desktops that use ati videocards.. There needs to be an easier way to get this going for users.

---

### Post by lazy_bones1987 on 2009-04-16
> **kazuya said:**
> lazy has some valid points. I am still having issues with palying videos after enabling proprietary restricted ati driver. I  start vlc or totem-player and they simply exit without warning.

To the folk that say go to Microsoft.. are you kidding.? No way I'm I going that route again. I use windows xp/vista for only one thing, .....gaming...

For my day to day use, video watching, editing, social networking ,.  etc., its linux and real life. lol

This issue is a major one for many users with laptops or desktops that use ati videocards.. There needs to be an easier way to get this going for users.

alright...i guess i'm not enabling proprietary drivers then

---

### Post by gali98 on 2009-04-16
Look... Testing propreitary drivers is very easy, and not that much of a pain if you know what you are doing.
If you print these commands out and then try it, there is no way you can mess up. All the propreitary driver does is edit your xorg.conf. If you make a backup then you're safe. If it fails, all you have to do is boot into recovery mode, run one command and reboot and it will be back to the way it was before. Here is a simple list that you can run, and everything will be okay.

1. Open the terminal. (Applications->Accessories->Terminal)
2. Type in this command and hit enter.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
3. For good measure we will back it up in one other place.
```
sudo cp /etc/X11/xorg.conf ~/xorg.conf.bak
```
4. Now go Enable the Restricted Driver. (System->Administration->Hardware Drivers)
5.After the Applications finishes installing the driver, reboot.
6. If the login screen comes up, then great! Test it out to see if the videos work with compiz. If not, then continue on.
7.Restart the machine and when when the Grub loading screen comes up - Hit the Esc button.
8. Move the bar down to the entry labeled Recovery Mode.
9. At this point it will boot up. Depending on your Version of ubuntu it will either drop you to a terminal, or will come up with a menu. If it does come up with the menu, choose the Terminal option. (It may ask you for your password. If your password does not work, press ctrl+D)
10. At the terminal type this command:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
(and enter your password when promted.)
11. Reboot, and your video settings will be restored and  the proprietary driver will be disabled.

See? Easy Right.
You can't ever fix things if you don't take chances :)
Kory

---

### Post by lazy_bones1987 on 2009-04-17
> **gali98 said:**
> Look... Testing propreitary drivers is very easy, and not that much of a pain if you know what you are doing.
If you print these commands out and then try it, there is no way you can mess up. All the propreitary driver does is edit your xorg.conf. If you make a backup then you're safe. If it fails, all you have to do is boot into recovery mode, run one command and reboot and it will be back to the way it was before. Here is a simple list that you can run, and everything will be okay.

1. Open the terminal. (Applications->Accessories->Terminal)
2. Type in this command and hit enter.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
3. For good measure we will back it up in one other place.
```
sudo cp /etc/X11/xorg.conf ~/xorg.conf.bak
```
4. Now go Enable the Restricted Driver. (System->Administration->Hardware Drivers)
5.After the Applications finishes installing the driver, reboot.
6. If the login screen comes up, then great! Test it out to see if the videos work with compiz. If not, then continue on.
7.Restart the machine and when when the Grub loading screen comes up - Hit the Esc button.
8. Move the bar down to the entry labeled Recovery Mode.
9. At this point it will boot up. Depending on your Version of ubuntu it will either drop you to a terminal, or will come up with a menu. If it does come up with the menu, choose the Terminal option. (It may ask you for your password. If your password does not work, press ctrl+D)
10. At the terminal type this command:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
(and enter your password when promted.)
11. Reboot, and your video settings will be restored and  the proprietary driver will be disabled.

See? Easy Right.
You can't ever fix things if you don't take chances :)
Kory

hey! 
Thanx for your help, But when i try to activate the proprietary drivers, it just doesnt download (theres no problem with my internet connection).
So I guess I will have to find a different way for it.

---

### Post by gali98 on 2009-04-17
hmmm... Okay, try going to 
System->Administration->Software Sources
and change the Server (Download From:)
Either to Server from the United States or Main Server (i.e. flip it from whichever you have.)
And the when you close it out it should ask to reload. Go ahead and do that then try and enable the restricted driver again.
Kory

---

### Post by lazy_bones1987 on 2009-04-18
Alright...tried downloading it again and it worked.

So now with the restricted drivers on, I tried watching the video with the desktop effects enabled. The video clarity is not pixelated however, I do get flashy lines in the screen.

But If I turn the effects off, it works fine.

Thanx to all who helped me out here! 

p.s. I dont know how to mark this thread as solved.

---

### Post by _Purple_ on 2009-04-18
> **lazy_bones1987 said:**
> 

p.s. I dont know how to mark this thread as solved.

You can see the "Edit Tags" marked with black in the attached image. Click "Edit Tags", type "SOLVED" under "Add Tags" and hit "Save Changes".

---

### Post by gali98 on 2009-04-18
Good Deal! At least you got the drivers... Maybe in Jaunty, the video issue will be fixed where compiz can be enabled...
Kory

---

