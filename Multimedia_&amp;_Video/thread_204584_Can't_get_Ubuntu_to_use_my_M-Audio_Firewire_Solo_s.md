---
title: "Can't get Ubuntu to use my M-Audio Firewire Solo sound card"
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by christiandransfield on 2006-06-27
I've used windows since birth but just created a dual-boot system with the latest version of Ubuntu to see what all the fuss is all about, so go easy on me if this is a very dumb question! ;)

I have a laptop with a built in sound card but also have any external M-Audio Firewire solo attached to it.

When I open 'volume control' and go to the 'change device' option, the only two options it gives me are 'sis sl7012 (alsa mixer' and 'Realtek alc655 rev 0 (oss mixer)'.

It shows the firwire solo in the device manager options but I don't know how to disable my onboard sound card and get it to use the firewire instead. Can anyone help?

---

### Post by 23meg on 2006-06-27
I'm not sure about firewire audio device support at present, but does your device appear in the "Default sound card" combo box in System / Preferences / Sound?

---

### Post by christiandransfield on 2006-06-27
In system / preferences / sound it only shows the 'sis sl7012' sound card. 
I remember when I tried Ubuntu at my friends house (perhaps not the latest version) by booting from the cd my external sound card worked fine then.
Any ideas?

---

### Post by miikkee on 2006-06-29
Hi there, 
I also need badly to set up my firewire solo with Ubuntu. No success yet... I contacted M-Audio and specified I needed a driver for the firewiresolo. Their answer was: 

[COLOR="DarkOrange"][I]M-Audio uses a 3rd-party Vendor for Unix support.

4Front Technologies develops and supports Unix drivers for our Revolution and Delta series of products.

The software is available for free evaluation and non-profit use but 4Front charges a fee for technical support and commercial use.

They can be found at the following web address:

[http://www.opensound.com](http://www.opensound.com)


There are also Linux drivers available for some of our products on this website:

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-MAudio#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-MAudio#matrix)

Please note that M-Audio does not endorse the use of these drivers and we have no direct involvement in developing them.[/I][/COLOR]

**However it seems that there is NO LINUX DRIVER for firewire solo. Please let me know if you find anything....**

---

### Post by miikkee on 2006-06-29
May want to check that. I'll try it when I'll get some time...

[http://freebob.sourceforge.net/index.php/List_of_Supported_Devices](http://freebob.sourceforge.net/index.php/List_of_Supported_Devices)

Mick The Ouf

---

### Post by apollo1900 on 2006-10-13
Sorry for the bump, but I, too have one of these. It works fine in OSX but I want to see if it will run on Ubuntu. Any more info out there?

---

### Post by Lykil on 2006-10-18
I have exactly the same problem. Haven't installed Ubuntu as of yet, since I really need to be able to use the soundcard (use precisely the same: Firewire Solo).

If anyone figures it out, please let me know, as this really is the largest hindrance for me to move to the dark side...

---

### Post by tristan_koen on 2006-12-18
Hi

The Firewire Solo box works fine on linux - there just any ALSA support for it (yet!). To use your Firewire solo box you will need to use Freebob and jackd.

Freebob doesn't exist in the Ubuntu repositories yet, but it will be included in Feisty Fawn when it is released in April. In the interim, you can install the package from the Debian unstable repository.

Note: You *must* install the corresponding Debian jackd and *not* the Ubuntu one. The ubuntu version doesn't have freebob support compiled into it. It is a bit of a bugger, but you have to do the same for all your audio apps (Ardour, etc) since Synaptic won't install them without the Ubuntu versions being installed.

---

### Post by iain_m on 2007-04-19
Hi,

I also have the FireWire Solo and have just upgraded to Ubuntu 7.04, I have no sound...yet.

I see that Freebob is already installed according to the Synaptic Package Manager, but the FW Solo does not seem to have been detected. 

Now that freebob is included in Ubuntu, is it ok to download jackd from the Ubuntu package manager?

If not, where can I get the Debian jackd? The Jack site doesn't seem to say - it just says Linux users should use their distro package manager.

Thanks in advance for any help.
[B]
UPDATE[/B]: The FW Solo is visible in Device Manager ("ieee1394.product: FW Sol"), but that's as far as it goes - it's not doing anything.

**NEW UPDATE**: In the terminal a constant stream of messages appears as follows:
```
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
```

---

### Post by iain_m on 2007-04-24
Sorry for the double post, but does anyone have any ideas about this? 

I'm afraid I just have no idea what to do now that FreeBob ("libfreebob 1.0.0-3") and Jackd (including "Libjack0.102.20-1") are installed. 

Is something supposed to happen automatically? 

I haven't managed to glean anything else about this from searching the net. :(

---

### Post by Meyer on 2007-04-24
Just for information, my M-Audio Audiophile USB works straight out of the box under ubuntu 7.04.
It did work like a charm with 6.10 too.

So, some M-audio cards do work, and thats nice, because they rule :)

---

### Post by iain_m on 2007-04-24
Thanks for the info. I'd be interested to hear if other people have got specifically a _firewire_ audio interface working out of the box - that would help me troubleshoot! :)

---

### Post by stmiller on 2007-04-24
The Freebob project is the current hope for firewire devices in Linux. If your device has 'BeBob' firmware, it will work with the Freebob project. If not, you are out of luck at the moment. 

Check the Freebob page for details.

---

### Post by iain_m on 2007-04-25
The FireWire Solo is indeed listed on the freebob compatibility page ([http://freebob.sourceforge.net/index.php/List_of_Supported_Devices]("http://freebob.sourceforge.net/index.php/List_of_Supported_Devices")). M-Audio support also told me that freebob works with the FW Solo.

So.... if it's not working out of the box, is this more likely to be a problem with my particular system/installation, rather than a generic problem?

---

### Post by David Corrales on 2007-05-24
I haven't been able to get my firewire solo going either. I'm using Feisty, with freebob/jack installed but no go.

---

### Post by iain_m on 2007-05-24
David, did you upgrade from Ubuntu 6 or is it a clean install of Ubuntu 7?

---

### Post by iain_m on 2007-06-01
Any news on this from anyone? Has _anyone_ got this type of firewire sound card to work under Ubuntu? 

I'd like to know if it's even possible before I start trying to fiddle with the configuration. The Freebob page, to a newbie, is *really* not clear at all, I'm afraid, though I appreciate its good intentions.

---

### Post by iain_m on 2007-07-03
I hope i'm not breaking forum etiquette in bumping this... Any news?

---

### Post by huhitschris on 2007-07-05
I too have the same problem, in fact i'm using ubuntu studio, with JACK and freebob installed and I can't get my Firewire Solo to work at all. I'm a total newbie and I would appreciate any help with getting this to work.

---

### Post by AstarothCY on 2007-07-11
Bump, I'm about to buy this card and I just want to see one person say they've got it working.

---

### Post by damo21 on 2007-07-17
I know for a fact that this card works with freebob... BUT I think the 'Firewire Audiophile' is a better device... it comes with midi and better dac/adc...  I would like to know if anyone has got THIS box working with freebob... [http://freebob.sourceforge.net/index.php/List_of_Supported_Devices](http://freebob.sourceforge.net/index.php/List_of_Supported_Devices)

M-Audio Firewire Audiophile...  wanting to buy one of these IF it works in linux.

---

### Post by iain_m on 2007-07-31
damo21, when you say "I know for a fact that this card works with freebob", do you mean you have definitely got the FW Solo working under Ubuntu?

---

### Post by WestCoastSuccess on 2007-08-19
Hi iain_m. 

I can confirm I have the M-Audio FireWire Solo working under Feisty - you can see more info here:

[http://ubuntuforums.org/showthread.php?t=509312](http://ubuntuforums.org/showthread.php?t=509312)

1.67ms latency with no X Runs on my AMD 64 X2 w/2GB RAM.

---

### Post by iain_m on 2007-08-21
Thanks for the info and link! :)

---

