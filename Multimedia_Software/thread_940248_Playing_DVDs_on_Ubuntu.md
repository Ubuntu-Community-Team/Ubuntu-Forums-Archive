---
title: "Playing DVDs on Ubuntu"
date: 2008-10-06
forum: Multimedia Software
---

### Post by rfkrocktk on 2008-10-06
I've had a lot of problems playing DVD's on Ubuntu. I have an X-Files DVD that will only go to the warning and attention screens present at the beginning of most DVDs. What program should I install to play DVD's best?

---

### Post by tuxxy on 2008-10-06
VLC is a great player, plays virtually any file format.

also make sure you have libdvdcss2 and w32codecs installed.

---

### Post by yamushk on 2008-10-06
> **tuxxy said:**
> VLC is a great player, plays virtually any file format.

also make sure you have libdvdcss2 and w32codecs installed.

Hi,

I have been trying for almost a whole day to play a DVD using mainly Kaffeine and VLC, but also other players - in vain. Sometimes I can play the DVD menu, but that's it. I uninstalled and re-installed them many times with different plugins libraries that I cannot remember what I currently have... *sigh*. Can anyone guide me slowly through the process until I can finally play a DVD? I prefer using either Kaffeine or VLC.

The most annoying thing is that Kaffeine used to work; then I messed something up in the operating system and had to reinstall Kubuntu - now nothing does :(

I am running Ubuntu 8.04.1 for 64 bit (actually Kubuntu). I don't know which version of KDE I have, but I installed it today (October 2008 ). In this case I should install w64codecs instead of w32codecs?

Thanks,

Yamushk
:popcorn:

---

### Post by Therion on 2008-10-06
Make sure you have the Multiverse repo enabled in your sources.lst file.

Open Synaptic.  

Search for, and install, the following two packages:

[b]ubuntu-restricted-extras
libdvdcss2[/b]

You should be good to go.

---

### Post by yamushk on 2008-10-06
> **Therion said:**
> Make sure you have the Multiverse repo enabled in your sources.lst file.

Open Synaptic.  

Search for, and install, the following two packages:

[b]ubuntu-restricted-extras
libdvdcss2[/b]

You should be good to go.

Thank you very much for your help but I have a few more questions... :confused:

I am running Kubuntu, not Ubuntu.
Shall I install ubuntu-restricted-extras or kubuntu-restricted-extras?

I could not find in the Adept Manager libdvdcss2. I have libdvdnav4 and libdvdread3 installed.

I also could not find the file sources.lst.

Will that help me with the VLC or with Kaffeine (or both?)

Thanks, :-\"

Yamushk

---

### Post by mc4man on 2008-10-06
go here and add medibuntu as a repo for version of ubuntu your using (7.10, 8.04, 8.10 ect.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Then ck. again in adept

For kaffeine change the the dvd device from /dev/dvd to dev/scd[COLOR="Red"]x[/COLOR] (change x to match your drive
Settings -> xine engine parameters -> media (scroll down a bit

If your not sure ck. when you play in vlc or run 
```
sudo lshw -C disk
``` to see

---

### Post by yamushk on 2008-10-07
> **mc4man said:**
> go here and add medibuntu as a repo for version of ubuntu your using (7.10, 8.04, 8.10 ect.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Then ck. again in adept

For kaffeine change the the dvd device from /dev/dvd to dev/scd[COLOR="Red"]x[/COLOR] (change x to match your drive
Settings -> xine engine parameters -> media (scroll down a bit

If your not sure ck. when you play in vlc or run 
```
sudo lshw -C disk
``` to see

Thank you very much for your patience... But... still doesn't work. 

First of all: I'm sorry, what does repo mean?

I installed Medibuntu but adept still doesn't have libdvdcss2.
The Multiverse repo needs to be enabled in the /etc/apt/sources.list.d/medibuntu.list file or sources.lst file? 

in /etc/apt/sources.list file I found the following:

```

deb http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

Should I change any of those?

Updated the DVD device to scd0... Still no luck   ](*,)

Thanks,

Yamushk

---

### Post by rfkrocktk on 2008-10-07
Yeah, I've installed every "DVD Player" app I could find in the add/remove programs list and I can not get DVD's to play. Is there a program that will simply do it for us out of the box?

---

### Post by cariboo on 2008-10-07
To play DVD's make sure you have installed the following packages:

```
ubuntu-restricted-extras
```

or kubuntu or Xubuntu, which ever version of Ubuntu you are using.

Then go [here]("https://help.ubuntu.com/community/Medibuntu") to add the Medibuntu repositories to your sources.list. Be sure to follow the instructions.

Once you have done the above go to the package manager for your version, Synaptic for Gnome, Adept for KDE, not sure what Xubuntu uses, and search for libdvdcss2 and install it.

Once you have done all of the above, and you've done everything right you should be able to watch DVD's,

Remember to check local laws to see if this is legal in your country.

Jim

---

### Post by mc4man on 2008-10-07
@ yamushk
For hardy ( if your not seeing where or how on link. Run in konsole

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
followed by 
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```
then
```
sudo apt-get install libdvdcss2 libxine1-ffmpeg
```

Kaffeine  needs the libxine1-ffmpeg

---

### Post by yamushk on 2008-10-07
> **mc4man said:**
> @ yamushk
For hardy ( if your not seeing where or how on link. Run in konsole

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
followed by 
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```
then
```
sudo apt-get install libdvdcss2 libxine1-ffmpeg
```

Kaffeine  needs the libxine1-ffmpeg

Great! Now both Kaffeine and VLC work - thanks so much Mc4Man! \\:D/
Thank you also Jim (and Therion before); I didn't have a chance to try Jim's suggestions, but it's always good to have for future reference.

Have a great day - my case is solved here; hope it also helps rfkrocktk.
 :D

---

### Post by rfkrocktk on 2008-10-13
Yes! Thanks so much for the fix. I got DVD's up and running in like 3 minutes this weekend after reading your post. Thanks a lot!

---

