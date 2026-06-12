---
title: "No Sound, Soundcard...Kind of Detected?"
date: 2012-02-03
forum: Multimedia Software
---

### Post by Tk007LwZFJW5ej on 2012-02-03
```
aplay -l
``` with/without sudo gives ```
aplay: device_list:240: no soundcards found...
```

I've tried following the sound troubleshooting guide here:

[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

following procedure Ac. 

```
echo "Sound cards recognized by the system:"; lspci -nn | grep --color=none '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done; echo "Sound cards recognized by ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done

```

```
Sound cards recognized by the system:
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
Sound cards recognized by ALSA:
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
Sound cards recognized by ALSA, and activated:
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)

```

So, I tried to make sure appropriate modules for my system, but I get the error that they aren't found. The system is updated and upgraded. I tried to check to see if alsa supports my soundcard here:

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

I'm not sure if I'm reading it correctly, but it doesn't look like my soundcard is supported.

What else can I do?

---

### Post by Hasues on 2012-03-05
I never saw a response on this.  I'm not sure the Ubuntu way of attacking this problem, but I can say with the PCI Id's you listed, you could verify the kernel modules are loaded by doing:

$ lsmod |grep snd_hda_intel                                           
snd_hda_intel          20923  4 
snd_hda_codec          58907  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_pcm                70598  6 snd_pcm_oss,snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd                    52264  26 snd_seq_oss,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq_device,snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm,snd_timer
snd_page_alloc          6841  2 snd_hda_intel,snd_pcm

Also, I'm not sure if you have the module loader configured, but you can configure this with alsa's utilities using /usr/sbin/alsaconf.

Depending on where Ubuntu stores its module loader configuration, there should be a file alsa.conf in /etc in either an /etc/modprobe.d/alsa.conf or somewhere similar.  The alsaconf utility should modify this file.  However, if one was to do it by hand, it could have configuration such as:

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss
options snd cards_limit=2

However, this will vary depending if you have OSS support enabled and a few other factors, but that is where I would look if I were in your shoes.  I'm only posting here as I was looking for other information, and I noted no one ever answered this question.  I thought it might put one in the right direction.

If you are compiling your own kernel, I would suggest looking for CONFIG_SND_HDA_INTEL and choosing from those options.

Hope this helps...

Has

---

### Post by Tk007LwZFJW5ej on 2012-03-07
Thanks but I forgot to mark this solved. The problem disappeared after my kernel was updated.

---

### Post by Vaibhav089 on 2012-03-11
I have a Dell Vostro 1540 running Ubuntu 10.10.
I am not getting any sound from the laptop speakers. The headphone jack is working fine. But I need to fix this! Last time I had this problem, I had to re-install Ubuntu. I don't want to do that again! :(
Is there a fix?
Someone please help! :(
P.S. I am new with linux but I am familiar with the use of Terminal in case I need to run some commands.
Any kind of help is appreciated!

---

### Post by HoTMetaL on 2012-03-11
> **Vaibhav089 said:**
> I have a Dell Vostro 1540 running Ubuntu 10.10.
I am not getting any sound from the laptop speakers. The headphone jack is working fine. But I need to fix this! Last time I had this problem, I had to re-install Ubuntu. I don't want to do that again!

Vaibhav089: I've been wrestling with this problem for two days now on a brand new *Ubuntu-certified* Dell Vostro 1540. Here's what I've learned so far:
[LIST]
[*]Audio from speakers *does not work* in Ubuntu 10.04 LTS, but headphone jack works.
[*]Audio from speakers *does not work* in Ubuntu 10.10, but headphone jack works.
[*]Audio appears to be _fully working_ in 12.04 LTS beta 1 (download it [here: link]("http://cdimage.ubuntu.com/releases/precise/beta-1/")).
[*]This laptop uses a less-common audio codec (IDT ID 76d1) which is unsupported in ALSA <1.0.25.
[*]The pre-installed 10.10 image from Dell *had* working audio, but I need to run 10.04 instead (and I didn't backup Dell's Ubuntu respin to analyze the differences).
[/LIST]
As a temporary workaround until 12.04 becomes mature and I decide that I can tolerate Unity, I'll use external speakers for laptop audio on the Vostro 1540. **No** amount of adjusting the *snd-hda-intel* audio driver options has worked. You may want to delve into upgrading the ALSA driver for 10.10, but that is *way* more advanced than I can cover here *(and probably not worth the effort/risk).*

---

### Post by acc61287 on 2012-03-11
> **Vaibhav089 said:**
> I have a Dell Vostro 1540 running Ubuntu 10.10.
I am not getting any sound from the laptop speakers. The headphone jack is working fine. But I need to fix this! Last time I had this problem, I had to re-install Ubuntu. I don't want to do that again! :(
Is there a fix?
Someone please help! :(
P.S. I am new with linux but I am familiar with the use of Terminal in case I need to run some commands.
Any kind of help is appreciated!

try installing pavucontrol:
sudo apt-get install pavucontrol

---

### Post by HoTMetaL on 2012-03-11
> **acc61287 said:**
> try installing pavucontrol:
sudo apt-get install pavucontrol
Installing Pulseaudio Volume Control does not solve the audio issue with the Dell Vostro 1540. It has been tried.

---

### Post by Tk007LwZFJW5ej on 2012-03-11
> **Vaibhav089 said:**
> I have a Dell Vostro 1540 running Ubuntu 10.10.
I am not getting any sound from the laptop speakers. The headphone jack is working fine. But I need to fix this! Last time I had this problem, I had to re-install Ubuntu. I don't want to do that again! :(
Is there a fix?
Someone please help! :(
P.S. I am new with linux but I am familiar with the use of Terminal in case I need to run some commands.
Any kind of help is appreciated!

I suggest you make a new thread. This thread being marked solved, people with solutions to offer you are not likely to be looking here.

---

