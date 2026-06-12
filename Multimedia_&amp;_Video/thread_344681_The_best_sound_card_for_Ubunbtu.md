---
title: "The best sound card for Ubunbtu"
date: 2007-01-23
forum: Multimedia &amp; Video
---

### Post by miceagol on 2007-01-23
During my Linux years on my own desktop, I've used two sound cards: SoundBlaster Live! 1024 and an integrated sound card on my new Asus P5B-E mobo ( SoundMax AD1988 ). Both of them have failed to cover my main need, namely 5.1 surround. Thus, I have come to the conclusion to buy a new sound card that I know will function on my Linux system. My main question is: 

[SIZE="4"]**What sound card do you recommend for Ubuntu?** [/SIZE]

Don't post anything here unless you know that card works absolutely flawless with a **5.1 surround system**, without the problems stated in the last paragraph or any other problems. For starters, anybody know it these work with 5.1 surround?
[LIST]
[*] [Creative SB Audigy SE PCI, 7.1]("http://www.komplett.no/k/ki.asp?sku=312201")
[*] [Creative SB Audigy 4 PCI, 7.1]("http://www.komplett.no/k/ki.asp?sku=313615")
[*] [Creative SB X-Fi Xtreme Audio]("http://www.komplett.no/k/ki.asp?sku=325912")
[*] [TerraTec SoundSystem Aureon 7.1]("http://www.komplett.no/k/ki.asp?sku=309631")
[*] [Creative SB X-Fi XtremeGamer]("http://www.komplett.no/k/ki.asp?sku=326406")
[/LIST]

You don't need to read this part, but here's what didn't work with the two sound cards I've had. My SoundBlaster Live! card had too much volume on the rear channels when playing a 5.1 movie. Increasing the volume of the front channels to compensate was possible, but then the sound then had low quality and was awful to listen to. The sound card I'm now using with my new PC don't give me 5.1 at all. It can duplicate the sound from the front channels to the rear channels, but that's all. The rear channel volume is called "side" in alsamixer, but doesn't give 5.1 surround nonetheless.

EDIT: I successfully managed to find the best sound card for Ubuntu, namely **M-audio Revolution 5.1**. :D Check post #25 in this thread for help configuring it and to decide if it suits your needs (e.g. I'm not able to test the S/PDIF output).

---

### Post by Absurd on 2007-01-23
I don't know, but I'll tell you one thing.

Creative X-Fi cards are not yet supported by ALSA.

---

### Post by miceagol on 2007-01-23
> **Absurd said:**
> I don't know, but I'll tell you one thing.

Creative X-Fi cards are not yet supported by ALSA.

Well, you bet that was very important information. Thanks! :)

Geez, I hate these hardware manufacturers. No Linux support whatsoever. And I'm going to give them money anyway. :-|

---

### Post by Pablasso on 2007-01-24
i'm interested in special to know if the Creative SB Audigy SE PCI, 7.1 works fine on a 5.1 home theater.. before wasting my money.. again

---

### Post by miceagol on 2007-01-25
Ok, I've done some more reasearch now and taken a look at the Alsa list over supported cards, so I'll rephrase my questions. The X-Fi cards are [out of the question]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix"). 

[LIST]
[*] The above link to the alsa supported Creative cards, says that [Creative SB Audigy SE]("http://www.komplett.no/k/ki.asp?sku=312201") doesn't work on analog/digital outputs. Isn't that the same as not working at all, since you get no output to your speakers? 
[*] Does anybody have experience with the [Creative SB Audigy 4 PCI]("http://www.komplett.no/k/ki.asp?sku=313615")? It's listed as supported.
[*] New card on the list: [Terratec Aureon 5.1 PCI]("http://www.komplett.no/k/ki.asp?sku=304753"). I can find similar cards on the [Alsa list]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Terratec#matrix") (Aureon 5.1 Fun, etc.) Are they essentially the same card? Anybody tried it?
[/LIST]

---

### Post by miceagol on 2007-01-25
> **Pablasso said:**
> i'm interested in special to know if the Creative SB Audigy SE PCI, 7.1 works fine on a 5.1 home theater.. before wasting my money.. again

Exactly why we just can't go buy before asking. 

I wish I could buy and hand back all the sound cards in the shop, and test them one at a time until I found one that worked. Would have been easier. But that's of course impossible when the cards are only guaranteed to work in Windows, so I can't use "doesn't work in Linux" as an argument to deliver them back. ](*,)

---

### Post by jual_mahal1 on 2007-01-25
You just need to be patient...read below at this link: [Creative OpenSource]("at http://opensource.creative.com/")

> May 18, 2006 -- Creative plans to make proprietary (closed source) drivers available for the X-Fi series of sound cards in the second quarter of 2007. These drivers will have full support for ALSA (playback, recording, mixer, MIDI, synthesis) and OpenAL 1.1 (with EAX effects).

---

### Post by Patrick K on 2007-01-25
Here is one you might check out
[http://www.m-audio.com/products/en_us/Revolution51-main.html](http://www.m-audio.com/products/en_us/Revolution51-main.html)
A lot of M-Audio cards are supported in ALSA. 
Here is a 7.1 card
[http://www.m-audio.com/products/en_us/Revolution71-main.html](http://www.m-audio.com/products/en_us/Revolution71-main.html)
I don't know how well either will work but M-Audio has an excellent reputation in pro audio. I'll leave it to you to research them.

---

### Post by miceagol on 2007-01-26
> **jual_mahal1 said:**
> You just need to be patient...read below at this link: [Creative OpenSource]("at http://opensource.creative.com/")

That was a surprise, but I don't beleive it before I see it. Second quarter of 2007 can still be late June, and there's no guarantee it'll be out at that time, even if they say so.

---

### Post by miceagol on 2007-01-26
> **Patrick K said:**
> Here is one you might check out
[http://www.m-audio.com/products/en_us/Revolution51-main.html](http://www.m-audio.com/products/en_us/Revolution51-main.html)
A lot of M-Audio cards are supported in ALSA. 
Here is a 7.1 card
[http://www.m-audio.com/products/en_us/Revolution71-main.html](http://www.m-audio.com/products/en_us/Revolution71-main.html)
I don't know how well either will work but M-Audio has an excellent reputation in pro audio. I'll leave it to you to research them.

These guys send you to OSS when you select Linux drivers on their website, so that's positive. I'll need more research, but M-audio is now very high on my list over possible cards, and it's also possible for me to get the 5.1 version in Norway. Great! 

Thanks for the tip! ;)

---

### Post by Rhubarb on 2007-01-26
IMO my advice (and past experience) would be to stay well away from creative products.
I've had problems with most creative products:
[LIST]
[*]8 bit sound cards (yes, they're old)
[*]Soundblaster 16 (yes these are also quite old)
[*]Soundblaster Live 5.1DE
[*]Audigy Platinum with live drive
[*]Muvo
[*]CD-ROM drives
[*]Web cams
[*]Inspire / cambridge soundworks speakers + amplifier
[/LIST]
The only product that I've briefly delt with manufactured by creative that did not immediately present me with problems was an external usb Audigy box for notebooks.

I've found that all integrated AC97 chips (realtek, etc) have a better, and much less distorted sound than my Live 5.1.

Sound cards that perform very well / excellent:
Terratec (only tried in windows though)
Hercules DJ console (USB sound card, 5.1 works in windows, 2ch in Linux - though I'm sure this could be fixed up)
Turtle beach (only tried in windows though)

I'd certainly have a look at the M-Audio cards.  And of course look on the ALSA website to check support.

---

### Post by eightysix on 2007-01-27
I'm looking for a good sound card that works well with Linux as well.

If you look on the drivers page for the Revolution 5.1/7.1, you'll notice that the latest drivers are from 2004! Actually, pretty much ALL of the Linux drivers are from 2004! :mad: 

Don't know how well they work in ALSA. Any M-Audio users want to chime in?

---

### Post by Patrick K on 2007-01-27
Both cards use the ICE-1724 driver. The latest ALSA stable release is 1.0.13rc2 dated  9/25/06. Not too old.. The Windows version, which I also have, is dated 2004, but then Windows doesn't change as often as Linux. 

I have had some issues with my Audiophile 2496 card. It works fine except with Audacity. The volume controls in Audacity don't work properly. Whether it is the driver, the card, or Audacity, I don't know. I've had no problems with any other apps. Of course, the card with M-Audio drivers works perfectly in Windows. The Evny24Control is a nice mixer for the Envy chipset, which the R5.1 and 7.1 have.

---

### Post by E-Jey on 2007-01-29
Did you already buy a new soundcard? Which one did you choose? I also need a new audio card. I think I buy an Terratec Aureon 7.1.

---

### Post by miceagol on 2007-01-30
> **E-Jey said:**
> Did you already buy a new soundcard? Which one did you choose? I also need a new audio card. I think I buy an Terratec Aureon 7.1.

Oh no, still on the lookout. ;) I've seen some good remarks on the M-audio Revolution, so I might go for that, but this still needs more reasearching. Don't want to buy a half working card again, so I'm taking my time. I've abondoned the Creative cards I suggested. No drivers for X-Fi (at least for the time being) and mixed reports about Audigy 4 and Audigy SE. Thus, still considering the Terratec cards also.

Nice if somebody with 5.1-experience with the Terratec Auron and the M-audio Revolution cards could share their experience with us. :)

---

### Post by stunted on 2007-01-30
Over on the MythTV mailing list (where sound is important) the card of choice is the Turtle Beach Riviera. As far as I know most supported Sound card with digital I/O can do S/PDIF pass through and output raw PCM as digital so it gets decoded by the high quality DAC in your AV receiver, away from your CPU, GPU and other sources EM noise. 

I have a bunch of Creative Sound Blaster Live cards (5 of them, they were very cheap second hand) and despite the fact that the "DSP runs fixed at 48 kHz," which means that every sound runs through some internal interpolation to get it up to 48 kHz so "digital 1:1 copies are impossible (the 48 kHz SPDIF frequency can't be changed to anything else either)" it sounds great and was very cheap, though next time I'll go for Turtle Beach Riviera cards.

One thing I don't think any card can do under linux is DDL (Dolby Digital Live) or as it used to be DICE, or the DTS equivalent (DTS Connect), which allows the card and driver to upmix the stereo output from your ogg file (or whatever) to a full 5.1 (AC3/DTS compliant) feed, which is useful if your AV receiver doesn't have a "7 channel stereo" option (should be more configurable even if it does) or when watching a video with 6 channel sound stored in some other format.

I did some research on this a while ago and posted the results on the MythTV users mailing list.
[http://www.gossamer-threads.com/lists/mythtv/users/196611](http://www.gossamer-threads.com/lists/mythtv/users/196611) 
For some old but still relevant info on digital sound in linux go
[http://lau.linuxaudio.org/audio_quality_HOWTO.htm](http://lau.linuxaudio.org/audio_quality_HOWTO.htm)

---

### Post by miceagol on 2007-02-06
Just thought I'd let you know about these two pages:
[LIST]
[*] [http://phoronix.net/forums/showthread.php?t=18](http://phoronix.net/forums/showthread.php?t=18)
[*] [http://www.phoronix.com/scan.php?page=article&item=416&num=1](http://www.phoronix.com/scan.php?page=article&item=416&num=1)
[/LIST]

The M-audio Revolution and Chaintech AV-710 are amongst those given thumbs up, so I've decided for a M-audio Revolution. I'll report back to you when I've received and tested it. :KS

---

### Post by sulu on 2007-03-01
This interests me greatly, as I'm planning to either purchase the Aureon 7.1. Space or the M-Audio Revolution 7.1.

Any feedback here yet?

---

### Post by miceagol on 2007-03-03
They didn't have anymore Revolution 7.1's in stock (even though it said so on the website), so I had to wait a month or so. It's been three weeks since I ordered it now, so they should be getting in stock soon. I'll give feedback as soon as I've tested it, so be patient. ;)

---

### Post by miceagol on 2007-03-26
I'll get the soundcard today or tomorrow, so you can expect a report anytime soon. :) Had to take the 5.1 version though. Too long to wait for the 7.1 version.

---

### Post by Phulerock on 2007-03-26
I tried to finding one best soundcard in linux, its seem so hard, Creative is the famous manufactor about audio, but don't support linux well, I want to but Creative xmod device that using USB, but I cant any document in alsa project, or anyone can play it with full feature.

M-audio and Terratec can not be found in Vietnam, only Creative is the best sound device. Anyone help me to find the USB sound device work well in linux !??! and how to ship it to Vietnam.

---

### Post by herbster on 2007-03-26
I just got a Soundblaster Audigy SE to try out and have a Logitech z-5300e surround system. I have tried a bunch of tweaks, like editing my .asoundrc file and such, but I can't get the rear or center speakers to go.

I have raised the levels of every control in alsamixer to full, and running speaker-test in shell gives silence to rear left right and center speakers still. I have no clue how the hell to make it work, or if it's just the doggone card itself. Having a booming speaker system like this and not being able to use it fully is weak. I boot into Windows MCE to watch DVDs and I'd like Ubuntu to replace that as the sole function a Vista dualboot has left on my PC...

I'd be very interested as well to know which card(s) can actually support 5.1+ sound in Ubuntu, cuz I will get it... Please report the results of your sound card experiences guys!!!

---

### Post by syxbit on 2007-03-29
waiting to hear back about the revolution
i bought an xmod and it works just fine, although it's not 5.1

---

### Post by miceagol on 2007-03-30
Okay, here's a temporary report. :)

The card did not work out of the box unfortunately. When I booted with it into Linux the first time I got only sound from the front right speaker. I went into alsamixer, and increased the volume of the front speakers, and then I got sound from the left speaker too. I've read that it's a bug with the left speaker being muted at boot, and that adjusting the volume after boot "solves" it.

The rear speakers did not work, even if I increased the volume in alsamixer. No surround in movies too. I then read [this page]("http://seehuhn.de/comp/hardware/revolution"), which says that the card is badly supported with alsamixer versions older than 1.0.12. Edgy has 1.0.11, so installed 1.0.13 with the result that I [couldn't modprobe]("http://www.ubuntuforums.org/showthread.php?t=394124") any sound drivers. Then I tried 1.0.14rc3 with the same result.

Then I decided to upgrade to Feisty Fawn beta which includes alsamixer version 1.0.13. I got sound, but same results as with Edgy, no sound from rear speakers and left speaker muted at boot. I didn't get to try the card much in Feisty, because after downloading all the updates you get after a fresh install, Feisty got completely unstable. Had some very strange errors I won't go into here. :-|

This is a bit weird, because I've read about people who have got it to work great, and at the same time all the specs of the card has been released to Linux developers. Why doesn't such cards work out of the box? Argh, why??? Anyway, I think I  might need some editing of my **.asoundrc**, inserting upmixing (copy sound from front speakers to rear) and a line about 4.1 surround (I don't have 5.1). **Anybody know how to do this properly for my card?**

So that's were I stand now. I'll try to fix the issues with Feisty, and if I don't fix it quickly, I'll install Edgy again and try working it out from there. I'll also split the partition in two and install Freepire too, because [someone]("http://forum.freespire.org/showthread.php?t=941") said it worked out of the box there and not in Ubuntu.

---

### Post by miceagol on 2007-04-01
Everyone, it's working now! :D Let me tell you what I did.

I got rid of Feisty, and reinstalled Edgy. First thing I did was to try upgrade alsa again, and this time I did it with success. You have two options. Either install latest development release of alsa or install Feisty (it most probably will work fine for you). I'll show you how to install alsa properly. I probably got the severe errors described in my last post, because I forgot to do this before I installed the new alsa drivers:
```

sudo /etc/init.d/alsa-utils stop

```
This stops the alsa machinery. [COLOR="Red"]It's important that you do not forget the above command.[/COLOR] Now, download the latest development release of *alsa-driver*, *alsa-lib* and *alsa-utils* from [alsa webpage]("http://www.alsa-project.org/"), and do the following with all the tarballs in the order I listed the three tarballs:
```

tar xvf <filename>.tar.bz2
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=ice1724 --with-oss=yes
sudo make
sudo make install

```
If you have any other cards (like an onboard card), you can add it to --with-cards seperated by commas. After the installation is finished, do a complete reboot. Then run
```

cat /proc/asound/version

```
to check if you successfully upgraded alsa.  The first time you reboot after upgrading, you must increase the volume of all channels in *alsamixer*.

I should note that after any reboot, the front left channel is muted, but it's a known bug, and will probably be fixed in a future alsa release. To fix it for the current session, you have to adjust the volume of the front channels in alsamixer, e.g. up and down once. There is one more known bug, which is the headphones output. It does not work. Unfortunately I'm not able to test the digital S/PDIF output.

Now, you should have a working card. If you try play a DVD with Totem, you will hear 5.1 surround. :) If you want to duplicate the stereo stream in the front channels to the rear channels you should continue reading. 

To make that work you need to edit your *~/.asoundrc*. If it doesn't exist, create it. I went through a lot to find out what to add to the file. I tried to copy different .asoundrc files I found here at the forum and on the net, but no files worked correctly. Most of them did duplicate the speakers, but they also added a chipmunk effect, i.e. sound was playing slightly too fast. Sharon den Adel on speed. ;) Anyway, in addition any sound using the xine engine (e.g. amarok) was also choppy.

I ended up in the #alsa IRC channel at irc.freenode.net, and you have no idea how helpful they're there. I got some personal service, and was given this final working .asoundrc. It's fine-tuned for the M-audio Revolution 5.1 (and 7.1?) :)
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
For the changes to take effect, run
```

sudo /etc/init.d/alsa-utils restart

```
and reopen any program using the sound card. Now **amarok** will duplicate the channels as default, and **totem** will play DVD movies with 5.1 surround as default. 

What you have to do with some other programs: 
[LIST]
[*] **xmms**: Open the preferences. Go to "output plugin" and click on "configure", and write default as audio device.
[*] **mplayer**: Files with a 2 channel audio stream will automatically be duplicated as default. To play a file with a surround stream (e.g. AC3), use the following command:
```

mplayer -ao alsa:device=plug=dmix6 filename

```
[/LIST]

Conclusion: ***I highly recommend the M-audio Revolution 5.1 for Ubuntu.*** There are three main reasons for choosing this card. With this card your *5.1 configuration works*, you get a *high quality* card and you *support a manufacturer* who releases the card's specs to the linux community. **Don't support Creative!** With their attitude towards Linux, they should not get our money. The Revolution 5.1 is a bit more expensive than a Creative eqvivalent, but it's worth the extra money.

I'll make a How to-thread of this post. :KS 
*happy with his new sound card*

miceagol

---

### Post by miceagol on 2007-04-04
I've now written a HOWTO, which you can find [here]("http://ubuntuforums.org/showthread.php?t=400268").

---

### Post by Yellow Pasque on 2007-07-06
Has anyone gotten the headphone jack on their Revo 5.1 to work yet?

---

### Post by herbster on 2007-07-06
> **Temüjin said:**
> Has anyone gotten the headphone jack on their Revo 5.1 to work yet?

Hmm I have not even tried, as I use a z-5300 surround system and plug my headphones right into the remote control.

I will give it a shot tonight and see.

---

### Post by BDNiner on 2007-07-19
This is great that you got the revolution to work. I have the fast track pro and it crashes my box when i plug it into a USB port. I am debating whether to get the revolution, but i spent $250 to get the fast track, so i don't know yet.

---

### Post by dabl on 2007-07-19
Geeez, I read the whole thread and now I think I must be the "2 percenter" in the crowd.

I bought an Intel D975XBX motherboard which included the integrated "HDA" sound system (using SigmaTel STAC chip).  Here are the specs: [http://www.intel.com/design/chipsets/hdaudio.htm](http://www.intel.com/design/chipsets/hdaudio.htm)

I haven't tried "surround 5.1", but it works fine for recording whatever I send in the "line-in" analog port, and it plays back using ALSA or OSS.  Works great in Ubuntu Feisty 64-bit, Kubuntu Feisty 32-bit, and E-live 0.6.9, not to mention Windows.  :)

---

### Post by Yellow Pasque on 2007-07-24
I got tired of messing around with ALSA. I tried the guides on this page as well as some others. I finally got 1.0.14 installed and working, but still no love for my headphone jack.

Finally, I went to the m-audio page and found out that there are custom OSS drivers at [http://www.opensound.com/](http://www.opensound.com/) They just put out a new build (4.0 build 1004) and have now open-sourced the code. Install was extremely easy and I finally have my headphone jack working! It also runs nicely with wine and I'm currently running foobar2000 under wine as my audio player.

Thanks for the help everyone.

---

### Post by studo77 on 2007-10-18
I bugged around alot with my Audigy SE.

First having stereo, but no surround. Then after a lot of messing about, i only had one front speaker....
After a purged reinstall i used 1.0.13 ALSA(Feisty, Ubuntu1), straight out of box and have stereo and surround.

Then i wanted a simple upmix, after a few guides from this forum, and googling i came up with this, and everything seems to go fine, upmixes stereo, and surround passes through.

[http://pastebin.ca/464795?srch=upmix]("http://pastebin.ca/464795?srch=upmix")

Simple and easy...

.asoundrc
```
pcm.!dmix {
   type plug
   slave {
       pcm surround51
       channels 6
   }
}
pcm.!default {
   type plug
   slave.pcm "dmix"
   slave.channels 6
   route_policy duplicate
}
```

Now i only need to get my saa7134 to be nice....

---

### Post by txdmb on 2007-11-14
> **Temüjin said:**
> I got tired of messing around with ALSA. I tried the guides on this page as well as some others. I finally got 1.0.14 installed and working, but still no love for my headphone jack.

Finally, I went to the m-audio page and found out that there are custom OSS drivers at [http://www.opensound.com/](http://www.opensound.com/) They just put out a new build (4.0 build 1004) and have now open-sourced the code. Install was extremely easy and I finally have my headphone jack working! It also runs nicely with wine and I'm currently running foobar2000 under wine as my audio player.

Thanks for the help everyone.

How did you install the oss? Did you use the rmp, deb or tar files? Also, how did you get the headphone jack working?

---

### Post by Yellow Pasque on 2007-11-14
> How did you install the oss? Did you use the rpm, deb or tar files? Also, how did you get the headphone jack working?

I'm using the deb file, which is the package management system for Debian/Ubuntu. 
General Note: RPM is for package management on Redhat (and other distros that use that system), and you can't use those files on ubuntu without converting them using a utility called 'alien'

Please see [my post here:](http://ubuntuforums.org/showpost.php?p=3768418&postcount=7)
Two caveats: skip the first block of commands on uninstalling a botched OSS install since you haven't done that. Also, in the dpkg -i command, your file will be named differently if you're not using AMD64-bit Ubuntu. Just start typing the name of the file and hit TAB to auto-complete the name.

Also, the headphone jack works great once you get OSS installed. It's just not supported under ALSA.

---

### Post by txdmb on 2007-11-14
> **Temüjin said:**
> I'm using the deb file, which is the package management system for Debian/Ubuntu. 
General Note: RPM is for package management on Redhat (and other distros that use that system), and you can't use those files on ubuntu without converting them using a utility called 'alien'

Please see [my post here:](http://ubuntuforums.org/showpost.php?p=3768418&postcount=7)
Two caveats: skip the first block of commands on uninstalling a botched OSS install since you haven't done that. Also, in the dpkg -i command, your file will be named differently if you're not using AMD64-bit Ubuntu. Just start typing the name of the file and hit TAB to auto-complete the name.

Also, the headphone jack works great once you get OSS installed. It's just not supported under ALSA.

Ok, so I just did a fresh install of Ubuntu Studio 7.10. Do I need to uninstall the default ALSA drivers before I install OSS? When you say boot into the terminal, does that mean I have to restart and use the terminal before Ubuntu loads? Or can I just use the terminal on the drop down menu? I'm a bit of a noob to all this stuff.

---

### Post by Yellow Pasque on 2007-11-14
> **txdmb said:**
> Ok, so I just did a fresh install of Ubuntu Studio 7.10. Do I need to uninstall the default ALSA drivers before I install OSS? When you say boot into the terminal, does that mean I have to restart and use the terminal before Ubuntu loads? Or can I just use the terminal on the drop down menu? I'm a bit of a noob to all this stuff.

Use this link where I wrote instructions for a fresh install: [http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60)

Let me know how it goes.

---

### Post by txdmb on 2007-11-14
> **Temüjin said:**
> Use this link where I wrote instructions for a fresh install: [http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60)

Let me know how it goes.

It didn't work. The installation failed, it said that it couldn't stop the previous sound drivers, although I did the alsa remove step. Thanks for the help though.

---

### Post by Yellow Pasque on 2007-11-15
> It didn't work. The installation failed, it said that it couldn't stop the previous sound drivers, although I did the alsa remove step. Thanks for the help though.
Let's not give up just yet!
Which step failed? Removing the alsa-base package? I guess it's possible that you need to boot into recovery mode through GRUB so you can run that command before ALSA loads.

---

### Post by txdmb on 2007-12-18
I tried your method under Ubuntu and it worked. However, when I tried it under ubuntu studio it failed. While installing OSS, the installation failed and said that the sound drivers were still in use. Do you know what may be causing this?

---

### Post by alzamabar on 2008-02-17
Did you buy the card? Does it work?

I've got 7,10 GG and would like a sound card which can work without problems.

M.

---

### Post by jaytek13 on 2008-02-19
Okay, I see this thread is old but this is where a google search brought me. So, have we decided the  M-audio Revolution 5.1 is the best sound card for Linux that supports 5.1?

---

### Post by miceagol on 2008-02-21
> **jaytek13 said:**
> Okay, I see this thread is old but this is where a google search brought me. So, have we decided the  M-audio Revolution 5.1 is the best sound card for Linux that supports 5.1?

Well, I have myself only tested three soundcards in 5.1, and M-audio Revolution 5.1 is best of those three. However, since these are my only statistical subjects, I can't conclude it's the best sound card. ;)

It's not perfect, but when it works, it works great (sound quality is very good). For S/PDIF you need to tell alsa to use that output as default through .asoundrc. Analog will work out of the box, but I experienced problems with pitched sound, but it was also fixed through .asoundrc. Solutions for this can be found in [this thread]("http://ubuntuforums.org/showthread.php?t=400268").

Of cards with good quality, I've also heard about ESI Juli@. Think that one works in Ubuntu.

---

### Post by AmpersUK on 2008-03-26
And, nearly two years later, still aren't :-(

---

### Post by Yellow Pasque on 2008-03-26
The M-Audio Revo 5.1 is a great soundcard.

I use OSS4 because ALSA mutes the left speaker every time you restart and the headphone jack won't work with it. I didn't see either of those issues on the changelog for ALSA 1.0.15 or 16, so those issues will probably persist in Hardy (I'm sure you could fix the mute issue with a little startup script though).

I'm guessing other Envy24HT-based cards will behave similarly to the Revo. Also worth taking a look at are cards based on the C-Media 8788 'Oxygen' chip. Just avoid Creative/X-fi and you should be okay.

---

### Post by AmpersUK on 2008-03-26
Thanks. I looked at these cards but was hoping for something a little cheaper. I have asked whether there is an updated list of supported cards in 8.04 and am waiting to hear.

---

### Post by Yellow Pasque on 2008-03-26
For those in the U.S. looking for a cheaper alternative, this card looks promising: [http://www.amazon.com/SIIG-SoundWave-7-1-PCI-IC-710012/dp/tech-data/B0006HDF6S/ref=de_a_smtd](http://www.amazon.com/SIIG-SoundWave-7-1-PCI-IC-710012/dp/tech-data/B0006HDF6S/ref=de_a_smtd)
SIIG Soundwave 7.1, C-Media 8768 chipset

AmpersUK: don't look for a compatibility list from Ubuntu, look for compatibility with ALSA 1.0.16, which is what Ubuntu 8.04 will use. What kind of cards are you looking at? What chipsets do they have?
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

---

### Post by AmpersUK on 2008-03-27
Thanks for that, I have just ordered an MAudio Revolution 5.1 card  and won't care if it doesn't work with 7.10 as I have been without sound for so long.

I wonder what the second hand value of a X-Fi card is :-)

As Creative haven't been too helpful I decided to avoid buying any of there that do work. And was prepared to pay a little extra because of that.

Ampers.

---

### Post by AmpersUK on 2008-03-27
there/theirs

---

### Post by AmpersUK on 2008-03-27
Dammit, and I have already paid for it. :-(

I need the headphone jack working :-(

However, I think I have an old USB Plantronics pair somewhere, those should work.

A script, once I learn how to do them, will be written.

Thanks for your help, and your lightening reply.

Ampers.

---

### Post by Yellow Pasque on 2008-03-27
AmpersUK, the headphone jack will work with OSS4, which I prefer over ALSA anyway (no mute bug either). It's fairly easy to convert to OSS4 now that the M-Audio Revolution drivers have been open-sourced.

I think the main issues with OSS4/Revo 5.1 are with some commercial apps like Skype. I think you'll be pleased with your purchase, as the Revo has excellent fidelity (though it leans to the warm side) and should last you a long time.

---

### Post by kloos on 2008-03-28
Hi there,
All this talk of 5.1 etc is all well and good.  But I need a good sound card for midi work.  I used to use an SW1000XG on Windows as there is no Linux driver for it.  But it has stopped working which is annoying as it cost so much.  That has the best midi sounds that I have ever heard, but I can't find any reviews for Linux cards that mention midi quality.  

Does anyone have any experience with midi on sound cards and which one is best?  I currently don't use Ubuntu but am looking to switch over as soon as I have a card.
Thanks

---

### Post by AmpersUK on 2008-03-28
Thanks for your help but I no longer have a problem.

My Creative "x-fI" now works perfectly with Ubuntu.

All I did was to download Hardy Herpn's (8.04) LTS Beta.

Worked immediately.

---

### Post by AmpersUK on 2008-03-28
Ooops, Hardy Heron

---

