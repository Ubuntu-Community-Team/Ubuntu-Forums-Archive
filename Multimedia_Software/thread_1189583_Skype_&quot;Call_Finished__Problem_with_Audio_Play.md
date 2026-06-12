---
title: "Skype &quot;Call Finished:  Problem with Audio Playback&quot;"
date: 2009-06-16
forum: Multimedia Software
---

### Post by pwrcul on 2009-06-16
I installed 9.04 some weeks ago and am still trying to get the functionality I am used to under Win XP.

I installed Skype this afternoon.  I used the direct download from Skype.com and GDebi installer after adding the Medibuntu repository and key but without success in getting Skype itself to show up in Synaptic.  I had followed this guide:
help.ubuntu.com/community/Skype and pages it referred to.

After the GDebi install, I started Skype and called echo123 and another friend's Skypename and got the same message in a little window from Skype:   "Call Finished:  Problem with Audio Playback"

I opened Preferences->Sound to test what is working:  The top 3 options set to "Autodetect" (Events, Music, Conferencing) all work, i.e., generate sound.  The 4th for Conferening when set to ALSA and PulseAudio are silent when tested.

I used Synaptic to verify both ALSA and PulseAudio are installed.  They are there with a good number of their support packages that comes from the install of 9.04 Live CD.

I suspect there may be a solution in the Comprehensive Sound Solutions Guide, but it may even be simpler.  If someone can point out the relevant section in the Comprehensive or suggest a simple fix I would be grateful.

---

### Post by Pressondude on 2009-06-16
I have been having a similar problem, although I installed through Synaptic. What's odd is that my microphone recieves in other programs (including google talk) but not in Skype.....I'm thinking that it might be a Skype bug...

---

### Post by brigid walsh on 2009-06-17
I also have the same problem and would like help to put it right.

Thanks

---

### Post by kebabbaro on 2009-06-18
> **brigid walsh said:**
> I also have the same problem and would like help to put it right.

Thanks

Add me to the party: i have the same problem.
And I'd really appreciate any feedback about it.

KEB

---

### Post by xc3RnbFO8P on 2009-06-18
In Option> Sound Devices, did you try to change input source
Example:
In Ubuntu I use HDA Intel (hw:intel.0)

Change the input source,  Apply and make test call.

---

### Post by kebabbaro on 2009-06-19
> **Ringi said:**
> In Option> Sound Devices, did you try to change input source
Example:
In Ubuntu I use HDA Intel (hw:intel.0)

Change the input source,  Apply and make test call.

Thank you, that almost fix my problem: now my mic gives me a low volume playback, but at least the sound is working and i can make calls.

Thanks again
KEB

---

### Post by pokeyThePenguin on 2009-06-19
I kept having audio playback problems too.

I solved the problem by uninstalling pulseaudio and installing esound.

---

### Post by psyke83 on 2009-06-19
If you haven't uninstalled PulseAudio, see my guide (there's specific instructions to configure Skype correctly).

---

### Post by psyke83 on 2009-06-19
> **pokeyThePenguin said:**
> I kept having audio playback problems too.

I solved the problem by uninstalling pulseaudio and installing esound.

Just FYI, esound is unsupported and very few applications use it nowadays.

---

### Post by fester225 on 2009-06-21
I'm having the same problem in Ubuntu 9.04. In addition to tricks other posters have suggested, I also did an apt-get build-dep skype, but the system said it couldn't find the source package.

---

### Post by Andavane on 2009-06-29
> **Ringi said:**
> In Option> Sound Devices, did you try to change input source
Example:
In Ubuntu I use HDA Intel (hw:intel.0)

Change the input source,  Apply and make test call., 

I had the same problem and this solution solved the problem completely.
I am on an EeePC 9.04 and I have folowed the upgrade path to Jaunty.

Thank you,

Regards

John

---

### Post by Decoy on 2009-07-04
'pulse' devices work for me.
Cheers.

---

### Post by fester225 on 2009-07-05
I too went to Options> Sound Devices. After changing the default in and out devices, now it works fine.

---

### Post by arnoldjames on 2009-07-05
I had this problem also.  My solution was to run "alsamixer" in a console and turn everything up to max and then reopen skype.  I also had to have pulse as audio.  Then I had to lower microphones in alsamixer due to feedback, but it did work.  I think the versions of skype are not yet tweaked. I'm getting intermittent camera not detected also.  They will undoubtedly fix it up in the near future.

---

### Post by Paddy Landau on 2009-07-08
To get it to work for me, I went into *Skype -> Options -> Sound Devices*.

I had to set all three of *Sound In*, *Sound Out* and *Ringing* to "HDA Intel (hw:Intel,0)".

---

