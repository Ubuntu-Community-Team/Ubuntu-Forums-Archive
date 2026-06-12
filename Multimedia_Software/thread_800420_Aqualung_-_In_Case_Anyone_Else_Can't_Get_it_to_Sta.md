---
title: "Aqualung - In Case Anyone Else Can't Get it to Start"
date: 2008-05-19
forum: Multimedia Software
---

### Post by brewstah on 2008-05-19
I wanted gapless playback.  And Aqualung claimed to deliver this.  But it wouldn't start after installation using Synaptic.  So I tried running it from the command line and got an error message that said:```
No output driver specified, probing for a usable driver.
Probing JACK driver... JACK server not found
Probing ALSA driver... unable to start with default params
Probing OSS driver... device busy
No usable output driver was found. Please see aqualung --help
and the docs for more info on successfully starting the program.
```Apparently Aqualung attempts to autodetect sound drivers with which it's compatible upon startup.  So I tried specifying output drivers manually using the -o switch. ```
aqualung -o jack
``` returned this:```
Aqualung couldn't connect to JACK.
There are several possible reasons:
	1) JACK is not running.
	2) JACK is running as another user, perhaps root.
	3) There is already another client called 'aqualung'. (Use the -c option!)
``````
aqualung -o alsa
```returned this:```
alsa_init warning: failed setting buffersize to 4096.
Parameters were: nperiods = 2, period = 8192
alsa_init: error setting HW params.
```The only one that worked was OSS.  And so I changed the command in the menu to: ```
aqualung -o oss
```This works fine.

I don't even know what JACK is.  So it's probably not installed.  As for why ALSA didn't work for this, it may have to do with some quirk in my hardware more than anything else.  Since OSS worked and allowed the player to run and work, I'm happy.

All I wanted a nice basic audio player.  Aqualung plays all the usual formats, like ogg, mp3, flac, etc., has a nice clean UI, is skinnable, is highly configurable, will move back and forth through a file using the left and right arrows keys, ala' mplayer (a *must have* for me), uses fonts that are large enough to see (unlike too many other players), as well as the gapless playback feature, makes me not miss xmms.

I don't know if my initial difficulties getting the app to run constitute a bug or something about my hardware and software configuration.  The fix was easy enough, so my purpose here is to help others get it running in case they ran into the same bumps as I.

Oh, I'm running Hardy x86_64

---

### Post by joris1977 on 2008-08-15
To add some more advice:

On several dual core machines i noted  choppy playback in aqualung. Someone on another forum proposed this: 

aqualung --output alsa --nperiods 4 

I have no idea why, but this seems to solve the problem :)

Aqualung is really a great player.

The only thing i miss is last FM support...

---

### Post by shantiq on 2010-04-26
[B][COLOR="Blue"]

ok there got problems too starting it

but as regards the oss only thing that i understand


if you run

```
aqualung -V
```

it gives you all the specs of your version

often it will say

```
  Output driver support:
    [ ] sndio Audio
    [+] OSS Audio
    [ ] ALSA Audio
    [ ] JACK Audio Server
    [ ] PulseAudio
    [ ] Win32 Sound API

```


and that is why only OSS is available


myself i am getting this at the moment and OSS is not busy so far as i know any ideas anyone?

```
No output driver specified, probing for a usable driver.
Probing OSS driver... device busy
No usable output driver was found. Please see aqualung --help
and the docs for more info on successfully starting the program.

```[/COLOR][/B]

---

