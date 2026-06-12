---
title: "System Sounds"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by matburton on 2007-08-04
Hey,

I have two accounts on my Ubuntu Feisty install. On my account I have no system sounds but sound from all other apps works fine. On the other account system sounds work OK.

When I open gnome-sound-properties from the console and try and play a system sound I get the following errors:

```

ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM dmix:Intel
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM dmix:Intel
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM dmix:Intel

```

The annoying thins is that the sounds used to work before I upgraded to feisty, the other account was created after the upgrade.

Is there anyway I can copy the sound settings from the new working account to mine?

I read [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=27989") post but it seems to be no longer applicable.

Thanks,
Mr.B

---

### Post by n.aggel on 2007-08-04
i am not an expert, but have you enabled system sounds from System->preferences->sound ?

maybe you disturbed this setting somehow....

---

### Post by matburton on 2007-08-04
Hey,

gnome-sound-properties opens the same app as System->Preferences->Sound.

The settings in gnome-sound-properties are fine as far as I can see and the same as the other account.

Anyone have any idea where the settings for the system sounds are stored? Then I could copy and paste I assume? Or is my sound server not starting as in [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=27989") post?

---

### Post by matburton on 2007-08-04
I've got a bit further now...

It appears that my esd (Enlightened Sound Daemon) is not running!
When I try and start it on the terminal it exits with this error:
```

ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM dmix:Intel

```

But using esd -h tells me that I have two sound card options, one being the one I want hw:0.
So then running esd -d hw:0 works! And then my system sounds work!

But where are the settings so that I can fix the default device for esd to hw:0???

---

### Post by matburton on 2007-08-04
Ah!
Fixed! :)

What I did was open /etc/esound/esd.conf and added -d hw:0 to the default options like this:
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=-d hw:0

```

Now everything works again! :)

---

