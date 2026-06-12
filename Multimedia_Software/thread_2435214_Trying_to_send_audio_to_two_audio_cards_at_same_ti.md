---
title: "Trying to send audio to two audio cards at same time, I am confused."
date: 2020-01-17
forum: Multimedia Software
---

### Post by adrian-h on 2020-01-17
I am using Ubuntu 18.04 LTS, this is the output from uname -a if it helps.

```
Linux plex780 5.0.0-37-generic #40~18.04.1-Ubuntu SMP Thu Nov 14 12:06:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

If I use aplay -l this is the output

```
a@plex780:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD1984A Analog [AD1984A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: AD1984A Alt Analog [AD1984A Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

I am running a normal desktop version.  If I go into settings - sound I can see outputs for 
Speakers  Built in audio, and,
HDMI/Displayport 4 - GK107 HDMI Audio Controller.

Even though I can have them both 'ON' I can only got audio from one or the other depending on which one I last selected in settings, it seems it can be an exlusive output only?, some times it works more often then not i get nothing.
I have done some searching and seen one solution is to install paprefs.  But, this did not work as I got an error of 
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable                                                                                                                                        
distribution that some required packages have not yet been created                                                                                                                                        
or been moved out of Incoming.                                                                                                                                                                            
The following information may help to resolve the situation:                                                                                                                                              
                                                                                                                                                                                                          
The following packages have unmet dependencies.                                                                                                                                                           
 paprefs : Depends: pulseaudio-module-gconf but it is not going to be installed                                                                                                                           
           Depends: pulseaudio-module-zeroconf but it is not going to be installed                                                                                                                        
E: Unable to correct problems, you have held broken packages.
```

As I am probably a bit grey in the head for this I decided that without checking could be bad for my computer!

In case it helps provide information as to why I would like this, I am running OBS Studio and require the audio to be sent to HDMI to an external UDP stream hardware box and to the internal audio card headphones to provide a monitor for my self.

Adrian

---

### Post by CatKiller on 2020-01-17
> **adrian-h said:**
> Even though I can have them both 'ON' I can only got audio from one or the other depending on which one I last selected in settings, it seems it can be an exlusive output only?,

Not quite. By default each source goes to one sink. Not all sources need to go to the same sink, though.

PulseAudio comes with the ability to create virtual output devices that do exactly what you're after: mirror the stream to one sink to another sink for monitoring. In KDE, which is what I use, that configuration is simply part of the volume widget. I understand that Gnome's options are more limited, which is why you'd need something extra like paprefs.

>                                                                                                                                                                                                 
```
The following packages have unmet dependencies.                                                                                                                                                           
 paprefs : Depends: pulseaudio-module-gconf but it is not going to be installed                                                                                                                           
           Depends: pulseaudio-module-zeroconf but it is not going to be installed                                                                                                                        

```

Looks like a dependency issue. You could try doing all of them at once to try to help the package manager out:

```
sudo apt install paprefs pulseaudio-module-gconf pulseaudio-module-zeroconf
```

Otherwise, the configuration option is probably available in a config file as well.

---

### Post by adrian-h on 2020-01-17
Thank you for the response, sorry I missed it I got no notification, something I need to check in settings.

Yes I use Gnome, which I think was my default installation setting, not sure.

I tried as you suggested 
```
sudo apt install paprefs pulseaudio-module-gconf pulseaudio-module-zeroconf
[sudo] password for a: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 pulseaudio-module-gconf : Depends: libpulse0 (= 1:11.1-1ubuntu7.4) but 1:11.1-1ubuntu7.5 is to be installed
                           Depends: pulseaudio (= 1:11.1-1ubuntu7.4)
 pulseaudio-module-zeroconf : Depends: libpulse0 (= 1:11.1-1ubuntu7.4) but 1:11.1-1ubuntu7.5 is to be installed
                              Depends: pulseaudio (= 1:11.1-1ubuntu7.4)
E: Unable to correct problems, you have held broken packages.
```

I found this web page
[https://askubuntu.com/questions/78174/play-sound-through-two-or-more-outputs-devices](https://askubuntu.com/questions/78174/play-sound-through-two-or-more-outputs-devices)

Which basically seems as though the author is trying to do the same thing.

I noticed a recent response which I copied here:-
                                               Yes, the version of paprefs  in Ubuntu 18.04 repos is useless (because it still thinks GConf is in  fashion and hence fails to work). 
The best alternative is to, you know,  load the module-combine-sink of PulseAudio yourself (because that's all paprefs does behind-the-scene anyway). 
Use command pactl load-module module-combine-sink and check the Sounds section of Ubuntu Settings.                                      &#8211; [AneesAhmed777]("https://askubuntu.com/users/638121/aneesahmed777")                 [URL="https://askubuntu.com/questions/78174/play-sound-through-two-or-more-outputs-devices#comment1942099_78174"]Aug 11 '19 at 16:16
[/URL]                                                             
Now I have tried this and it does provide a solution but looks like it needs to be done every time I power on the PC as it is not permanent.

Time for zzzzz

Adrian

---

### Post by CatKiller on 2020-01-18
> **adrian-h said:**
> Now I have tried this and it does provide a solution but looks like it needs to be done every time I power on the PC as it is not permanent.

It's a while since I played with them, but PulseAudio's config files are pretty straightforward. Now that you've found the name of the option, it's just a case of adding that option to the file. I *think* it's default.pa that loads the modules, but I'm not near my computer to check.

---

### Post by adrian-h on 2020-01-18
Thank you for your assistance,  I added  load-module module-combine-sink 
to the end of default.pa and it appears to be working all OK.
It certainly loads the extra module for it to be in settings audio.

i will now continue on my way with OBS etc

Again thank you.

Adrian

---

