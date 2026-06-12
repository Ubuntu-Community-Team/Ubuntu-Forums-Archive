---
title: "Sound card problem,can be detected but not work"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by rolandocdf on 2006-06-15
I have used Ubuntu 6.06 and the kernel is 2.6.15-23-386,my sound card is creative SB Audigy LS and the module is ca0106 which is supported in the alsa list. And in Ubuntu it is also detected as ca0106 but it doesn't work. I ran alsaconf and alsamixer to turn up the sound,however it was useless.The version of the alsa is 1.0.11.
Please help me,thank you!

---

### Post by BitTorrentBuddha on 2006-06-15
Did you make sure to disable integrated audio through the bios settings?

---

### Post by rolandocdf on 2006-06-15
This sound card is the integrated audio, so I'm puzzled.Even at the time when ubuntu starting hardware drivers I can hear something caused by the current just like when windows starting,but it doesn't  work, no error,no warning and no sound....

---

### Post by ViperAFK on 2006-06-15
[QUOTE=rolandocdf]This sound card is the integrated audio, so I'm puzzled.Even at the time when ubuntu starting hardware drivers I can hear something caused by the current just like when windows starting,but it doesn't  work, no error,no warning and no sound....[/QUOTE]
Yes, ive been having the same problem with my integrated sound, and so has many people, has anyone found a solution yet?

---

### Post by rolandocdf on 2006-06-16
[QUOTE=ViperAFK]Yes, ive been having the same problem with my integrated sound, and so has many people, has anyone found a solution yet?[/QUOTE]

I think it is not a serious problem, but I can not find what's wrong with it. All seem right.

```

cdf@cdf-ubuntu:~$ cat /proc/asound/cards
0 [CA0106         ]: CA0106 - CA0106
                     AudigyLS [Unknown] at 0x9000 irq 50 

```
```

cdf@cdf-ubuntu:~$ lsmod | grep snd
snd_ca0106             38180  1
snd_rawmidi            26848  1 snd_ca0106
snd_seq_device          9228  1 snd_rawmidi
snd_ac97_codec         99808  1 snd_ca0106
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  10 snd_ca0106,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_ac97_bus            2400  1 snd_ac97_codec
snd_page_alloc         11304  2 snd_ca0106,snd_pcm 

```

---

### Post by mofodojodino on 2006-06-16
I had the same problem, I could hear sound on startup at the login screen but had no should once logged in.

My problem was that I was not part of the audio group. To see if you are type this in a terminal.

```
cat /etc/group |grep audio
```

If you don't see your username at the end of this line you need to add it. Then log out and in again to reset.

Cheers

---

### Post by rolandocdf on 2006-06-16
[QUOTE=mofodojodino]I had the same problem, I could hear sound on startup at the login screen but had no should once logged in.

My problem was that I was not part of the audio group. To see if you are type this in a terminal.

```
cat /etc/group |grep audio
```

If you don't see your username at the end of this line you need to add it. Then log out and in again to reset.

Cheers[/QUOTE]

thank you for your answer, but I'm still int the audio group
```

cdf@cdf-ubuntu:~$ cat /etc/group |grep audio
audio:x:29:cdf

```

---

### Post by grip82 on 2006-07-03
Same problem here. :( 

After a lot of messing around, I got my sound working in breezy. Then I upgraded to dapper, and it's all gone now. 

Anyone a suggestion?

edit: It did help to downgrade from kernel 2.6.15-25-386 to kernel 2.6.12-10-386 ... but that's not a real solution.

---

### Post by butterman on 2006-08-29
I have the same problem.  I'm running Dapper with an SB Audigy LS card. The card is recognized by the device manager and I'm in the audio group. I, too, have played with the alsamixer extensively without success.  I don't have any insights beyond what has already been posted.  Hopefully my post (in addition to the others) will give this problem more attention.

---

### Post by polly1 on 2006-11-11
hi 

In case you still do not have sound, have you tried setting your card to be the default one. Try-

System>Preferences>Sound and then click Sounds and at the bottom heading
adjust "Default Sounds" to your card. you can also make other  sound adjustments by this menu

When I installed Breezy I had to do this to get sound this because the default card was my on-board Intel 5. In addition, I had to change the Intel to my Audiology card by double clicking the volume icon on right of top bar and changing the device on the file menu, Also I got rid of all headings on the alsa mixer by Edit>Preferences to leave just Master Front Surround and CD, adjusted to nearly maximum output by leaving ticks on these boxes only.
The output jack box was also ticked- Switch heading.

My Creative system has 4 speakers

---

### Post by ebozzz on 2006-11-11
> **polly1 said:**
> When I installed Breezy I had to do this to get sound this because the default card was my on-board Intel 5.

What if you are using the on-board sound and are having problems?

---

### Post by 14bmail on 2006-11-12
I just found this too frustrating. I've been using nix servers for close on to 15 years and never had to bother with sound cards. Decided to install nix on recently acquired laptop, can't get sound working on it, yet I can get sound working on my desktop. I had sound working once in ubuntu edgy but it stopped working and hasn't worked since. Going to use windows for time being on laptop as it's too ](*,) ](*,) ](*,)  and I'd love to have more 'fun' time to myself with computers instead of tinkering the past week. [-(

---

### Post by 14bmail on 2006-11-12
Hmm, a bit on inspiration came to me. I tried using "acpi=off" in my grub options and I got sound.  Even through I'm losing battery stuff for the laptop, much prefer that to not having sound + video on my lappy for time being.. And it beats the hell out of windows

---

