---
title: "Ubuntu 8.10 (Ibex) Pulse Audio removal."
date: 2008-11-06
forum: Multimedia Software
---

### Post by DSCP46 on 2008-11-06
I totally understand why Ubuntu is pushing for this technology, but also understand that it does hinder the community.  I myself have found PulseAudio to be more trouble than its worth, and removed it.

See I like to play my World of Warcraft and Music in the back ground _without 10% of my CPU being used by Pulseaudio_, when I could be enjoying smoother game play..  Not to mention there was a clear reduction in sound clarity, but this may have been something related to my Soundcard's configuration through Pulseaudio.

First things First. Remove the packages though Bash.

[I]sudo apt-get remove pulseaudio
sudo apt-get install esound

sudo rm /etc/X11/Xsession.d/70pulseaudio[/I]  (You may want to back this up)

Now this is done you will want check your Gnome Preferences.

Under **System -> Preferences -> Sound**
Make sure they are all set to 'Autodetect'.
The only one you will have to set manually to ALSA is 'Sound Capture' under 'Audio Conferencing'.
Note at this point Pulseaudio is now nolonger an option under these drop menus.

Under **System -> Preferences -> Sessions**
Deselected or Remove the Pulseaudio Manager

The last part is one I think a lot of people have missed.  Your asoundrc's under your Home Directory are still configured for Pulse.

[I]cd ~
rm .asound*[/I] (Again! You may want to back this up)

One this is done your back to ALSA's default configuration.

This worked a charm for me and found all my software picked up Dmix and Dsnoop.
I hope it does wonders for you..  Good Luck.

---

### Post by wolfen69 on 2008-11-07
thanks for this, but you will need to change ```
sudo apt-get remove pulse
``` to ```
sudo apt-get remove pulseaudio
``` cheers.

---

### Post by DSCP46 on 2008-11-07
> **wolfen69 said:**
> thanks for this, but you will need to change ```
sudo apt-get remove pulse
``` to ```
sudo apt-get remove pulseaudio
``` cheers.

Thanks for the heads up!  Done now.

Cheers

---

### Post by NeeBone on 2008-11-07
This doesnt work without wanting to take ubuntu-desktop with it. Any suggestions?

---

### Post by theduffman on 2008-11-07
> **NeeBone said:**
> This doesnt work without wanting to take ubuntu-desktop with it. Any suggestions?

thats just the metapackage it wont actually remove ubuntu or the desktop :)
i may try this out, i hate pulse too

---

### Post by NeeBone on 2008-11-08
Sweet! Worked fine.... AFTER I deleted /etc/asound.conf as well as the one in ~/

Sound working flawlessly now. Thanks!

---

### Post by iamnotthemessiah on 2008-11-08
thanks for this, i ran the following:
killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound esound-clients libao2
sudo mv /etc/X11/Xsession.d/70pulseaudio ~/backup/pulsebackup/

and ive got my ubuntu back :D first time ive got decent sound since gutsy

---

### Post by falkaholic on 2008-11-08
Thanks worked for me.

My usb audio device start only partially working in Intrepid, this fixed it.

---

### Post by maninsitu on 2008-11-09
After reading this string. It sounds like this will work, but will not remove the desktop right? :o Also, please what is the easiest, quickest way to backup the files that are mentioned here?

Can you give me the code to backup files? Linux newb here. I was sooo use to DOS in the day but this is like learning French! :D

I am so tempted to try without backing up, but Murphy's law will get me as it usually does! Thanks all!

---

### Post by Seinfeld on 2008-11-09
Thanks very very much DSCP46 and all .  worked flawlessly.. I was one step away from going baack to hardy..Pulse audio is just a pain..

BUT...Just one problem though still persistent since I upgraded to Ibex yesterday, Front Mic on my Desktop case is not working,..Speakers are working on rear and front case panels  perfectly. Mic is working in rear panel as well, only the Front panel Mic.. No way.. I made sure many times that alsamixer Captures and mics settings are all boosted and unmuted.. 
was never been a problem with Hardy.. :(
I have an HDA Intel Realtek ALC888 Chip..

Can you please help ??

Thanks

---

### Post by maninsitu on 2008-11-09
[B][COLOR="DarkGreen"]Quote is edited by me...see original post!
[/COLOR][/B]
> **DSCP46 said:**
> I totally understand why Ubuntu is pushing for this technology, but also understand that it does hinder the community. I myself have found PulseAudio to be more trouble than its worth, and removed it...I hope it does wonders for you..  Good Luck.


Moderator, these instructions that DSCP46 provided, deserves a Sticky :D :guitar: Worked like a charm for me as well. I left my sound preferences on Autodetect and the sound capture on ALSA. I also restarted before attempting anything after all was complete. Also, I could not find .asound* in my home directory, even after displaying hidden files and folders. I assume that it was never there.

Here I thought my problem was with Adobe Flash 10 in Mozilla and a conflict with Intrepid! Newbie to linux and failed Computer Science course in University, so help from good folks like you makes me feel all warm and gushy lol - thanks again!

---

### Post by VTphilipv on 2008-11-09
B-E-A-UTIFUL... maybe interpid won't be as frustrating as I thought!
Now jus webcam support, and I'm ALMOST back to where I was before the upgrade!

---

### Post by beercz on 2008-11-09
Thanks DSCP - worked like a charm!

---

### Post by metalgtr on 2008-11-09
Thanks! This makes my docking station speakers work where they did not previously.

---

### Post by WSmart on 2008-11-09
[QUOTE=maninsitu;6135481]
Can you give me the code to backup files? 

Open a terminal, Applications>Accessories>Terminal, and enter man cp .

That will give you the syntax for copying files.  You basically just cp address/file file.backup .  You can use whatever name you want.  If you need to get it back, just cp file.backup file .  

I'm cautious about making changes.  You make one change and you could be sitting for hours trying to figure out what you did.  Get a second hard drive and install a test system to try stuff out before you 'buy it'.

---

### Post by douham on 2008-11-09
Hi, I performed DSCP46's instructions, one issue however is that starting the sound preferences in sytem>preferences takes ages to  load up and loads my processor right up.

---

### Post by psyke83 on 2008-11-09
Although PulseAudio take up 10% CPU sometimes (when the audio bitrate is different to the PulseAudio server's bitrate; otherwise it's about 3%), I'm not so sure that ALSA's dmix is any better. ALSA's dmix also operates in software for 99% of users (who use cards without hardware mixing support). The reason you may not notice dmix's overhead is that it will be registered as "system" CPU overhead, whereas PulseAudio will register under "user" CPU overhead through the "pulseaudio" process.

---

### Post by Seinfeld on 2008-11-09
Guys.. It seems that I am downgrading back to Hardy.. The front Mic NEVER works. I spent hours trying to know why I checked reinstalled alsa.... etc etc.. No way...  I have Intel HDA Realtek ALC888... Also the webcam does not work anymore on Skype.. Everything was just PERFECT with Hardy.. Any help before I just go ahead..?? Thanks

---

### Post by ECPCLINUX on 2008-11-10
OMG!! Thank you sooooo very much! I had just downgraded to Ubuntu 7.10 because I have had problems with Skype and playing music. I was unable to play music at the same time with Skype or even just play music close Amarok and attempt to use skype. Once I played music, I could not use Skype at all (had to reboot). This issue began Since 8.04LTS when Ubuntu changed to Pulseaudio. I read endlessly and could not solve this issue. On my readings I figured it could be a problem with Skype being proprietary. Maybe later Skype, will get in tune with Ubuntu's new Pulseaudio. But for now this is absolutely great! I was a bit worry what would happen once Gutsy would no longer be supported. I use Skype for all my long distance calls and it's a must for me, saves me a lot of money. When I tried to install Intrepid (8.10), there was an error with the Kernel 2.6.27-7. I sent an error report. Not discouraged, Tried a second install and it went thru perfect.  I read something which might be related, not sure, here: [http://news.softpedia.com/news/Linux-Kernel-Regression-in-Ubuntu-8-10-Upgrade-Now-96839.shtml](http://news.softpedia.com/news/Linux-Kernel-Regression-in-Ubuntu-8-10-Upgrade-Now-96839.shtml) 

Furthermore, the sound volume was much lower in Intrepid than in Hardy, dunno why?:confused: I adjusted all I could for the highest volume possible, yet still not very loud. My sound card in this system is realtek ALC883.  I had recently downgraded back to Gutsy, but I never stopped searching for a solution. Recently, I came upon your Thread and people seems very happy and I decided to once more remove Gutsy,lol and installed Intrepid. As I mentioned this worked great, once more thank you very much!:guitar:

---

### Post by hickop on 2008-11-10
Thanks, I did the removal on Ubuntu 8.10 amd64 with hda intel audio system.

But whenever i play some song or launch a video, i got a 5-10 seconds delay before it starts.

By changing all options in "System -> Preferences -> Sound" (taking long time to load too) to ALSA i got it to work as expected, strange thing is that pulseaudio still appear in the list.

So it works, but need to clarify why "auto detect" makes delays.

---

### Post by Seinfeld on 2008-11-10
Just be sure to "completely remove" pulseaudio.. ```
sudo apt-get --purge remove pulseaudio 
``` Then just do ```
sudo apt-get autoremove
``` Now reboot and you should be fine and pulseaudio free :)

Now I solved the Mic problem just in case... Here is the point.. Intrepid treats the front Mic as "input source" so just select "inout source" option and choose your Mic. I guess you cannot work both Mics at a time... 

Thanks

As for Skype.. Here is the BEST post that will solve all your problems...

[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)


I love Ubuntu.. :)

---

### Post by hickop on 2008-11-10
> **Seinfeld said:**
> Just be sure to "completely remove" pulseaudio.. ```
sudo apt-get --purge remove pulseaudio 
``` Then just do ```
sudo apt-get autoremove
``` Now reboot and you should be fine and pulseaudio free :)


This was not enough, so i checked all "pulse" related in synaptic and found those:

pulseaudio-utils
pulseaudio-module-conf
pulseaudio-module-hal
pulseaudio-module-x11
libpulsecore5
gstreamer0.10-pulseaudio
libpulse-browse0

I removed all of them and now "Autodetect" works and no more Pulseaudio in list.

---

### Post by quazi on 2008-11-10
I'm fairly tempted to remove pulse audio (I have to run wine programs and firefox with padsp if I want sound), but I'm not sure what I'm losing by removing Pulseaudio.  Will I lose any functionality/quality by just going back to ALSA?

---

### Post by ubun_two on 2008-11-10
> **quazi said:**
> I'm fairly tempted to remove pulse audio (I have to run wine programs and firefox with padsp if I want sound), but I'm not sure what I'm losing by removing Pulseaudio.  Will I lose any functionality/quality by just going back to ALSA?
Only thing I noticed that no longer works after uninstalling pulseaudio (so far) is the sound for VMWare.  Everything else that worked with pulseaudio seem to work fine with ALSA (and more stable).

---

### Post by ubun_two on 2008-11-10
> **Seinfeld said:**
> Just be sure to "completely remove" pulseaudio.. ```
sudo apt-get --purge remove pulseaudio 
``` Then just do ```
sudo apt-get autoremove
``` Now reboot and you should be fine and pulseaudio free :)


Actually it might take few more steps to remove pulseaudio from Intrepid.  

Simply removing pulseaudio with apt-get/Synoptic could cause error when you log back into Ubuntu, because somehow it keeps trying to load pulseaudio that's no longer there and cause some error.

Here is what I did:

Steps:
1, Remove pulseaudio and its dependency through Synoptic (yes, that means ubuntu-desktop, too).
2, Add esound through Synoptic.
3, Preference->Sound on Device tab, changed all audio options to ALSA.
4, Preference->Sound on Sounds tab, disabled alert and sound effects.
5, On Preference->Session, uncheck PulseAudio Session Management.
6, In /etc/X11/Xsession.d directory, make sure there is no 70pulseaudio. If it is, move it or delete it.
7, Reboot.

---

### Post by kellypl on 2008-11-11
> **ubun_two said:**
> Actually it might take few more steps to remove pulseaudio from Intrepid.  

Simply removing pulseaudio with apt-get/Synoptic could cause error when you log back into Ubuntu, because somehow it keeps trying to load pulseaudio that's no longer there and cause some error.

Here is what I did:

Steps:
1, Remove pulseaudio and its dependency through Synoptic (yes, that means ubuntu-desktop, too).
2, Add esound through Synoptic.
3, Preference->Sound on Device tab, changed all audio options to ALSA.
4, Preference->Sound on Sounds tab, disabled alert and sound effects.
5, On Preference->Session, uncheck PulseAudio Session Management.
6, In /etc/X11/Xsession.d directory, make sure there is no 70pulseaudio. If it is, move it or delete it.
7, Reboot.

to start off im gonna say im a complete linux newb. I tried to delete the 70pulseaudio and it said i did not have permission, how do i get around that.

---

### Post by psyke83 on 2008-11-11
I just noticed that we have two identical guides on removing PulseAudio. IMHO, it's a bad idea to remove the PulseAudio packages as they are now a part of the core system, so you could experience problems with upgrades.

Please see my post [here]("http://ubuntuforums.org/showpost.php?p=6149347&postcount=51") for information to either a) configure PulseAudio properly, or b) disable PulseAudio **safely**.

---

### Post by kellypl on 2008-11-11
thanks ill try that

---

### Post by sreekanth27 on 2008-11-11
even after removing pulse  my audion does not seem to work. Any help will be appreciated..

---

### Post by Kelsin on 2008-11-12
> **ubun_two said:**
> Actually it might take few more steps to remove pulseaudio from Intrepid.  

Simply removing pulseaudio with apt-get/Synoptic could cause error when you log back into Ubuntu, because somehow it keeps trying to load pulseaudio that's no longer there and cause some error.

Here is what I did:

Steps:
1, Remove pulseaudio and its dependency through Synoptic (yes, that means ubuntu-desktop, too).
2, Add esound through Synoptic.
3, Preference->Sound on Device tab, changed all audio options to ALSA.
4, Preference->Sound on Sounds tab, disabled alert and sound effects.
5, On Preference->Session, uncheck PulseAudio Session Management.
6, In /etc/X11/Xsession.d directory, make sure there is no 70pulseaudio. If it is, move it or delete it.
7, Reboot.

For me using --purge with apt-get (or purge with aptitude) removes the 70pulseaudio config file so I didn't have to remove it manually. For me fixing this on my Lenovo X61s was a matter of

```

sudo aptitude purge pulseaudio
sudo aptitude install esound

```

And a reboot.

---

### Post by Unanimated on 2008-11-12
Thank GOD - I've wanted to remove that horrendous excuse for a program since about a month after I downloaded it. Thank you so much!

---

### Post by legolas_w on 2008-11-13
Hi
I did all steps and now I do not have pulseaudio in the sounds/devices tab.
but when I select "ALSA Advanced Linux Sound Architecture" and press test it shows an error like:

```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

```

when I choose "HDA Intel ALC883 Digital (ALSA)" and press test it shows no error but I can not head anything.

I should say that I can not hear any voice by running amarok, vlc, ... and when I issue ```
alsamixer
``` command I get:

```

ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused


```

Any help is really welcome as I can not use skype which is an integral part of my daily work.

Thanks

---

### Post by psyke83 on 2008-11-13
> **legolas_w said:**
> Hi
I did all steps and now I do not have pulseaudio in the sounds/devices tab.
but when I select "ALSA Advanced Linux Sound Architecture" and press test it shows an error like:

```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

```

when I choose "HDA Intel ALC883 Digital (ALSA)" and press test it shows no error but I can not head anything.

I should say that I can not hear any voice by running amarok, vlc, ... and when I issue ```
alsamixer
``` command I get:

```

ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused


```

Any help is really welcome as I can not use skype which is an integral part of my daily work.

Thanks

If you insist on living without PulseAudio (what a miserable existence)...
```
$ sudo rm ~/.asoundrc* /etc/asound.conf
```

(I think) the problem on your system is that the PulseAudio ALSA plugins are still enabled, therefore all ALSA applications are trying to connect to a non-existant PulseAudio server, which is causing an error.

---

### Post by legolas_w on 2008-11-13
Hi
The command returns 
```

rm: cannot remove `/home/legolas/.asoundrc*': No such file or directory


```

is it normal?

Thanks

---

### Post by legolas_w on 2008-11-13
Thanks and I should add that when I execute 
```

sudo alsa reload

```

I get
```

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/masoud/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 5787(mixer_applet2). 
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-intel snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

```

---

### Post by psyke83 on 2008-11-13
> **legolas_w said:**
> Hi
The command returns 
```

rm: cannot remove `/home/legolas/.asoundrc*': No such file or directory


```

is it normal?

Thanks

Yep (the configuration could have been in the ~/.asoundrc* files, or /etc/asound.conf. In your case, it was the latter).

You should log out and back in, then open alsamixer to verify that your Master and PCM volume is **not** muted or set to 0%:

```
$ alsamixer -Dhw
```

---

### Post by legolas_w on 2008-11-13
Hi
Thank you for your help, it is almost working :-D
Now It just works as Mono and not stereo :O, the main jack which I use in 8.4 produce powerful but mono voice while another jack produce stereo but weak voice (it is weaker in comparison with when I had 8.4)

Also when I run alsamixer, it usually shown two bars for PCM but now it shows one bar for PCM volum.

I found two volum meters that can affect the output sound, they are named **Center** and **LFE** does it mean anything about the problem?



thanks.

---

### Post by schmidtbag on 2008-11-19
uh... my ubuntu desktop is removed...

now what?  i did just as the guide said and it removed the desktop.  i didn't restart yet but is this going to hurt me?  i checked synaptic and when i checked it back on it was going to reinstall nearly 300mb of stuff i deliberately removed, including pulseaudio

---

### Post by psyke83 on 2008-11-19
> **schmidtbag said:**
> uh... my ubuntu desktop is removed...

now what?  i did just as the guide said and it removed the desktop.  i didn't restart yet but is this going to hurt me?  i checked synaptic and when i checked it back on it was going to reinstall nearly 300mb of stuff i deliberately removed, including pulseaudio

Yet another reason not to remove PulseAudio...

This will hopefully restore your installation without further issues:
```
$ sudo apt-get install ubuntu-desktop
```

---

### Post by schmidtbag on 2008-11-19
well no thats exactly what i don't wanna do because its just going to install all this stuff i don't want.  will ubuntu work without the "ubuntu-desktop"?


btw, removing pulseaudio fixed EVERY SINGLE sound problem i have



edit:
apparently removing ubuntu-desktop didn't harm anything.  i remember in earlier versions of ubuntu, it ruined the whole system

---

### Post by danf_1979 on 2008-11-20
> **maninsitu said:**
> After reading this string. It sounds like this will work, but will not remove the desktop right? :o Also, please what is the easiest, quickest way to backup the files that are mentioned here?

Can you give me the code to backup files? Linux newb here. I was sooo use to DOS in the day but this is like learning French! :D

I am so tempted to try without backing up, but Murphy's law will get me as it usually does! Thanks all!

You can use nautilus, or the "cp" command in a terminal.

```

Backup to another directory
$ cp /some/original/file /home/youruser/backup/file
Backup in the same directory
$ cp somefile somefile.backup

```

---

### Post by psyke83 on 2008-11-20
> **schmidtbag said:**
> well no thats exactly what i don't wanna do because its just going to install all this stuff i don't want.  will ubuntu work without the "ubuntu-desktop"?


btw, removing pulseaudio fixed EVERY SINGLE sound problem i have



edit:
apparently removing ubuntu-desktop didn't harm anything.  i remember in earlier versions of ubuntu, it ruined the whole system

It won't harm your system - until you dist-upgrade to the next release.

---

### Post by Dragonseer on 2008-11-25
I tried following this guide and the sound for me stopped working completely.  I have tried to reinstall pulseaudio but I don't know how to restore it in the System>Preferences>Sessions dialogue.  How would I go about getting pulseaudio back to it's original state?

---

### Post by james.wilde on 2008-11-26
> **psyke83 said:**
> I just noticed that we have two identical guides on removing PulseAudio. IMHO, it's a bad idea to remove the PulseAudio packages as they are now a part of the core system, so you could experience problems with upgrades.

Please see my post [here]("http://ubuntuforums.org/showpost.php?p=6149347&postcount=51") for information to either a) configure PulseAudio properly, or b) disable PulseAudio **safely**.

This is bad.  I've just gone through the process of re-installing/re-configuring pulseaudio in an attempt to make Skype work.  I didn't get Skype working but I screwed up a lot of other stuff so badly that I almost considered going back to Windows!  So I went through the process of removing pulseaudio again, found earlier in this thread and Skype works perfectly.

Now I'm told that future updates of Ubuntu are going to screw up my system again, since they're presumably going to try and update a pulseaudio that I don't have.

So what's the word on the street?  Live with a working system till I upgrade and try and refix it then, or put all this pulseaudio crap back and try again to make all my applications work with it?  And if the latter, what's the best way to go about re-instating pulseaudio?  Will psyke83's guide that he refers to in the quote above do the trick?  There are so many threads on this and related topics that I'd like to see the moderators mark one of them as definitive and preferably remove all the others.

//James

---

### Post by taavi on 2008-11-26
Thanks, Pulseaudio made my flashplayer under FX3 mute, so I uninstalled it and now use ALSA for all.. works like charm.

---

### Post by buntu_hugenewbie11 on 2008-11-29
Do these instructions work for Hardy?
My worst idea ever was believing that pulse audio was an improvement to working sound.

---

### Post by arrancaru on 2008-11-30
thanks lord i get this crap removed. maybe someday they gonna put pulseaudo working, but today is a total crap. Now I can see movies again.

---

### Post by markbuntu on 2008-11-30
There is no need to remove pulseaudio just because a few critical packages were left out of the default Ubuntu install. If you take a few minutes to follow my new guide you can get pulseaudio working properly now and avoid all the trouble future updates will cause for you if it is removed:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by NoThanksM$ on 2008-11-30
It seems that, at least in my case, these guides don't help.  My problem, and main reason for giving up on PulseAudio, is that I can't switch back and forth between regular analog output and digital output on my Montego DDL card.  The link you provided, [http://ubuntuforums.org/showthread.php?t=776958](http://ubuntuforums.org/showthread.php?t=776958) will help if you want to permanently switch to your digital output (or any secondary output), but it does not provide a way for someone to easily switch back and forth - as you said, that is a known limitation of PulseAudio.  

In addition to that, I find that PulseAudio (or soemthing connected to it) locks up regularly (at least once/day, especially if I have something with an audio track paused), at which point I have to force quit it and any programs that were using it.  

When you combine these problems with the other problems people in this thread are having, and the fact that you yourself have written two lengthy tutorials on it and linked to numerous others, all just to get Ubuntu's default sound solution working....that, to me, is unacceptable.  And the worst part is that instead of admitting Ubuntu really messed up with this implementation and/or the PulseAudio folks have a lot of work to do before their product is ready for prime time, we're encouraged to spend hours and hours of our time to get something as basic as audio output working.  As much as I loathe Windows, this is exactly why Linux will never be considered a legit option by 99% of the public.

---

### Post by markbuntu on 2008-11-30
I already said ubuntu screwed up its pulseaudio implementation and so I am trying to fix that rather than just whine about it. Anyway, there is nothing wrong with pulseaudio, it works just fine in Mandriva and Gentoo and SuSe. It was, and still is poorly implemented in Ubuntu. 

The Ubuntu audio team should be tarred and feathered. I will not defend them. I am only trying to clean up their mess so people can have a pleasant experience.

Anyway, it should take no more than 15 minutes following my latest guide unless you have hardware problems in which case you are better off here than in some vista google search hell.

Have you looked in the pulseaudio site and read the faq and perfect setup?
There is a fairly easy way to get your digital output controllable in pulseaudio, there is a link in my guide.

Have you filed bug reports on your problems?
If you do not report bugs, how do you expect them to get fixed?
Posting in these forums is not bug reporting.

If you are having issues with pulseaudio, you can talk directly to the devs on their mailing list.

I have used every version of windows from 2.1 to XP and it has always sucked, crash crash crash. Even in 1997 Linux was more stable. At least with linux if you don't like the way something is working you have a whole lot of alternatives.

gotta go now, my ubuntustudio has finished downloading and I need to reboot.

Anyway, if you are looking for rock solid stability you should use Debian.

---

### Post by NoThanksM$ on 2008-12-01
Don't get me wrong, I appreciate you taking the time to post here and to write up the tutorials you have. Regarding my main issue, you cited the same bug report I found, [http://www.pulseaudio.org/ticket/139](http://www.pulseaudio.org/ticket/139), so it doesn't seem that there's any sense in me reporting it again and I obviously already know this is a confirmed bug, so the only thing left for me to do is abandon PulseAudio for the time being.

---

### Post by Connyank on 2008-12-05
> **DSCP46 said:**
> I totally understand why Ubuntu is pushing for this technology, but also understand that it does hinder the community.  I myself have found PulseAudio to be more trouble than its worth, and removed it.

See I like to play my World of Warcraft and Music in the back ground _without 10% of my CPU being used by Pulseaudio_, when I could be enjoying smoother game play..  Not to mention there was a clear reduction in sound clarity, but this may have been something related to my Soundcard's configuration through Pulseaudio.

First things First. Remove the packages though Bash.

[I]sudo apt-get remove pulseaudio
sudo apt-get install esound

sudo rm /etc/X11/Xsession.d/70pulseaudio[/I]  (You may want to back this up)

Now this is done you will want check your Gnome Preferences.

Under **System -> Preferences -> Sound**
Make sure they are all set to 'Autodetect'.
The only one you will have to set manually to ALSA is 'Sound Capture' under 'Audio Conferencing'.
Note at this point Pulseaudio is now nolonger an option under these drop menus.

Under **System -> Preferences -> Sessions**
Deselected or Remove the Pulseaudio Manager

The last part is one I think a lot of people have missed.  Your asoundrc's under your Home Directory are still configured for Pulse.

[I]cd ~
rm .asound*[/I] (Again! You may want to back this up)

One this is done your back to ALSA's default configuration.

This worked a charm for me and found all my software picked up Dmix and Dsnoop.
I hope it does wonders for you..  Good Luck.



followed your instructions up to the .asound* and couldn't find any rc files.  pulse still being called for at start up and since it ain't there, x won't start.  
Any idea which file I should edit to remove the offending script?

xsessionerrors reads:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Couldn't exec /usr/bin/pulse-session: No such file or directory


Thanks

jg

---

### Post by steve_q on 2008-12-11
Big thanks for the walkthru, DSCP46.

In addition to your instructions, and this may go w/o saying for most users, I also had to use synaptic to remove any/all pulse related apps to get my sound working..

---

### Post by vickyt on 2008-12-11
i am in failsafe gnome session because i could not login to gnome session after I have done the following
        * killall pulseaudio
        * sudo apt-get remove pulseaudio
        * sudo apt-get install esound
        * sudo rm /etc/X11/Xsession.d/70pulseaudio

Then i came across with the .xsession-errors (couldn't exec/usr/bin/pulse-session)
what shall i do now so i can properly login into gnome session? I am only 3 days old in ubuntu...

thanks a lot

---

### Post by Connyank on 2008-12-11
> **vickyt said:**
> i am in failsafe gnome session because i could not login to gnome session after I have done the following
        * killall pulseaudio
        * sudo apt-get remove pulseaudio
        * sudo apt-get install esound
        * sudo rm /etc/X11/Xsession.d/70pulseaudio

Then i came across with the .xsession-errors (couldn't exec/usr/bin/pulse-session)
what shall i do now so i can properly login into gnome session? I am only 3 days old in ubuntu...

thanks a lot



Go back in this thread to the start - someone posted (I think it was here) about changing the various scripts that call for pulse audio - they aren't immediately apparent even to a more experienced eye.  

Been doing this for 3 days and already uninstalling s/w?  watch out...

---

### Post by vickyt on 2008-12-11
Thanks to Kelsin, i managed to go back to gnome session and remove completely pulse audio.

Thanks Connyank for your concern. As to reason for removing programs already, this was due to a skype  problems.

thanks again

---

### Post by zika on 2008-12-11
> **markbuntu said:**
> There is no need to remove pulseaudio just because a few critical packages were left out of the default Ubuntu install. If you take a few minutes to follow my new guide you can get pulseaudio working properly now and avoid all the trouble future updates will cause for you if it is removed:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

finaly a voice of reason! you do not have to uninstall pulseaudio in order not to use it.

in System->Preferences->Sessions uncheck Pulse Audio and add new item with appropriate name and comment and in command field put ```
killall pulseaudio
``` or ```
pkill pulseaudio
``` or, even simpler ```
pulseaudio -k
``` and that way it won't come up on boot and everything is OK, check in with ```
alsamixer
```

that way in distribution upgrade or whatever You won't have a bunch of warnings or even worse ...

the only case where my reasoning is not valid are computers with poor sound hw where help from sw for mixing is needed.  then all the fuss might be needed.

---

### Post by buntu_hugenewbie11 on 2008-12-17
I have taken a few days to try and get this working. No luck.
Btw I am using HARDY 64 and KUBUNTU.
Your guide is for Intrepid no?
Either way since trying to set up Pulse audio from this guide [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
I do not get sound for most applications (Skype, kde notifications, audacity).
Thank goodness for a dual boot machine and windows.
Whenever I try to get pulse working I get the following errors:

$ pulseaudio & pavucontrol
[1] 17782
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device=hw:0"): initialization failed.
E: module.c: Failed to open module "module-esound-protocol-tcp": module-esound-protocol-tcp.so: cannot open shared object file: No such file or directory
E: module-gconf.c: pa_module_load() failed
E: module.c: Failed to open module "module-esound-protocol-tcp": module-esound-protocol-tcp.so: cannot open shared object file: No such file or directory
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
[1]+  Exit 1                  pulseaudio

Any ideas?


> **markbuntu said:**
> There is no need to remove pulseaudio just because a few critical packages were left out of the default Ubuntu install. If you take a few minutes to follow my new guide you can get pulseaudio working properly now and avoid all the trouble future updates will cause for you if it is removed:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by zika on 2008-12-17
> **buntu_hugenewbie11 said:**
> I have taken a few days to try and get this working. No luck.
Btw I am using HARDY 64 and KUBUNTU.
Your guide is for Intrepid no?
Either way since trying to set up Pulse audio from this guide [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
I do not get sound for most applications (Skype, kde notifications, audacity).
Thank goodness for a dual boot machine and windows.
Whenever I try to get pulse working I get the following errors:

$ pulseaudio & pavucontrol
[1] 17782
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device=hw:0"): initialization failed.
E: module.c: Failed to open module "module-esound-protocol-tcp": module-esound-protocol-tcp.so: cannot open shared object file: No such file or directory
E: module-gconf.c: pa_module_load() failed
E: module.c: Failed to open module "module-esound-protocol-tcp": module-esound-protocol-tcp.so: cannot open shared object file: No such file or directory
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
[1]+  Exit 1                  pulseaudio

Any ideas?

try in Terminal:```
pulseaudio -k
``` and if that works for You, following my previous post kill pulseaudio in every session without removing it from installation to avoid problems with upgrades.[B]

note: [/B]after reading Your message one more time I am not sure if You are trying to use pulseaudio or to get rid of it. it looks as if You were unable to have soumd without it and You do not have esound modules installed. sorry for my intervention if that is the case ...

---

### Post by foilonfilling on 2008-12-18
I've been scanning through this thread and have decided against ever installing Pulse to begin with. My trouble is that update manager keeps pestering me about it. I've unchecked all the pulse stuff on the last three rounds of updates, but it still lingers. Is there a way to banish pulse for good? Sorry if the solution to this is glaringly obvious. Just switched to ubuntu last week. Still wet behind the ears. Thanks in advance.

---

### Post by NoThanksM$ on 2008-12-18
Are you sure you don't have it installed already?  AFAIK, the only way you wouldn't have it is if you had been upgrading through the last few releases.  8.04 and 8.10 have both had it installed by default on new installs.  If update manager is pestering you, I think that's for the recent update to PA that was released, not asking you to install the whole package.  You can use Synaptic (under System -> Administration) to check if you have it installed already by doing a search and seeing if it's selected.

---

### Post by foilonfilling on 2008-12-18
> **NoThanksM$ said:**
> Are you sure you don't have it installed already?  AFAIK, the only way you wouldn't have it is if you had been upgrading through the last few releases.  8.04 and 8.10 have both had it installed by default on new installs.  If update manager is pestering you, I think that's for the recent update to PA that was released, not asking you to install the whole package.  You can use Synaptic (under System -> Administration) to check if you have it installed already by doing a search and seeing if it's selected.

Right you are! Thanks for the pointer. I've still got a lot to learn. Maybe some more homework in the Absolute Beginners sec. is what I need.

---

### Post by NoThanksM$ on 2008-12-18
No problem.  I've been using Ubuntu for about 18 months and I still feel like a beginner, too.  Definitely takes some time to get the hang of things.  Good to have you on board, though!

---

### Post by rabideau on 2008-12-29
Just a quick THANK YOU! This fixed my audio (Dell e1505).:popcorn:

---

### Post by koolkatkiwi on 2008-12-29
> **psyke83 said:**
> If you insist on living without PulseAudio (what a miserable existence)...


But . . . Psyke83 - what is one supposed to do, then? I have read your long thread about how to fix the problem. Thank you so much for selflessly putting in the time to do this and try to help everyone. 

But, I did exactly as you said, and STILL no sound whatsoever. I asked for help on that thread, but got no reply. No wonder - it's over 100 pages long - people are tired of trying to deal with it. I've spent ages Googling for solutions - none has worked yet. And, being a novice, I'm frankly afraid to try things that are quite drastic (like this thread seems to be, to me).

So, I along with numerous other people are starting to hate PulseAudio. Why a "miserable existence" without it? With it, I may as well be deaf, because I get no sound. THAT is a miserable existence.

Cheers,
Kath

---

### Post by zika on 2008-12-30
> **koolkatkiwi said:**
> But . . . Psyke83 - what is one supposed to do, then? I have read your long thread about how to fix the problem. Thank you so much for selflessly putting in the time to do this and try to help everyone. 

But, I did exactly as you said, and STILL no sound whatsoever. I asked for help on that thread, but got no reply. No wonder - it's over 100 pages long - people are tired of trying to deal with it. I've spent ages Googling for solutions - none has worked yet. And, being a novice, I'm frankly afraid to try things that are quite drastic (like this thread seems to be, to me).

So, I along with numerous other people are starting to hate PulseAudio. Why a "miserable existence" without it? With it, I may as well be deaf, because I get no sound. THAT is a miserable existence.

Cheers,
Kath

do You have sound with Pulseaudio "kill"-ed?

---

### Post by enfant_terible_1 on 2008-12-31
Damn thanks.. i've been looking for a solution and going mad for make it work... and when i've typed killall pulseaudio someone entered on msn and i've heard the classic emesene sound. Thanks again

---

### Post by zika on 2008-12-31
> **enfant_terible_1 said:**
> Damn thanks.. i've been looking for a solution and going mad for make it work... and when i've typed killall pulseaudio someone entered on msn and i've heard the classic emesene sound. Thanks again

#57 and #59 in this thread :). as soon as I've written those I've learned that pulse audio is not so bad, but about that in the next year ... ;)

---

### Post by koolkatkiwi on 2009-01-04
> **zika said:**
> finaly a voice of reason! you do not have to uninstall pulseaudio in order not to use it.

in System->Preferences->Sessions uncheck Pulse Audio and add new item with appropriate name and comment and in command field put ```
killall pulseaudio
``` and that way it won't come up on boot and everything is OK, check in with ```
alsamixer
```



Hi. I did this, killing PulseAudio on boot. When I was booted up I got a message saying:

New Information Available

Refresh Advanced Linux Sound Architecture (ALSA) configuration presets

New Advanced Linux Sound Architecture (ALSA) configuration presets have been added.  Please execute the asoundconf(1) set-default-card macro in a Terminal now to refresh your user's configuration presets.  You may accomplish this task by executing the following command in a Terminal: asoundconf set-default-card

So I did this, setting the NVidia card as the default (I also have an M-Audio Delta 44 installed).

Then, I did as you said and put:

```
billkath@musicmaker:~$ alsamixer
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused
billkath@musicmaker:~$
```

. . . that's the result.


I still get no sound in any program that I've tried. I'd especially like to get Skype going, but no dice.

Any other advice on what I should do next? Thanks in advance.

Cheers,
Kath

---

### Post by koolkatkiwi on 2009-01-04
With the command "alsamixer" the "connection is refused". Is this supposed to happen? And, what do I do now?

Thanks.

Cheers,
Kath :KS

---

### Post by koolkatkiwi on 2009-01-04
Well, I did something - changed a few settings to re-instate PulseAudio, and now I do get a result from the above command:

&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.17 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: PulseAudio                                                             &#9474;
&#9474; Chip: PulseAudio                                                             &#9474;
&#9474; View:  Playback  Capture [All]                                               &#9474;
&#9474; Item: Master 

and then a couple of coloured bar graphs with "Master" and "Capture" labels.

So, I'm getting somewhere, I guess - not sure where, though. I have a DVD playing so that I'll know if and when sound appears, though of course if a reboot is necessary, that won't help.

Cheers,
Kath :KS

---

### Post by koolkatkiwi on 2009-01-04
Now I have rebooted and when playing a DVD and looking at the PulseAudio Applet Device Chooser, and looking at the Volume Control Playback tab, I do see that something is playing back (where before there was nothing). 

However, the maximum volume it seems to allow, with volume sliders full up, is o.oo dB - which is NO volume at all, right?

So, anyone have an idea how to change that 0 dB setting?

Cheers,
Kath:KS

P.S. Though this thread is for removal of PulseAudio, I'm continuing to post in it because if I started a new thread, all the other responses here leading up to my present situation would be lost. So, please bear with me.

---

### Post by koolkatkiwi on 2009-01-06
Hi. I'm just reporting in that I have now got sound working partially, after a fashion, but without PulseAudio, and only on the onboard soundcard. Here's what I did:
[http://ubuntuforums.org/newreply.php?do=postreply&t=789578](http://ubuntuforums.org/newreply.php?do=postreply&t=789578)

I haven't removed PulseAudio, but it has been disabled somehow, when I did this tutorial.

Good luck to those who still have no sound!

Cheers,
Kath :KS

---

### Post by gaston.alegre on 2009-01-06
Thanks so much, all audio is working now. After the latest Pulseaudio update sound was broken.

Thanks.

---

### Post by koolkatkiwi on 2009-01-07
:popcorn: Many thanks to DSCP46 for starting this thread and giving us the means to get back our sound. The "thank you" button has disappeared from your first post or I would have thanked you officially.

I was stubbornly going to get PulseAudio to ***work***. After faffing around with it for several weeks, and trying some of the other threads to try to get it going, and eventually getting partial (poor) sound, I tried to watch a YouTube video. No dice - horrible distortion, etc. 

So, I finally admitted defeat and followed the instructions in post #1 and #6 in this thread. I now have my sound back, and can watch YouTube videos, movies in Totem and VLC, use Skype, hear computer "event" sounds. Everything, so far, works ***brilliantly***.

I am not sorry at all to lose PulseAudio, and my plan now is to keep Intrepid on this computer for as long as I possibly can - 18 months, I think it will be supported for. The frustration with PA has been enormous.

The worst thing about Ubuntu is that when you upgrade, some stuff that was working great before, gets broken (possibly not fair to single out this one distro, though). While some good and useful things get added to the new release, is it really worth it in the long run? The time spent trying to fix things is enormous and frustrating. Maybe fewer new releases with a longer time between would be better, with more time for testing and fewer things broken. This is just MHO, of course - what do I know, as a Newbie?

Cheers,
Kath :KS

---

### Post by Izek on 2009-01-23
I did what was done in the first post,

but PulseAudio sounds server is still selectable from the sound configurations. I also did killall pulseaudio, but that didn't help. And this problem:

```
ian@ian-desktop:~$ cd ~
ian@ian-desktop:~$ rm .asound*
rm: cannot remove `.asound*': No such file or directory
ian@ian-desktop:~$ rm .asound
rm: cannot remove `.asound': No such file or directory
```

---

### Post by jmd9qs on 2009-01-24
thank you so much! this was beginning to piss me off since I couldn't hear sound in any flash applications! all hail Ubuntu Forums!

jmd9qs

---

### Post by ricardisimo on 2009-02-12
The original poster's instructions working like a dream so far. Thank you very much. One little burp: my custom login sound is jumpy now, to say the least. Any ideas there?

---

### Post by cougarsky on 2009-02-18
I've followed the instructions to remove *pulseaudio* and everything is now fine.  But just say if I want to reinstall it back if I do have problems without it in the future, anyone knows how to re-install it??

---

### Post by bsalt on 2009-02-23
Nice post! Thanks for this how-to! I have both Gnome and XFCE installed and I wanted to go to something XFCE supports better, and this helped me out.

Thanks again.

---

### Post by fibercode on 2009-03-16
This worked for me like a charm.
I had no sound on my old box when I played embedded flash.

Just for the record, the sound card on it is:

Intel Corporation 82801BA/BAM AC'97 Audio

---

### Post by villevalorox on 2009-03-20
OMFG!! U ROCK!!! thanks so much! I looked days and days for this!! Much love:D

---

### Post by cfmunster on 2009-03-24
> **psyke83 said:**
> I just noticed that we have two identical guides on removing PulseAudio. IMHO, it's a bad idea to remove the PulseAudio packages as they are now a part of the core system, so you could experience problems with upgrades.

Please see my post [here]("http://ubuntuforums.org/showpost.php?p=6149347&postcount=51") for information to either a) configure PulseAudio properly, or b) disable PulseAudio **safely**.

Sweet, that worked for me. Thanks for posting....

---

### Post by brucewagner on 2009-04-20
Why why why why does Ubuntu still come with Pulseaudio by default?  

....when so many have troubles with it?

Is it still included in 9.04 ?

Have any of the PulseAudio problems been fixed in 9.04 ?

---

### Post by redenex on 2009-04-20
> **brucewagner said:**
> Why why why why does Ubuntu still come with Pulseaudio by default?  

....when so many have troubles with it?

Is it still included in 9.04 ?

Have any of the PulseAudio problems been fixed in 9.04 ?

I wish I knew it, I havebeen asking the same questions for a while now, but no one seemsto know for sure. Once Jautny is released and if is still have the same issues, I would perhaps embrace another distro and sayu goodbye to Ubuntu.

---

### Post by NoThanksM$ on 2009-04-20
From what I've seen, the PulseAudio implementation in 9.04 is supposed to be improved over past releases.  I believe it includes PulseAudio 0.9.14.  Also, PulseAudio 0.9.15, which fixes a number of additional bugs, was released a few days ago and you should be able to upgrade to that after installing Jaunty.

---

### Post by markbuntu on 2009-04-20
> **redenex said:**
> I wish I knew it, I havebeen asking the same questions for a while now, but no one seemsto know for sure. Once Jautny is released and if is still have the same issues, I would perhaps embrace another distro and sayu goodbye to Ubuntu.

Fedora, Mandriva, Suse and many other distros also use pulseaudio though their users seem to have far fewer issues with pulseaudio. Probably because they included the pa volume control and pre-configured all the sound to actually go through pulse which Ubuntu still does not do in Jaunty so if you are looking for some sort of miracle with Jaunty forget it.

If you want to see a proper implementation of pulseaudio try Fedora or Mandriva. You will quickly see that the problem is not pulseaudio, it is ubuntu.

Anyway, it takes less than 10 minutes to get pulse set up properly.

---

### Post by SuperZ on 2009-05-05
thanks... this helped =)

---

### Post by Baelus on 2009-05-18
Wish I'd seen this sooner. I borked my whole system trying to get rid of the damn thing.

Reinstalling now...:mad:

---

### Post by Darth Buh on 2009-05-18
I tried using Jaunty, and found that PulseAudio support for my Audigy 2 card was so bad, I wiped my machine and went back to 8.10.

As for using ALSA and World of Warcraft, how does one use Ventrilo at the same time?  With my current PulseAudio config, I have PTT supported while in-game and when Ventrilo is the top level program on my desktop when not in-game.

When I tried using ALSA exclusively, PTT behavior was erratic, and also when I held down the PTT key, any audio coming from WoW was picked up by my outgoing voice communication, making my voice jumbled with all game sounds.

PulseAudio remains a source of frustration for me with every release, however the way I use my machine for gaming, I'm stuck with it.

DB

---

