---
title: "M-Audio Audiophile 24/96 suddenly stopped working"
date: 2014-09-07
forum: Multimedia Software
---

### Post by a-shkoporov on 2014-09-07
Hi all! I've got Ubuntu 14.04 and M-Audio Audiophile 24/96 sound card (based on Envy24 chipset). I use Mudita24 as mixer. The card was correctly recognized during Ubuntu installation and worked perfectly until yesterday when the sound suddenly disappeared during audio file playback. Now there's no sound in all applications. Under Windows everything is OK, so probably there's no hardware problems. I'm definitely not a pro in Linux, so any kind of help will be highly appreciated!

---

### Post by tgalati4 on 2014-09-08
Did you try resetting PulseAudio?  Open a terminal:

```
pulseaudio -k
```

Sometimes the patches need to be remade.  Try creating a new profile with fresh patches.

---

### Post by a-shkoporov on 2014-09-08
I tried to remove pulseaduio user configuration folder (~/.config/pulseaudio) and restarted pulseaudio using -k option. There is still no sound. Interestingly, audio and video files cannot be played at all. The playback of video stops on first frame. If I choose alsa or OSS in vlc and mplayer the video is played but with no sound. Does this mean that the problem is with pulseaudio? I was thinking of making a clean re-install of Ubuntu...

---

### Post by a-shkoporov on 2014-09-08
> **tgalati4 said:**
> Try creating a new profile with fresh patches.

Could you please give me a more detailed description how to do this?

---

### Post by vro2 on 2015-01-18
Hello, I've got the exact same problem as you:
Same sound card and using mudita24
Suddenly no more sound
And sound are not playing except with vlc but still no sound

Have you been able to solve it and if yes how?
Many thanks in advance!

---

### Post by tgalati4 on 2015-01-19
Try removing *mudita24* with the purge switch and reinstalling.

You will have to remake your input and output patches to get sound.

```
sudo apt-get purge mudita24
sudo apt-get install mudita24
```

---

### Post by vro2 on 2015-01-19
Hi, thank you very much for your reply!

I removed mudita24 with the purge switch and reinstalled.
but i'm sorry i don't understand what are the patches, please could you explain to me?

when i first installed linux i had no sound, but installing mudita24 and moving the DAC sliders up solved the problem. that's all i had done and it worked fine for 2 months.

now like for the OP the sound has suddenly stopped (not after an update, just like that), videos freeze on first frame and sound files are not played, except on VLC (but no sound).
But it works on windows xp, and it also works when booting to live usb with same linux distribution (mint 17) and installing mudita24 in live session and pushing sliders up.

I compared all the settings of alsamixer, gnome-alsamixer, pavucontrol and mudita24 between the live session and the installed version and they are all the same,
except for the "multi track master clock rate" which is '44100' in the live session and 'S/PDIF In' on the machine, but if I try to change it it reverts back. dunno if this is relevant.

i've also tried changing stuff in the pulseaudio conf files as explained here: [http://doc.ubuntu-fr.org/m-audio_audiophile_2496](http://doc.ubuntu-fr.org/m-audio_audiophile_2496)  (3.1 and 3.2)
but that didn't work.

please let me know if i should test something else or if you think of any solutions (input and output patches ?) , as you can see i'm new to linux and don't know much about sound.
thank you very much in advance,
Véro

---

### Post by tgalati4 on 2015-01-19
Bring up *mudita24* and go the patchbay/router tab.  Start pushing some buttons.  When you get sound, save your active profile in the Profile tab.

The m-audio cards need to be told what inputs get connected to what outputs.  Otherwise, you get no sound.

---

### Post by vro2 on 2015-01-20
aaah ok thanks! i understand that now. the default settings worked for me there so i hadn't changed them.

But I found what the problem was now : the master clock rate.

I was able to reproduce the exact same problem in windows by changing the master clock rate.
In linux i had to kill the jackd process and close firefox to be able to change the clock rate in mudita24, and as soon as i did the sound came back :))

But I still don't know what suddenly changed the master clock rate in the first place, so the problem might come back. Could that be firefox ?

I'll save the profile in mudita24.

Thank you for your help and your time!

---

### Post by tgalati4 on 2015-01-20
It could be HTML5 audo/video engine in Firefox.  Some sound cards use 44.1 kHz as the default clock speed.  Others use 48 kHz.  There might be a setting in Firefox that you can change.  Search through [http://about:config](http://about:config).  I found video bitrates but no audio bitrates, so perhaps a plug-in that you are using is causing the change.

This could have been the OP's problem as well.

---

### Post by vro2 on 2015-01-22
[FONT=Calibri]hello,[/FONT]
  [FONT=Calibri]i checked the list in firefox and just like you I only found video bit rates (between 200 and 2000), and nothing that seem to correspond to 44100.[/FONT]
  [FONT=Calibri] [/FONT]
  [FONT=Calibri]Googling it I found this thread that could be related but concerns graphics card:[/FONT]
  [FONT=Calibri][http://forums.guru3d.com/showthread.php?t=380114](http://forums.guru3d.com/showthread.php?t=380114)[/FONT]
  [FONT=Calibri] [/FONT]
  [FONT=Calibri]But yes I think the master clock was also the OP problem, we reported the same effects on sound and videos and VLC.[/FONT]
  [FONT=Calibri] [/FONT]
  [FONT=Calibri]If the master clock rate gets switched again, I'll report here as well.[/FONT]
  [FONT=Calibri] [/FONT]
  [FONT=Calibri]Thanks for your help!
[/FONT]

---

### Post by tgalati4 on 2015-01-22
Understand that many high definition videos have sound recorded at 48 kiloHertz.  44.1 kiloHertz is an old recording standard roughly based on twice the upper limit of human hearing (22 kHz).  This allows digital recordings to capture these high frequences--Nyquist Theorem.  48 kHz came from 3x16MHz, where 16MHz is a very common timing chrystal speed and used in many sound cards.

So, perhaps you played a high-def Youtube video with 48kHz sound.  Your sound card should automatically switch to play the sound track.  The problem is after playing, the sound card doesn't know to switch back.  This is either an Adobe Flash problem, an HTML5 problem, or a sound card driver problem.

Because the M-Audio sound cards have many channels and both record and playback, a master clock is needed to syncronize all of the channels.  Obviously, you can't record at 48kHz on some channels and 44.1kHz on other channels.  You have to choose.  I don't know how to set the master clock with a configuration file.  That might be something to research.

After a few minutes of googlefu, I found:

[https://wiki.archlinux.org/index.php/Envy24control](https://wiki.archlinux.org/index.php/Envy24control)  Good explanation between master clock rate and locked rate.
[http://ubuntuforums.org/archive/index.php/t-1758446.html](http://ubuntuforums.org/archive/index.php/t-1758446.html)  Settings are stored in the Profiles! Duh, but what is the default profile?
[http://www.jrigg.co.uk/linuxaudio/ice1712multi.html](http://www.jrigg.co.uk/linuxaudio/ice1712multi.html)  Using multiple M-audo cards and syncing clocks.
[http://www.remastersys.com/forums/index.php?topic=1208.0](http://www.remastersys.com/forums/index.php?topic=1208.0) Tutorial on how to get 16 channels of audio.
[http://forums.linuxmint.com/viewtopic.php?t=187670&p=972072](http://forums.linuxmint.com/viewtopic.php?t=187670&p=972072)  This thread looks familiar.

---

### Post by vro2 on 2015-01-23
haha yes i asked on the mint forum as well :)

thanks for your links i had seen some of them but not this one which is really useful if the problem come again (control stuck):
[http://ubuntuforums.org/archive/index.php/t-1758446.html](http://ubuntuforums.org/archive/index.php/t-1758446.html) 
that's also the same problem i had: clock set to S/PDIF (probably because the patchbay configuration was also changed, i didn't report it because this was easy to revert back to normal, and made no difference), and difficult to modify.


i've just watched some HD /4K videos on youtube to test but that didn't change the settings.
also it never happened on windows.

anyway if an application changes the settings again i'll just change them back.

thanks :)

---

