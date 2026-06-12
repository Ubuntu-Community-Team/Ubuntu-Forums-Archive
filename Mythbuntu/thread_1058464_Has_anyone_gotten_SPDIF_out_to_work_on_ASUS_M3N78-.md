---
title: "Has anyone gotten SPDIF out to work on ASUS M3N78-VM With MythBuntu 8.10?"
date: 2009-02-02
forum: Mythbuntu
---

### Post by nicoloks on 2009-02-02
Hi All,

I'm pretty new to linux and am building a new HTPC for a mate using the [ASUS M3N78-VM NVidia 8200 / Via VT1708B 8 -Channel High Definition Audio CODEC]("http://www.asus.com/products.aspx?modelmenu=2&model=2268&l1=3&l2=149&l3=643&l4=0") based motherboard. My mate is wanting to to use the optical SPDIF output on this motherboard as an audio pass through device to allow his external receiver to do the DD/DTS decoding, but I am having awful trouble getting it to work, so at present I have it hooked up via 6 channel analog which works fine.

Steps I have taken are;
[LIST]
[*]Used the ALSA upgrade script on these forums to upgrade to ALSA 1.0.19 (my alsa-info.sh output can be seen [here]("http://www.alsa-project.org/db/?f=806304b85240b1fa6af464c720abb195df467c38"))
[*]Ensure that IEC958 was not muted in alsamixer
[*]In MythTV and Xine I have set the audio to use the SPDIF as the output, and also set the pass through option for AC3/DTS.
[*]Verified that BIOS was set to use SPDIF for digital audio
[*]Followed the [DigitalOut]("http://alsa.opensrc.org/index.php/DigitalOut") guide on the ALSA project WIKI
[/LIST]

I've searched these forums and the Internet quite a bit, and am as yet to find anyone who has successfully gotten digital audio pass through to work on this motherboard. So before I continue to waste more time on this I though it best I check if it was actually possible. **Has anyone gotten digital audio to work over SPDIF (or HDMI for that matter) on the Asus M3N78-VM motherboard? I would also appreciate hearing from anyone who has successfully gotten digital audio to work over SPDIF on any motherboard using the VIA VT1708B 8 -Channel High Definition Audio CODEC.**

---

### Post by nicoloks on 2009-02-03
Have made some progress. I set the BIOS to use HDMI rather than SPDIF and now I am able to get PCM sound. However I am still unable to get AC3/DTS pass through to work. 

I created /etc/asound.conf and put the following into it;
```
pcm.!default {
        type hw
        card 0
        device 3
}
```

What must I do now to force digital audio pass through? I made these modifications to asound.conf, however sounds doesn't work at all after this;

```

pcm.!default {
        type hw
        card 0
        device 3
		{
        pcm "spdif"
        rate 48000
        format S16_LE
		}
		}
```


Any suggestions?

---

### Post by rodercot on 2009-02-03
> **nicoloks said:**
> Have made some progress. I set the BIOS to use HDMI rather than SPDIF and now I am able to get PCM sound. However I am still unable to get AC3/DTS pass through to work. 

I created /etc/asound.conf and put the following into it;
```
pcm.!default {
        type hw
        card 0
        device 3
}
```

What must I do now to force digital audio pass through? I made these modifications to asound.conf, however sounds doesn't work at all after this;

```

pcm.!default {
        type hw
        card 0
        device 3
		{
        pcm "spdif"
        rate 48000
        format S16_LE
		}
		}
```


Any suggestions?


 I am pretty sure you need to add your stack configuration to the end of 

 /etc/modprobe.d/alsa-base before this will work. 

 I had to do this for my P5N7A-VM as well before I could get sound out of spdif or hdmi. 

 I am pretty sure that if you hooked an rca output to the ext spdif connector on the board you would have sound right now as well. There is a file in the Alsa 1.0.19 directory that you downloaded that tells you which stack config = which codec, but I cannot remember the name of the file. You can search for this on the Alsa-site it would be like ?? = 6stack-digital.

 if you list your aplay (-l) is device 3 not your hdmi output? After you updated to 1.0.19 your alsamixer is reporting to be version 1.0.19 now correct?

 HDMI does work fine without using the alsa-base edit for me, you only need to set myth as 

 under general where you set MYTH:spdif change to MYTH:hdmi and then on the next line from iec958 change to hdmi as well and go through the menu to finish. I DO NOT use an asound or asoundrc file on either of my machines, I have the bedroom machine connected to the TV hdmi input and no problems.

 Dave

---

### Post by nicoloks on 2009-02-03
Hi Dave, thanks for the reply.

Never even heard of that before, which hopefully explains why I've been hard up against this wall for the most part of a week now. I'll go do some hunting around on alsa-base, but in the meantime if you post what you added to your alsa-base might help.

---

### Post by rodercot on 2009-02-03
Hi,

 This is what I place in the alsa-base for the Asus P5N7A-VM Board I am not sure that it will be the same for the M3N78-VM. 

 sudo vim /etc/modprobe.d/alsa-base

 and then add to the end of that file. I am pretty sure this tells alsa what devices you have on top of the hdmi capability.

 options snd-hda-intel model=6stack-dig 

 Not sure if this will work for the M3N board, as I said I did not have to add this to my M3N board for hdmi output to work and I did not have to create either an asound (rc) file.

 rgds,

Dave

---

### Post by jayman8547 on 2009-02-03
I have an M3N78-VM and pass everything over HDMI addressed here: (Scroll down to my post)

[http://ubuntuforums.org/showthread.php?t=957581&page=3](http://ubuntuforums.org/showthread.php?t=957581&page=3)

The first link is a great guide by Rodercot and the second link deals with /etc/asound.conf.

I am using 180.22 and Alsa 1.0.18. 

It took me a while to get everything working over HDMI but it works pretty good now.  Also, just a note but when I upgraded the video drivers I had to rerun all the alsa scripts.

---

### Post by nicoloks on 2009-02-03
Thanks for the reply Jayman and Dave.

I went through the steps in your post jayman and ended up more or less in the same spot. However, my reciever is still showing it is getting a PCM signal rather than AC3/DTS. I think though that I have hit a seperate issue.

Because my reciever is a bit old and does not have HDMI inputs, I have my HDMI going into a Panasonic PZ80 plasma with the S/PDIF optical out from the Plasma going into my reciever. I thought that the Plasma TV was able to do digital audio passthrough from the HDMI input to the optical S/PDIF output, however I am now not so sure. When I run mplayer with the following syntax;

mplay -ao alsa:device=hdmi -ac hwac3,hwdts, /path/to/video.mkv

I can see that mplayer IS reporting that it is using AC3 or DTS pass-through (depending what is detected in the movie), however I get no sound at all. If I don't specifiy and audo codec then mplay starts decoding the AC3/DTS into a 2 channel stream and I get sound. 

Long story short, I don't think I will be able to get digital passthrough working without upgrading to a HDMI enabled reciever. Best I can hope for is perhaps 6 channel PCM :( .

---

### Post by jbman on 2009-02-04
I have the M3N78-EMH HDMI. I am not sure if it has the same chipset but it worked out of the box with 8.04. I have not upgraded to 8.10 as there has been no need yet.

I would try a live cd or 8.04 and see if it works.

---

### Post by rodercot on 2009-02-04
> **nicoloks said:**
> Thanks for the reply Jayman and Dave.

I went through the steps in your post jayman and ended up more or less in the same spot. However, my reciever is still showing it is getting a PCM signal rather than AC3/DTS. I think though that I have hit a seperate issue.

Because my reciever is a bit old and does not have HDMI inputs, I have my HDMI going into a Panasonic PZ80 plasma with the S/PDIF optical out from the Plasma going into my reciever. I thought that the Plasma TV was able to do digital audio passthrough from the HDMI input to the optical S/PDIF output, however I am now not so sure. When I run mplayer with the following syntax;

mplay -ao alsa:device=hdmi -ac hwac3,hwdts, /path/to/video.mkv

I can see that mplayer IS reporting that it is using AC3 or DTS pass-through (depending what is detected in the movie), however I get no sound at all. If I don't specifiy and audo codec then mplay starts decoding the AC3/DTS into a 2 channel stream and I get sound. 

Long story short, I don't think I will be able to get digital passthrough working without upgrading to a HDMI enabled reciever. Best I can hope for is perhaps 6 channel PCM :( .

 If you make the change to alsa-base You can run hdmi video to your TV and you can run the optical from your pc to the rcvr. The switch in the bios for hdmi to spdif as far as I understand is only for the ext output on the motherboard if you are using alt. video card with hdmi output and not the one on board but does not affect the opt. output on the backplane.

 rgds,

 Dave

---

### Post by SnafuFlux on 2009-02-21
Hi all, I just wanted to let people know that there is a solution to getting SPDIF working for this motherboard - Not the onboard, however.

if you're looking for a solution for the onboard, don't bother reading this, as my solution will not fix that.

Preamble:
BIG thanks to jayman8547, rodercot, pmosinskis and troipoison.  With out their help, I could not have accomplished full HDMI or spdif.

My system consists of ASUS M3N78-VM with mythbuntu 8.10 x64, Nvidia 180.29 x64 drivers and Alsa 1.0.19.  I am in NO way a linux expert.  I've literally just started using it.  if it wasn't for the people mentioned above, I wouldn't even be posting.  I just want to save people the headache and aggravation I went through!

The Juice:
Yesterday I set out to get my HDMI fully working (video and sound).  This proved to be a hell of a task.  

The following url is what set me on the right path for setting up HDMI audio (look for post by jayman8547:
[http://ubuntuforums.org/archive/index.php/t-957581.html](http://ubuntuforums.org/archive/index.php/t-957581.html)

after successfully getting HDMI working (though I did not get  DTS/DD5.1 to pass through), I realized that this isn't exactly what I want.  I began to implement the SPDIF out.  Right off I noticed that I have no light coming from my onboard optical port.  I thought nothing of it and attempted to setup mythtv to use spdif.  until I ran across this thread as well as another thread.

I was banging my head against the wall for 3 hours, not knowing what the heck was going on.  Frustrating to say the least.  Until I put two quotes together:

from this thread:
> **rodercot said:**
>  I am pretty sure that if you hooked an rca output to the ext spdif connector on the board you would have sound right now as well. 

from another thread(look for the post by troipoison for the meat and potatoes):
[http://ubuntuforums.org/archive/index.php/t-983458.html](http://ubuntuforums.org/archive/index.php/t-983458.html)
> To get to it, I snipped an old 3pin wire that goes from cd/dvdrom audio to mobo. Pulled a toslink from an old dead dvd player (try an alley or salvation army or goto an electronics shop for an adapter.) The pin config on the mobo goes like this >
_____
5volt
_____
_____data
gnd
if that makes sense, the singled out pin is 5v and then data and ground are right next to each other. It's up by the last pci slot.I got the light on it right away, so I knew it was good to go, set the bios to read front audio HD. It still wasn't enough. Then I used the alsa update script again, but this time I did it -snap, and grabbed the latest snapshot. Set the audio switches to iec958 default pcm, and iec958 on. iec958 1 I just left off.

In short, troipoison created his own SPDIF port.  I recalled reading rodercots post and the motherboards manual stating you can get an external spdif.  I called my local computer shop and asked them if they had the Asus SPDIF optical/coax out.  One left for $15 cnd!  
[http://ncix.com/products/?sku=111102044&vpn=SPDIF-OUT%2FOPT&manufacture=Asus](http://ncix.com/products/?sku=111102044&vpn=SPDIF-OUT%2FOPT&manufacture=Asus)

I said to myself, if troipoison can build his own spdif out, and rodercot says it should work off the mobo, why not try this.

Best 15bux I've ever spent!  I'm a stubborn person, and I would really like to have the onboard optical work.  However, imo, $15 to save me the headaches AND time, I think it's worth it.  

After installing the new ports and hooking it into the mobo, I rebuilt the alsa drivers.  I also changed /etc/asound.conf pcm-digital-hw (this is mentioned in the above links to get HDMI working) to 2, instead of 3.  
```
pcm.digital-hw {
     type hw
     card 0
     device 2
}
```
I have no idea if this portion is needed, but it hasn't adversely affected me yet.  But what I can tell you is, I now get DTS/DD5.1 from my newly built MythTv box.

Movies will play perfectly from within Mythbuntu using VLC, however when I use Mythtv to play the movies, I get some static on the line.  I can attribute this to a configuration issue.  But I DO know that optical will work perfectly once I've configured it correctly.

I hope I can save at least ONE person the hell I've been through to get this to work.  if you need any more information, I will do my best to provide it.

Good luck!

---

### Post by rodercot on 2009-02-21
Great Stuff, glad I could help you some. I will tell you your static is likely come from the circuit you are using. If you google optical or spdif circuits you will find a simple scematic for building a toslink output connector on a bread board. I did one last year as I could not find an Asus one anywhere. So I made one including a toslink and an RCA on the same board the rca ofcourse is easy but there are specific optical connectors like the toshiba TOTX176 that get used alot in PC's and Audio devices and the output driver circuit is pretty easy.

 [http://www.scottcraftboats.com/spdif.htm](http://www.scottcraftboats.com/spdif.htm)

 This is the one I made last year. not pretty but it worked on both outputs at the same time and sounded just fine as well.

 rgds,

 Dave

---

### Post by SnafuFlux on 2009-02-21
Hey Dave, a fellow canuck.  I didn't realize!

I only get static using mythtv itself.  if I watch the same video using VLC outside of mythtv (but still in mythbuntu), I don't get the static.  I think the toslink port itself is ok?  I think it's just the internal player not passing the digital audio through properly?  I don't know though, I have LIMITED knowledge with this.

Imo, if the audio is fine outside of mythtv, it's gotta be a config thing?

---

### Post by rodercot on 2009-02-22
> **SnafuFlux said:**
> Hey Dave, a fellow canuck.  I didn't realize!

I only get static using mythtv itself.  if I watch the same video using VLC outside of mythtv (but still in mythbuntu), I don't get the static.  I think the toslink port itself is ok?  I think it's just the internal player not passing the digital audio through properly?  I don't know though, I have LIMITED knowledge with this.

Imo, if the audio is fine outside of mythtv, it's gotta be a config thing?

 Oh! OK, then what are your settings under utilities setup - general's 2nd page.

 They should be Alsa:default or Alsa:spdif and Alsa (aes???:spdif) then DD and DTS passthrough should be checked as on.

 Yep, I am in Ottawa.

 Dave

---

### Post by SnafuFlux on 2009-02-24
Hey Dave, sorry for the late reply.  

The settings I have are ALSA:Spdif, ALSA (0X2) - I'm at work, I can't recall this, can look when I get home.  I also have AC3 and DTS passthrough checked off.

I've been able to get Mplayer to play with out the weird reverb, but I can't get the internal player to do it.  But I haven't really researched much.  I was burnt out after spending so much time just to get the damn spdif to work!  I should note that I only get this problem with one of my files that uses DTS.  Other files pass DTS no problem using the internal player.  Strange.  

what does mythtv use for an internal player?  I wonder if I could try it out side of mythtv and see if I get the same reverb.

---

### Post by rodercot on 2009-02-24
> **SnafuFlux said:**
> Hey Dave, sorry for the late reply.  

The settings I have are ALSA:Spdif, ALSA (0X2) - I'm at work, I can't recall this, can look when I get home.  I also have AC3 and DTS passthrough checked off.

I've been able to get Mplayer to play with out the weird reverb, but I can't get the internal player to do it.  But I haven't really researched much.  I was burnt out after spending so much time just to get the damn spdif to work!  I should note that I only get this problem with one of my files that uses DTS.  Other files pass DTS no problem using the internal player.  Strange.  

what does mythtv use for an internal player?  I wonder if I could try it out side of mythtv and see if I get the same reverb.

 Is it not xine, maybe I am wrong. That DTS file wouldn't happen to be a music file by chance. 

 Dave

---

### Post by SnafuFlux on 2009-02-24
Nope.  Music (mp3) works fine for me.  Infact, I have the XM 'plugin' working for mythtv as well, with out any issue.

---

### Post by rodercot on 2009-02-24
> **SnafuFlux said:**
> Nope.  Music (mp3) works fine for me.  Infact, I have the XM 'plugin' working for mythtv as well, with out any issue.

 I am referring to the DTS file you are trying to playback. Is that a DTS Music CD like a 96/24 file or just a regular DTS encoded movie.

 Dave

---

### Post by SnafuFlux on 2009-02-24
Oh sorry, I've never heard of DTS music cd.  it's just a regular DTS encoded movie.

---

### Post by smgendler on 2009-03-03
Oh my goodness, this worked!!! Thank you so very much!!!

But, you guys, can rodercot or snafluflux or any one please explain, why does this solution work?  Why does the on-board SPDIF not work but the auxiliary SPDIF work?  further,it bugs me that the SPDIF works in Windows first off, but not linux.  I'm not super technical, but, though I bought the aux SPDIF ports and it worked, which I thankful for, it doesn't make sense.  Would one of you geeks following this thread be willing to explain to a not-so-geek?

---

### Post by rodercot on 2009-03-04
> **smgendler said:**
> Oh my goodness, this worked!!! Thank you so very much!!!

But, you guys, can rodercot or snafluflux or any one please explain, why does this solution work?  Why does the on-board SPDIF not work but the auxiliary SPDIF work?  further,it bugs me that the SPDIF works in Windows first off, but not linux.  I'm not super technical, but, though I bought the aux SPDIF ports and it worked, which I thankful for, it doesn't make sense.  Would one of you geeks following this thread be willing to explain to a not-so-geek?

 Well there are a couple things that come to mind here, One if you noticed in your bios (until you upgraded or atleast in my case,) you had the option to turn spdif or hdmi to output, This as far as I can tell is handled by the nvidia codec the actual on board spdif is handled by the VT1708b codec and it is reporting as an ALC ???? in further searching at first I found this to be an ALC888 codec and then after a bios upgrade it became a ALC1200, SO bottom line I am not sure if this is an actual other driver needed or an actual issue with the board or a combination of both. 

 WHAT aplay should show in my guess

 VT1708B Analog
 VT1708B Digital (iec958 2) spdif onboard
 ALC ???? Digital (iec958 spdif out header)this could be the MCP78A HDMI 10de mode that some get in there aplay -l or -L listing and I think this is turned on with Alsa 1.0.19 as the spdif out header and the iec958 switch found in alsamixer, looking at the ctl struct for this VT1708b chipset they have the onboard digital output listed as a digital input for some reason and that is wrong but at the very least it should show a digital VT1708b in aplay.

 And as for the switch in the bios I think asus figured it was not needed as seen with the bios upgrades it has been removed. Thus we should be able to get spdif out from the header and hdmi output at the same time.

 regards,

 Dave

---

### Post by SnafuFlux on 2009-03-04
hah, thanks Dave.  No way was I going to be answering this question!

---

### Post by Nav0 on 2009-03-04
Hey guys, 

I was actually looking at the same problem, with the latest Alsa drivers the motherboard SPDIF connector works, but the onboard (back panel) does not. Did some research, and found their is an open bug in bugtrack for Alsa for this, [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4330](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4330), I am guessing we won't have the rear SPDIF port working ont his motherboard until this bug is closed off.

Regards,
Nav

---

### Post by smgendler on 2009-03-04
the output of aplay -l is:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

But my question is more theoretical than that.  My question is, why the heck is linux so hard?  Why doesn't it see the on-board SPDIF? It sees the auxiliary SPDIF, but not the one that it "should see" more easily.   What makes it hard for linux to see hardware it should see (meaning the on-board SPDIF)?  What made the purchase of the secondarry SPDIF work when Windows could see it right away?

---

### Post by rodercot on 2009-03-05
> **smgendler said:**
> the output of aplay -l is:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

But my question is more theoretical than that.  My question is, why the heck is linux so hard?  Why doesn't it see the on-board SPDIF? It sees the auxiliary SPDIF, but not the one that it "should see" more easily.   What makes it hard for linux to see hardware it should see (meaning the on-board SPDIF)?  What made the purchase of the secondarry SPDIF work when Windows could see it right away?

 Alot of owners see that aplay output and it is confusing to me as to why the opt. output does not work when they do, it should be only a matter of forcing the device with a asoundrc or asounf file placed somewhere. I never saw the VT1708B digital on my system at any time with aplay and IT should work.

 As to your other questions well, I am not sure, certain things in Linux can be trivial and certain things are much harder, I am by no means a guru and wish now I would have stuck with it back in the early 90's when I started playing with red hat. 

 You have open source software and open source manually created drivers and then you have hardware companies who supply virtually NO information to linux coders to use so a lot of info needs to be created to get any of this stuff to work. 
 
 comparing to M$ is just not fair, as most hardware vendors I would assume submit there hardware white papers to M$ before they even decide to manufature a product so M$ can jump on building support for it. More and more hardware suppliers are getting on board with Linux and Asus being one should hopefully have better support in the future, but we take it as it comes. I know that what I do with my systems and what I watch with my media center is not possible in any windows enviroment without hacking up the registry and then sometimes not at all. 

 So for ANYTHING media for me it is linux, myth and xbmc all the way, I have two copies of M$ XP MCE2005 and one Vista HOME(MCE) version sitting in my filing cabinet that have not been installed on anything in over two or three years and I am pretty sure it will stay that way. 

 rgds,

 Dave

---

### Post by smgendler on 2009-03-05
It's interesting to me that for media playing, linux is your system.  I hope to become better at it so I can make statements like that.  From what reading I have done, it seems that viewing BluRay discs is nearly impossible.  Do you have BluRay playback working on your system?

---

### Post by troipoison on 2009-03-23
Hey SnafuFlux I'm stoked that my first post actually got to help somebody!! :D
Fellow Cuhnuk here too in Vancouver. 
I ended up back on this forum because I grew tired of running XBMC through a full Ubuntu. Also my 180 rev of Nvidia driver decided to stop working one day. (watch out). So I grabbed the latest XBMC live disc and installed it as a completely hasslefree playback machine. I'm not into recording DTV anyway. 

smgendler: As long as you have kernel 2.6.27 and up they have integrated udf 2.5 so blueray playback should be feasible. You just need to recognize m2ts files. For that I would look into "Ubuntu on the Playstation 3" forums.

I'm stoked you got yourself up and running SnafuFlux, as I was writing this I ran the alsaupgrade -snap and there it is!! my alsa mixer has a front and rear iec958 selection. Now if only the onboard optical would light up. :D

I've earned a beer....:cheers!!

---

### Post by SnafuFlux on 2009-03-23
Hey Troipoison,

Yep, working like a champ.  I've actually since blew away my mythbuntu install and installed again.  worked as well as it did last time.  If you hadn't of posted saying you built your own port, I prob wouldn't have bothered trying this option!  

I was trying to setup an appletv for a lightweight front end, but I just could not get it to work smoothly.  The cpu could barely handle 720p mkv files.  sad to say I had to give it up.

I've since converted my current computer into a front end.  I tried the instructions I posted and I cannot get spdif to work (Mobo: Asus A8N deluxe).  

I'm in London myself.  I don't know how much support there is in this city, so I'm glad I've got the interwebs.

Question: can anyone comfirm or deny that mythtv works well on ps3?  I've got one and contemplated using it, but I heard you cannot get access to all the ram, so playback can be kinda crappy (HD).

---

### Post by pcooley on 2009-04-10
I, too, was unable to get the onboard optical SPDIF on the ASUS M3N78-EM Geforce 8300.

I found that in the alsamixer I needed to turn on the IEC958 (pressing m while it was selected) and suddenly it turned on the optical out.

I was happy to find that after an hour of spelunking around.

Paul Cooley

---

