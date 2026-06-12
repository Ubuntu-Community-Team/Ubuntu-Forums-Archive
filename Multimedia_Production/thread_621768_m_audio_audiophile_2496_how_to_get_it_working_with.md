---
title: "m audio audiophile 2496 how to get it working with ALSA and/or jack audio?"
date: 2007-11-24
forum: Multimedia Production
---

### Post by streamsanddragonflies on 2007-11-24
HI!
I've worked with this soundcard in windows up to now and used it with ASIO drivers, which is the professional music standard in windows, supposedly.  Also I can set the mixer panel; input/out, the buffer size, hardware settings (Hrtz). ect... will I find all these features with the apps related to ALSA or jack audio or do I need to add an open source equivalent not found in the repositories?  So far, Ubuntu "sees" the card but no sound comes out.   Also the m audio company refers linux users to 4front technologies for drivers and these are not free...& I don't know how good they are.  I got very interested in recording music in linux when I read about it being used in studios and by musicians so I hope I can learn to use it and move away from windows eventually!

---

### Post by d_in_Conduct on 2007-11-25
You could check for the Envy24 mixer app.  If your 2496 uses the same chip as the Delta series, it should be on there.  Everything is muted when it is first installed, so you have to bring up the faders.

For that matter, look for the alsa mixer.  I think there is a alsa-mixer-gui in the menu.  That one is probably all muted also.

---

### Post by Stochastic on 2007-11-25
Jack (or qjackctl) is what I would recommend. It will give you much more control and flexibility than AISO.

---

### Post by Lagos on 2007-11-26
i have a delta66 card and everything works on mine.  i just had to bring up the faders and unmute the sound. 

try double clicking on the speaker icon, and then going to edit/preferences, to enable all the other audio channels.

---

### Post by streamsanddragonflies on 2007-11-27
Hello again and thanks for the suggestions/confirmations!

Well the good news is that my card is part of the delta series so I should be alright!  I had jack and ALSA mixer ect... installed but I never got to explore all their settings, so I have to find the volumes that are set to zero!    A question directed to Stochastic: did you found the latency to be negligeable, as with the ASIO drivers?  The other question is a reiteration...has anyone seen or tried the windows mixer panel for these soundcards and are all those settings found in jack?  I ask because I can't access my Ubuntu studio right now:   I just messed up my grub  and SuperGrubtDisk couln't help.  I will spare furthur details, cause It's not related to this thread, but until I fix the problem I can't study the sound features directly, but I wanted to at least get a little prepped... 
Just curious if anyone in this forum is working with linux music apps in a professional setting? (I'm still an amateur) and any musicians recording with linux apps..?

---

### Post by oskar2000 on 2007-12-14
I record professionally, but not with linux. Mainly because I can't get comfortable with Ardour, and I don't really have a reason to mess with VST's in wine when I don't really have a problem with windows for that purpose.
 However, running [reaper]("http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio/") in wine works very well, and that's what I use for home recording.

---

### Post by oskar2000 on 2007-12-14
> **streamsanddragonflies said:**
> A question directed to Stochastic: did you found the latency to be negligeable, as with the ASIO drivers?  The other question is a reiteration...has anyone seen or tried the windows mixer panel for these soundcards and are all those settings found in jack? 
Latency is negligible.
Yes, the settings can be either found in Jack, or in the Envy24 control

---

### Post by streamsanddragonflies on 2007-12-25
Hi!
And Merry Xmas to evryon'!
In case your wondering, my family just left and I have a bit of free time 'til tomorow,
 xmas-day!  They were intrigued by my finally re-installed U.St.(and Xubuntu) and we had fun finding all kinds of music from youtube.  

I got the card to work from ALSA Gui and config. for playing cds but music from the web was only playing from the lousy onboard card and I coudn't figure out how to chnge it!  I ended up switching back to windows on my main computer for now but I got things working alright in Xubuntu-somehow it's a little easier to set up in Xfce!  I now turned off the onboard card from the bios, but will this be enough-make my card the default- so that all programs play with my soundcard?  So far VLC had no sound!!!  I think I have to install jack, but I thought it was already on there! I will try to read some man pages and hlp files cause when I fiddled with jack in jacklab 1.0 (suse) I was a little confused... 

Thanks for all the replies so far, I'm trying to process and learn so many aspects at once, and the more I look in Ubuntu the more questions arise.

In case it works in wine...I suggest trying Kristal audio engine by kreatives.  For a simple quick multitrack recording program with VST plug in capabilites, it's fun to use! 
Happy New Year (in advance)!


:guitar:                                                             :guitar:                                                                    :guitar:

---

### Post by xl_cheese on 2007-12-25
from qjackctl click the setup button.  In that panel you'll see Input Device: and Output Device:.  Click on the arrow next to them and make sure to select the maudio card.

---

### Post by streamsanddragonflies on 2008-01-10
Hi!  Thanks for replying to my aging thread, but I still am confused by jack audio connection kit. The only part I could understand a bit was in setup: where I did choose m-audio as the input/output device... or it could be under the other designation of ice1712 multi with the difference of hw0,0 rather than just hw0.  
(ubuntu sees my card as ice 1712 actually, which I managed to set as the default after all!)  I have no idea what to add in patchbay actually and 
 I could not start jack or connect:  Here is the message:

"02:35:55.932 Patchbay deactivated.
02:35:55.954 Statistics reset.
JACK tmpdir identified as [/dev/shm]
02:35:56.025 MIDI connection graph change.
02:35:56.169 MIDI connection change.
02:36:28.884 Startup script...
02:36:28.885 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /home/d/.kde/socket-ubuntustudio.
02:36:29.135 Startup script terminated with exit status=256.
02:36:29.135 JACK is starting...
02:36:29.136 jackd-realtime -R -dalsa -r44100 -p1024 -n2 -D -Chw:0 -Phw:0 -i2 -o2
02:36:29.139 Could not start JACK. Sorry.
02:36:33.420 JACK was stopped successfully.
02:36:33.424 Post-shutdown script...
02:36:33.428 killall jackd
jackd: no process killed
02:36:33.665 Post-shutdown script terminated with exit status=256."

Ok I will try to read up on their site ect... real soon, but in the meantime I wanted to mention that I did manage to set my preferred soundcard as the default, as directed in another thread** and that was my first real foray into the line command/terminal and it was nice to see the positive results!  Also in the Envy24  Control Utility,  I found that by unlocking the rate in the hardware settings, as is done when in MS Windows, this solved a horrid latency issue when listening to music in YouTube for example.  I left all the rest at default settings.  I hope this helps in case someone else may have the same problems!
Anyways, I wanted to add how pleased I am with ubuntu and linux so far!  And the added challenges and solving problems with command lines is so satisfying, (as long as they stay manageable-I hope!)

**in case someone needs it, here is a 'copy' of a post with the commands to remove the wrong soundcards  'cause I can't find the thread in the forum:  
"here is a quick guide that i found here on ubuntu forums (can't remember which user it was though?) which helped me get sound back all the time.



In terminal type



less /proc/asound/modules



That will show you which soundcards occupy which slot and what their names are.



My output is



0 snd_cmipci

1 snd_mpu401

2 snd_via82xx



Now identify which cards you don't want to use and note their names.



In terminal now type



sudo gedit /etc/modprobe.d/alsa-base



Find the place where it says something like

# Prevent abnormal drivers from grabbing index 0

and in the list below add

options snd_whateveryourcardnameswere index=-2



(replace whateveryourcardnameswere with the soundcard you don't want to use, also snd_ may appear as snd- )



If you have two cards you want to blacklist then you add two lines with different names.



Now save /etc/modprobe.d/alsa-base and reboot the computer. It *should* now set the "wrong" sound cards to slot -2 (thus, making them disabled) and the correct soundcard should thus grab slot 0 and work."

__________________


:p                                                                                                        :popcorn:

---

### Post by warbread on 2008-01-11
Have you given the proper permissions to the audio group?  

```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'

```

I also have an Audiophile 24/96 and it works flawlessly in 32-bit Gutsy.

---

### Post by chunderbunny on 2008-01-11
I have recently found to my dismay that the ALSA drivers do NOT support the latest revision of the Delta series of cards. If you have a "REV-E" card (it's written on the card itself) then you will find that while the card appears to work (all apps recognise it and envy24 shows activity on the meters) you may not get any actual audio out of the device.

"REV-E" cards were produced during 2007 and the end of 2006, so if your card is fairly recent then it will be unlikely to work until the ALSA driver is fixed.

---

### Post by geoff123 on 2008-01-15
FWIW - I have a couple year old audiophile2496 and it works great.  It should work out of the box on gutsy.  

-Take the time to learn jack - it's really sweet how you route stuff around in it.  But it took me a couple tries to really get it. be creative
-start by messing around with hydrogen, ardour, and maybe rosegarden for midi. learn about the jack connections. Once you got that down, start exploring other programs. 
-ardour is great, but can be a pain to learn.
-I wouldn't mess around with VSTs/wine yet, it's still too bleeding edge. Try some of the packaged soft synths if thats what you want.

Hope this helps.

---

### Post by streamsanddragonflies on 2008-01-18
Hi!
I haven't had the time to read up on jack yet unfortunately but continue to use ALSA for now and I've been getting cinelerra and other multimedia downloaded instead.  In case if you read again, warbread, I was curious if the commands for the permissions for the audio group were taken from the jack site or from ubuntu docs? " security limits?" what's that about?
 
 Will have to try another night, I'm burned out again by what I thought would be a couple of simple changes to try to my grub.....

My card is a bit older than the one chunderbunny mentionned (rev-E series), so it's compatible thank God, but my webcam or future photo scanner are not yet.   I am confident that they will find a way soon enough with most missing drivers- the Ubuntu community seems very dedicated!  I am still doing some things in windows rather than wine for now, 'cause learning each new app. or finding the commands is time consuming so I am pacing myself.  I found ways to just import the multimedia files from the windows apps and edit further in linux and that's fine with me!  I'm staying with linux for the long haul-I love it!

:lolflag:                                                     :guitar:

---

### Post by sanjeevpunj on 2008-05-09
I got it working in a previous installation, and now I have forgotten how I did that! I am sure sooner or later I can get it working again, but if someone can provide a basic clue as to which driver really needs to be installed for M-Audio Delta Audiophile 2496 card, I would be grateful indeed.

---

### Post by ZootHornRollo on 2008-05-19
drivers from 4front are available here for free for non-commercial use :

[http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)

i am thinking of getting one of these cards to use my pc as an audio source for FLAC files through my hi-fi.  if someone could confirm that it does work in linux i'd be grateful.  (i would be buying a brand new one)

not sure which driver to donwload for ubunto 8.1 tho?  any idea's?

---

### Post by ZootHornRollo on 2008-05-20
should be version 8.04 LTS...  sorry...  new to linux!

<<<<<  nOOb

---

### Post by ZootHornRollo on 2008-05-22
nobody?

---

### Post by oskar2000 on 2008-05-23
The m-audio cards have worked with oss for years, and with alsa for just a couple years less. - so you don't need additional drivers.

It's pulseaudio that screws up the compatibility, and it's one of many reasons why I've switched to PCLinuxOS for the time being.
There are bug reports on this, and we can only hope that the Ubuntu team will fix this issue soon. 

It's the same with Fedora - so I'm pretty positive that it's a pulseaudio issue, since I've used this card with many distributions over the years and never had any issues.

edit
I for one welcome our Psychedelic Rock overlords to the Ubuntu Forum!
/edit

---

### Post by ZootHornRollo on 2008-05-25
hi,

i got a second hand rev B m-audio 2496 from ebay and cannot get a peep out of it.

I have installed eAR OS Linux (ubunto based i think) which is more orientated towards my final usage - purely an audio source.  

is there an idiots guide anywhere to get this card working?  i mean real idiots guide.  One that takes me by the hand and talks through step by step.

you mention you think it is a pulse audio issue.  Is there any way to disable that?

in the absense of a better solution just now i may just a get a Behringer UCA202 in the mean time.

edit :  i have been playing about with all the audio settings and i have no idea what i have changed what i have not.  any way to reset to default?

---

### Post by ZootHornRollo on 2008-05-25
i have reinstalled eAR OS to get evrything back to default settings then gone through Comprehensive Sound Problem Solutions Guide v0.5e thread and it still doesn't work.

i can get the output meters in the envy24 control are showing activity, but no sound from the analogue rca outputs of the card.

i guess its time for plan A which was the behringer.

If nothing else i have learned a little about how to use linux (even if it was unsuccessful)  the terminal thingy was a bit scary at first but have had to use it  a bit in troubleshooting this card.  so not a complete loss.

might give the m-audio a go in my windows machine.

---

### Post by oskar2000 on 2008-05-25
I wish I could help you, but I had exactly the same problem. Theoretically you should just have to set everything to ALSA in System - Preferences - Sound, but that gave me an error message.

This problem should really only affect two distributions for the time being: Fedora 9 and Ubuntu 8.04. The soundcard should work out of the box with the previous versions of Ubuntu and Fedora - and all versions of Mandriva, Suse and Debian for at least 4 years.
I wouldn't waste too much time on this (I know I have). Just try another distribution. PCLinuxOS works fine for me. Plus it works very similar to Ubuntu despite being an RPM based distribution.

---

### Post by ZootHornRollo on 2008-05-26
ok,

I am downloading PCLinuxOS just now and will try it when I get home from work.

i'll let you know how I get on.

---

### Post by ZootHornRollo on 2008-05-26
i tried the live disc for pclinuxos and cannot say i liked it.

as a novice i found it hard to use and very difficult to confidently test my sound card due to the lack of a sample audio file and i cannot open the cd drive. (presumably as it contains the live cd)

back to square one.

i am going to use the linux machine purely as an audio source for my hifi, and i still have my windows machine for general use.  but i am now considering transfering my windows instalation onto the music box and using ubuntu for general use.  thinking about my usage i very rarely play games on pc these days so it probably wouldn't be a major loss going full time linux.

---

### Post by oskar2000 on 2008-05-26
It contains all the media plugins for firefox, so you can just go to youtube, or listen to internet radio, or download an mp3.

If you start the live cd with the "to ram" option you can eject the cdrom after it loaded (probably won't work so well if you have less than 1 gig of ram.)

- I know it's butt-ugly, but you can change that very easily. KDE isn't hard to configure, and you can install gnome with the 'task-gnome' meta package from synaptic.

---

### Post by ZootHornRollo on 2008-05-26
ok,

i'll try pclinuxos one more time.

i'm desperate to get this card to work!!!!

;)

---

### Post by ZootHornRollo on 2008-05-26
i couldn't get pclinux to configure my wireless connection which worked flawlessly in eAR and ubuntu adn i only have 512mb ram so wouldn't do the ram install.

i have put the card in my xp machine and i can't get any sound out of there either.  i'm now wondering if it may be faulty.

---

### Post by oskar2000 on 2008-05-26
Well.. XP does *not* have the drivers.
For some reason even the ones you can download from the m-audio page didn't work for me. You have to install it from the cd, and after a reboot Windows sais "new hardware found, search for drivers?..." - and then you have to say yes and point it to the cd even though they're already installed. It's a bit tricky.

Do you have a sound-on-board card in there? You might want to disable that in the bios.

You can check with:
lspci | grep audio

If the card is in there - it should look something like this:

00:0a.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

If two devices show up - the sound manager thingy might just have decided to use the wrong one.

---

### Post by oskar2000 on 2008-05-26
For the wireless network people have reported that the autostarting the network applet worked for them:

copy and paste this into a terminal:
> mv ~/.net_applet ~/.net_applet.backup && echo AUTOSTART=TRUE > ~/.net_applet 

And log out and in again.

---

### Post by ZootHornRollo on 2008-05-27
i tried both drivers on cd and drivers from m-audio website in XP, with no success with either.  i have disable the onboard sound in the bios.

i am on my way to work so don't have time to play around just now.    will try the command line later.

thanks for helping.

---

### Post by ZootHornRollo on 2008-05-27
IT LIVES!!!!!!   ;) :)

i have managed to get it to work in XP.

i will try once more in Linux, if no success i will switch to linux for my main computing.

DELIGHTED!!!!   a small but significant step!

---

### Post by ZootHornRollo on 2008-05-27
still no usccess with ubunto, eAR or pclinux.

but without internet access  in pc linux it is hard to trouble shoot.

:(

---

### Post by oskar2000 on 2008-05-27
> **ZootHornRollo said:**
> still no usccess with ubunto, eAR or pclinux.

but without internet access  in pc linux it is hard to trouble shoot.

:(

Well, if ear uses pulseaudio too, then that doesn't surprise me.
Don't you have a usb stick... floppy... mp3 player... usb harddrive... mobile phone with usb... something that you can put some media on? Didn't you say you wanted to use it as media center? Where did you plan to get the media from? I suggest you do just that, as the live-cd is a fully functional system, only that it will forget all the changes that you make.
If you double-click the speaker symbol and you see the m-audio card in "File - Change Device" you can be pretty sure that it will work.

I think amarok should come with a sample mp3 (Applications - Multimedia - Sound - Amarok)

Oh... and of course the system sounds are in /usr/share/sounds ](*,)

---

### Post by ZootHornRollo on 2008-05-27
SUCCESS!!!!!!!!

Tried PCLinux again and after playing about for a while it just started working.  The unfortunate thing is that i don't really have any idea what i did to get it on.  Nevermind.  At least i know it works.

I will now do a proper install of PCLinux.

Thanks for all your help.  I really appreciate it.

I'll keep you up to date.

---

