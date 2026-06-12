---
title: "a lot of trouble with MIDI"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by JungleJoker on 2007-08-23
Hi, I've made the windows-linux change just a couple of weeks ago and although I absolutely love the simplicety and stability of Linux Ubuntu, I just can't get MIDI sounds to work. I've tried about any tutorial i could find but no help. Just a moment ago, I Installed EasyUbuntu, which said that MIDI was already installed. But I don't hear any sounds comming out!

ANY help would be much appreciate it (but don't forget you're dealing with quite the linux-n00b)

---

### Post by Gwasanaethau on 2007-08-23
Hmmm, this might be a long one, but hopefully I might be able to help a little bit (I had problems setting up MIDI on my Ubuntu installation too).

First of all, you need to find a Sound Font. There are many places on the web that you can get them from (unfortunately I can't remember where I got mine from).

Next, you need to install some items from the repositories. In your terminal (assuming you're using Ubuntu rather than any of the derivatives), type in:
```
sudo apt-get install alsa-base libasound2 libasound2-dev alsa-oss alsa-source awesfx
```
Then you need to check that everything is set up for MIDI; type in:
```
lsmod | grep snd
```
and check the list for all of the following:

snd_seq_midi
snd_emu10k1_synth
snd_emux_synth
snd_ seq_oss
snd_seq
snd_emu10k1
snd_rawmidi

Once you've checked that everything's OK, you need to start your sound-font. Type in:
```
sfxload /path-to-sound-font
```
Lastly, you need to install a MIDI player (I recommend pmidi):
```
sudo apt-get install pmidi
```
You then need to find out which ports pmidi can play from by using:
```
pmidi -l
```
To play the file, simply use:
```
pmidi -p n:n [midi-file]
```
where n:n is any of the numbers from the previous command.

I know it's long-winded, but I hope it helps a bit!

---

### Post by kissg1988 on 2007-08-23
you can find a lot of high quality sound fonts here: [http://www.sf2midi.com/](http://www.sf2midi.com/)

I recommend the SF of the Kawai Grand Piano, it sounds wonderful.

---

### Post by JungleJoker on 2007-08-24
So I tried the "lsmod | grep snd" command and got this:

snd_rtctimer            4384  1 
snd_usb_audio          79744  0 
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_usb_lib            17280  1 snd_usb_audio
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_hwdep               9988  1 snd_usb_audio
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  15 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
usbcore               134280  8 snd_usb_audio,snd_usb_lib,usblp,usb_storage,libusual,ehci_hcd,ohci_hcd

now, being the n00b that i am, i'm guessing that something isn't OK. But to be honoust, this stuf looks a bit like chinese too me :s Any help?:confused:

BTW: I wan't to install MIDI because I would like to use either Guitar Pro (using Wine) or Kguitar and be able to hear the MIDI sounds

---

### Post by Gwasanaethau on 2007-08-27
Hi there,

First of all, apologies for taking so long to get back to you.

I've finally found the page that I used to get MIDI working on my computer - would you believe it but it's actually a thread from this very forum! The link is [here]("http://ubuntuforums.org/showthread.php?t=8736"). Unfortunately, my Linux programming skills aren't exactly up to scratch, so I don't really understand what it all does. All that I know is that I followed the instructions in it and I was able to play MIDI!

Looking at the results of the 'lsmod…' command, it looks like you're missing the following modules:
snd_emu10k1_synth
snd_emux_synth
snd_emu10k1

I believe you can add them by using 'sudo modprobe', but I strongly recommend you take a look at the other thread first just to be sure!

---

### Post by JungleJoker on 2007-08-29
Thnx for all the help, my midi sounds still aren't playing the way they should, but I tried installing TuxGuitar and plays the midi files... Which is actually the only reason I want to be able to play midi. When i'm a bit more used and enlighten about all the linux stuff all probably have another go at it, but for now i'm satisfied i have working TuxGuitar :-) Thnx again for all your effort.

(Gwasanaethau: i tried that thread before and kinda got lost, but as i said, i'll probably try it again after while so thnx for all your help!)

---

### Post by Gwasanaethau on 2007-08-29
You're welcome - sorry you couldn't get everything working the way you wanted it. I'm not that great at explaining things at the best of times! :lolflag: Glad you got some of it working though! Happy guitar-ing! :guitar:

---

