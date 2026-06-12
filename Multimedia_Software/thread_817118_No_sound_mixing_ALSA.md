---
title: "No sound mixing ALSA"
date: 2008-06-03
forum: Multimedia Software
---

### Post by bl4ck32 on 2008-06-03
Newbie user here- using 8.04 with a Logitech USB headset.

Problem - No sound from more than one app at one time.

Ive tried system->preferences->sound and anything but alsa doesnt seem to give back a sound under testing.

Example one - Ive had WoW and ventrilo running (at the same time) so that i can hear ppl speak, but cant talk to them while i can hear wow sounds, and the opposite (i can talk and hear ppl in vent, but cant hear sound from WoW)

Example 2 - I cant use Rhythmbox to listem to music and hear anything else that requires sound 

Ive setup wine to use alsa for wow and vent, and its the only one that works.

How do i get Ubuntu to mix the audio so i can hear / do 2 things at once? (listen to music + play a game for example)

Any ideas, or help appreciated. Ive searched and tried a few things (including losing all sound / partial sound etc at one point, then stressing ive blown it all :( )

---

### Post by markbuntu on 2008-06-03
check and see if you have libesd-alsa0. This is the Enlightened Sound Demon which allows multiple audio streams on one device. It is in the repos if you don't have it.

You should also set your Sound preferences to alsa instead of automatic and set your alsa default to your sound card. You can get asoundconf-gtk for that. It is handy if you have more than one sound card or switch between pulseaudio and alsa a lot.

I also use the gnome-alsamixer. It has a mix button. All the sound from everywhere plays all at once for me if I have them all unmuted in the mixer.

The only problem I have now is with flash but everyone has that problem and until flash is fixed I guess I will have to live with it.

I do not use WoW or ventrilo but your problem sounds more generic and this should fix you up, at least with alsa.

---

### Post by bl4ck32 on 2008-06-04
> **markbuntu said:**
> check and see if you have libesd-alsa0. This is the Enlightened Sound Demon which allows multiple audio streams on one device. It is in the repos if you don't have it.

i tried :
 ```
sudo apt-get install libesd-alsa0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libesd-alsa0 is already the newest version.
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libxine1-x librdf0 kdebase-runtime-data-common
  libxine1-misc-plugins libxcb-xv0 mysql-common libxine1-bin librasqal0
  libmysqlclient15off libxine1-ffmpeg libgmp3c2 kdelibs5-data libgif4
  libxcb-shape0 libstreamanalyzer0 libxine1-plugins libpq5 libstreams0
  libraptor1 libmodplug0c2 libxcb-shm0 libmpcdec3 libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
```

?
> **markbuntu said:**
> 
You should also set your Sound preferences to alsa instead of automatic and set your alsa default to your sound card. You can get asoundconf-gtk for that. It is handy if you have more than one sound card or switch between pulseaudio and alsa a lot.

I also use the gnome-alsamixer. It has a mix button. All the sound from everywhere plays all at once for me if I have them all unmuted in the mixer.


all sound prefs are set to alsa, and the default is my ush headphones. Only audio i have is the onboard one that comes with the Gigabyte DS3.

Ive also got the gnome -alsamixer installed...

---

### Post by jocko on 2008-06-04
To activate software mixing in alsa, you need to set up a ~/.asoundconf file.
The easiest way I have found is:

1. Find out what your card is called by asoundconf:
```
asoundconf list
```
This will output the name of your soundcard, or if you have more than one card it will give you a list.

2. Make asoundconf generate a default configuration for that card:
```
asoundconf set-default-card *name_of_card*
``` where *name_of_card* is the name of your card as it was reported by the previous command.

3. Restart alsa:
```
sudo alsa force-reload
```(or reboot your computer).

Now alsa will use the dmix (software mixing) plugin as default output unless you specifically set an application to acces the hardware directly.
One problem that still remains is that pulseaudio ignores the alsa settings and uses the hardware directly, so if you use pulseaudio it will block anything else from accessing the sound card.

---

### Post by bl4ck32 on 2008-06-05
> **jocko said:**
> To activate software mixing in alsa, you need to set up a ~/.asoundconf file.
The easiest way I have found is:

Had set my default sound device already (my USB headset)

alsa is working fine for all applications. Its just that if i try to run more than 1 thing at a time, i cant get audio from anything but the first thing loaded...

BTW my ~/.asoundconf file only contains the following :

```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/<username>/.asoundrc.asoundconf>


```

Is it supposed to contain anything?...like to enable sound mixing?

the : </home/<username>/.asoundrc.asoundconf> file contains :
```

# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card Headset
defaults.ctl.card Headset
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format S16_LE
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off
```

---

### Post by bl4ck32 on 2008-06-05
SOLVED!!!! - ALMOST (no mic now, but sound works great!)

Added this to my ~/.asoundrc file:

```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/<user>/.asoundrc.asoundconf>

     pcm.!default {
	type hw
	card 0
	}

	ctl.!default {
	type hw           
	card 0
        }

    pcm.!default {
	type plug
	slave.pcm "dmixer"
    }

 
    pcm.dmixer  {
	type dmix
	ipc_key 1024
	slave {
	    pcm "hw:1,0"
	    period_time 0
	    period_size 1024
	    buffer_size 4096
	    rate 44100
	}
	bindings {
	    0 0
	    1 1
	}
    }
 
    ctl.dmixer {
	type hw
	card 0
    }
	
    pcm.mixin {
        type dsnoop
        ipc_key 5978293	# must be unique for all dmix plugins!!!!
        ipc_key_add_uid yes
        slave {
                pcm "hw:0,0"
		channels 2
		period_size 1024
		buffer_size 4096
		rate 44100
		periods 0 
		period_time 0
        }
        bindings {
                0 0
                0 1
        }
    }

```

I can now hear sound from multiple things at once :)

Now, to see if i can use my mic as well :)

---

### Post by blackmachine on 2008-06-05
bl4ck32.. I need your help.
Is this your sound preference looks like?
[[IMG]http://img219.imageshack.us/img219/8862/screenshotsoundpreferenyx2.th.png[/IMG]](http://img219.imageshack.us/my.php?image=screenshotsoundpreferenyx2.png)

my problem still exist after I follow instructions from you and jocko
thanx..

---

### Post by bl4ck32 on 2008-06-05
> **blackmachine said:**
> bl4ck32.. I need your help.
Is this your sound preference looks like?
[[IMG]http://img219.imageshack.us/img219/8862/screenshotsoundpreferenyx2.th.png[/IMG]](http://img219.imageshack.us/my.php?image=screenshotsoundpreferenyx2.png)

my problem still exist after I follow instructions from you and jocko
thanx..

nope...

the first 3 are set to alsa - Advanced....etc

the last one (default mixer tracks) is set to my Logitech USB headset (ALSA mixer)

---

### Post by grndslm on 2008-06-05
I've never had problems with sound coming from multiple apps after installing the alsa-oss package!!!

---

### Post by bl4ck32 on 2008-06-05
> **grndslm said:**
> I've never had problems with sound coming from multiple apps after installing the alsa-oss package!!!

Yes, but my pc seems to like the alsa only.

Searching around here, it seems that what works for one, doesnt mean it will work for all :(

I fixed my sound, but now my mic doesnt work....1 step forward...1/2 step back

---

