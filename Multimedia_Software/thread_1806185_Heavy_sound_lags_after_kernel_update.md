---
title: "Heavy sound lags after kernel update"
date: 2011-07-17
forum: Multimedia Software
---

### Post by Nebukadnezar II. on 2011-07-17
Hi there, Ubuntuusers,

After I upgraded from kernel 2.6.32-31 to 2.6.32-32 and then 2.6.32-33, my sound started to lag(the lag occurred on 2.6.32-32 and stayed to 2.6.32-33, but it worked perfectly ever before). 
Sound does work in itself, but frequently lags and pieces that were already played before will be played again, pretty much like an old vinyl that occasionally jumps or hangs. When I start to replay something, it does not put out anything for a second or two and then starts, when I stop it will keep playing for the exact same amount of time. So, sound is synced to videos(video replay works perfectly well and without the lag).
Problem is definitely related to the sound drivers, not to replay software or any buggy file. It occurs with DVDs, Flash Videos in Firefox, music in gmusicbrowser, movie files with VLC, whatever you want. 
I never experienced such problems with any kernel before. Although I've seen many others posting similar problems, I cannot see any valid solution for myself. 

I'm running Ubuntu 10.04 and I sure don't want to go to 10.10 for the second.

I reinstalled Alsa and Pulse, no joy. 
My sound card is recognized correctly by alsa and can be found in aplay -l. It's a generic onboard surround sound device, although I only use stereo channels.

Does anyone have any cool ideas on how to fix that kind of stuff?
Regards and Thanks,
Nebukadnezar

---

### Post by handy on 2011-07-17
If no one offers a workaround you could go back to the kernel that worked before you upgraded it.

---

### Post by RudyG on 2011-07-17
Did you upgrade the kernel through a package manager or by downloading the sources and building yourself?

Rudy

---

### Post by Nebukadnezar II. on 2011-07-17
handy: yes, that is one possibility and I do consider it, but I'd rather fix the problem, that promises to have more future ;)

RudyG: It was installed using apt/synaptic, so it should be reliable.

Regards,
Nebukadnezar II.

---

### Post by lidex on 2011-07-17
Throw some info up here and let's pick at it.
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*
Next use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by handy on 2011-07-18
> **Nebukadnezar II. said:**
> handy: yes, that is one possibility and I do consider it, but I'd rather fix the problem, that promises to have more future ;)

RudyG: It was installed using apt/synaptic, so it should be reliable.

Regards,
Nebukadnezar II.

I'm using 2.6.39-rc6-ARCH-54949-g2a9e586-dirty & it has no problems, so perhaps you could move to a later kernel than the one your using?

There is a good how-to here which covers the xorg-edgers ppa as well, check down in the "Ubuntu stuff" section of the OP:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by Nebukadnezar II. on 2011-07-18
Thanks Handy for the link, but for the second, I'd like to stick to 2.6.32. I have another machine with 2.6.39 installed and it won't run some drivers like the Wacom tablet drivers and stuff, so I'd like to avoid it.

To lidex: followed your instructions. The effects reside, the alsainfo file is attached. Looks pretty correct to my unknowing eyes...

Regards,
Nebukadnezar II.

---

### Post by lidex on 2011-07-18
> **Nebukadnezar II. said:**
> Thanks Handy for the link, but for the second, I'd like to stick to 2.6.32. I have another machine with 2.6.39 installed and it won't run some drivers like the Wacom tablet drivers and stuff, so I'd like to avoid it.

To lidex: followed your instructions. The effects reside, the alsainfo file is attached. Looks pretty correct to my unknowing eyes...

Regards,
Nebukadnezar II.

Didn't get all of it. Can you run the script again, this time choose y at the prompt to upload.

---

### Post by Nebukadnezar II. on 2011-07-18
Sorry. I ran the script with the --upload option, this is the link:
[http://www.alsa-project.org/db/?f=bb444e50d1f79a818c9f5d42480f716371fe809d](http://www.alsa-project.org/db/?f=bb444e50d1f79a818c9f5d42480f716371fe809d)
Funny though, I ran both options and the file it outputs does not contain all the information that are uploaded to alsa-project.org. 

Regards,
Daniel

---

### Post by lidex on 2011-07-18
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=6stack-dig" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**
Set your channel element in alsamixer to 8ch, then check your profile setting in 'Sound Preferences'

---

### Post by Nebukadnezar II. on 2011-07-18
okay. executed the command(returned the command, basically), rebooted, set it to 8 channels in alsamixer and changed the sound profile for the internal sound card to analog surround 5.1 output with no inputs (from analog stereo duplex).
Still lags. Feels like it's lagging less, but that might as well be wrong. 

Regards,
Daniel

---

### Post by lidex on 2011-07-18
This may take some trial and error. Edit the alsa-base.conf line we added earlier:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Change this:
```
options snd-hda-intel model=6stack-dig
```
To this:
```
options snd-hda-intel model=6stack-dig enable_msi=1
```
Save. Close. Reboot.

---

### Post by Nebukadnezar II. on 2011-07-19
did it.no joy, sorry. 
Thank you for your patience, anyway!

Regards,
Daniel

---

### Post by Nebukadnezar II. on 2011-07-22
hmm...although this is not exactly a solution that seems plausible, reinstalling the exact same kernel fixed the problem, as it seems. I had tried to upgrade to a higher version, failed to get all my drivers working, downgraded again and bam - problem erased. weird. 

Anyway, that's it. Thanks for the help.

Regards,
Daniel

---

