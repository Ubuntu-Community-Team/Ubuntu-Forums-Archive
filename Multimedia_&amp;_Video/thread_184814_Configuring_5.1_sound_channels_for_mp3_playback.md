---
title: "Configuring 5.1 sound channels for mp3 playback"
date: 2006-05-30
forum: Multimedia &amp; Video
---

### Post by RobMongoose on 2006-05-30
Hi,

I was on here recently asking for help because I thought that my sound card wasn't correctly configured to use all of the channels needed for 5.1 sound. What I thought was happening was that my computer would only play sound out of the front 2 speakers. The volume sliders for the other speakers were appearing in alsamixer, and the speakers are correctly connected as the sound works fine in Windows.

Since then I've done a bit of digging and have discovered that if I play a movie with 5.1 sound from DVD in xine the surround sound works! So I'm happy with that, but I still have a bit of a problem - I still only get the 2 channel sound with everything else, like amarok and totem. I don't really care about full surround sound for these (although it would be nice), I just want my subwoofer to work so that my mp3s stop sounding so crap.

I've also tried creating an .asoundrc file in my home directory using the info from [here]("http://www.ubuntuforums.org/archive/index.php/t-31829.html") and what this does is give me stuttery sound from my rear speakers, but nothing else. So, I reckon this file may be the way forward for me, but I can't suss out what the settings mean enough to be able to troubleshoot it for my card.

Has anyone else had any experience configuring sound channels that can help me?

I'm running kubuntu breezy and my sound card is an SB Audigy SE using the CA0106 driver. I've also tried following the article in the Ubuntu wiki on configuring this card but this hasn't fixed anything.

Can anyone help me with this please? I reckon I'm so close to sussing it, but not quite there...

---

### Post by RobMongoose on 2006-05-30
Oh yeah, forgot to mention, I also tried running speaker-test 0.0.8 in konsole and that only gives sound from the front 2 speakers (this is without the .asoundrc file in place)

Cheers :)

---

### Post by RobMongoose on 2006-06-21
SOLVED! Finally! I'm so chuffed....

What I did was to create a .asoundrc file in my home folder and used a script that I found [here]("http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix")  which goes a little something like:

```
#########################################################
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

pcm.!default {
        type plug
        slave.pcm "surround51"
        slave.channels 6
        route_policy duplicate
}
########################################################
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
    type plug
    slave.pcm "hw:0,1"
}

#######################################################
#This is what one could call the "factory default setting", in other words, it only plays the actual channels. so if you fx want to watch a 5.1 movie, on the analog output, this is the option you want. 


pcm.analog {
    type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}
```

Then I logged out and back into KDE, reinstalled Amarok, amarok-xine and amarok engines

```
sudo apt-get remove amarok
sudo apt-get install kubuntu-desktop
```

Then I started up Amarok, went into the settings, and selected xine as my engine, then told it was using alsa as my output plugin, then put 'default' in all of the 'Alsa Device Configuration' boxes, and BINGO! Lushious bass ridden sound.

The sound works fine in kaffeine now as well.

Hope this helps someone - I reckon it may well work on other sound cards n all.

---

### Post by sdyson on 2006-06-22
I'm also having problems playing mp3s in Amarok since upgrading to dapper :(

---

### Post by s@bertooth on 2006-07-14
this worked for me well with an onboard SB Live! 7.1 24bit
thank you very very mutch!

---

### Post by asplode on 2006-07-22
This "script" (config file) just worked for me in ubuntu dapper.

Words cannot express my heartfelt thanks for this.  Truly, you are a god among men.

---

### Post by Yellow Onion on 2006-08-08
Lovely!! I can say it works with a Nivdia CK804 + realtek ALC850
No need to Reinstall amaroK just 
Close amaroK

$ /etc/init.d/alsa-utils restart

and then reopen amaroK

only thing is it doesnt mix sounds cause I dont get sound from gaim when im playing a song
anyway of adding it to the file?

---

### Post by Garyu on 2006-08-09
> **Yellow Onion said:**
> 
only thing is it doesnt mix sounds cause I dont get sound from gaim when im playing a song
anyway of adding it to the file?

```
killall esd
```

If you're running Ubuntu (gnome) there is a really old and bad sound daemon called esd running to make it possible for apps to mix sounds on software level. However, most apps now use mixing in soundcard, not software, so they don't even ask esd to mix for them. As long as esd is running this means some sort of conflict so no mixing will be done unless you go through esd. If you kill esd all other apps that don't use esd for mixing will be able to mix sounds. So, kill esd and you should be able to hear everything nice enough. (until you start something that requires esd that is, then you won't hear a thing until you restart it)

---

### Post by greglee on 2006-08-09
Hi all
i follow the instrcutions in this thread, got sound from all 5.1ch.  But the sound output is choppy; lots of pop and stutter.

I use Totem to playback, then try VLC.  When the setting is 'Default" in ALSA->Output module, same problem.  But when changed to the second seting, which is "Intel ICH: Intel ICH (hw:0,0)", I got good sound, but its back to 2ch.

Anything else I can do?  Very much appreciate the help.

---

### Post by bitrain on 2006-08-19
> **Yellow Onion said:**
> Lovely!! I can say it works with a Nivdia CK804 + realtek ALC850
No need to Reinstall amaroK just 
Close amaroK

$ /etc/init.d/alsa-utils restart

and then reopen amaroK

only thing is it doesnt mix sounds cause I dont get sound from gaim when im playing a song
anyway of adding it to the file?
I had to plug my center/bass speaker cable into line-in for the script to work.

---

### Post by Yellow Onion on 2006-08-21
```
killall esd
```
doesn't Work

any other Ideas?

also make sure "Surround Jake Mode" is on "Inderpendent"

or you wont get any sound out of the Centre and Sub

---

### Post by pixiemb on 2006-08-21
I have gone to the ALSA page but I am getting lost there
tried the killall and got this
... -desktop:~$ killall esd
esd(5695): Operation not permitted ...

still reading ... still trying to get to play mp3s lol

---

### Post by Yellow Onion on 2006-08-22
What Media Player Have You Got?
Do You have the Codec installed?

---

### Post by greglee on 2006-08-23
OK, after days of tinkering, finally found a solution.

The problem seems to be with the gstreamer.  I replace totem-gstreamer with totem-xine, and it finally worked.  Don't know why, or the difference between gstreamer or xine.

Problem is, Totem don't have customisations of the shortcut keys.  Finally settled on another player, Gxine, which works, though that has other annoyance issues.

Just my two cents worth, in case someone else has the same problem.

---

### Post by nekirc on 2006-09-01
It's works fine to me but when i start firefox i can't hear a sound in flash videos also it crashes all sounds in system. I can't hear anything since i'll kill firefox-bin process. Help.

---

### Post by conanm4 on 2006-09-04
Okay so it worked but now I have a bigger problem. When I start up my audio is crap untill I wait a few minutes then it's fine. However when i'm listening to music, about 25 minutes in I get a high pitched noise and then amarok or whatever program open with sound will bring up that the audio driver is gone. Any ideas?

---

### Post by manca on 2006-09-10
> **RobMongoose said:**
> SOLVED! Finally! I'm so chuffed....

What I did was to create a .asoundrc file in my home folder and used a script that I found [here]("http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix")  which goes a little something like:

```
#########################################################
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

pcm.!default {
        type plug
        slave.pcm "surround51"
        slave.channels 6
        route_policy duplicate
}
########################################################
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
    type plug
    slave.pcm "hw:0,1"
}

#######################################################
#This is what one could call the "factory default setting", in other words, it only plays the actual channels. so if you fx want to watch a 5.1 movie, on the analog output, this is the option you want. 


pcm.analog {
    type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}
```

Then I logged out and back into KDE, reinstalled Amarok, amarok-xine and amarok engines

```
sudo apt-get remove amarok
sudo apt-get install kubuntu-desktop
```

Then I started up Amarok, went into the settings, and selected xine as my engine, then told it was using alsa as my output plugin, then put 'default' in all of the 'Alsa Device Configuration' boxes, and BINGO! Lushious bass ridden sound.

The sound works fine in kaffeine now as well.

Hope this helps someone - I reckon it may well work on other sound cards n all.

Thanks for sharing man.
This one really helped! Although I had to change connectors, central and woofer are now plugged in line in. This won't be compatible with windows, damn...but hey i got it working here ;)

Once again thx!

---

### Post by manca on 2006-09-10
btw. I've just experienced first problems with this one...
It seems like amarok freezes somewhere at the middle of each song and then refreezes after 10ish secs. What could be the problem?

---

### Post by city-17 on 2006-09-11
People with a SB Audigy 2 ZS in Dapper should try the command alsamixer in a terminal and make sure Sorround and Center volumes aren't muted.

That worked for me.

---

### Post by Shed on 2006-09-11
Thanks, RobMongoose :D !

---

### Post by Chantanito on 2006-09-16
> **RobMongoose said:**
> SOLVED! Finally! I'm so chuffed....

What I did was to create a .asoundrc file in my home folder and used a script that I found [here]("http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix")  which goes a little something like:

```
#########################################################
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

pcm.!default {
        type plug
        slave.pcm "surround51"
        slave.channels 6
        route_policy duplicate
}
########################################################
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
    type plug
    slave.pcm "hw:0,1"
}

#######################################################
#This is what one could call the "factory default setting", in other words, it only plays the actual channels. so if you fx want to watch a 5.1 movie, on the analog output, this is the option you want. 


pcm.analog {
    type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}
```

Then I logged out and back into KDE, reinstalled Amarok, amarok-xine and amarok engines

```
sudo apt-get remove amarok
sudo apt-get install kubuntu-desktop
```

Then I started up Amarok, went into the settings, and selected xine as my engine, then told it was using alsa as my output plugin, then put 'default' in all of the 'Alsa Device Configuration' boxes, and BINGO! Lushious bass ridden sound.

The sound works fine in kaffeine now as well.

Hope this helps someone - I reckon it may well work on other sound cards n all.
-----


It worked just fine for me. Thanks RobMongoose for your dedication. I bought my sound card yesterday, the same as yours. I just did:

$ gedit .asoundrc

then i pasted the script into the .asoundrc file and saved the changes. No
need to log out, the changes where inmediate :grin: 

I must say that my system is Dapper AMD64...

Thanks again..

I just wonder if there's a way to control all the volumes at the same time, 'cuz every time i need to graduate it i need to move all of them, so any solutions to that?

---

### Post by ShinjiLeery on 2006-10-12
Hi

With the .asoundrc the rear speakers work perfectly!! Tnx

Bau there's another thing that i wanna ask. I have a 7.1 system with the live 24 bit creative. The two side speaker didn't work yet. How can i modify the file to activate it?
Tnx

Luca.

---

### Post by peter07 on 2006-10-28
> What I did was to create a .asoundrc file in my home folder and used a script that I found here which goes a little something like:

```
:

######################################################### #This is the standard setting (see: "!default") #This profile, the default loaded, upmixes stereo sound to 5.1. pcm.!default { type plug slave.pcm "surround51" slave.channels 6 route_policy duplicate } ######################################################## #This is the normal spdif output profile (optical, toslink). pcm.!spdif { type plug slave.pcm "hw:0,1" } ####################################################### #This is what one could call the "factory default setting", in other words, it only plays the actual channels. so if you fx want to watch a 5.1 movie, on the analog output, this is the option you want. pcm.analog { type plug slave analog_slave; } pcm_slave.analog_slave { pcm surround51; format S32_LE; }

```


I have ck804 on A8N-E mainboard. This .asoundrc doesn't work correctly. I have all six speakers working, but something is wrong with the sound. Sound is played with stops, it's breaking off. What I can do with it??

PS. I'm using egdy

---

### Post by ShinjiLeery on 2006-11-02
Hi,

the .asoundrc works perferctly on my Sound Blaster 24bit Live! (Ubuntu Edgy) but when i reboot, the pc freeze after the login. If i delete the file all works? 

Anyone have an idea why?

---

### Post by psychok9 on 2006-11-07
Guys, I've tryed but don't work!
I Have Edgy and SBLive + Realtek ALC850 (ALi M5455).
With SBLive 5.1 i have this error:
```
psychok9@psychok9-desktop:~$ speaker-test -c 6

speaker-test 1.0.11

Playback device is default
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.surround51.card'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directory
ALSA lib conf.c:3936:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM surround51
Playback open error: -2,No such file or directory
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.surround51.card'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directory
ALSA lib conf.c:3936:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM surround51
Playback open error: -2,No such file or directory

psychok9@psychok9-desktop:~$ sudo gedit /etc/asound.conf
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.surround51.card'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directory
ALSA lib conf.c:3936:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM surround51

```

Please helpme!

---

### Post by psychok9 on 2006-11-11
Hi,
I've tried to active the sound 5.1 in Ubuntu 6.10 with my integrated sound card Realtek ALC850 (on Linux M5455), but it doesn't work anything.
This is my .asoundrc (/home/psychok9/):

```

pcm.!default {
        type plug
        slave.pcm "surround51"
        slave.channels 6
        route_policy duplicate
}

pcm.!spdif {
    type plug
    slave.pcm "hw:0,1"
}

pcm.analog {
    type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}


```

And this is the output by speaker-test -c 6:
```

psychok9@amd64x2:~$ speaker-test -c 6

speaker-test 1.0.11

Playback device is default
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 3 to 5461
Period size range from 3 to 5461
Using max buffer size 5461
Periods = 4
was set period_size = 5461
was set buffer_size = 5461
buffer to small, could not use
Unable to determine current swparams for playback: Errore di I/O
Setting of swparams failed: Errore di I/O
```

---

### Post by techop on 2006-11-22
Thank you very much! This thread worked for me perfectly. I finally have 5.1 sound in Ubuntu!

---

### Post by vak on 2006-12-09
> **psychok9 said:**
> Hi,
I've tried to active the sound 5.1 in Ubuntu 6.10 with my integrated sound card Realtek ALC850 (on Linux M5455), but it doesn't work anything.
This is my .asoundrc (/home/psychok9/):

```

...
was set buffer_size = 5461
buffer to small, could not use
Unable to determine current swparams for playback: Errore di I/O
Setting of swparams failed: Errore di I/O
```

same with me

---

### Post by poekie on 2006-12-09
Thanks ever so much RobMongoose!

It works!

[edit] After a reboot, my arstd went up to 50+ % CPU-usage and Amarok couldn't find a sounddriver..... hmmm.. Any help?
[edit2] I purged alsa and set .asoundrc back to it's original form. Reboot, sound works. I put the new .asoundrc back and voila, it still works. But Amarok, even after the alsa-purge, still no sounddriver. Mplayer and Xine work fine. 
And with the sounds building up while watching a movie, oh well, I'd rather have 5.1 sound than kopete-sounds blaring through movies ;) (yes going on away means no sound as well, but hey, we all forget that sometimes, don't we? ;) )
[edit3] See edit 1... Back to old settings, reboot has immediate effect, sound works. 
Arts seems to have a problem with the 'new' settings, after booting with the script of RobMongoose it just goes up to the 50+ % CPU-usage and no way to fix it, except placing old asoundrc back and a reboot.. :S 
Does anyone have *any* idea how to solve this? I'd really like the 5.1 sound instead of 2.0 on my 5.1 speakers :( Not ever rebooting my system seems like such a desperate measure.. ;)
Oh, I do have a 'normal' question about this. In my old asoundrc which I got from the alsa-project site, there was no !default but the name of the chip (ca0106). Could this have anything to do with it? I'll just post it: 
```
pcm.ca0106 {
       type hw
       card 0
       }

ctl.ca0106 {
       type hw
       card 0
       }
```
And what is the ctl thing doing? Because that is not in the code of RobMongoose?

---

### Post by SonnY963 on 2006-12-23
In 6.06 this works for me but when i reinstalled my system and upgraded to 6.10 and then used this settings it doesn't work anymore. Any ideas?

---

### Post by Yellow Onion on 2007-01-24
heres my config to upmix to 5.1 and mix multiple sound sources together mite help some one 

```

pcm.!spdif {
    type plug
    slave.pcm "hw:0,2"
}

pcm.!surround51 {
type plug
slave.pcm "dmixer"
}

pcm.!default {
  type plug
  slave.pcm "dmixer"
  route_policy duplicate
}

pcm.dmixer  {
        type dmix
        ipc_key 321456
        ipc_key_add_uid true
        slave {
                pcm "hw:0,0"
                channels 6
                period_time 0
                period_size 1024
                buffer_size 4096
                rate 96000
        }

        ## 0 = Left, 1 = Right, 2 = Centre, 3 = Subwoofer , 4 = Rear Left, 5 = Rear right.
        bindings { 
            0 0
            1 1
            2 4
            3 5
            4 2
            5 3
        }
    }
 
    ctl.dmixer {
        type hw
        card 0
    }


```

---

### Post by Grefven on 2007-01-30
Thank you Yellow Onion.

Got my sound to work with your conf. 
Although I had to plug my Center/Sub to the Line-In to get sound from the center speaker, as has been mentioned before.

//Grefven

---

### Post by zeny on 2007-03-21
Hey!

Thanks I got this to work for me (RobMongoose asoundrc file), HOWEVER I noticed a bit of lag after the first song, and it sounded like a echo because some of the speakers had a delay.

And input would be great, thanks!

---

### Post by herbster on 2007-03-26
RobMongoose,

I am using the exact same card as you, the SB Audigy SE on Ubuntu 6.10, and I used your script and this is what I get:

```
bobby@bobby-ubuntu:~$ speaker-test -c 6

speaker-test 1.0.11

Playback device is default
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.surround51.card'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directory
ALSA lib conf.c:3936:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM surround51
Playback open error: -2,No such file or directory
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.surround51.card'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directory
ALSA lib conf.c:3936:(snd_config_expand) Args evaluate error: No such file or directory
```

I also tried Yellow Onion's above and got another error as well. I just cannot get this damned thing to work on more than the left/right front speakers!!! :mad: :mad:

Anyone any ideas ?!?!

---

### Post by miceagol on 2007-04-01
With my card (an M-audio Revolution 5.1) I got a chipmunk effect (sound played too fast) when using the ~/.asoundrc files in this thread. In Amarok I also got choppy playback. If you have these issues, try this .asoundrc. Got it tailor made on #alsa. :D
```

# 6 channel dmix:
pcm.dmix6 {
     type dmix
        ipc_key 1024
        ipc_key_add_uid false
        ipc_perm 0660
        slave {
                pcm "hw:0,0"
                rate 48000
                channels 6
                period_time 0
                period_size 1024
                buffer_time 0
                buffer_size 5120
        }
     }

# upmixing: 
pcm.ch51dup {
        type route
        slave.pcm dmix6
        slave.channels 6
        ttable.0.0 1
        ttable.1.1 1
        ttable.0.2 1
        ttable.1.3 1
        ttable.0.4 0.5
        ttable.1.4 0.5
        ttable.0.5 0.5
        ttable.1.5 0.5
   }

pcm.duplex {
     type asym
     playback.pcm "ch51dup" # upmix first
     capture.pcm "hw:0"
}

# change default device:
pcm.!default {
     type plug 
     slave.pcm "duplex"
}

# for aoss
pcm.dsp "duplex"

pcm.dsp1 "duplex"

```
For more information, [take a look here]("http://www.ubuntuforums.org/showpost.php?p=2387139&postcount=25").

---

### Post by RobMongoose on 2007-04-26
Glad the file helped a few people. 

For those still having problems, sorry I don't really know what to suggest - I just found this by googling around until I found something that worked...

---

### Post by Yellow Onion on 2007-05-17
> **Grefven said:**
> Thank you Yellow Onion.

Got my sound to work with your conf. 
Although I had to plug my Center/Sub to the Line-In to get sound from the center speaker, as has been mentioned before.

//Grefven

Theres a Switch in the sound controls cant remember the name but the options are shared and independent try changing that to get sub/centre working as it does the same for me.
if that doesnt work try changing the bindings to some thing else just in case the sub/centre are on different channels than my card

OSS emulation 
i also added something like this (im not at my computer at the mo so i wouldnt know but the basic Principle is there)

```

pcm.dsp {
     type plug 
     slave.pcm "dmixer" # or try default to upmix to 5.1
}

```

try dsp0, dsp1, etc if dsp doesnt  work (try all of them (at same time) if ya want)im not exacly how oss works but i also think you can make Multiple ones and change settings in the app to use different ones and then you could have a 5.1 for doom3 or something and a 2.0upmix for something else
then for oss apps put aoss in front of the cmd or most oss apps like doom 3 have a script file to launch then and you can add it to that

Now next things to do is get Master volume to actually control the "master volume"  (just not the frount two speakers)
get the PCM volume to control All PCM channels ( just not the frount two)
get a independent volume control for the Frount speakers
and when i  change it from 6 channels to 2 channels it should down mix 6 channels to 2 and turn off the other speakers
And Spdif Passthrough(at the moment it makes a ficker sound and then says no digital data) so i can listen to my DVDs with better sound quality

Then the sound will match my windows install

---

### Post by sAmiZZle on 2008-06-12
I just did the last bit in amaraok after installing Hardy> Then I started up Amarok, went into the settings, and selected xine as my engine, then told it was using alsa as my output plugin, then put 'default' in all of the 'Alsa Device Configuration' boxes, and BINGO! Lushious bass ridden sound....and it's all good now!. Thanks heaps.

---

### Post by foolean on 2008-06-20
I have a soundblaster live 5.1, tried the .asoundrc config, restarted alsa-utils, but to get sound I had to change to the line-in(?) connector, that gave me sound in all speakers, but also an annoying background noise.

So I switched back the connectors and then tried this, 
-Open alsa-mixer 
-Find the 'SB Live Analog/Digital Output jack' (far right)
-Mute it! (press m)

And now I got sound in all speaker + no annoying noise.


btw: I'm not using the .asoundrc config now (remove the file and restart alsa-utils)

---

### Post by jippers on 2008-06-28
> **foolean said:**
> I have a soundblaster live 5.1, tried the .asoundrc config, restarted alsa-utils, but to get sound I had to change to the line-in(?) connector, that gave me sound in all speakers, but also an annoying background noise.

So I switched back the connectors and then tried this, 
-Open alsa-mixer 
-Find the 'SB Live Analog/Digital Output jack' (far right)
-Mute it! (press m)

And now I got sound in all speaker + no annoying noise.


btw: I'm not using the .asoundrc config now (remove the file and restart alsa-utils)

THANK YOU!!!!!!!!

I have a SBLive 5.1 Platinum and this buzzing I got since installing 8.04 was driving me insane!  Unchecking the A/D Output jack fixed EVERYTHING.
No more distorted audio from my apps, no more buzzing.

---

