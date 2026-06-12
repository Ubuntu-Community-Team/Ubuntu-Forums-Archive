---
title: "natty-11.04 32 bit Desktop - AcerAspireOne Skype builtin-Microphone problem"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Hakunka-Matata on 2011-04-03
Please help me SOLVE, the trusty AOA is my smart phone when I travel (which is most of the time)

[COLOR=black]_**natty-11.04 32 bit Desktop**_[/COLOR] - AcerAspireOne model 110: Atom N270: 1GBRam: 8GB SSD: Skype builtin-Microphone problem
it works fine with Maverick (10.10) can I use a driver from there?

Everything except the builtin microphone works :intel 945GME

---

### Post by Sef on 2011-04-03
Moved to Natty thread.

---

### Post by cariboo on 2011-04-03
I'd suggest you check aksamixer to see if the mic volume level is turned up. I had the same problem on my Compaq Mini 1100 netbook. Once you have the settings where you want them, use:

```
sudo alsactl store
```

to save the settings

---

### Post by Hakunka-Matata on 2011-04-03
```

Sunday, April 3, 2011
[11:53:12 PM EDT] Doug: das@das-AOA110:~$ cat /var/lib/alsa/asound.state^C
das@das-AOA110:~$ clear

das@das-AOA110:~$ cat /var/lib/alsa/asound.state
state.Intel {
        control.1 {
                iface MIXER
                name 'Master Playback Volume'
                value.0 64
                value.1 64
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 64'
                        dbmin -6400
                        dbmax 0
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
        control.2 {
                iface MIXER
                name 'Master Playback Switch'
                value.0 true
                value.1 true
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.3 {
                iface MIXER
                name 'Mic Boost Capture Volume'
                value.0 2
                value.1 2
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 2'
                        dbmin 0
                        dbmax 4000
                        dbvalue.0 4000
                        dbvalue.1 4000
                }
        }
        control.4 {
                iface MIXER
                name 'Beep Playback Volume'
                value.0 0
                value.1 0
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 12'
                        dbmin -2400
                        dbmax 0
                        dbvalue.0 -2400
                        dbvalue.1 -2400
                }
        }
        control.5 {
                iface MIXER
                name 'Beep Playback Switch'
                value.0 true
                value.1 true
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.6 {
                iface MIXER
                name 'Capture Volume'
                value.0 31
                value.1 31
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 31'
                        dbmin -1500
                        dbmax 3150
                        dbvalue.0 3150
                        dbvalue.1 3150
                }
        }
        control.7 {
                iface MIXER
                name 'Capture Switch'
                value.0 true
                value.1 true
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.8 {
                iface MIXER
                name 'PCM Playback Volume'
                value.0 255
                value.1 255
                comment {
                        access 'read write user'
                        type INTEGER
                        count 2
                        range '0 - 255'
                        tlv '0000000100000008ffffec1400000014'
                        dbmin -5100
                        dbmax 0
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
}
[11:53:52 PM EDT] Doug: das@das-AOA110:~$ cat /var/lib/alsa/asound.state^C
das@das-AOA110:~$ clear

das@das-AOA110:~$ cat /var/lib/alsa/asound.state
state.Intel {
        control.1 {
                iface MIXER
                name 'Master Playback Volume'
                value.0 64
                value.1 64
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 64'
                        dbmin -6400
                        dbmax 0
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
        control.2 {
                iface MIXER
                name 'Master Playback Switch'
                value.0 true
                value.1 true
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.3 {
                iface MIXER
                name 'Mic Boost Capture Volume'
                value.0 2
                value.1 2
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 2'
                        dbmin 0
                        dbmax 4000
                        dbvalue.0 4000
                        dbvalue.1 4000
                }
        }
        control.4 {
                iface MIXER
                name 'Beep Playback Volume'
                value.0 0
                value.1 0
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 12'
                        dbmin -2400
                        dbmax 0
                        dbvalue.0 -2400
                        dbvalue.1 -2400
                }
        }
        control.5 {
                iface MIXER
                name 'Beep Playback Switch'
                value.0 true
                value.1 true
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.6 {
                iface MIXER
                name 'Capture Volume'
                value.0 31
                value.1 31
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 31'
                        dbmin -1500
                        dbmax 3150
                        dbvalue.0 3150
                        dbvalue.1 3150
                }
        }
        control.7 {
                iface MIXER
                name 'Capture Switch'
                value.0 true
                value.1 true
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.8 {
                iface MIXER
                name 'PCM Playback Volume'
                value.0 255
                value.1 255
                comment {
                        access 'read write user'
                        type INTEGER
                        count 2
                        range '0 - 255'
                        tlv '0000000100000008ffffec1400000014'
                        dbmin -5100
                        dbmax 0
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
}

```

---

### Post by Hakunka-Matata on 2011-04-04
Thanks, guess I'm making progress, looks like I can change the record volume, it shows up on under the "sound preferences" , speaker Icon when I'm trying to record during the skype test call.  but I don't understand how to read section 3:>  control.3 {
 iface MIXER                 
name 'Mic Boost Capture Volume'                 
value.0 2 
                value.1 2                 
comment {                         access 'read write' 
                        type INTEGER
count 2
 range '0 - 2' 
dbmin 0 
                        dbmax 4000 
                        dbvalue.0 4000
 dbvalue.1 4000
 }         
}
is it turned on?

---

### Post by cariboo on 2011-04-04
I guess I should have been a bit more specific, in a terminal type:

```
alsamixer
```

use the arrow keys to navigate. Press esc to exit, then:

```
sudo alsactl store
```

to save the settings.

---

### Post by Hakunka-Matata on 2011-04-04
You're doing fine teach, feed me byte size slices.  I did it all as you show, everything came out as  your Thumbnail shows, but the )#%*)( test call still does not work. 
tomorrow I'll load maverick back in and see what's different.  

Could be bug???   maybe bug???  I could see that possibility, I'm dealing with a bleedin Beta (or are we still Alpha3) after all.  Ain't complainin, just trying to fix it.  I love this release.  Thanks Cariboo

---

### Post by Hakunka-Matata on 2011-04-04
It's not that the microphone volume is low, it is ZERO.  Like the mic is turned off.................  I could have been more precise in stating the problem

---

