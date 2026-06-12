---
title: "Vuvuzela filter requested"
date: 2010-06-14
forum: Mythbuntu
---

### Post by derolf on 2010-06-14
Folks,

at [http://www.surfpoeten.de/tube/vuvuzela_filter](http://www.surfpoeten.de/tube/vuvuzela_filter) I read that the anoying Vuvuzela noise can be cancelled from the audio cast by a small-band-width filter at 233 Hz + octaves.

Can someone give a quick walk-thru how this could be done on a Mythbuntu setup?

Thanks!

derolf

---

### Post by gontofe on 2010-06-14
I spent ages trying to do this last night, eventually settling on playing alsa://pulse in vlc and trying the graphic equalizer. I couldn't, however get decent sound in VLC, it was very very stuttery. Couldn't help but think I was onto something, though...

Any ideas?

---

### Post by zebulon M on 2010-06-14
Here is something:

[http://fetzig.org/2010/06/13/vuvuzela-filter-using-fedora/](http://fetzig.org/2010/06/13/vuvuzela-filter-using-fedora/)

---

### Post by Chris Musampa on 2010-06-14
Viva la <snip>!

---

### Post by greybot on 2010-06-14
Found this Works very well. Use google translate to read

[http://indregard.no/2010/06/14/vuvuzela-demper/](http://indregard.no/2010/06/14/vuvuzela-demper/)

---

### Post by laffinet on 2010-06-15
> **greybot said:**
> Found this Works very well. Use google translate to read

[http://indregard.no/2010/06/14/vuvuzela-demper/](http://indregard.no/2010/06/14/vuvuzela-demper/)

Hm, tried to install but get this error message when tryin to run it:

```
pulseaudio-equalizer-gtk
Getting settings...
/usr/bin/pulseaudio-equalizer: line 111: pacmd: command not found
/usr/bin/pulseaudio-equalizer: line 112: pacmd: command not found
/usr/bin/pulseaudio-equalizer: line 116: pacmd: command not found
/usr/bin/pulseaudio-equalizer: line 124: pacmd: command not found
ls: cannot access /home/laffi/.pulse/presets/*.preset: No such file or directory
Traceback (most recent call last):
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 519, in <module>
    Equalizer()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 362, in __init__
    icon = self.window.set_icon_from_file("/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg")
glib.GError: Failed to open file '/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg': No such file or directory

```

Any ideas ?

---

### Post by peterlustig on 2010-06-15
This is how I did. 
First I [installed pulseaudio-equalizer]("http://digitizor.com/2010/02/08/how-to-install-system-wide-pulseaudio-equalizer-in-ubuntu-9-10-and-10-04/")
Then I adapted the frequencies in the equalizer. Just change some settings in ~/.pulse/equalizerrc
This is how mine looks:
```

mbeq_1197
mbeq
Multiband EQ
1.0

1
0
-70
30
15
0
0
0
-70.0
0
-70.0
0
-70.0
0
-70.0
0
0
0
0
0
50
100
156
233
311
466
622
932
1250
1864
2500
3500
5000
10000
20000

```

Then start pulseaudio-equalizer-gtk and activate the equalizer. Done.
gOOD LUCK :)
Peter

---

### Post by peterlustig on 2010-06-15
hi laffinet, 
please check, if pulseaudio-utils is installed
```

sudo apt-get install pulseaudio-utils

```
It looks like pacmd, which is a part of that package, is not installed on your system.
Cheers!
Peter

---

### Post by laffinet on 2010-06-15
> **peterlustig said:**
> 

Then start pulseaudio-equalizer-gtk and activate the equalizer. Done.
gOOD LUCK :)
Peter

That's where my problem is, I can't start the equalizer. See the output in the terminal in my post above.

---

### Post by laffinet on 2010-06-15
Getting closer, but now I get this error

```
The following packages have unmet dependencies:
  pulseaudio-utils: Depends: libpulse-browse0 (>= 0.9.8) but it is not going to be installed
                    Depends: libpulse0 (= 1:0.9.19-0ubuntu4.1) but 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 is to be installed

```

---

### Post by laffinet on 2010-06-15
OK, I forced the libpulse0 version, installed pulseaudio-utils, now I get the following:

```
pulseaudio-equalizer-gtk
Getting settings...
No PulseAudio daemon running, or not running as session daemon.
No PulseAudio daemon running, or not running as session daemon.
No PulseAudio daemon running, or not running as session daemon.
No PulseAudio daemon running, or not running as session daemon.
ls: cannot access /home/laffi/.pulse/presets/*.preset: No such file or directory
Traceback (most recent call last):
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 519, in <module>
    Equalizer()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 362, in __init__
    icon = self.window.set_icon_from_file("/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg")
glib.GError: Failed to open file '/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg': No such file or directory

```

---

### Post by laffinet on 2010-06-15
Ok, looks like I don't have pulseaudio installed (I'm obviously running mythbuntu).

Since I read about a few people having problems with pulseaudio and mythbuntu I'm wondering if I should risk installing pulseaudio. 

I don't want to cause other audio issues by installing pulseaudio. Any thoughts ?

---

### Post by Milos_SD on 2010-06-15
Can this be done if sound is coming directly from tv card to sound card with CD audio cable, so it doesn't use pulseaudio, just a sound directly from /dev/dsp ?

---

### Post by yusufk on 2010-06-15
Hi,

I think I've found an easier way to implement a vuvuzela filter, see here: [http://www.yusufk.za.net/?p=520](http://www.yusufk.za.net/?p=520)

Regards,
Yusuf

---

### Post by peterlustig on 2010-06-15
Hi Yusuf,
thanks! Does your approach work in real-time, while playing some tv-program in e.g. mplayer or me-tv?
Peter

---

### Post by peterlustig on 2010-06-15
HI Laffinet,
I don't know what installing pulse might do to your system, but maybe you want to try the mplayer filter at the end of the link in post [#3]("http://ubuntuforums.org/showpost.php?p=9458854&postcount=3"). The original seems to be from [here]("http://pastebin.com/KunkS0uk"). It's not perfect, but I don't know of any better way when not using pulse.
```

mplayer -af pan=1:0.5:0.5,sinesuppress=233:0.01,sinesuppress=466:0.01,sinesuppress=932:0.01,sinesuppress=1864:0.01,sinesuppress=232:0.01,sinesuppress=465:0.01,sinesuppress=931:0.01,sinesuppress=1863:0.01,sinesuppress=234:0.01,sinesuppress=467:0.01,sinesuppress=933:0.01,sinesuppress=1865:0.01

```
Good luck!
Peter

---

### Post by peterlustig on 2010-06-15
Hi Milos,
if I understand correctly, the pulseaudio-equalizer way should work for you, since pulseaudio-equalizer is a system-wide equalizer.
Peter

---

### Post by Milos_SD on 2010-06-15
> **peterlustig said:**
> Hi Milos,
if I understand correctly, the pulseaudio-equalizer way should work for you, since pulseaudio-equalizer is a system-wide equalizer.
Peter

I have system-wide equalizer, but it doesn't afect tvtime audio. It uses audio directly from tv card to sound card via inner CD audio cable.

---

### Post by gnuthor on 2010-06-16
Filters out B flat and its multiples, it's not perfect but reduces the Vuvu noise quite a bit.

_Mini HOWTO for Lucid_
> 
[LIST=1]
[*]Install **pulseaudio-equalizer** as described here: [http://www.webupd8.org/2010/02/pulseaudio-system-wide-equalizer-now.html](http://www.webupd8.org/2010/02/pulseaudio-system-wide-equalizer-now.html) if you don't have it yet

[*]Download the attached preset file into **~/.pulse/presets** and rename it to **Vuvuzela.preset**

[*]Start **Applications/Sounds&Video/PulseAudio-Equalizer**, select Vuvuzela preset, enable and apply settings

[*]Prepare to be labelled intolerant or worse  [-X

[/LIST]


Based on Vuvuzela frequency infos posted by Tube of of surfpoeten.de.

**Update** Oops didn't read the post by "peterlustig" before posting this, my file does more or less the same thing
**Update2** If you f*k up your pulseaudi-equalizer settings just stop the app, delete ~/.pulse/equalizerrc.availablepresets and ~/.pulse/equalizerrc and restart

---

### Post by Neon Dusk on 2010-06-16
There's a patch for MythTV [here](http://svn.mythtv.org/trac/ticket/8568) - although it's only for trunk.

---

### Post by dakota34 on 2010-06-16
Looks like JYA has updated the [above referenced patch]("http://svn.mythtv.org/trac/ticket/8568") for 23-fixes! Anyone know how long it will take b4 it's available through mythbuntu .23 repos ....?

---

### Post by Neon Dusk on 2010-06-16
The patch hasn't been comitted. 

So unless JYA commits it to the 0.23-fixes branch or the MythBuntu devs include it in their 0.23-fixes build you'll need to add the patch yourself.

---

### Post by jyavenard on 2010-06-17
> **Neon Dusk said:**
> The patch hasn't been comitted. 

So unless JYA commits it to the 0.23-fixes branch or the MythBuntu devs include it in their 0.23-fixes build you'll need to add the patch yourself.

Hi..

It won't be committed, not even the trunk version...

I've added it to my 0.23-release build and my trunk build on my repo:
[http://www.avenard.org/media](http://www.avenard.org/media)

Will remove it after the world cup..

There's still a bug in the 0.23-release patch with multi-channels AC3 ... Need to track this down a bit further.

Shortly I will upload a new patch, a bit more severe removal..

---

### Post by azmyth on 2010-06-17
Hi, Can you make current patch available for 0.23 fixes? The current filter still lets a fair amount pass and boy those vuvuzelas are horrible.

---

### Post by azmyth on 2010-06-17
Thank you.

---

### Post by hgghfnvk on 2010-06-18
> **jyavenard said:**
> I've added it to my 0.23-release build and my trunk build on my repo:
[http://www.avenard.org/media](http://www.avenard.org/media)


I added your repository and upgraded all mythtv packages (deselected all the other ones) but I can't hear any difference. Do I need to activate the filter somewhere? I thought there will be an option menu, but there's nothing.

---

### Post by Neon Dusk on 2010-06-18
From the MythTv trac [ticket](http://svn.mythtv.org/trac/ticket/8568)

> 
How to use it: Go to the settings -> general in the audio section. Activate Advanced Audio and check the Vuvuzela box. Validate all pages to the end.

Now when watching a game, press menu, you'll see an entry "Toggle Vuvuzela Filter"

The vuvuzela filter is disabled by default, and needs to be manually enabled each time 


Do you see the Vuvuzela option in Settings -> General -> [audio page] when 'Activate Advanced audio' is enabled?

---

### Post by hgghfnvk on 2010-06-18
> **Neon Dusk said:**
> From the MythTv track [ticket]("http://svn.mythtv.org/trac/ticket/8568")



Do you see the Vuvuzela option in Settings -> General -> [audio page] when 'Activate Advanced audio' is enabled?

Yes, now I can see it. Have to play with it later to see what difference it makes.

Thanks for pointing me into the right direction.

---

### Post by jastonas on 2010-06-21
Just tested the pulseaudio-equaliser and it makes a difference.

---

