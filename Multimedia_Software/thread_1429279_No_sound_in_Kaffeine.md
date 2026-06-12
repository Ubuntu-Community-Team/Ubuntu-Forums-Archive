---
title: "No sound in Kaffeine"
date: 2010-03-13
forum: Multimedia Software
---

### Post by Pat500 on 2010-03-13
Hello.
I am very new at Ubuntu and forums on the internet. Ubuntu is really cool though, I like what I've experienced with it so far!
I am having an issue with Kaffeine. It recognizes my DVB tuner fine and I can watch television but the only problem is that I have no sound. Videos play fine, in Kaffeine, I can see the picture and hear the sound, but when I view television, the sound is quiet. I think that there is some issue with unusual sound codecs being used here in New Zealand, as I had a lot of problems trying to play my recorded tv programs in other software, when I was a Windows user, I would often get the picture but no sound. 
Mythtv works fine for me, I get sound and picture no worries, it's just with Kaffeine I have the sound issues. 
The audio channel is  greyed out, when I click on a channel and then click on edit. I suspect that this may mean that the sound codec that Freeview television uses, in New Zealand, may not be supported in Kaffeine. I hope that I'm wrong though and that someone can help me to get the sound working.
Thanks for your help.

---

### Post by chrisme52 on 2010-03-16
Hey mate
I have the same problem here in New Zealand
will let u know if i find a solution

---

### Post by chrisme52 on 2010-03-16
Well, I can get dvb ok in VLC media player.
The sound's great etc but the videos a bit choppy, probably just my pc

---

### Post by wonderingwhy on 2010-07-08
I'm in New Zealand too - did you find a solution.  I'm having a mare of a time installing and configuring Myth - so would love it if I could just use kaffeine.  

I can play back HDTV I've recorded from Kaffeine on VLC and I have sound, which would suggest that it's not the codecs.  Also if you look under system>preferences>sound>input and click on your TV card and watch TV at the same time you'll see the sound follow the talking.

Interesting I originally used Zapping before I realised it was only analogue and I couldn't get sound with that either.

This lead me to think that it is the audio output from the TV card (I'm using Hauppauge WinTV-HVR-4000). 

If I find a solution I'll post back - I've asked on other threads - so heres hoping.

---

### Post by Yellow Pasque on 2010-07-08
> I can play back HDTV I've recorded from Kaffeine on VLC and I have sound, which would suggest that it's not the codecs.
VLC has its own codecs, kaffeine uses xine, so make sure you have:
```
sudo apt-get install libxine1-all-plugins
```
If it's still not working, try starting kaffeine from the terminal to see if it produces helpful error output.

---

### Post by wonderingwhy on 2010-07-08
Hey Temüjin

Thanks for the suggestion, I appreciate all the help I can get. I down loaded the plugin and rebooted to be sure, but I still have all the same issues, no sound, jerky HDTV and I have to close the app to change channel.  I tried opening Kaffeine in the terminal, and it just opened the app and gave me no useful info.

...maybe it's back to MythTV after all

---

### Post by svaens on 2010-12-14
Hi, 

I had to work this out too. 

In the end, what fixed it for me was increasing the engine audio buffer size... 

I found the information here:

[http://hftom.free.fr/phpBB2/viewtopic.php?t=493&sid=95f02a2e5582de4581fc79e28d50737c](http://hftom.free.fr/phpBB2/viewtopic.php?t=493&sid=95f02a2e5582de4581fc79e28d50737c)

> 
$HOME/.kde4/share/apps/kaffeine/xine-config 

You may find the following file on your system if you don't have the .kde4 directory in your $HOME: 

$HOME/.kde/share/apps/kaffeine/xine-config 

I have these settings now in this file and the HD channels work for me like a charm: 

Quote:
# number of audio buffers 
# numeric, default: 230 
engine.buffers.audio_num_buffers:1500 

# number of video buffers 
# numeric, default: 500 
engine.buffers.video_num_buffers:2000 

# default number of video frames 
# numeric, default: 15 
engine.buffers.video_num_frames:50 


---

### Post by scorptig on 2012-04-19
*[COLOR="Green"]The issue I had prior to modifications below, audio worked a few seconds, then stopped, or was choppy and intermittent.[/COLOR]*

In [COLOR="DarkRed"]Canada[/COLOR], using [COLOR="RoyalBlue"]ATSC[/COLOR], local off-air television [COLOR="Purple"]NTSC[/COLOR].
Antenna basic Philips amplified unit [COLOR="Lime"]HDTV[/COLOR] indoor type.
Hauppauge HVR-1600 PCI card & HVR-950Q USB tested.

Important xine-ui needs to be installed, and enable Master of the Universe setting & save. Next select AUDIO, set Audio from auto to ALSA setting.

home folder CTRL+H (View Hidden files)

```
gedit /.kde/share/apps/kaffeine/xine-config 
```

**xine-config** file edit

```
 # number of audio buffers 
 # numeric, default: 230 
 engine.buffers.audio_num_buffers:750

 # number of video buffers 
 # numeric, default: 500 
 engine.buffers.video_num_buffers:1000

 # default number of video frames 
 # numeric, default: 15 
 engine.buffers.video_num_frames:30

 # audio driver 
 # { auto  pulseaudio  sndio  alsa  oss  jack  file  none }, default: 0 
 audio.driver:alsa
```

Also running in Terminal 

```
dmesg
```
command line may assist

Additional Notes : 

Ubuntu 11.10 64 Bit, Intel Quad-Core CPU, Speed 2.40 Gigs, 4 Gigs of RAM 
Gkrellm shows 20% max to 5% usage running, browser Opera, Kaffeine, Nautilus & Gedit.

The above settings are working well for me.. Sound & Video excellent.

Great posts and link assisted me. Thank you again.

---

### Post by wonderingwhy on 2012-05-15
Thanks chaps, tried expanding the buffers.  That didn't work for me. I still only have video and no sound.  Interesting I can stream some video from some sites via Kaffeine with sound, I can also play both podcasts and DVDs	](*,)

---

### Post by wonderingwhy on 2012-05-15
I just realised as well that I didn't alter the audio - I did that now and still no joy. > Important xine-ui needs to be installed, and enable Master of the Universe setting & save. Next select AUDIO, set Audio from auto to ALSA setting.


So I have xine-ui installed, but I'm not sure what you mean by "Master of the Universe setting & save".  I had a look and could find anything that remotely resembled this - where do I look to do this?

And do I just set the Audio settings from multimedia settings in the preference tab under system?  I couldn't find this in xine-ui either.

I have to say: I'm really a techniphobe driven to Ubuntu because I can't stand MS so none of this stuff is intuitive.

---

### Post by wonderingwhy on 2012-05-16
One last thing - interesting I can record HDTV in Kaffeine - with apparently no sound, and watch it in VLC with sound? - The plot thickens...

If I find a solution - I will definitely post

---

### Post by scorptig on 2012-05-19
> **wonderingwhy said:**
> I just realised as well that I didn't alter the audio - I did that now and still no joy. 

So I have xine-ui installed, but I'm not sure what you mean by "Master of the Universe setting & save".  I had a look and could find anything that remotely resembled this - where do I look to do this?

And do I just set the Audio settings from multimedia settings in the preference tab under system?  I couldn't find this in xine-ui either.

I have to say: I'm really a techniphobe driven to Ubuntu because I can't stand MS so none of this stuff is intuitive.

OK if you have installed xine-ui, you'll find it in your multimedia settings, open xine-ui, the player in lower left has icon mouse over says
setup Window click, First Panel you see, 2nd item, Configuration Experience Level, it's a drop down menu, select last item Master of the Known Universe. Then bottom panel button click apply.
Then go to Audio Tab, 2nd item, audio driver to use, similar drop-down menu
select Alsa, click bottom panel apply.
Close xine-ui
Now we check again our config file
You are using Nautilus, you are in your home folder go CTRL+H shows hidden folders & files, scroll down to 
```
/home/user/.kde/share/apps/kaffeine
```
xine-config file right click edit with gedit, look for these lines, my current settings work very well with Kaffeine.

```
# audio driver
# { auto  pulseaudio  alsa  oss  jack  esd  none  file }, default: 0
audio.driver:alsa

# number of audio buffers
# numeric, default: 230
engine.buffers.audio_num_buffers:750

# number of video buffers
# numeric, default: 500
engine.buffers.video_num_buffers:1800

# default number of video frames
# numeric, default: 15
#engine.buffers.video_num_frames:15
```

Trust this helps.

---

### Post by wonderingwhy on 2012-05-20
Thanks scorptig

but it didn't work.  I think it must be something outside of Kaffeine. I still only have ALSA-UTILs 1.0.21 so an upgrade to .25 is probably in order once I figure out how to do that.  And then I need to check the audio portion of my TV media card is pointing to the right place - once I figure out how to do that - I've asked about that on another thread.

Thanks again

---

### Post by scorptig on 2012-05-20
> **wonderingwhy said:**
> Thanks scorptig

but it didn't work.  I think it must be something outside of Kaffeine. I still only have ALSA-UTILs 1.0.21 so an upgrade to .25 is probably in order once I figure out how to do that.  And then I need to check the audio portion of my TV media card is pointing to the right place - once I figure out how to do that - I've asked about that on another thread.

Thanks again

Well is your computer a workstation, is the audio card a seperate piece of hardware, possibly more details on your hardware is in order and antenna and TV card, install these useful utilities hardinfo & sysinfo & give an output of your terminal running command dmesg, 

foot note to using terminal, right click profile and find tab scrolling select unlimited.

This way you get complete output from running command above.

terminal copy & paste

```
sudo apt-get install hardinfo sysinfo
```

These utilities will reveal more about your hardware.

Post relevant data, that might prove useful, in finding the issue.

And last I have tested this in Ubuntu 11.10 & 12.04 on a workstation
using a Hauppauge HVR-1600 card. Also tested & working with Hauppauge HVR-950Q USB stick on laptop Lenovo Z570 using 12.04LTS

Curious as to why your setup does not work in a optimum fashion, one thing don't give up, this is a learning process and it's fun.

---

