---
title: "Listen to USB Turntable - how to reroute input to output"
date: 2009-11-06
forum: Multimedia Software
---

### Post by Labello on 2009-11-06
hello everybody,

i spent several hours last night on being able to listen to the music that my usb turntable plays. it is properly recognized by the system and i can set the recording volume with the gnome volume mixer. moreover i have been able to record the input via audacity, but thats noch what i wanted.

all i need is a small tool that is able to direct my input directly to the speakers. something like a monitoring option. but i don't want to install pulseaudio since i am running on crunchbanglinux which is a derivative of ubuntu, but which wants to stay as slim as possible. moreover pulseaudio would mess up my skype and mumble configuration.

so i need a programm that does not depend on pulse and that is able to direct the input from usb to my speakers/headphones. it could also be a little script or some commandline-app. i would not care. i just want to get my turntable working =)

thanks in advance!

labello

---

### Post by aquavitae on 2009-11-06
Not sure if it will work, but maybe try jack.

---

### Post by Labello on 2009-11-06
> **aquavitae said:**
> Not sure if it will work, but maybe try jack.

Thanks for the advice but I already tried this. But maybe I did something wrong. To be honest I was already expecting "Jack" to be the first answer. Moreover I could not find any helping documentation concerning Jack's setup =(.

I mean it can't be that hard that I have got to use Jack for this simple task. But I would be glad if it worked anyhow -.-

---

### Post by Labello on 2009-11-06
Well I finally found a solution! And to be honest: I LOVE LINUX!

Solution one is rather simple:

```
sudo cat /dev/dsp1 > /dev/dsp
```

Solution two is to install the programm "ecamegapedal". start it, select input and output and hit play. and voila you will be hearing your input. you can even apply some filters.

so maybe this thread is some of a helpfor some others!

---

### Post by aquavitae on 2009-11-06
I found that the qt frontend for jack (qjackctl I think) made the setup quite easy, but the one line command is certainly a much simpler solution!  I think I'm using windows too much since it even occur to me to look for something like that!

---

### Post by Labello on 2009-11-06
Could you please preovide your setup within jack? i would also like to try this one! thanks in advance

---

### Post by aquavitae on 2009-11-09
Sorry about the late reply - been away.

I don't actually have jack set up at the moment, but I used it a couple of months ago to route a digital piano through the computer.  I was experimenting with fluidsynth and rosegarden, so most of the time my set up was quite complicated, but at one stage I had the piano just playing directly out of the computer speakers (but through midi).  IIRC, there is a dialog in qjack which allows various connections to be made between inputs and outputs, both midi and raw audio. So in your situation you should be able to connect the turntable input to alsa output.

---

### Post by russellnation on 2010-11-13
This solution had helped me out a while back, but now with 10.10 it no longer works.

Here's how I got it back.

First install paman (pulse audio manager)

```
sudo apt-get -y install paman
```

open it up (just type paman in terminal if it's not in your menu)

Click on the **Devices** tab and look for the **Sinks** area, this is your output, then in the **Sources** area find your device.

[Visual Aid]("http://i.imgur.com/zedhx.png")

Then use pacat to connect the two. Mine looked like this.

```
pacat -r -d alsa_input.usb-AKM_AK5371-00-default.analog-stereo | pacat -p -d alsa_output.pci-0000_00_10.1.analog-stereo
```

To make a launcher that either launches or disables the pacat command copy this into a file

```

#!/bin/bash

SERVICE='pacat'
 
if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    killall pacat
else
    pacat -r -d alsa_input.usb-AKM_AK5371-00-default.analog-stereo | pacat -p -d alsa_output.pci-0000_00_10.1.analog-stereo
fi

```

save it somewhere (i saved mine as vinyl.sh), cd to the folder where the script is and make it executable.

```

cd ~/Scripts
chmod 0777 vinyl.sh

```

and add the script in the Command field of the Launcher Properties box.

---

### Post by paultag on 2010-11-13
Reddit love, rock on my man. Thanks for updating this :)

---

