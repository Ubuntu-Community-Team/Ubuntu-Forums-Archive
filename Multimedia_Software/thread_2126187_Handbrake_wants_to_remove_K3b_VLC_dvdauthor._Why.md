---
title: "Handbrake wants to remove K3b VLC dvdauthor. Why?"
date: 2013-03-16
forum: Multimedia Software
---

### Post by coldraven on 2013-03-16
Using Ubuntu 12.10
I added the ppa for handbrake from here: [https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)
Using synaptic I was alarmed to see that installing handbrake would remove a whole bunch of programs.
I'm sure that I have installed it before with no problems, any ideas what is going on?
Thanks

---

### Post by mc4man on 2013-03-16
Not sure yet what the issue is (assuming you have a 64 bit install), here it does want to remove a whole bunch in synaptic.
(bit different then you but I've other things installed

So for a 64 bit install synaptic **only shows the :i386 packages** when searched directly.
If you were to click on "Architecture" > arch:amd64 , then find handbrake* you'd come across the proper amd64 packages that install as expected. (see screen), you have to scroll down when in a particular arch,  bit of a pita

Or try from command line as a sim -  should work fine
```
sudo apt-get -s install handbrake-gtk handbrake-cli
```

If ok then remove the -s from command

Not sure whether this is some issue in synaptic or the ppa of handbrake

Edit:
software-center does show all 4 (:i386 & amd64), screen 2, but what's curious is the :i386 are at the top &  shown as the "(default)" ?? - screen 3

---

### Post by coldraven on 2013-03-16
> Not sure whether this is some issue in synaptic or the ppa of handbrake

Edit:
software-center does show all 4 (:i386 & amd64), screen 2, but  what's curious is the :i386 are at the top &  shown as the  "(default)" ?? - screen 3

Yes this is 12.10 64bit

Strange, Synaptic showed no results  when I tried Arch64.
The Software Centre showed no results with the "All Software" default, but did show four when I selected ""Handbrake Releases". (the drop down from the "All Software" button) That must be a bug!

The two reviews said that this version was broken and to add the ppa. That is some crazy vicious loop :(

All I'm trying to do is convert some .FLV files to play on a Sony Playstation.
ffmpeg conversion failed with the audio.
Arista Transcoder wants to take hours so I thought of giving Handbrake a go.
I'm going to the pub :)
I'll buy you a pint...

---

