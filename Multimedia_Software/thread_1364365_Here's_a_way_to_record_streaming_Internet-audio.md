---
title: "Here's a way to record streaming Internet-audio"
date: 2009-12-25
forum: Multimedia Software
---

### Post by Leafshooter on 2009-12-25
I suspect many folks would like to record audio from youtube, streaming radio stations, and other sources on the Internet. You could simply connect Line-Out to Line-In on the back of your computer, but you lose a little quality that way. Here's a method I've found that works well on both of my computers (with Ubuntu 9.04 and 9.10), using Audacity. I was not able to get the simple Sound Recorder to do this, but Audacity records well.

The essence is to change the default audio-source used by the Pulse Audio sound-server system, which you do by specifying the environment variable PULSE_SOURCE. You want Pulse Audio to use the monitor of the audio-output. A "monitor" is an input-device which is simply a loop-back of the output-device, and can be used for displaying output levels. One can also record from it, which is what we will do.

You will need to use the CLI (Command Line Interface) in a terminal (Applications->Accessories->Terminal). Here are the details:

To get the name of your monitor, type this command:[INDENT]     pactl list | grep monitor
[/INDENT]On my computer with a Sound Blaster Live! card, the output is:[INDENT]     Monitor Source: alsa_output.pci_1102_2_sound_card_0_alsa_playback_0.monitor
[/INDENT][INDENT]     Name: alsa_output.pci_1102_2_sound_card_0_alsa_playback_0.monitor
[/INDENT][INDENT]     device.class = "monitor"
[/INDENT]So the name of the monitor-device on my computer is:[INDENT]     alsa_output.pci_1102_2_sound_card_0_alsa_playback_0.monitor
[/INDENT]Knowing that name, edit the file /etc/environment by typing:[INDENT]     sudo nano /etc/environment
[/INDENT]In the nano editor, add the following line to the bottom of the file:[INDENT]     PULSE_SOURCE=alsa_output.pci_1102_2_sound_card_0_alsa_playback_0.monitor
[/INDENT]But use the name of your monitor instead. In nano, you use control-characters (shown at the bottom) to do operations. Press ^O (control-O) to "output" (write) your change, and then ^X to exit.

It's also a good idea to tell Audacity to use Pulse. Open Audacity, then click Edit->Preferences, and then click Audio I/O in the left pane. Change the host (if it's shown) to ALSA, and change Recording Device to "pulse" or "ALSA: pulse".

After making the above changes, reboot the computer, which will add PULSE_SOURCE to the environment variables. Then Audacity should record whatever is being sent to Line-Out.

---

### Post by tgalati4 on 2009-12-25
or install streamripper

---

### Post by Leafshooter on 2009-12-26
> **tgalati4 said:**
> or install streamripper

I tried streamripper first, and it only appears to work with shoutcast-type radio broadcasts, and not with other types of audio-sources such as flash video or other types of radio. That's what drove me to find a general solution.

---

### Post by startling on 2009-12-28
Hi Leafshooter, and many thanks for your Howto. 

Unfortunately it hasn't worked for me. Even after a reboot Audacity does not list Pulse as an option. (Audacity seems to be rather flaky for me - I used Synaptic to install it on 8.10 and it installed 1.3.5-beta which seems an odd thing to do! I'd have thought it sensible to install a stable version but there you go...) An Audacity readme I saw refers to a pull-down menu on the mixer toolbar but there is no pull-down menu on my installation! It's all very frustrating.

Is there another program that can record flash-type streaming audio, or a way to get Audacity behaving itself?

---

### Post by Leafshooter on 2010-01-01
I read that Audacity added pulse-support relatively recently, within the last year or two. Also, Ubuntu added Pulse-support around 8.04 or 8.10. You mention 8.10, so I'm wondering if an upgrade would help. I've tried this pulse-trick on 9.04 and 9.10, but nothing earlier. Good luck.


> **startling said:**
> Hi Leafshooter, and many thanks for your Howto. 

Unfortunately it hasn't worked for me. Even after a reboot Audacity does not list Pulse as an option. (Audacity seems to be rather flaky for me - I used Synaptic to install it on 8.10 and it installed 1.3.5-beta which seems an odd thing to do! I'd have thought it sensible to install a stable version but there you go...) An Audacity readme I saw refers to a pull-down menu on the mixer toolbar but there is no pull-down menu on my installation! It's all very frustrating.

Is there another program that can record flash-type streaming audio, or a way to get Audacity behaving itself?

---

### Post by startling on 2010-01-02
Thanks again Leafshooter. After a lot of searching I found another way! In case it's helpful to anyone else, here it is:
Over at linuxquestions.org someone posted this:

[I]you can just use the arecord program (which is part of the ALSA utilities). For example:
Code:[/I]
```
**arecord -f cd -d 15 myrecording.wav**
```

The full thread is here: 
[http://www.linuxquestions.org/questions/linux-software-2/recording-radio-using-sox-606378/]("http://www.linuxquestions.org/questions/linux-software-2/recording-radio-using-sox-606378/")

---

