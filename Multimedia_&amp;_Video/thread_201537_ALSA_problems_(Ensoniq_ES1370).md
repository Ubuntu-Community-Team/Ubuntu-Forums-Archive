---
title: "ALSA problems? (Ensoniq ES1370)"
date: 2006-06-22
forum: Multimedia &amp; Video
---

### Post by emveedeeaych on 2006-06-22
Hey all,

I'm a relative newbie to Ubuntu and Linux (okay, complete). I installed Dapper on a second hand HP Pavilion 8660C and everything worked great, save for sound. After researching, I found that this computer had a modem/audio card called Riptide, which is near impossible to make work under a Debian-based distro.

So, going for broke, I yoinked the Ensoniq ES1370 sound card out of our old Gateway computer, circa 1998, and hoped it might work in the Riptide's stead. Sadly, as much was not the case. But Ubuntu at least recognizes the card in the hardware panel thingy now. It just doesn't work.

Which leads me to think I need drivers. How do I go about getting them? They're listed on ALSA, but I see no download link. As far as I can tell, the ALSA stuff on my system is all up to date and such. I'm just very very confused.

(Also, I'd installed OSS trying to get the Riptide working (didn't). Could that be interfering? Should I uninstall it? And. Uh. How do I do that?)

Thanks!

---

### Post by pellgarlic on 2006-06-22
can you type "modprobe es1370" into a terminal window, and report back what it says? (with the ensoniq card attached).

---

### Post by emveedeeaych on 2006-06-22
Thanks pellgarlic,

It says:

"FATAL: Module es1370 not found."

Any ideas?

---

### Post by Jvaldezjr on 2006-06-22
What this means is that the module for your soundcard is not loaded into the kernel.  There are a few ways of doing so, and I would think if the ALSA site says your card is supported, then the default kernel should have that module loaded.

1st- try editing the modules file in gedit or kate (GNOME or KDE respectively).
sudo gedit /etc/modules

and add es1370 at the last line.  Then restart and see what that does.

The message you posted is saying it is not, but that could mean that your kernel was build with support for your card coded into the kernel (so no module would exist), or you don't have it supported in the kernel at all, or it's just not loading right for some reason.  If the kernel was built without support, you may have to recompile a new kernel, and since you said you were a newbie, and I'm not really an advanced user (I've compiled a couple kernels) I don't think I'm the best person to walk you through the process.

Also before you do anything, can you post what the command 'cat /proc/asound/cards' says, that will help with other people figuring out what or how to edit your sound files.

---

### Post by emveedeeaych on 2006-06-22
The tried the first and it didn't work, but this shows up in the terminal when I enter the command:
'ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default'

Trying the second just gives me:
"cat: /proc/asound/cards: No such file or directory"

---

### Post by Jvaldezjr on 2006-06-22
type and post what 'uname -r' which is the kernel version you are using, and also this: 'lsmod | grep snd'

---

### Post by emveedeeaych on 2006-06-22
Kernel Version: 2.6.15-25-386

lsmod | grep snd doesn't do anything. Just returns to the default prompt again.

---

### Post by Protostar on 2006-06-23
I'm using the same kernel version this guy is using and am having the same problems. I typed in "lsmod | grep snd" and this is what I got:

```
snd_ens1370            19552  3
gameport               15496  1 snd_ens1370
snd_rawmidi            25504  1 snd_ens1370
snd_seq_device          8716  1 snd_rawmidi
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_ens1370,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd_page_alloc         10632  2 snd_ens1370,snd_pcm
snd_ak4531_codec        7936  1 snd_ens1370
snd                    55268  12 snd_ens1370,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_ak4531_codec
soundcore              10208  1 snd

```

I added "es1370" to my etc/modules file, and rebooted and still no sound.   As always, any help will be greatly appreciated.

---

### Post by emveedeeaych on 2006-06-23
Okay, problem fixed, methinks. By complete accident. You see, while trying to un/re-install ALSA. I. Uh. I think I kinda deleted half the OS or something. So. Yeah. I took this opportunity to toss in my Dapper ALT Install CD and completely reinstall Ubuntu.

And it, as if by magic, was recognized. That was the most heavenly bongo noise I'd ever heard.

Maybe the card has to be in during the OS setup to be recognized? Before I killed Ubuntu or whatever and reinstalled, I swapped the card into a different slot (it was in the space occupied by the modem part of the Riptide Sound/Modem Card Combo previously.). I'm no hardware genius, but I kinda thought Ubuntu may still have a hook on that slot or something saying it was a modem (I'd got the modem part to work, just not the sound.). If I recall, it still didn't make a difference till after I reinstalled Dapper...

Anywho. Thanks for all your help guys. I'm surprised how peppy Ubuntu is on older hardware. (Not too crazy bout Xubuntu)

Hopefully this'll work for you too, Protostar.

---

### Post by trorion on 2006-06-23
[QUOTE=emveedeeaych]Okay, problem fixed, methinks. By complete accident. You see, while trying to un/re-install ALSA. I. Uh. I think I kinda deleted half the OS or something. So. Yeah. I took this opportunity to toss in my Dapper ALT Install CD and completely reinstall Ubuntu.

And it, as if by magic, was recognized. That was the most heavenly bongo noise I'd ever heard.

Maybe the card has to be in during the OS setup to be recognized? Before I killed Ubuntu or whatever and reinstalled, I swapped the card into a different slot (it was in the space occupied by the modem part of the Riptide Sound/Modem Card Combo previously.). I'm no hardware genius, but I kinda thought Ubuntu may still have a hook on that slot or something saying it was a modem (I'd got the modem part to work, just not the sound.). If I recall, it still didn't make a difference till after I reinstalled Dapper...

Anywho. Thanks for all your help guys. I'm surprised how peppy Ubuntu is on older hardware. (Not too crazy bout Xubuntu)

Hopefully this'll work for you too, Protostar.[/QUOTE]

Hopefully it doesn't go down on your next update.  My sound died on the most recent system update and I'm still working on it -)

If you think ubuntu is fast try it with XFCE as your display manager some time; makes the system fly comparatively.

---

### Post by Protostar on 2006-06-23
Well I installed the ubuntu Beta 2 and then updated to the final release. I have the Ubuntu Final iso and am going to burn it shortly. I really don't want to reinstall as I sort of have everything set up the way I want it. I guess I could if this would really solve the problem, as sound is a must.

---

### Post by pellgarlic on 2006-06-23
[QUOTE=emveedeeaych]Maybe the card has to be in during the OS setup to be recognized?[/QUOTE]

not really, but it makes it easier - when you installed ubuntu the first time, it would have found the sound card you had installed, and setup the correct modules to load for it. changing it, meant that the modules were not set up for that card, so the setup would have to be done manually. not sure what the commands would be for that. reinstalling with the second sound card installed, meant that ubuntu automatically setup that card, rather than having to do it manually.

---

### Post by Tom H on 2007-01-14
> **Jvaldezjr said:**
> What this means is that the module for your soundcard is not loaded into the kernel.  There are a few ways of doing so, and I would think if the ALSA site says your card is supported, then the default kernel should have that module loaded.

1st- try editing the modules file in gedit or kate (GNOME or KDE respectively).
sudo gedit /etc/modules

and add es1370 at the last line.  Then restart and see what that does.

The message you posted is saying it is not, but that could mean that your kernel was build with support for your card coded into the kernel (so no module would exist), or you don't have it supported in the kernel at all, or it's just not loading right for some reason.  If the kernel was built without support, you may have to recompile a new kernel, and since you said you were a newbie, and I'm not really an advanced user (I've compiled a couple kernels) I don't think I'm the best person to walk you through the process.

Also before you do anything, can you post what the command 'cat /proc/asound/cards' says, that will help with other people figuring out what or how to edit your sound files.

This may be a dumb question but how do you edit the modules file I tried as sudo and would not let me in, tried as myself it let me edit it it but not save it?  Also it already has the following line "snd-ens1370" and I still get the fatal error so can't figure out how to starte the darn thing to get sound to work.   Thanks,  Tom

---

