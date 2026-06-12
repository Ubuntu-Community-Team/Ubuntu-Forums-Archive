---
title: "Just upgraded to 10.10 from .04 and now it wont boot. Help!"
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Iniquit-e on 2010-09-21
Well, it DOES boot, but it's weird. Normally I select the OS in the boot menu and then it loads up the login screen, I type in my password and bam, we're in. 

Now, for whatever reason, I select the OS and it acts like it is loading the login screen but then it goes to something that looks like the terminal or whatever. It has my laptop name (brandon-laptop) and asks for a login, then password. When I type "Brandon" (my login name for ubuntu) and my password, it goes like I am actually using the terminal.

How do I get it to boot NORMAL, as in with the login screen and everything displayed? I am computer illiterate with Ubuntu (windows user trying to crossover, ha) and know nothing about terminal and all these commands. Why wont it boot to the colorful login screen anymore? Why is it booting into a bland black screen with terminal stuff? Is there a way to just 'erase' the boot and go back to how it was? 

Thanks.

(note: I upgraded this morning to 10.10. I was late to work so I didn't stick around for the entire procoss. It got like halfway (it hadn't restarted or anything yet) before I left. My fiance might have come home and seen the screen and being even more computer illiterate than me, she could have pushed a bunch of keys and messed something up. I don't know. ) (note again: I am using windows right now to type this, that's how I got here)

---

### Post by uRock on 2010-09-21
Moved to MM Testing & Discussion, as 10.10 is still in the beta testing phase.

When you log in via the terminal screen and enter the **startx** command does it start or return an error message?

---

### Post by SmokeyThePanda on 2010-09-21
Try installing a login manger. GDM if you have Gnome, KDM if you have KDE, XDM if you want something light and looks don't matter, and you can also try Slim, which is kinda sexy. Your login manager may have gotten deleted in the upgrade, or something. However, what you are referring to is called a command line login, I believe. To get it running from the command line, just type in "startx" and you're there, unless you've figured that out. Honestly, alot of people don't use a login manager because it takes up a few system resources.

---

### Post by Iniquit-e on 2010-09-21
It gives me an error. It was way too much to write down and type here, but I did see something about nvidia in there I think. Does that matter?

EDIT: I am referring to using startx after I type my login and pass.

---

### Post by Rasa1111 on 2010-09-21
Consider it a lesson. 

 Did you even try 10.10 from a disc before upgrading? 

 You realize 10.10 is still in beta testing, yeah? 

I had the same problem you are explaining about a week ago,
only I could boot into 10.10 at first, until I ran "partial upgrade"..
then I couldnt get past shell.  
[ the black "terminal like screen" youre seeing.]

i didnt know how to fix it so i just reinstalled 10.10 on the same partition, and avoided the partial upgrade when it was offered. 

 Im not sure how to recover your desktop back from here, 
So my apologies. 

But someone will come along with better info im sure. 

 In regards to the 'lesson' .. lol

 From now on, you should create a disc, with the version you are wanting to upgrade to,
and make sure everything works as it should before installing. 

 It is also, usually wiser to just do the install from the CD, rather than doing the "upgrade" from update manager. 

 good luck mate.

---

### Post by Iniquit-e on 2010-09-21
What?! So you are telling me I am basically screwed and because I upgraded the way the official Ubuntu site told me to, I am now paying the price?! I understand it is still in Beta, but this is a little bit much. There has got to be a way to fix this and get it working normal again.

---

### Post by Rasa1111 on 2010-09-21
uh, no, I didnt say you were screwed. 

 and i did say someone more knowledgeable would be able to help you,
just not me.
 I just told you my recent situation and I how i resolved it.

but there is always "a way". 
and usually always more than just one way. 

If you read the other posts,
it doesnt quite sound like 'youre screwed', does it?

---

### Post by SmokeyThePanda on 2010-09-21
Honestly, there is a reason why it's called beta...With Debian, it's alright to use the testing and unstable versions, as long as you understand the risks that come with it..I would never upgrade Ubuntu until the next version is stable, especially since 10.04 Lucid Lynx was like a benchmark, sorta. Though, normally, my solution up there would work. :p I haven't used Ubuntu in forever, so I don't know what's stable and what's not.

---

### Post by uRock on 2010-09-21
Lets stay positive folks.

> [CENTER]***A computer is a means to an end. The person you're helping probably cares mostly about the end. This is reasonable.* **[/CENTER]
 [CENTER]***By  the time they ask you for help, they've probably tried several things.  As a result, their computer might be in a strange state. This is  natural.***[/CENTER]


---

### Post by Iniquit-e on 2010-09-21
Ugh. This sucks. I just want my system to friggan work again. 10.04 worked great, I loved EVERYTHING about it and it had just about swayed me to get rid of Windows altogether. Boy am I glad I didn't do that.... Had I known there was a chance that my computer wouldnt boot up right, I wouldn't have even chanced installing the upgrade. And I wouldn't be so sour about it if it wasn't the default version on the OFFICIAL Ubuntu site right now and when I followed the official sites directions (as in not using the cd, but just installing with the update manager thing) it does this.

Not to strike a low blow and be THAT guy, but honestly - you would never see this happen with Windows or Mac. Even if they had a beta version out being used, it wouldn't be their default option and you can sure as heck be sure it would at least boot right before ruining your day, ha. 

Anyways, let me know what I need to do or what information you guys need from me and I will get it to ya. Thanks again. Sorry for the frustration.

---

### Post by Iniquit-e on 2010-09-22
[[IMG]http://img25.imageshack.us/img25/6208/092110225200.th.jpg[/IMG]](http://img25.imageshack.us/i/092110225200.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

Here is the screen I get after startx

---

### Post by uRock on 2010-09-22
When W7 came out, it crashed many of systems. There are lots of blogs and forums full of those.

If the startx doesn't work like I am sure it won't then, please be patient and someone may be able to help you out.

At the grub screen can you select the restore kernel? If yes, can you give it a try and see if it can repair the system?

I have had a bad upgrade experience in the past and I know it isn't fun.

---

### Post by Iniquit-e on 2010-09-22
> **uRock said:**
> When W7 came out, it crashed many of systems. There are lots of blogs and forums full of those.

If the startx doesn't work like I am sure it won't then, please be patient and someone may be able to help you out.

At the grub screen can you select the restore kernel? If yes, can you give it a try and see if it can repair the system?

I have had a bad upgrade experience in the past and I know it isn't fun.

Restore kernal? What is that? Sorry, I am BAD when it comes to this stuff.

---

### Post by uRock on 2010-09-22
Do you get a grub menu or are you not dual booting?

---

### Post by Iniquit-e on 2010-09-22
> **uRock said:**
> Do you get a grub menu or are you not dual booting?

Yea I do. I just went to it and I didn't see anything remotely like restore kernel anywhere. I have the options for ubuntu with linux, the memory test stuff, and then the options for Windows.

---

### Post by uRock on 2010-09-22
You don't have either of the choices with the red arrows? If not, then I am not sure what else to try.

---

### Post by mc4man on 2010-09-22
Maybe try returning to nouveau, then see about restricted drivers

Get to the login but **don't run startx**
(you may want to try thru the recovery menu, if you get to it then choose the 1st. option, then login

Anyway after login run each of these in order (5 separate commands in total

```
sudo update-alternatives --config gl_conf
```

Pick the alternative provided by mesa (enter the number

```
sudo ldconfig
sudo update-initramfs -u
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_old
sudo reboot
```

---

### Post by Iniquit-e on 2010-09-22
> **uRock said:**
> You don't have either of the choices with the red arrows? If not, then I am not sure what else to try.

Oh those, yea I have those. I tried one of them once I realized there was a problem, to see what I could do and I didn't see any options in there that I thought would help me, but I could be wrong. I will double check and try again while I am trying the other suggestion by mc4man quick.

---

### Post by Iniquit-e on 2010-09-22
> **mc4man said:**
> Maybe try returning to nouveau, then see about restricted drivers

Get to the login but **don't run startx**
(you may want to try thru the recovery menu, if you get to it then choose the 1st. option, then login

Anyway after login run each of these in order (5 separate commands in total

```
sudo update-alternatives --config gl_conf
```Pick the alternative provided by mesa (enter the number

```
sudo ldconfig
sudo update-initramfs -u
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_old
sudo reboot
```

Oh wow, this actually worked! Thanks a ton! This is a huge sigh of relief, I am so glad I was able to get back into Ubuntu normally. I have a bunch of a non-replaceable pictures from my last deployment overseas saved on the computer. Now I have them backed up (it was the first thing I did when I got back into Ubuntu).

Now that fixing that is out of the way, time for a sub-question: Is it possible to switch back to 10.04 LTS? I don't feel very confident using this Beta anymore, at least not until it's "stable" as you guys put it.

---

### Post by manuw2009 on 2010-09-22
Hi,

Yep, failed upgrades are a real pain...unfortunately, they DO happen sometimes.
Looks like you're either using the wrong graphic card driver or that the nvidia driver isn't properly installed.

I would try the following :

```

sudo dpkg-reconfigure xserver-xorg

```try to pick the "vesa" driver then, 
```

sudo reboot

```this should enable to boot properly with a graphical user interface.
You should then check in synaptics that nvidia packages are properly installed

---

### Post by VMC on 2010-09-22
> **Iniquit-e said:**
> ...
Now that fixing that is out of the way, time for a sub-question: Is it possible to switch back to 10.04 LTS? I don't feel very confident using this Beta anymore, at least not until it's "stable" as you guys put it.

That would be very difficult. This question has been asked before, and usually without much success. You have updated libraries that are now Maverick.

Why are you not comfortable now using Maverick? If its your video display, you could try updating using the latest driver.

---

### Post by uRock on 2010-09-22
> **Iniquit-e said:**
> Oh wow, this actually worked! Thanks a ton! This is a huge sigh of relief, I am so glad I was able to get back into Ubuntu normally. I have a bunch of a non-replaceable pictures from my last deployment overseas saved on the computer. Now I have them backed up (it was the first thing I did when I got back into Ubuntu).

Now that fixing that is out of the way, time for a sub-question: Is it possible to switch back to 10.04 LTS? I don't feel very confident using this Beta anymore, at least not until it's "stable" as you guys put it.
I am glad you got it working. 

If you want to go back to 10.04, then you'll have to back up your data, unless you have a /home partition, then reinstall.

Regards,
uRock

---

### Post by cariboo on 2010-09-22
It's good idea to back up your data before an install, but apparently, even if your home directory is on the same partition as / it doesn't need to be overwritten. See [this]("https://wiki.ubuntu.com/komputes/HowToUbuquityPreserveHome") howto.

---

### Post by xebian on 2010-09-22
> **Iniquit-e said:**
> What?! So you are telling me I am basically screwed and because I upgraded the way the official Ubuntu site told me to, I am now paying the price?! I understand it is still in Beta, but this is a little bit much. There has got to be a way to fix this and get it working normal again.

But those are for upgrading to the current stable release which is 10.04 from an older release.  10.10 is not released yet still in beta.

---

### Post by xebian on 2010-09-22
> **Iniquit-e said:**
> Oh wow, this actually worked! Thanks a ton! This is a huge sigh of relief, I am so glad I was able to get back into Ubuntu normally. I have a bunch of a non-replaceable pictures from my last deployment overseas saved on the computer. Now I have them backed up (it was the first thing I did when I got back into Ubuntu).

Now that fixing that is out of the way, time for a sub-question: Is it possible to switch back to 10.04 LTS? I don't feel very confident using this Beta anymore, at least not until it's "stable" as you guys put it.

If going to 10.10 beta is a mess, going back to 10.04 from such a state is 100x worse.  Only a pro would even attempt it but then he is smart enough to do a fresh install.

---

### Post by uRock on 2010-09-22
> **xebian said:**
> But those are for upgrading to the current stable release which is 10.04 from an older release.  10.10 is not released yet still in beta.
The ubuntu page does recommend upgrading already. [http://www.ubuntu.com/testing/maverick/beta](http://www.ubuntu.com/testing/maverick/beta) 

But it also says this, 
> **This is a beta release. Do not install it on production machines. The final stable version will be released on October 10, 2010.**   
 
Personally, I'd never try another upgrade. I have an HP brick from trying that.

---

### Post by Rasa1111 on 2010-09-22
Im with ya uRock. 
no upgrades for me. 
fresh installs only. lol

 Glad you got your photos back OP. 

I had a feeling someone would get ya' in. lol

and I learned how to possibly get back to the desktop should this ever happen to me again. lol, :)

 If you want to use 10.04 instead..

 It really isnt that difficult to install it where 10.10 currently is. 

Youll just need to burn yourself a 10.04 liveCD first.
(no "downgrading") 

But if you dont feel comfy editing partitions, 
then maybe hold off.. lol

 10.10 has been working pretty flawlessly since i reinstalled it about a week ago though.

---

