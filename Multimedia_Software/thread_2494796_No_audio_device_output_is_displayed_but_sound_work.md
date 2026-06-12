---
title: "No audio device output is displayed but sound working"
date: 2024-01-27
forum: Multimedia Software
---

### Post by rodride on 2024-01-27
hi,

I'm running Ubuntu 23.10 with pipewire and wireplumber

Command "pactl list short sinks" return nothing

```

 aplay -l
**** Liste des périphériques matériels PLAYBACK ****
carte 0 : PCH [HDA Intel PCH], périphérique 0 : ALC892 Analog [ALC892 Analog]
  Sous-périphériques : 1/1
  Sous-périphérique #0 : subdevice #0
carte 1 : NVidia [HDA NVidia], périphérique 3 : HDMI 0 [VG27A]
  Sous-périphériques : 1/1
  Sous-périphérique #0 : subdevice #0
carte 1 : NVidia [HDA NVidia], périphérique 7 : HDMI 1 [HDMI 1]
  Sous-périphériques : 1/1
  Sous-périphérique #0 : subdevice #0
carte 1 : NVidia [HDA NVidia], périphérique 8 : HDMI 2 [HDMI 2]
  Sous-périphériques : 1/1
  Sous-périphérique #0 : subdevice #0
carte 1 : NVidia [HDA NVidia], périphérique 9 : HDMI 3 [HDMI 3]
  Sous-périphériques : 1/1
  Sous-périphérique #0 : subdevice #0
carte 2 : Audio [iFi (by AMR) HD USB Audio], périphérique 0 : USB Audio [USB Audio]
  Sous-périphériques : 1/1
  Sous-périphérique #0 : subdevice #0

```

```

wpctl status
PipeWire 'pipewire-0' [1.0.1, filip@ubuntu, cookie:1726766967]
 &#9492;&#9472; Clients:
        32. WirePlumber                         [1.0.1, filip@ubuntu, pid:1040]
        33. WirePlumber [export]                [1.0.1, filip@ubuntu, pid:1040]
        34. pipewire                            [1.0.1, filip@ubuntu, pid:1041]
        35. GNOME Settings                      [1.0.1, filip@ubuntu, pid:8380]
        45. GNOME Volume Control Media Keys     [1.0.1, filip@ubuntu, pid:1383]
        50. gnome-shell                         [1.0.1, filip@ubuntu, pid:1250]
        51. GNOME Shell Volume Control          [1.0.1, filip@ubuntu, pid:1250]
        52. xdg-desktop-portal                  [1.0.1, filip@ubuntu, pid:1814]
        53. Terminal                            [1.0.1, filip@ubuntu, pid:1866]
        54. Firefox                             [1.0.1, filip@ubuntu, pid:2666]
        55. Nightly                             [1.0.1, filip@ubuntu, pid:2666]
        57. wpctl                               [1.0.1, filip@ubuntu, pid:12773]

Audio
 &#9500;&#9472; Devices:
 &#9474;      42. GM204 High Definition Audio Controller [alsa]
 &#9474;      43. iFi (by AMR) HD USB Audio           [alsa]
 &#9474;      44. Built-in Audio                      [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  *   49. iFi (by AMR) HD USB Audio Pro       [vol: 0.70]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Video
 &#9500;&#9472; Devices:
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    alsa_output.usb-iFi__by_AMR__iFi__by_AMR__HD_USB_Audio_0003-00.pro-output-0
         1. Audio/Source  alsa_output.usb-iFi__by_AMR__iFi__by_AMR__HD_USB_Audio_0003-00.pro-output-0

```

```

pactl info
Chaîne du serveur&#8239;: /run/user/1000/pulse/native
Version du protocole de bibliothèque&#8239;: 35
Version du protocole du serveur&#8239;: 35
Local&#8239;: oui
Index client&#8239;: 77
Tile Size&#8239;: 65472
Nom d’utilisateur : filip
Nom d’hôte : ubuntu
Nom du serveur : PulseAudio (on PipeWire 1.0.1)
Version du serveur : 15.0.0
Spécification d’échantillon par défaut : float32le 2ch 48000Hz
Plan de canaux par défaut : front-left,front-right
Destination par défaut : @DEFAULT_SINK@
Source par défaut : @DEFAULT_SOURCE@
Cookie : 66ec:5f77

```

How can I display my audio output devices in gnome-control-center and with the "pactl list short sinks" command?

Thanks for help

---

### Post by rodride on 2024-01-27
in fact i don't have sound in rhythmbox

---

### Post by rodride on 2024-01-27
After a fresh install, all woks fine

---

