---
title: "NEW -- mythprime .69 beta released for testing"
date: 2008-08-09
forum: Mythbuntu
---

### Post by majoridiot on 2008-08-09
**THE MOST RECENT SOURCE PACKAGE FOR MYTHPRIME AND OTHER FIREWIRE TOOLS CAN BE FOUND HERE: [https://wiki.ubuntu.com/majoridiot](https://wiki.ubuntu.com/majoridiot)**

[i]as of 7 December 2008, mythprime has been thoroughly tested and is considered "stable". it remains "beta" status 
because it is not an "official" mythbuntu application.[/i]

---------------

a new version of mythprime has been released and is ready for wide testing.  it supports both motorola and scientific atlanta STBs- and likely others that use firewire connections

major improvements have been made and include:

* STB detection functions improved

* P2P and broadcast priming functions optimized

* added built-in channel changing to tune a known "clear" channel before priming

* STB power-on is now optional

* added optional function to reset firewire bus before doing anything else, to help with STBs that jump nodes on the first bus reset
and for STBs that need resetting before priming

the latest source can be found linked in the post below.

it is **strongly** recommended you test mythprime from the command-line **before** adding it into your production system- to ensure
it will function correctly in your set-up.

compiling for testing is quick and painless.  after un-taring the folder:

```
$ cd mythprime.69.beta
$ make clean
$ make
```

you can the test it from the command line (while still inside the mythprime.69.beta directory) with:

```
$ ./mythprime
```
**adding any options you may need/want to try, including -v (verbose output to see what's going on under-the-hood)*

when you are satisfied with the results and any option(s) you may need, you can permanently install it to /usr/bin (REPLACING the old one
so back it up!) by issuing the following command (while still in the mythprime.69.beta dir):

```
$ sudo make install 
```

PLEASE read the included README for more complete info.

feedback to this thread and bug reports PMd or via email to me, please.

i hope this works out for everyone... ENJOY!

---

### Post by majoridiot on 2008-09-28
a new version of mythprime (.69b) has been uploaded to address a 4250HDC channel changing bug.

---

### Post by majoridiot on 2008-10-14
***Added for version .69c beta:***

new vendor number for motorola DCH-3200 stbs... and possibly other moto boxes.

---

### Post by majoridiot on 2008-11-10
**ADDED for mythprime .69d:** vendor info update for new SA firmware

---

### Post by majoridiot on 2008-12-07
***Added for .69f beta:***

updated moto vendor info for DCH-3200 and improved moto channel changer selection

latest source is available here: [https://wiki.ubuntu.com/majoridiot](https://wiki.ubuntu.com/majoridiot)

---

### Post by bmwman on 2008-12-08
I tried your newest script today and it seems to work. It recognized my STB and it says it's primed. I have two questions though: Is this script gonna run by itself when I restart or I need to manually run it? Also, The picture looks nice even in HD, but I have no sound. Does the firewire carry only video or it has both audio and video? I used to use my HDhomerun before I moved and it was working fine.

Thanks for your help

---

### Post by volkswagner on 2008-12-08
Firewire carries the sound and video.  Check the logs for any errors.  Do you have sound on any channels?  SD vs. HD?

---

### Post by majoridiot on 2008-12-08
> **bmwman said:**
> I tried your newest script today and it seems to work. It recognized my STB and it says it's primed. I have two questions though: Is this script gonna run by itself when I restart or I need to manually run it? Also, The picture looks nice even in HD, but I have no sound. Does the firewire carry only video or it has both audio and video? I used to use my HDhomerun before I moved and it was working fine.

Thanks for your help

it will not run by automatically- you will need to edit the mythtv-backend init script. the simplest
way is to just remove the conditional check.  using mousepad (or your editor of choice):

```
$ sudo mousepad /etc/init.d/mythtv-backend
```

near the head of the file, you will see:

```
prime_firewire()
{
    if [ "$ENABLE_FIREWIRE" = "TRUE" ]; then
	log_daemon_msg "Priming Firewire "
        su - $USER -c "/usr/bin/mythprime"
	log_end_msg $?
    fi
}
```

remove the check so it looks like this:

```
prime_firewire()
{
    	log_daemon_msg "Priming Firewire "
        su - $USER -c "/usr/bin/mythprime"
	log_end_msg $?
    fi
}
```

and save it.  the primer will now run every time the backend server is started or restarted.

***note for anyone forcing a channel changer:***

be sure to add the correct command line for mythprime in the above function. e.g. if you need to force 
channel changer 4, change this part:

```
su - $USER -c "/usr/bin/mythprime"
```

to:

```
su - $USER -c "/usr/bin/mythprime -f 4"
```

volkswagner was correct in saying sound is part of the firewire transport stream.  if you get video and
no audio, you need to check your audio settings in frontend setup (playback) and check your
mixer levels, etc.

---

### Post by bmwman on 2008-12-09
I will try this tonight. Haven't had much time to play with it. Also I haven't cleaned my encrypted channels so when I try to change the channel it locks up after one or two channels. I remember the sound was working fine with my HDhomerun and i do get sound with MythVideo or MythMusic. I tried to run the ScanFW script but my STB is not in there.

Thanks for the info.

---

### Post by bmwman on 2008-12-09
ups, posted twice.

---

### Post by majoridiot on 2008-12-09
> **bmwman said:**
> I will try this tonight. Haven't had much time to play with it. Also I haven't cleaned my encrypted channels so when I try to change the channel it locks up after one or two channels. I remember the sound was working fine with my HDhomerun and i do get sound with MythVideo or MythMusic. I tried to run the ScanFW script but my STB is not in there.

Thanks for the info.

scanfw has been updated to include all known STbs... you might give version .98c a shot now.

[https://wiki.ubuntu.com/majoridiot](https://wiki.ubuntu.com/majoridiot)

---

### Post by majoridiot on 2008-12-17
source for mythprime version .69h beta has been posted at: [https://wiki.ubuntu.com/majoridiot](https://wiki.ubuntu.com/majoridiot)

changes include:

added vendor and model info for new moto and sa stbs

default motorola channel changer is now the single-digit method (7)

if you experience issues with your motorola stb with changer 7, you can force the "fast" changer with -f 6.
if the new changer affects you, please email me... i am trying to sort out where the various firmwares
are being deployed.  my email addy is in the README.

---

### Post by stefanst on 2008-12-30
Just tried the latest mythprime and scanfw with a Motorola QIP 6200 and they work beautifully! 

Thanks MI.

ST

---

