---
title: "Crackling sound in all applications"
date: 2013-02-20
forum: Multimedia Software
---

### Post by elgrandehaxor on 2013-02-20
Hello.

I have looked many places for solutions on this issue, tried all I could find but nothing helped out there. Hope some of ye can give me some tips regarding this. (back on ubuntu after 6 years, forgive me for some weird questions I might ask in the future)

I installed a new clean install of Ubuntu 12.10 recently. My rig is with a ASUS P8P67 Deluxe motherboard. But dug out a headset from Razer, the Razer Megalodon. (it consists of it's own soundcard and is an USB headset)

Here is the problem:

The sound is distorted in all sound applications, it gives a crackling sound on top of the audio. I have tried to alter the daemon.conf and the default.pa "sudo pico /etc/pulse/default.pa" but the only thing I was able to do was to "cut" the sound on one ear and switch that around a few times. 

If there is some extra information that is needed please say so and I will try to get the information needed.

Thank ye all in advance ^^

---

### Post by MrsUser on 2013-02-21
What graphics card do you have? If you have anything Intel related, this might help:
[http://www.webupd8.org/2012/10/how-to-enable-intel-sna-acceleration-in.html](http://www.webupd8.org/2012/10/how-to-enable-intel-sna-acceleration-in.html)

The article has nothing to do with sound really, but the thing is that I had crackling sound as well -- at least in games. It was a coincidence that I found this out for me. However, after I enabled SNA acceleration for my graphcis card (Intel HD), my sound problem disappeared. I really don't know why, but it worked. Didn't have any issues with 12.04, but with 12.10 the problem started. Don't know if this applies to your problem though.

---

### Post by elgrandehaxor on 2013-02-21
I have a NVIDIA GeForce GTX 580.

That is something I would never have thought about, starting to wonder how a graphics card can distort the sound. (not thinking about the spdif or HDMI here)

Thanks for the tip MrsUser, I'll test that as soon as I get home to my rig.

[EDIT]
Tested this out, thought Nvidia was a product witch favoured intel chipsets so thereby thought it would be the same as an intel graphic card. 

I used the "gksu gedit /etc/x11/xorg.conf" line as said and tried to paste:
"Section "Device"         Identifier "intel"         Driver "intel"         Option "AccelMethod" "sna" EndSection"but it couldn't find the file, guess it's not intel enough xD

---

### Post by krishna85 on 2013-02-21
I hope I can post here because I have the very same problem and did not want to create an new thread. 

I have a GTX 580 on Asus P8Z68 V mother board. I have the same cracking/popping sound on any media I play. What I have noticed is that when the speaker/headphones are connected to the audio ports on the back panel there is the popping sounds, but if I connect the same to the front panel the audio is clean, BUT the volume levels keep changing on its own, even if I decrease it, they go up gradually.(I think they go up to just half way to full).

I tried the steps above created the file pasted the lines, logged out and logged back in, unfortunately the popping sound is still there

---

### Post by Shark711 on 2013-05-31
Hi all,
I have a [Razer Megalodon]("http://www2.razerzone.com/Megalodon/") and Ubuntu 12.04.2 LTS (on an [MSI GT780DX]("http://www.msi.com/product/nb/GT780DX-GT780DXR-.html")) with the exact same problem. When I boot up and go to Sound Settings, I see it in the list and everything works. I click the Test Sound Button, this opens the Speaker Testing for Analog Output.
I click any button, all of them works, except it is scratching each time the women says anything (e.g. "Front Left), this is before I even started a game or anything.
Things I have tried (that made it slightly better but not at all resolved) are:
[https://wiki.archlinux.org/index.php/PulseAudio#Glitches.2C_skips_or_crackling](https://wiki.archlinux.org/index.php/PulseAudio#Glitches.2C_skips_or_crackling)
[https://wiki.archlinux.org/index.php/PulseAudio#Choppy_Sound_with_Analog_Surround_Sound_Setup](https://wiki.archlinux.org/index.php/PulseAudio#Choppy_Sound_with_Analog_Surround_Sound_Setup)

The only work-around I got (which works for some time, then goes back to the crackling, scratching):
In the sound settings window I select "Analog Surround 7.1 Ouput", then anything else (test the sound) then go back to "Analog Surround 7.1 Ouput", I repeat this until the crackling stops. This works for about 20 minutes or so, then go back to crackling. If you are lucky this will work for your entire session.

I am curious to find out if anybody got a resolution for this. This is the only Razer peripheral I have that is not working as it should

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1184025](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1184025)

While I searched for this I've also found: [http://blogs.operationaldynamics.com/paul/opensource/razer-megalodon-usb-headsets-and-fedora-or-ubuntu](http://blogs.operationaldynamics.com/paul/opensource/razer-megalodon-usb-headsets-and-fedora-or-ubuntu) which focuses on a lot of things, I did not try everything, but his resolution for the crackling was as per the URLs above I've already tried. I've tried the script as per this post and now I need to replug my device for it to work, oppose to working after reboot

---

### Post by Shark711 on 2014-02-17
Got a solution to my specific issue after a LOT of experimenting:
I run the following 2 commands as root (shut down pulse first and restart once done):
sed 's/; default-sample-rate = 44100/default-sample-rate = 96000/g' -i /etc/pulse/daemon.conf
echo "options snd-usb-audio nrpacks=16" > /etc/modprobe.d/audio-force.conf

---

### Post by sir-marky on 2014-02-17
I have just tried this myself on my new PC.
I was having terrible crackling and popping sounds when playing sound files, although weirdly CDs were fine.
Now I have clear sound.  Although sounds a little deep and bassy on the files I have tried.  Will try with some other tunes but I'm feeling a little more positive.

update - it worked for a while but the crackling is now back :-(

update - This seems to be more common when I'm using the computer than letting it sit and just serve files.  I suspect the cause could be read/write buffers associated with ALAC flies.  I am largely guess there because my evidence is more observable that reproducible. I've increased the readahead cache on the drive with,

[FONT=courier new]sudo blockdev --setra 65536 /dev/sdc[/FONT] to see if it helps.

---

