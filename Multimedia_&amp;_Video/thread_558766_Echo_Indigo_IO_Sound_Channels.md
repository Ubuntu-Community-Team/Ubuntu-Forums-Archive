---
title: "Echo Indigo IO Sound Channels"
date: 2007-09-24
forum: Multimedia &amp; Video
---

### Post by iggee85 on 2007-09-24
I got the Echo Indigo IO to work but I was wondering if anyone had any idea on how to setup the sound channels in alsamixer. Right now, I got Vmixers 0,1,8,9 unmuted but I'm not sure if I'm supposed to have 4 channels open. 
There is a sound difference if I mute one channel. Vmixers 0,1 control the left while 8,9 control the right. Any additional info would be welcome.

---

### Post by Rob_Frohne on 2007-09-25
Hi,

I think you need to install the alsa-utils package and then from the terminal execute echomixer.

Now, maybe you can help me...  I can't get the Indigo IO to work.  What did you do to make it work.  I have installed all the ubuntu studio packages, and all the alsa packages except the source and alsa players.

I can see it in lspci, but echomixer says no echo sound cards found, and I don't see it in the Sound preferences.

Thanks,

Rob

---

### Post by iggee85 on 2007-09-26
Oh ok, I'll tell you exactly how I got it to work on my system. I'm running Kubuntu on a laptop with onboard Intel HD sound. I looked at these two pages to get it to work:

[https://help.ubuntu.com/community/EchoMia]("https://help.ubuntu.com/community/EchoMia")
[http://www.alsa-project.org/main/index.php/Matrix:Module-indigoio]("http://www.alsa-project.org/main/index.php/Matrix:Module-indigoio")

And then I figured out what I needed to do to get the card to work. Be warned, I built alsa up from source, I didn't use any prebuilt packages so make sure you have "build-essential" package installed.
First, I downloaded and extracted the source for alsa-driver:

```

cd /usr/src
sudo mkdir alsa
cd alsa
sudo wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
sudo tar xvf *driver*

```

Then you have to figure out what modules you need when you build alsa, in my case they were hda-intel and indigoio:

```

cd *driver*
sudo ./configure --with-cards=hda-intel,indigoio --with-oss=yes --with-sequencer=yes
sudo make
sudo make install

```

Then I repeat the steps with the alsa-firmware except you don't need any options for configure:

```

cd /usr/src/alsa
sudo wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.14.tar.bz2
sudo tar xvf *firmware*
cd *firmware*
sudo ./configure
sudo make
sudo make install

```

Then to make sure Intel HD was default and Echo Indigo IO was secondary you edit:

```

sudo nano /etc/modprobe.d/alsa-base

```

And add these to the end, if you want you can reverse it to make the Indigo the default:

```

options snd_hda_intel index=0
options snd_indigoio index=1

```

And when you reboot, both your cards should be detected.
Now let's say in Amarok you want to output to card 1 instead of card 0 you would go to Settings->Configure Amarok->Engine 
Select Output plugin->alsa then in Stereo instead of "default" put in "plughw:1,0"

---

### Post by Rob_Frohne on 2007-09-26
Thanks, I did it from source, and it works now.  

I also found to make the suspend to ram work correctly with the Indigo IO I had to modify the files in /etc/acpi/suspend.d/

I renamed the 85-alsa-state.sh to 40-alsa-state.sh and changed the contents of that file to:

 #!/bin/sh

# Save the ALSA state
if [ -x /etc/init.d/alsa-utils ]; then
  /etc/init.d/alsa-utils stop
fi
if [ -x /etc/init.d/alsasound ]; then
  /etc/init.d/alsasound stop
fi

Maybe this wil help you too.  I have been using a Dell Latitude D600.

Thanks,

Rob

---

