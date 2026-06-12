---
title: "SPDIF Sound Issue"
date: 2009-03-20
forum: Mythbuntu
---

### Post by Nobodyspeshul on 2009-03-20
Hi all, first time really getting into Linux, I tried Mythdora but I hated it and let my HTPC sit and rot for a few months because I was so frustrated.

Decided to install Mythbuntu and it's visually amazing!  But I'm having the same problem as before with using my SPDIF on my motherboard to get sound out to my receiver, I know the cable is good because I use it with my current DVD player until my mythbox replaces it.

Here are my specs, let me know if you need more information and I'll readily give it since I want this issue resolved.

Mobo:
[Abit AN-M2HD]("http://www.overclockersclub.com/reviews/abit_m2hd/")

I've installed the Linux Ubuntu Realtek sound drivers and followed the sound issues thread setting the Alsamixer volume to the on position, I've redirected the sound settings on the BIOS to what I think is the correct position for the SPDIF to be enabled as well as the settings inside Myth that direct it to use the SPDIF port.

It's showing that the Alsamixer is using the ALC888 device.

Again, I'm a new guy to Linux, but want to learn more.

Thanks!

---

### Post by Dewey_Oxberger on 2009-03-20
Is there no audio at all over the spdif?  Is there static?  Any pops and clicks?

Here is how I'd approach the problem:

1) You'll need the somewhat current NVidia driver.  I'm not sure which driver started supporting spdif (I assume it has been supported for some time).  I'd guess if you use a reasonably current driver it would work.  That means you can use the "envy" script to install the video driver.  (google "envy script", I think you just 
sudo apt-get install envy-ng 
and then 
sudo envy -t 
to install but I can't recall).

You may even need to get the latest nvidia (but I doubt it).  If you do then google "nvidia manual" and you should find a wiki page on installing the nvidia drivers manually.  It has all the mojo for doing it by hand.

2) You need a recent version of alsa.  Ubuntu 8.10 has 1.18 something I think.  That should work.  If you want to upgrade then search these forums for "alsa upgrade script".  It's like envy for alsa.  Nice.

3) The default alsa config should work but your best bet is to tinker by hand to see if you can manually get it going.  Once you know it's working then you know it's just a mythtv configuration problem.

Go to alsa's website and read up on "aplay"

aplay -l   ... this lists the alsa audio hardware devices (giving card#, device#).  You should have a Digital Audio device at Card 0, Device 1.  I think that's the spdif device.

aplay -L   ... this lists all the alsa audio "virtual" devices.  Make sure you have one with the description containing S/PDIF.  Then write down the device name (it is probably named "iec958").

That name is what you set the various device names to (like when using aplay -D devicename or in Mythtv you change the audio device from Default to iec958).

Then have your spdif hardware connected and ready to go and play a sound sample:

aplay -D devicename somefile

There should be sound files in /usr/share/sounds/alsa/

So

aplay -Diec958 /usr/share/sounds/alsa/Noise.wav

Use the tab key to auto complete as you type the path.

Does aplay play noise out the speaker?

---

### Post by Nobodyspeshul on 2009-03-20
No audio at all, I've been using the apple trailers as a test if my sound will play through my speakers.

I'm also using the latest Realtek Audio Drivers for Linux off of their website, it does state that it has spdif support for them.  And the ALC888 is the sound device on the motherboard.

I'll try some of these options when I get home tonight.

---

### Post by Nobodyspeshul on 2009-03-21
So, I was talking to a friend and you can do sound and video through HDMI?

Since you have the same mobo as I do, what settings are you using in the BIOS and in Myth to get this working?

I should have the right drivers installed, and I checked the aplay -L output and I have no S/PDIF device listed.  If I can do the sound/video through the HDMI, I'll just do that.

Thanks in advance!

---

### Post by Nobodyspeshul on 2009-03-22
So I was looking around the forums and the walkthrough here.

[http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto](http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto)

Was a great fixer, everything works great now!

---

### Post by nicoloks on 2009-03-22
My motherboard also has ALC888 onboard sound. I've managed to get the SPDIF working just fine, however I've been battling for weeks trying to get full 5.1 sound. When I play any movie with 5.1 channel DTS or Dolby Digital sound using the hwdts and hwac3 switches in Mplayer I only get 2.1 channels (fronts and subwoofer). The DTS/Dolby Digital indicators on my receiver light up to indicate that there is a valid DTS/Dolby Digital audio stream, however no matter what I do I can only get 2.1 sound.

As you are using the SPDIF interface and also using the exact same sound chipset, I'd be very interested to know if you have been able to get full 5.1 channel sound from your DVD's / Movies?

---

### Post by Nobodyspeshul on 2009-03-23
I ended up using the HDMI for my sound and my video with help from the wiki page listed above.

I'm currently only using 3 speakers, FR, Center, FL.  I'll be adding more when I buy my new place, but I'll deal with it then.

---

