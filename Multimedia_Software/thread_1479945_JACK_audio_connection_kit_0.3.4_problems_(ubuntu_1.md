---
title: "JACK audio connection kit 0.3.4 problems (ubuntu 10.04)"
date: 2010-05-11
forum: Multimedia Software
---

### Post by hihihi100 on 2010-05-11
Hi there:

I want to use "Virtual MIDI Piano Keyboard" and for the MIDI sounds to be heard, I need to configure the channels via a JACK program, such as this kit. After downloading it from the software center and clicking on the icon, and trying to start it., in the messages window I read:

```
  p, li { white-space: pre-wrap; }  [COLOR=#999999]05:54:56.729 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]05:54:56.912 Statistics reset.[/COLOR]
 [COLOR=#66cc99]05:54:57.044 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]05:54:57.255 ALSA connection change.[/COLOR]
 [COLOR=#999999]05:55:06.115 Startup script...[/COLOR]
 [COLOR=#990099]05:55:06.116 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]05:55:06.518 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]05:55:06.532 JACK is starting...[/COLOR]
 [COLOR=#990099]05:55:06.533 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -Xraw[/COLOR]
 [COLOR=#999999]05:55:06.538 JACK was started with PID=2496.[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 [COLOR=#999999]05:55:06.585 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]05:55:06.585 Post-shutdown script...[/COLOR]
 [COLOR=#990099]05:55:06.586 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]05:55:07.006 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]05:55:08.663 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

```And, related to this, is JAMIN better? and JACKEQ? Patchage?

And please take a look at the uploaded screenshots

Why is the "shut" icon gone?

cheers

---

### Post by dv3500ea on 2010-05-11
Go to System -> Administration -> Users and Groups
click Manage Groups
click on 'audio' and click properties
select yourself as a user of that group then click ok

Afterwards press Alt-F2 and enter ```
gksudo gedit /etc/security/limits.conf
```
change the file so it contains:
```

@audio          -       rtprio          100
@audio          -       nice            -10

```
then reboot.

---

### Post by hihihi100 on 2010-05-12
Is it ok if I just add the pasted command -the 2 audio -10 and audio 100- at the end of the file? I wouldnt like to de-stabilize the system.

I just want to make sure that by default, in the amentioned document, there is not any line regarding "audio"... see attached file

---

### Post by dv3500ea on 2010-05-13
Yes, just paste it at the end of the file, but back up the file first just in case

---

### Post by cchhrriiss121212 on 2010-05-13
> And, related to this, is JAMIN better? and JACKEQ? Patchage?
Better than what exactly? Jack is a sound server, and these are applications that make use of jack. Jamin (jack audio mastering interface) is for mastering, jackeq is an equalizer and patchage is useful for giving a visual representation of the jack connection bay.

---

### Post by hihihi100 on 2010-05-14
> **cchhrriiss121212 said:**
> Better than what exactly? Jack is a sound server, and these are applications that make use of jack. Jamin (jack audio mastering interface) is for mastering, jackeq is an equalizer and patchage is useful for giving a visual representation of the jack connection bay.

Thanks, that was helpful, I had no idea of the differences

dv 3500, just did what u told me, next time I boot Ill see the changes

cheers

---

