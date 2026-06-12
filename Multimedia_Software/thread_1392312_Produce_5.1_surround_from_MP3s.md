---
title: "Produce 5.1 surround from MP3s"
date: 2010-01-27
forum: Multimedia Software
---

### Post by linuxyogi on 2010-01-27
In windows PowerDVD can create multichannel surround sound (Dolby Pro Logic 2) from 2 channel sources like Audio CDs, MP3s, etc. Is there any player in linux which can do this? Please reply.

---

### Post by linuxyogi on 2010-01-28
Please Someone

---

### Post by sports.car.guy on 2010-01-28
Every player is technically capable under Linux. It depends on the sound service you are using being setup for it. Now PowerDVD actually more or less upmixes a signal. There is a big difference between this and ProLogic technologies. ProLogic and ProLogic II are not an upmix and the information for the tracks is encoded into the audio as digital information inside an analogue track. It is an analogue stereo track with digital info saying send this here, send that there, and so on. That is not what I think you are looking for.

PowerDVD can decode ProLogic, that is another story all together and also not what I think you are talking about. As I said I think you are wanting to upmix and there is a lot online for information on how to do this. It is accomplished on the Linux system, not by the player.

Now in order to enable it you need to know what sound service you are running, whether you have PulseAudio or not, it is almost a given Alsa will be on the system. You can set up what you are looking for either way.

Type either depending on which you are using into Google.
[I]
Alsa upmixing.

PulseAudio Upmixing and surround. [/I] 

Both are accomplished in PulseAudio by uncommenting one line with it in a config file. It's upmixing can leave something to be desired in my opinion though. I prefer doing it though Alsa, but it is more entailed, with that you get a lot more control.

Like with my Alsa configuration I have not only setup a device to handle my upmixing, I can set the crossover points on high and low pass filters for the satellites and sub of my 5.1 system. That is something I have never found if it was possible with PulseAudio and can vastly improve the listening experience. Why have unwanted frequencies going to speakers muddying up the sound is my personal taste though. There are others who just want it to work and not caring to accurate reproduction.

Do you just want it to work? Then odds are PulseAudio will get you by. But if you want the best quality reproduction and are a bit of an audiophile I would suggest looking into setting it up right using Alsa.

---

### Post by linuxyogi on 2010-01-28
Thanks for your reply. I was talking  about the rear channel delays which Power DVD creates when the dolby prologic 2 option is enabled. My freind was actually playing an mp3 file. The surround effect was superb.  I don't want the rear channels to just replicate the front channels. Please reply.How do I know which conf. (alsa or pulse) is running?

---

### Post by linuxyogi on 2010-01-29
I tried searching "alsa upmixing" in Google but couldn't solve my problem.Can I get the surround effect by installing a new package? Is there anything called "open source surround".I mean is there any free utility or audio/video player which can create surround from 2 channel sources?.Again, REAL SURROUND SOUND & not just replication of the front channels.Please reply even if its not possible in linux. Just tell me that.

---

### Post by sports.car.guy on 2010-01-29
> **linuxyogi said:**
> I tried searching "alsa upmixing" in Google but couldn't solve my problem.Can I get the surround effect by installing a new package? Is there anything called "open source surround".I mean is there any free utility or audio/video player which can create surround from 2 channel sources?.Again, REAL SURROUND SOUND & not just replication of the front channels.Please reply even if its not possible in linux. Just tell me that.

Power DVD is not actually creating Dolby ProLogic2 on a file!!!!!

There is no point to it where all it store is channel data!

If you read my last post I explained how the two versions of ProLogic worked. All PowerDVD is doing, is taking the upmixing from Windows, which doesn't necessarily blend channels to get a true center and LFE, then applying a delay on the back channels, nothing more. It is the same exact thing and doing the delay to keep the sound representation in phase, as close to realistic it can, nothing more! The problem with how it does this is it is a set value and not adjustable. The channel mixing or delay are what you hear is what you get. I can assure you it is not re-encoding it to ProLogic!

It is not applying some special technology to get surround.

You can apply the same effect in Alsa. It is a matter of using LADSPA plugins appropriate to what you want to do. For example, my get me by asound.conf has an upmix for 2.0 to 5.1 with high and low pass filters on the channels to clean up any muddiness in my sub plus unwanted low frequencies in my satellites.

My speakers are slightly slightly out of phase depending on the audio being staged and getting the effect you are talking about that you don't want. I have not had a chance to look at the LADSPA plugins myself for controlling delay. If you looked more into it, instead of just at the simple setup, it would have lead you to what I am talking about.

Not only that the attitude I get for trying to help you!

PulseAudio does not have any way to control delay to adjust staging as far as I know, similarly to Windows. 

On the note of an Open Source a surround, I gave you what you are looking for! You though, just want something that you go oh ok installed here we go. That is what PulseAudio does but not with the delay to the back channels you're looking for. If you want more then just works, then you need to put some effort in. The ability is there to have what you want, all you had to do was dig deeper.

---

### Post by linuxyogi on 2010-01-29
> **sports.car.guy said:**
> Power DVD is not actually creating Dolby ProLogic2 on a file!!!!!

Not only that the attitude I get for trying to help you!

PulseAudio does not have any way to control delay to adjust staging as far as I know, similarly to Windows. 

On the note of an Open Source a surround, I gave you what you are looking for! You though, just want something that you go oh ok installed here we go. That is what PulseAudio does but not with the delay to the back channels you're looking for. If you want more then just works, then you need to put some effort in. The ability is there to have what you want, all you had to do was dig deeper.

I was just getting frustrated thats all.I am sorry.I will keep trying and write back if can get the surround sound working. Sorry.

---

### Post by sports.car.guy on 2010-01-29
> **linuxyogi said:**
> I was just getting frustrated thats all.I am sorry.I will keep trying and write back if can get the surround sound working. Sorry.

I understand frustration. It is all good.

Linux has come quite a ways since I started using it. I have been using it with at least one full time machine for well over, OMFG, well over 15 years now. Has it been that long? I am now feeling a bit old..lmao.

With what you are looking to try to do, one thing to also look at for a LADSPA plugin is echo effect. With delay from what I understand you can replicate different room depths.

LADSPA contains a lot and I did a little research for you on places to get you started. There are so many of these plugins to do things that I am shocked someone needs to manipulate audio in so many ways.

Here are a few links:

[http://alsa.opensrc.org/index.php/Ladspa_%28plugin%29](http://alsa.opensrc.org/index.php/Ladspa_%28plugin%29)

[http://www.ladspa.org/](http://www.ladspa.org/)

This last one so you can get an idea of how DSP works. It is a bit technical looking at quick glance, but lays out how it works.

[http://www.dspguru.com/](http://www.dspguru.com/)

Sorry for getting a bit short myself. I hope this helps.

---

### Post by linuxyogi on 2010-01-29
> **sports.car.guy said:**
> Here are a few links:

[http://alsa.opensrc.org/index.php/Ladspa_%28plugin%29](http://alsa.opensrc.org/index.php/Ladspa_%28plugin%29)

[http://www.ladspa.org/](http://www.ladspa.org/)

This last one so you can get an idea of how DSP works. It is a bit technical looking at quick glance, but lays out how it works.

[http://www.dspguru.com/](http://www.dspguru.com/)

Sorry for getting a bit short myself. I hope this helps.

Thanks for all that searching you did for me. I will definitely start checking out those websites you have mentioned. In the meantime let me tell you about this feature I came to know about mplayer. I typed the following command ----
&#8220;mplayer -af surround=15 -channels 4 filename.mp3&#8221;
I found out this command by typing man mplayer |grep surround
I guess I'am getting surround sound !!!
What is your opinion about this?
Now don't misunderstand. I will surely read those web pages you have mentioned.

---

### Post by linuxyogi on 2010-01-29
My speaker setup is like this --- A Creative 2.1 outputs the FR & FL. The RR & RL channels are connected to my Sony audio system. So, technically  I have created a quadraphonic speaker setup.

**_Please confirm_**
I guess using the &#8220;-channels 4&#8221; switch with mplayer will downmix the center & LFE channels in case I play a DVD with 6 channel (Dolby Digital) recording.

---

### Post by sports.car.guy on 2010-01-29
> **linuxyogi said:**
> My speaker setup is like this --- A Creative 2.1 outputs the FR & FL. The RR & RL channels are connected to my Sony audio system. So, technically  I have created a quadraphonic speaker setup.

**_Please confirm_**
I guess using the “-channels 4” switch with mplayer will downmix the center & LFE channels in case I play a DVD with 6 channel (Dolby Digital) recording.


Knowing how much they cram into MPlayer, I would not be surprised about a surround feature built into it that does effects processing on it to provide more then just fill on the other channels, like upmixing alone does.

You actually have a 4.0 system I am assuming that each 2.1 speaker system has only one connection to the sound card. The signal sent to each is a full range signal with the internal high and low pass filtering handled in the speakers. I have a couple of SB 2.1 systems like that. One being an original Cambridge Soundworks set after the buyout before the name change. They are the best sounding 2.1 speakers I have ever had too. Sound so much better then what SB puts out now. They killed the quality purchased with buying Cambridge Soundworks.

The -channels switch actually is to tell MPlayer how many speakers are available, and if a 5.1 audio track it should mux in the other tracks like center and LFE. Without the switch, Mplayer will only send out a stereo track nothing more. So for a 5.1 setup where each speaker physically connects into the sound card I send -channels 6. The thing is, if the track is stereo, it only goes to the front left and right speakers even with the -channels telling it there is more speakers available.

In those cases you now need to do the upmixing with LADSPA plugins for effects, or it appears you can pass that "switch" you found for surround. If you do the asound.conf way you send it to the device you created instead of the Alsa default.

---

### Post by linuxyogi on 2010-01-31
Wait, let me tell you that the process of upmixing (without the back channel delays) is already operational on my PC). When I play any 2 channel source, sound comes out of all the speakers (including the back channels). The thing I want to add are the delays. I'm confirming this because I want you to know that upmixing is already there and that is not the issue. And now the disappointing part -------- 


Sorry to tell you this but I give up. I read all those web pages you mentioned. And by the way I also read your thread [http://ubuntuforums.org/showthread.php?t=1383303]("http://ubuntuforums.org/showthread.php?t=1383303") !!!! It looks like its only you and I who wants to see surround sound to work under Linux. Not a single user joined our discussions !!! "We are surrounded by people who have no interest in SURROUND" !!!! Anyways, best of luck. I hope you succeed setting up surround sound. Sorry friend, trust me I tried.

---

### Post by Mazer1138 on 2010-03-22
> **linuxyogi said:**
> Can I get the surround effect by installing a new package? Is there anything called "open source surround".I mean is there any free utility or audio/video player which can create surround from 2 channel sources?.Again, REAL SURROUND SOUND & not just replication of the front channels.
> **sports.car.guy said:**
> Knowing how much they cram into MPlayer, I would not be surprised about a surround feature built into it that does effects processing on it to provide more then just fill on the other channels, like upmixing alone does.
I've been looking into this issue for myself and have come up with very little. What I have managed to find is that MPlayer does have a plugin for decoding matrix-encoded stereo (such as Dolby Stereo and Dolby ProLogic and ProLogic II) which is exactly what we want. To use it start MPlayer like this:

```
mplayer -af surround=15 -channels 4 media.mp3
```

The '-af surround=15' switch is the important part. It activates the surround decoder and sets the delay for the rear channels in ms. So if you wanted a delay of 20ms you would use '-af surround=20' instead.

This is not simple upmixing, it is full-on surround sound decoding.

Of course, what I really want is a way to configure ALSA to do this instead of going through MPlayer to do it. That way it would always be on, not just when using MPlayer, and so far I don't think there is (or I haven't found) a matrix decoder plugin for ALSA. It's a shame but maybe one day someone will make such a plugin.

---

### Post by Yellow Pasque on 2010-03-22
I doubt the person who was asking for it will see this, but there is an ALSA upmix plugin in libasound2-plugins package (with delay option). The code sample(s) given would be put into /etc/asound.conf or ~/.asoundrc file. The help file:
```
UPMIX PLUGIN
============

The upmix plugin is an easy-to-use plugin for upmixing to 4 or
6-channel stream.  The number of channels to be expanded is determined
by the slave PCM or explicitly via channel option.  For example, the
following PCM defines upmixing to 5.1 from 1-6 channels input:

	pcm.upmix51 {
		type upmix
		slave.pcm "surround51"
	}

You can use this PCM as a default one by defining below:

	pcm.!default "plug:upmix51"

The upmix plugin copies left and right channels to rear left and right
with a certain delay.  The delay size can be specified by "delay" PCM
option in msec.  For example, to set 10ms delay in the above case:

	pcm.upmix51 {
		type upmix
		slave.pcm "surround51"
		delay 10
	}

As default, 15ms delay is used.

The channel option specifies the number of channels of output.  Either
4 or 6 channels are supported.  When 0 is passed, the plugin tries 4
or 6 channels appropriately suitable for the slave pcm.  The channel
option is useful if the slave PCM has no strict input condition (like
plug or route plugin).

	pcm.myupmix {
		type upmix
		slave.pcm "something"
		channels 6
	}

The center and LFE channels are the average of sum of left and right
signals.

The accepted format is currently only S16.
```

---

### Post by AHD on 2010-08-01
> 
```
mplayer -af surround=15 -channels 4 media.mp3
```The '-af surround=15' switch is the important part. It activates the surround decoder and sets the delay for the rear channels in ms. So if you wanted a delay of 20ms you would use '-af surround=20' instead.

This is not simple upmixing, it is full-on surround sound decoding.

Thanks a lot. 
I just recently have converted to ubuntu because my desktop xp machine crashed. Whithout a recent os backup i tried a quite few distros and ended up using the 10.10alpha. (The 10.4 is a big bug in lynx disguise. But that another story)

After many weeks of (half) wasted time and frustration i stumbled across this thread. You saved me from setting up a xp machine to do audio.
Being used to SB X-Fi with foobar and its matrix mixer, everything else sounds like crap.

Audio in Linux in chaos. The only way having sound output without getting ear cancer was to plug in my old audigy card and alsa a the "sound server". (letting the onboard card doing the pulse stuff and spdiffing into the audigy (because of certain alsa imitations))

After much more wasted time finding workarounds for several annoying bugs/regressions in 10.4 i ended up with the 10.10 alpha. It's doing quite well for some weeks now. Several pulse/alsa issues have been fixed and after getting rid of all the useless audio plugin/plugout stuff i managed to get a nearly enjoyable sound output. (Note that the "unstable, alpha and using at your own risk" pulse is actually quite stable... and it's finally compiled to not dirty libs. which also fixed these libcanberra  zombie pulse clients

Finally this little option did it. After trying nearly all available media players  i'm using smplayer. Everything either sounds bad or has some other showstopper. (xbmc would be quite nice but it's frying the video card even when idle and minimzed ;)

Now i can start looking for a backend which can handle 100k of audio files without hardlocking my machine. But i can imagine that mplayer is able to act as a frontend whithout handling the library... 
On the other hand, a decent (not hardware/driver bound) decoder/matrix mixer would be the ultimate. 


Coming to an end, i'm also surrounded by non-surround people. 

Regards,
Alex.

btw: If you have a windows machine, check out foobar. There's an option to calculate the delay in relation to the distance of the speakers. Sadly there are no plans porting the imho perfect audio player to linux. (for instance it could handle 100000 files in a single playlist without using over 8G of RAM and deadlocking the machine or stalling around calculating the infinite loop, like banshee or exaile does...;) )

---

### Post by AHD on 2010-08-01
...felt the urge to pay something back: 

It also helps to read the f* manual:  "mplayer -ao  -af surround=17,sub=100:5,center=4 -channels 6" mixes up to 6 channels. sub cutoff att 100hz.  

Note that when using mplayer as a "plugin" like with smplayer the -channels option is defined elsewhere.

Now with fine tuning the center/sub/rear output with alsamixer you can get nearly as far as using foobar with an x-fi and it's integrated hardware decoder. (Alsa sucks with x-fi). But i think there's an issue with pulse resetting the alsa mixer settings. but that only appears on two onboard cards i tested.
A possible workaround could be done with a virtual alsa device, which only routes the input to the physical device.
Alsa stores the mixer settings at shutdown, but there's amixer which can dump the settings which can be loaded at startup.


Just for the record, my sound setup: 
- audigy2 (thankfully with hardware supported bass/tone control)
- 5.2 (L/R with standalone amp and real speakers, L/R/C/S front+RR/RL,Rsub. The second L/R volume turned down just do add some more high from a slightly different position)
- (now) smplayer with the above config in fine tuning progress...
- everything purged which could connect directly to alsa
- decided against alsa upmix due to odd sound. 
- currently searching for a backend to handle 100k audio files. 

Now i'll do some more experimenting. But feel free to ask for any detail. Spent quite some time getting this chaos under control...

Alex.

---

### Post by linuxyogi on 2010-08-01
When I started this thread I was using ubuntu 9.04.
Getting sound in linux was never an issue for me. It always worked without any tweaking.

In 9.04 I was able to select 2/4/5.1 channel speaker setup via the pulse audio mixer but starting 9.10 this very option vanished.

Now, I am using 10.04. Everything is fine except I still don't see the option to select my speaker setup (2/4/6).

Look, getting basic sound to work is no big deal in linux these days. But unfortunately surround is still an issue.  

**Even if this problem remains for another 100 years I will still stick with Ubuntu. I confess I am addicted to Linux (Ubuntu). **  \\:D/

I don't dual boot. So I can't say how my sound card will perform under windows or any other platform.

But you keep trying & please write back if you find the solution.

Solution in my case will be specify my "card type" by modifying some conf file which will then enable the option to specify the number of speakers & only then I can think of getting surround working. I guess I will start a thread for that and ask for help.
For now, I won't be able to utilize all those mplayer options you guys have mentioned because leaving the FL & the FR  all the other channels are mute.

Thanks a lot to all of you guys.

---

### Post by AHD on 2010-08-03
Hi linuxyogi

Just a short feedback. no time.

I i also used linux since suse was ugly as hell. but without audio. Server only
imho the main issue is the alsa driver problem.

Also all dual booties need to backup/restore once in a while ;)

Please start a new thread and me the url. [email]A.Doberauer@gmail.com[/email]. And please excuse my shitty english since i am a kraut. ;)

Regards,
Alex.

btw: mplayer sound is getting better and better. ...found this gmusixbrowser which handles 100k files nearly without lags.

---

### Post by linuxyogi on 2010-08-03
> **AHD said:**
> Please start a new thread and me the url. [email]A.Doberauer@gmail.com[/
.

Hi, this is my new thread regarding my sound card problem -------

http://ubuntuforums.org/showthread.php?t=1544072

Thanks.

---

### Post by AHD on 2010-08-03
Got a bit confused before with all those -ao -af...

working now is

mplayer -ao pulse -af surround=17,sub=100:5,center=4 -channels 6

sorry,
Alex.

---

### Post by linuxyogi on 2010-08-05
Latest: I  just finished setting up upmixing in 10.04 successfully.
Now about getting real surround: Let me tell you that delay is just one of the multiple factors which goes into creating a true surround sound. 

As I have mention before one of my friends uses PowerDVD. Listening to the rear channels I was/am quite sure that it was not only delays that was taking place there. Besides delay I guess reverb/echo is another factor. Again, I am not sure that it was reverb but I am quite definite that it not only the delays that goes into creating surround sound.

Currently experimenting  with mplayer.

I will write back if I find something more about mplayer's surround feature.

---

