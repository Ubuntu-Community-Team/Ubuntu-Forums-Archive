---
title: "Installing Alsa on Compaq Presario"
date: 2017-06-25
forum: Multimedia Software
---

### Post by angel mike on 2017-06-25
Have a built-in Intel HDA sound card on Compaq Presario but no sound. OS Ubuntu 16.04 and have downloaded the latest Alsa from the daily snapshot site and disabled the sound card from the BIOS.
Any further things that I should do ?

---

### Post by Autodave on 2017-06-25
I am a little confused. How did the sound card get disabled in the BIOS: did you do that?  What happens when you enable it in the BIOS?

---

### Post by angel mike on 2017-06-25
Sound did not work before I disabled the internal card - then used the 'advanced' option in the top line menu then scrolling down to 'Audio'.
One comment I have just picked up is that the daily build version must match the OS version which it does not. The only daily build version available  is for Ubuntu 16.04.1 but my OS is version 16.04.2 ! It seems crazy that you have to keep changing. Is there a generic ALSA version that would suffice I wonder ?
Thanks for responding Autodave

---

### Post by Autodave on 2017-06-25
What version of Ubuntu are you running?  Did you try to turn the sound on in the BIOS?

---

### Post by angel mike on 2017-06-26
The latest version Ubuntu 16.04.2. To get back to 16.04.1 I would have to re-install and presumably prevent the updater from working. But if I stayed with 16.04.1 I would miss out in any future security updates ! No sound with in-built audio on or disabled using the BIOS entry.

---

### Post by Bucky Ball on 2017-06-26
16.04.2 is fine. That has ALSA by default. You need to enable the sound card in BIOS or how are you going to hear anything? That should only be disabled if you have a separate sound card installed that is not part of the motherboard.

You have not been specific about exactly what your issue is. Have you installed Pulseaudio Volume Control and had a look there? I'm guessing you need to tweak with input and output ports.

As I say, ALSA and Pulse should be ready to go by default in a Ubuntu install. No need for re-installing ALSA from elsewhere. May just confuse the issue. Unless you are not using a stock standard Ubuntu install.

When posting for support, help us help you by giving as much info as possible, like the release you are using, what you've tried, and where you're at. For now, suggest you install Pulseaudio Volume Control (in the repositories), get some music going, open PAVControl and look at the output and playback tabs. See any sound bouncing up and down on the level meters? If so, everything is probably fine and you need to tweak your output/playback port.

---

### Post by angel mike on 2017-06-26
Thanks Bucky Ball for that - will try to make amends and follow your suggestions. Having installed a Alsa from the daily snapshot site I presume I should delete it? Mike

---

### Post by Bucky Ball on 2017-06-26
Did you add a repository (PPA) for the newest ALSA? Please provide a link to where you got it. 

If the ALSA version must match the kernel version and it doesn't, then yes, uninstall. Make sure you have the sound card enabled in BIOS, follow the previous about PAVControl and see if you get any sound. If you see the audio bouncing on the level meter, that is a good sign. Let's see if it works as things are.

You may need to reinstall the old ALSA to get things going.

Which release and flavour of Ubuntu are you using?

* Note: This is my ALSA version on 16.04.2.

```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version k4.4.0-81-generic.
```

FWIW, same as kernel:

```
$ uname -a
Linux tosh 4.4.0-81-generic #104-Ubuntu SMP Wed Jun 14 08:17:06 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```


Open a terminal and run:

```
cat /proc/asound/version
```

What do you get?

---

### Post by angel mike on 2017-06-26
Thanks Bucky Ball for that useful addition - bear with me while i try things out - nice to have the guidance. Using Ubuntu 16.04.2 LTS Xenial Xerus 
The Alsa Daily Snapshot Link is [https://launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily](https://launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily). I used the 16.04.1 version. Thanks.
Will now try your suggestions. Mike

---

### Post by angel mike on 2017-06-26
Have enabled Audio in BIOS.
Installed Pulseaudio Vol Control
Inserted music CD with Rythmbox -- and audio is bouncing on the level meter!
Ran the commands you suggested plus a few others.
```

michael@michael-RF786AA-ABU-SR2019UK-GB680:~$ sudo cat /proc/asound/version
[sudo] password for michael: 
Advanced Linux Sound Architecture Driver Version k4.4.0-81-generic.
michael@michael-RF786AA-ABU-SR2019UK-GB680:~$ uname -a
Linux michael-RF786AA-ABU-SR2019UK-GB680 4.4.0-81-generic #104-Ubuntu SMP Wed Jun 14 08:15:00 UTC 2017 i686 athlon i686 GNU/Linux
michael@michael-RF786AA-ABU-SR2019UK-GB680:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfcffc000 irq 16
michael@michael-RF786AA-ABU-SR2019UK-GB680:~$ lspci -v|grep -i audio
02:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
    Subsystem: ASUSTeK Computer Inc. High Definition Audio Controller
michael@michael-RF786AA-ABU-SR2019UK-GB680:~$ cat /proc/asound/devices
  1:        : sequencer
  2: [ 0]   : control
  3: [ 0- 3]: digital audio playback
  4: [ 0- 7]: digital audio playback
  5: [ 0- 8]: digital audio playback
  6: [ 0- 9]: digital audio playback
  7: [ 0- 0]: hardware dependent
  8: [ 0- 1]: hardware dependent
  9: [ 0- 2]: hardware dependent
 10: [ 0- 3]: hardware dependent
 33:        : timer
michael@michael-RF786AA-ABU-SR2019UK-GB680:~$ 

```
When I installed the ALSA snapshot I started with this link [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS) and installed DKMS

---

### Post by Bucky Ball on 2017-06-26
Well, that looks good. You are now getting sound out? If not, you may need to tweak with ports in the 'Ouput Devices' tab.

---

### Post by angel mike on 2017-06-27
Addional info - do not have Pulse Audio installed - only output listed on PAV is 'HDMI

---

### Post by angel mike on 2017-06-28
Still no sound.
Although the PAV registers sound if I go to ,Output Devices' the only option available is HDMI (Unplugged). 
What does this indicate ?

---

### Post by Bucky Ball on 2017-06-28
In the PAVControl 'Configuration' tab you have the correct HDMI device selected in the 'Profile' drop-down in the first, or top, port and the second port below that set to 'Analogue Stereo Duplex'?

---

### Post by angel mike on 2017-06-28
Thanks for coming back Bucky Ball
The list under the config tab is .Digital Stero (HDMI) Output(unplugged)
then the list continues with HDMI 2,3,4 variations
Then there is a series of Digital Surround 7.1 and 5.1 options all unplugged.
The 'off'
No Analogue.
All I am using is two small Logictech speakers 
Thanks Mike

---

### Post by angel mike on 2017-06-28
Not using HDMI connection just audio jack in 'green' port Mike

---

### Post by Yellow Pasque on 2017-06-28
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by angel mike on 2017-06-28
Thanks Temujin - here is the alsa info link [http://www.alsa-project.org/db/?f=3ad857dab1183e99b3d00307066b668b2d50a230](http://www.alsa-project.org/db/?f=3ad857dab1183e99b3d00307066b668b2d50a230)

Also I just remembered I upgraded the graphics card with ASUS Geforce 210
Thanks Mike

---

### Post by Yellow Pasque on 2017-06-28
It still looks like you have the onboard audio disabled in the BIOS, because it's not even showing up in lspci. I'm very confused as to what you're trying to do.

> Using Ubuntu 16.04.2 LTS Xenial Xerus 
You're still running the 4.4.x kernel from Ubuntu 16.04.1 (and that's okay, as it will be updated with security and bug fixes for the life of Xenial). DO NOT prevent the updater from running.

> The Alsa Daily Snapshot Link is .... I used the 16.04.1 version.
Like I said, you're still using the 4.4.x kernel. So if you're trying to pick an ALSA dkms module, you should use 16.04.1. I do agree their naming is confusing though.
But but but, we're getting ahead of ourselves. You need to get the device enabled in the BIOS and showing up in lspci before you can worry about updating ALSA. For a machine of this age, it shouldn't be necessary to upgrade ALSA anyway.

---

### Post by angel mike on 2017-06-28
I have just checked the BIOS and Onboard Audio was set to 'Auto'. There are three options Disable/Enable/Auto. 
I changed to 'enabled' but has not made any difference. Which one should it be. 
I do have an upto date Dell laptop XPS but the Compaq desktop has a dvd slot and I like to use it for MIT lectures !
Mike

---

### Post by Yellow Pasque on 2017-06-28
Set it to enable.

---

### Post by angel mike on 2017-06-28
I checked the Linux Kernel version on my Dell which has 16.04.2 installed and it showed the 4.4 version. I should get automatic updates but I used the 'Updater' and got the same result - yet I note that 16.04.2 is supposed to have 4.8 so I'm confused as well! 
Mike

---

### Post by Bucky Ball on 2017-06-28
```
sudo apt update
sudo apt full-upgrade
```

... should get you to the correct kernel on 16.04.2, but this has nothing to do with the topic of this support thread. Different computer, unrelated issue. Discussing two different issues on two different computers in one thread only ever gets confusing. ;)

---

### Post by angel mike on 2017-06-29
Thanks Bucky Ball - noted. sorry about that.
I think I have a spare PCI slot so would installing a separate sound card possibly solve the problem ?

---

