---
title: "HP dv6648se no sound"
date: 2007-10-02
forum: Multimedia &amp; Video
---

### Post by fhslacrosse13 on 2007-10-02
I recently bought a Hp dv6648se laptop and I am having trouble getting any sound.

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8600000 irq 23
 
that the output I get for the card.  Can't seem to find a thread that has a solution for me.  If there is one then I am sorry in advance for the double post.  Also, if someone could direct me on how to get the built-in web cam to work with the model that would be great.

One other thing.  I am running 7.10 beta.

---

### Post by fhslacrosse13 on 2007-10-03
Does anyone have a clue as what I need to do?

---

### Post by Daveth on 2007-10-03
so, are you getting any sound at all- the login drums? Or is the whole box mute?
I assume you have played with the obvious settings for volume etc.

---

### Post by fhslacrosse13 on 2007-10-04
No sound at all...I've tried playing around with the sound setting, but past that I have no idea as to what to do.  I'm not even sure as to the sound card that is in the laptop.  It seems to be a phantom model cause I can't even find it on the HP site, and there is no one on here as far as I've found that has the same computer/problem.

---

### Post by fhslacrosse13 on 2007-10-12
does anyone have a solution for sound problems of a dv6000?  I think that it is close to the same model.

---

### Post by trjnhrse44 on 2007-10-13
I am having the same problem, have tried multiple fixes, no joy yet.  Keep trying one of us will figure it out.

---

### Post by muito_fofinho on 2007-10-13
> **Daveth said:**
> so, are you getting any sound at all- the login drums? Or is the whole box mute?
I assume you have played with the obvious settings for volume etc.

Yes, i get the sound only at startup - the login drums.
But after login, i dond't have sound :(

 i got also a HP notebook dv6000 and i'm also having troubles to solve the problem.
At the beginning i hadn't sound at all, but after i follow the post:
[http://ubuntuforums.org/showthread.php?t=455147&highlight=HP+notebook+webcam]("http://ubuntuforums.org/showthread.php?t=455147&highlight=HP+notebook+webcam")

i start hearing the drums...
Do you know how to solve this situation?

---

### Post by Ya'akov on 2007-10-13
Same here!
The sound seems to be extremely low or off.
I'm using a Toshiba Satellite A100-583  Multi Media Laptop, We had the same problem with Ubuntu 7.04 in the beginning until the developers found the bug and fixed it!

Just keep on reporting the bug till it's fixed.

Ya'akov

---

### Post by fhslacrosse13 on 2007-10-15
tried the tutorial posted by muito_fofinho but no such luck.

---

### Post by muito_fofinho on 2007-10-16
Ok, i've found something interesting...

see the next post:[http://ubuntuforums.org/showthread.php?t=524506&page=2]("http://ubuntuforums.org/showthread.php?t=524506&page=2")

it will be my next bet...
But if some one wants to try it out....go for it ;-)

Good Luck!

---

### Post by trjnhrse44 on 2007-10-20
okay guys the problem me and fhslacrosse are having is _specific  _to our board, the 6648se uses the ICH**8** hda-intel soundcard with intel graphics intel centrino core duo processor and intel ICH8 sata controller, if you dont see ICH8 in the audio section of lspci, the fixes you propose for those systems won't work on ours.  This is a limited edition machine and has a hardware set that not alot of systems use yet.  Please check your hardware first and post to the appropriate section in the forums, there are alot of people that may need your help but if you post in the wrong section they will never find it.

Anybody that does have the ICH8 problem...
This is what i have tried...
Building the alsa-sources from the ubuntu repos.
Building both Alsa 1.0.15 rc3 and 1.0.15 final
Unmuting the offhook and caller id switches
Changing sound systems to OSS and ESD
NOTHING WORKS YET

I plan this weekend on trying installs of SUSE, Fedora, Debian, Feisty, and Dapper to see if it works with the default kernels in those systems

By the way lacrosse the webcam does work out of the box with Gutsy:
But it only supports v4l2 not v4l
So open the terminal and type in the following:
```
gstreamer-properties
```
and hit enter
select the video tab and under input select v4l2 and then HP webcam
and hit the test button
This cam will work with Kopete under msn and yahoo
and ekiga, skype etc.

---

### Post by trellis on 2007-10-21
I have also this bug , i have a hp dv2530ea . no sound , but i had it when i first installed it , so i am assuming the update broke it

---

### Post by trellis on 2007-10-21
i think this could be the bug on launchpad 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/130559]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/130559")

---

### Post by trjnhrse44 on 2007-10-21
**:guitar:**_***SOLUTION!!***_! :guitar:

Here is the solution for the ICH8 audio issues! And it's simple!
On a fresh gutsy (7.10) Install, simply adding the backports repo and enabling backports modules fixes sound!
Here is the process:

Go to System,Admin,Software Sources
Enable all Ubuntu repos under Ubuntu Software and Updates tabs.  (Esp. Backports updates)

Close window

Reload sources and do system update
Go to synaptic package manager and install linux-backports-modules
alternately this step can be completed by entering the following into a terminal:
```
sudo apt-get install linux-backports-modules
```Restart and Sound is magically working, This installs kernel modules that work with updated alsa drivers and those drivers themselves from what i can tell.

IMPORTANT:  This didn't work for me until I did a fresh gutsy install becuase I had previously compiled alsa drivers from source.  If you have compiled the alsa drivers you must do a fresh install or somehow uninstall those modules, I have no idea how to do that without breaking the system.

Best of luck to all!
Please respond with whether or not this worked for you.

---

### Post by trjnhrse44 on 2007-10-21
p.s. thanks trellis for the launchpad link, solution was eluded to there!

---

### Post by Thanawho on 2007-10-21
THAAANNNNK YOUUUUUU!

This is amazing. I've spent all day troubleshooting this on my HP dv6500 entertainment PC. I did NOT have to re-install ubuntu and I downloaded several different alsa tarballs. Now the sound works. Maaaad props to you. Now i have to go and clean up all the ALSA mess :). (Although I'm not really sure what is running and what isnt...think i'll just leave it all alone.)

Thanks.

---

### Post by Metaleks on 2007-10-22
Thank you very much!  My sound FINALLY works.

---

### Post by leras on 2007-10-25
thank you so much my friend the sound is working in my hp pavilion dv6543 ev
so iam looking now for the rest 
thanks again

---

### Post by alterKrieg on 2007-10-29
Whooot!  Worked like a charm on my HP dv9500. Awesome.  Mad props again to whomever figured this out.

---

### Post by pouriaba on 2007-10-30
works well, merci.

---

### Post by rodrigo.galvez on 2007-11-24
Thanks a lot men i was searching this solution in a lot of pleases  .....love UBUNTU jejeje and sites like this make me love it more....

Tanks alot from Mexico.... let me translate your Solution to others Ubuntu Forums In spanish becuase there are alot of people who has the same problems......

---

### Post by trjnhrse44 on 2007-11-26
That would be great, another example of Open Solutions crossing boundaries that others can't.  It's because of the way our communities work together that open source software projects will eclipse proprietary solutions.

---

### Post by trellis on 2007-12-02
yes you are right , that the diffrence . 

I ve still having problems with sound , although i have sound most of the time since doing the backport thing . If am using vista and then restart and boot into ubuntu , i have no sound . if i shut down and wait a bit . i have sound . god knows why .

---

### Post by Nasso on 2008-01-12
I have the same problem. Worked on install but not anymore. Have followed lots of tutorials and compiled alsa myself. This backport thing didnt help. Will keep an eye on the thread :) Can survive without sound for a while. Dont feel like reinstalling again :P

---

### Post by smathai on 2008-02-12
Awesome. I have an HP dv6000 series laptop, sound worked after the alsa driver install way back when... and then one day I noticed I had lost sound.

This fixed it... thank goodness I read up on this thread or I'd have started hours of alsa driver re-makes/installs and going nowhere.

edit -- I also did this before the reboot from this thread (could it also be responsible for my audio fix?) [http://ubuntuforums.org/showthread.php?t=583150:](http://ubuntuforums.org/showthread.php?t=583150:)

UPDATE 2: I ran the following commands:
* sudo apt-get install module-assistant
* sudo m-a update
* sudo m-a prepare
* sudo m-a a-i alsa
* Reboot and setup your sound settings

---

### Post by smit8678 on 2008-02-18
**This post could be related to an Ubuntu bug filed at**: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have an HP dv6000 series laptop. When I killed Windows and installed Gutsy, I had no sound. Gutsy was reading my sound card, and any audio program would respond like it was playing sound, but nothing was coming out. The fix posted on the Ubuntu wiki for Intel HD Audio Controllers did not work. I worked on a fix that appears to have fixed the sound problem for the HP dv6000. Here it is!

1. Enable the gutsy-proposed and gutsy-backports options

To do this, go to --> System --> Administration --> Software Sources and then go to the updates tab and make sure that all updates options are enabled. This will add extra repositories to Gutsy.

2. Open up a terminal and update the respositories. In the terminal, enter:

```
$ sudo apt-get update
```

Gutsy will run though a series of script, updating some of the repositories.

3. Fix ALSA. With HP dv6000, the ALSA drivers are a little buggy. Simply put, gutsy has
some conflicting dependencies, particularly if you have already attempted to update ALSA.
Gutsy is released with alsa release 1.0.14. If you have installed any version updates, 
this only furthers the conflicts. To fix this, you need to blast ALSA back to the Stone Age.
To do this, continue in the terminal. In the terminal, enter:

```
$ sudo apt-get remove --purge alsa-base alsa-tools
```

This will purge all ALSA dependencies and conflicts from gutsy. If this is a
new install, you probably will not have the alsa-tools package. Run the remove
anyway. This will remove ALSA and its dependencies. Next reinstall:

```
$ sudo apt-get install alsa-base alsa-tools
```

This will reinstall ALSA and its dependencies, free of conflicts. Then:

```
$ sudo gedit /etc/modprobe.d/alsa-base
```

Insert the following at the end of file and save:

```
options snd-hda-intel model=laptop
```

4. Restart your computer. ALSA should be good to go and you should have sound.

---

### Post by Piggio on 2008-03-15
trjnhrse44 
Yes it worked but just with the jack :(
My speakers doesnt make a sound..

---

