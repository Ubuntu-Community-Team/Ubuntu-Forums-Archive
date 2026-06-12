---
title: "Any experience with Flacon Audio Converter? Does it affect sound quality?"
date: 2012-12-01
forum: Multimedia Software
---

### Post by DutchDude on 2012-12-01
I consider using Flacon for splitting .flac files. 

I used to do this with cuebreakpoints and shnsplit. The codes I used for installing this programs and splitting files were respectively

```
$ sudo apt-get install cuetools shntool flac

$ cuebreakpoints file.cue | shnsplit -o flac file.flac 
```

The soundquality of the resulting files is good, but the disadvantage of this method is that you have to edit all the filenames and tags with Kid3... and that is a lot of work! 

Flacon uses a GUI to extract individual tracks from one big audio file containing the entire album of music and saves them as separate audio files. To do this, it uses information from the appropriate CUE file. Besides, Flacon makes it possible to conveniently revise or specify tags both for all tracks at once or for each tag separately. 

This should save a lot of work! However, I'm a bit hesitant. Although the .flac format is lossless, the method of making .flac files is NOT necessarily lossless. I learnt this the hard way when I used Rubyripper to backup my CD-collection. After days of work, I found out that the sound quality was poor and that I needed to install Exact Audio Copy 0.99 under WINE.

Furthermore, Flacon is not yet in the repositories. [In order to install it you need to add a PPA]("http://code.google.com/p/flacon/wiki/Ubuntu_Instalation"). This also makes me a bit cautious on sound quality...

Does anybody know if FLACON affects the quality of .flac files when you split them?

---

### Post by shantiq on 2012-12-01
perfect tool in my experience :KS


uses    > 

cuebreakpoints file.cue | shnsplit -o flac file.flac   in the script anyway

---

### Post by Yellow Pasque on 2012-12-01
flacon uses shntool to do the splitting, so it's not like one of those programs that reencodes your audio to split it (e.g. Audacity).

---

### Post by DutchDude on 2012-12-02
> **Temüjin said:**
> flacon uses shntool to do the splitting, so it's not like one of those programs that reencodes your audio to split it (e.g. Audacity).

Thanks for the info. 

Are you sure it is not reencoding? I just wonder what this encoding means:

[IMG]http://i48.tinypic.com/2hyjubt.png[/IMG]

This is what you see when you split a file with flacon.

Does this encoding alter the quality of the sound?

---

### Post by dun270 on 2012-12-16
Just installed flacon. Now I no longer need WinXP to use EAC. Flacon has all the different audio file outputs, converting any large wav, ape, flac, etc file to individual files w tags(using the cue file), all in one step, and with user adjustable quality output. Has some requirments so use the -f switch to install w apt-get.

get it:
    sudo add-apt-repository ppa:flacon/ppa

    sudo apt-get update

    sudo apt-get -f install flacon

site:[https://code.google.com/p/flacon](https://code.google.com/p/flacon)

---

