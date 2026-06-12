---
title: "HOWTO: get an undetected usb card or headset detected by alsa and configured for 5.1"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by mjkelly on 2007-10-18
It took 2 days to finally come to getting this usb card installed and working properly. I found a ton of posts on ubuntuforums that were unsolved with the same problem or similar problems with usb cards. This solution might solve a bunch of problems that arent exactly identical to mine.

My problem: My new usb sound card was not being detected by ALSA but was located by lsusb. Then after having it installed, it would not play 5.1 surround

So this might work for you IF:

"lsusb" shows your USB card listed
"aplay -l" or "asoundconf list" does not show your USB device listed
So your card is connected right, but ALSA is not detecting it as a USB sound card

The solution: Install the new 1.0.15 ALSA drivers from source, configure the sound card to be default, then add a script adding 5.1 functionality. (Not as hard as it sounds,)

First, open a terminal: Applications>Accessories>Terminal
*This code here is taken from: [http://ubuntuforums.org/showthread.php?t=535841&highlight=alsa+build](http://ubuntuforums.org/showthread.php?t=535841&highlight=alsa+build)*

```
sudo aptitude install mercurial autoconf libncurses5 libncurses5-dev
```


While those download, open firefox and head to: [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

Then:
```
mkdir ~/Alsa
```

In firefox, download stable release versions (1.0.15 at the writing of this) of drivers, utils, tools, and lib to the Alsa directory we just made.

Then:
```
cd ~/Alsa
bunzip2 *
```
Then:
Open a file browser:  Places>Home Folder
Browse to the Alsa directory. Double click on each Tar file and press Extract. Make sure your extracting to the Alsa directory and press Extract again.
Then:
```
cd ~/Alsa/alsa-driver-1.0.15
./configure
sudo make
sudo make install
```
This might take a little bit, dont worry about it.
Then:
```
cd ~/Alsa/alsa-lib-1.0.15
./configure
sudo make
sudo make install
```
Then:
```
cd ~/Alsa/alsa-utils-1.0.15
./configure
sudo make
sudo make install
```
Then:
```
cd ~/Alsa/alsa-tools-1.0.15
./configure
sudo make
sudo make install
```

Then restart your computer.

When you get back:
```
cat /proc/asound/version
```
That should reply:
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.15.
Compiled on Oct 18 2007 for kernel 2.6.20-16-generic (SMP).          #These dates on this line will be different. Dont worry about this line.

Make sure that output says 1.0.15.

```
cat /proc/asound/cards
```
If your usb device is listed your in good shape. Mine was not listed and i restarted again and then it was found. I dont have an explanation for this and neither did anyone in #alsa. Try resetting to see if its detected. It should be.

To set your usb device to the default device over the onboard:
```
sudo gedit /etc/modprobe.d/alsa-base
```
In that file, search for this line: 
options snd-usb-audio index=-2
Change that number to a 0. It might be a 2 or it might be a 1, change it to a zero so it looks like this:
options snd-usb-audio index=-0
Save that file.

Now, your device should be recognized by Alsa and set as the default device. Now for the 5.1.
```
gedit ~/.asoundrc
```
In that file copy and paste the following script. Then save the file:
```
#This asoundrc is a template to create a file that will upmix 2.0 (stereo) files to 5.1 speakers.
#It will also playback real 5.1 sounds, on 5.1 speakers, and also allow the playback of both stereo and surround sources at the same time.
#It may not work out of the box for all cards. If this is the case with your setup, please speak to me (wishie_) in #alsa on irc.freenode.net

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
    type softvol
    slave.pcm "duplex"
    control {
        name "Software Master"
        card 0
    }
}
```

Restart any open sound applications. 5.1 should be working now with your device. If it isn't, log onto #alsa on irc.freenode.net, they will help there if your card requires a different soundrc script.

I'd like to thank wishie_ and gnubien at #alsa and murkyMurk at #ubuntu for all the help.

---

### Post by victorgreen on 2007-10-28
Thanks very much. I have a GWC external usb sound card (5.1). 

I just did a clean install of gutsy so I needed to get this working again. The 1.0.15 drivers really are good. 

Your 5.1 asoundrc failed for me. 

Mine works through a fake 5.1 setup, with 3  2.1 systems connected to each plug on the sound card.

My file looks like this:

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}


Just very simple and it works. Sound comes out all 6 of my speakers and 3 subwoofers.

---

### Post by howardf42 on 2007-11-03
Hi,

I thought I posted a reply a few hours ago but it has never appeared in this thread.  I appologize if this is a duplicate reply.

I've worked through much of your How-to, but got stuck when there was no ./configure file to run in the alsa-tools-1.0.15 folder. Since I'm not a great terminal jockey,  I couldn't figure a way around this problem.  Can you or anyone else help?

Thanks,
Howard

---

### Post by gansao2006 on 2007-11-04
> **victorgreen said:**
> Thanks very much. I have a GWC external usb sound card (5.1). 

I just did a clean install of gutsy so I needed to get this working again. The 1.0.15 drivers really are good. 

Your 5.1 asoundrc failed for me. 

Mine works through a fake 5.1 setup, with 3  2.1 systems connected to each plug on the sound card.

My file looks like this:

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}


Just very simple and it works. Sound comes out all 6 of my speakers and 3 subwoofers.

Aqui funcionou de boa!!! Valew :guitar: Apesar que nao configurei o alsa-tools porque nao tem o ./configure no diretorio.....

---

### Post by kurrrt on 2008-04-09
> **mjkelly said:**
> 
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.15.
Compiled on Oct 18 2007 for kernel 2.6.20-16-generic (SMP).          #These dates on this line will be different. Dont worry about this line.

Make sure that output says 1.0.15.

```
cat /proc/asound/cards
```
If your usb device is listed your in good shape. Mine was not listed and i restarted again and then it was found. I dont have an explanation for this and neither did anyone in #alsa. Try resetting to see if its detected. It should be.
.

I installed the alsa 1.0.15 as described. However My Logitech USB Headset is still not listed, even after a reboot. Has anyone encounter the same problem or have some suggestions?

---

