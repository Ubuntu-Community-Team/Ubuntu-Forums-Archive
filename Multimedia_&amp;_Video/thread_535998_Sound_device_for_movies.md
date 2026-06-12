---
title: "Sound device for movies"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by starling on 2007-08-27
Since upgrading to fiesty, I have been unable to get sound out of any videos. Just tonight I discovered it was playing, but through the wrong sound card.
Rhythmbox works fine, but either of the video players, whether playing video or audio files, will play through the wrong device.

The sound properties has the music and movies set to the correct sound device (not to alsa), but it appears the move programs want to use alsa regardless.
Possibly what I need to do is change the defaults for alsa? I don't know, you tell me.

---

### Post by ddrichardson on 2007-08-27
You can specify alsa's default soundcard at the command line, it only needs to be done once. I'm not on Ubuntu just now so can't check the syntax - but do a man alsactl and its in there.

---

### Post by starling on 2007-08-28
SYNOPSIS
       alsactl [options] [store|restore|names] <card # or id>

DESCRIPTION
       alsactl  is  used  to  control advanced settings for the ALSA soundcard
       drivers. It supports multiple soundcards. If  your  card  has  features
       that  you can’t seem to control from a mixer application, you have come
       to the right place.

COMMANDS
       store saves the current driver state for the selected soundcard to  the
       configuration file.

       restore loads driver state for the selected soundcard from the configu&#8208;
       ration file.

       names generates list of available device names for  applications.   The
       card  number or id is ignored for this command. The list is always gen&#8208;
       erated for all available cards.

OPTIONS
       -h, --help
              Help: show available flags and commands.

       -f, --file
              Select   the   configuration   file   to  use.  The  default  is
              /var/lib/alsa/asound.state or /etc/asound.names (for  the  names
              command).

       -F, --force
              Used  with restore command.  Try to restore the matching control
              elements as much as possible.

       -d, --debug
              Use debug mode: a bit more verbose.

       -v, --version
              Print alsactl version number.


which option would you suggest?

---

### Post by ddrichardson on 2007-08-28
Sorry, my bad - its asoundconf!```
sudo asoundconf list
sudo asoundconf set-default-card card_name
```

It was a very late night last night ;-)

---

### Post by starling on 2007-08-30
Great! but I don't know if it has worked until I fix my [other problem]("http://ubuntuforums.org/showthread.php?t=536003")
I seem to have been left high and dry over there.

---

### Post by ddrichardson on 2007-08-30
Well you forgot sudo:```
mark@mark-desktop:~$ apt-get install libavcodec1d
```
should be```
mark@mark-desktop:~$ sudo apt-get install libavcodec1d
```

---

