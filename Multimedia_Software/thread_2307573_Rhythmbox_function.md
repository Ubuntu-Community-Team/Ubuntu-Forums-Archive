---
title: "Rhythmbox function"
date: 2015-12-26
forum: Multimedia Software
---

### Post by Donnie Love on 2015-12-26
Need cheat codes to make Rhythmbox 3.0.2 work in Lubuntu.

---

### Post by bapoumba on 2015-12-26
Which lubuntu version are you running ?
[http://packages.ubuntu.com/search?keywords=rhythmbox](http://packages.ubuntu.com/search?keywords=rhythmbox)

What is not currently working ?

---

### Post by Donnie Love on 2015-12-26
> **bapoumba said:**
> Which lubuntu version are you running ?
I have no way of knowing.

> What is not currently working ?
Rhythmbox won't play audio files. It freezes up and crashes.

---

### Post by bapoumba on 2015-12-26
Please post the outputs to :
```
lsb_release -rd
echo $DESKTOP_SESSION
apt-cache policy rhythmbox
rhythmbox &
```

---

### Post by Donnie Love on 2015-12-26
```

Description:    Ubuntu 14.04.3 LTS
Release:    14.04
donnie@R103:~$ echo $DESKTOP_SESSION
Lubuntu
donnie@R103:~$ apt-cache policy rhythmbox
rhythmbox:
  Installed: 3.0.2-0ubuntu2
  Candidate: 3.0.2-0ubuntu2
  Version table:
 *** 3.0.2-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
        100 /var/lib/dpkg/status
     3.0.2-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages


```

---

### Post by bapoumba on 2015-12-26
Thanks, and does rhythmbox give any errors when started from the command line (last command in my previous post) ?

---

### Post by Donnie Love on 2015-12-26
Not that I can tell.

---

### Post by bapoumba on 2015-12-26
Hmm, and does it start at all ?

---

### Post by Donnie Love on 2015-12-26
Yes, it starts. Shows files. If you try to play a file it freezes. Try again and it closes.

---

### Post by bapoumba on 2015-12-26
What does happen if you play a file directly from the command line ?
```
rhythmbox xyz.mp3 
```
Where xyz.mp3 is the file you want to play (including its path unless you already are in the right place).

---

### Post by Donnie Love on 2015-12-26
Nothing happens.

Isn't there a code you can put in to make it work normally?

No? There's no way to get Rhythmbox to work in Lubuntu?

There's got to be a way. Isn't there anyone out there who knows anything about this?

---

### Post by Donnie Love on 2015-12-28
Still looking for a way to get Rhythmbox to work.

---

### Post by bapoumba on 2015-12-28
Well, without any error message, it can be difficult to suggest fixes.
There seem to be a debug option : [http://manpages.ubuntu.com/manpages/hardy/man1/rhythmbox.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/rhythmbox.1.html)
Does that give any output ?

---

### Post by Vladlenin5000 on 2015-12-29
Have you already tried:

1. A different software player with the same audio files;
2. Audio files from a different drive - USB flash, SD card, etc. - with Rhythmbox?

This troubleshooting might give different picture altogether. I suspect you're barking at the wrong tree...

---

### Post by Dennis N on 2015-12-29
Did you elect to install the plug-ins for playback of restricted formats (which includes mp3) when you installed Lubuntu? That is not automatic. If not sure, install ubuntu-restricted-extras and try again.

---

### Post by bapoumba on 2015-12-30
> **Dennis N said:**
> Did you elect to install the plug-ins for playback of restricted formats (which includes mp3) when you installed Lubuntu? That is not automatic. If not sure, install ubuntu-restricted-extras and try again.
+1 :)

---

### Post by Donnie Love on 2015-12-31
> **Dennis N said:**
> Did you elect to install the plug-ins for playback of restricted formats (which includes mp3) when you installed Lubuntu? That is not automatic. If not sure, install ubuntu-restricted-extras and try again.

No. I've been trying to find a way to do that, but I don't know how.

---

### Post by Dennis N on 2015-12-31
> **Donnie Love said:**
> No. I've been trying to find a way to do that, but I don't know how.

Here is how you can do that:

Go:

**Menu > System Tools> Lubuntu Software Center**

Use the search box, and enter 'restricted extras'
Select 'Ubuntu Restricted Extras'
Add to 'Apps Basket'
Click on 'Apps Basket' in Toolbar
Click on 'Install Packages' at bottom of window
Enter password to complete installation.

Rhythmbox should now work better.

(My directions are made from Lubuntu 14.04. As far as I know, they would be the same in later versions.)

---

### Post by Donnie Love on 2016-01-01
Hmm, that didn't work. When I did the search, it came up as already installed. I removed from system and reinstalled, but still no dice. I really thought that was it, that I didn't install it correctly or completely or something.

---

### Post by Donnie Love on 2016-01-05
Is there a way to contact the designers and try to figure out what the problem is?

---

### Post by mc4man on 2016-01-05
> **Donnie Love said:**
> Is there a way to contact the designers and try to figure out what the problem is?

You could file a launchpad bug. Note that this is not an issue for most users, RB works fine with most audio files.
Maybe try deleting the .bin file in this location - 
~/.cache/gstreamer-1.0

---

### Post by Donnie Love on 2016-01-05
> **mc4man said:**
> You could file a launchpad bug.
I don't know how to do that, and I don't know what the problem is.
> 
Maybe try deleting the .bin file in this location - 
~/.cache/gstreamer-1.0
This had no effect, and it came back anyway.

---

### Post by mc4man on 2016-01-05
Gave lubuntu a quick try - correct, Rb will not play music in lubuntu.
The reason is it can't get an audio out, lubuntu just comes with alsa (and lubuntu is quite crappy at setting the proper device for alsa, seen here on a laptop w/ audacious, I have to find the correct device, nonsense really for a modern Os

Anyway install pulseaudio, then  Rb should work.
```
sudo apt-get install pulseaudio
```

---

### Post by Donnie Love on 2016-01-06
Yup. That did it. Thank you.

It's playing music now, but looks like it still won't extract tracks from a disc. Is there another patch that will make that happen?

---

### Post by mörgæs on 2016-01-06
If this solves the problem please mark the thread so.

---

### Post by Dennis N on 2016-01-06
> **Donnie Love said:**
> Yup. That did it. Thank you.

It's playing music now, but looks like it still won't extract tracks from a disc. Is there another patch that will make that happen?

I suggest you use a ripper application to extract tracks to mp3 or other audio file format. Search for "ripper" in Ubuntu Software Center.

I was surprised that Rhythmbox wouldn't work without pulse audio. The default player, Audacious, works just fine on Lubuntu without it.

---

### Post by mc4man on 2016-01-06
> **Dennis N said:**
> I suggest you use a ripper application to extract tracks to mp3 or other audio file format. Search for "ripper" in Ubuntu Software Center.

I was surprised that Rhythmbox wouldn't work without pulse audio. The default player, Audacious, works just fine on Lubuntu without it.
Audacious has quite a large number of available alsa output devices, don't think Rb does. Here by default in lubuntu aud does _not_ have sound, as mentioned I have to go into that list to pick the proper one
(shouldn't have been that hard for lubuntu to divine as it's a laptop with 2 internal speakers..
scr. shows about 2/3 of listing, don't see anything like that in Rb or any direct way for Rb to be told to use alsa. 
(not to say there isn't, just not obvious, maybe some lubuntu system setting if it has any..

---

### Post by Dennis N on 2016-01-06
Yes, it's full of output options. Audacious is working here (Lubuntu 14.04) with either plugin selected. I do install pulse audio in Lubuntu from the beginning because I need p.a. with Audacity.  Rhythmbox is not really my kind of player - I don't use use it.

I install pulse audio volume control as well (pavucontrol). I would suggest installing that also.

---

