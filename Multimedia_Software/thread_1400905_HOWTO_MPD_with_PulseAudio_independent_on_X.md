---
title: "HOWTO: MPD with PulseAudio independent on X"
date: 2010-02-07
forum: Multimedia Software
---

### Post by unimatrix on 2010-02-07
[SIZE="5"]_About:_[/SIZE]
This tutorial is meant for Ubuntu 9.10 Karmic Koala, but it might work in earlier or later versions as well. I wrote this tutorial mostly because it took me a full day of work using lots of help from people on #mpd and #pulseaudio from the FreeNode IRC server.

[SIZE="5"]_Goal:_[/SIZE]
The goal is to get the MPD daemon working using PulseAudio, but without it being dependent on the X server or a session. To do that we must configure PulseAudio to run in system-wide daemon mode (which is not recommended by the developers, but in this case we do not have a choice). This means it will be using the */etc/pulse/system.pa* config file instead of the usual */etc/pulse/default.pa*. We must also make sure the appropriate user/group permissions are set, or PulseAudio will be rejecting the connections.
The result will be an interrupt-less music environment, not dependent on the X server. Meaning we can for example log out and log in without the music having to stop for even a second. Switching TTYs (Ctrl+Alt+Fx) will also keep the music playing (not possible by default). All that and PulseAudio will still be able to detect and configure all your devices automatically.

[SIZE="5"]_Instructions:_[/SIZE]
[LIST=1]
[*] 
Make sure you add your username to the following system groups: *pulse*, *pulse-access* and *audio*.
Do that by going to *System* --> *Administration* --> *Users and Groups*.
Click the unlock button (the one with a picture of some keys), then click *Manage Groups*. In the list of groups that pops up, for each of the previously mentioned groups click "Properties" and select all the users that you want to have this functionality.

[*]
Press Alt+F2 and type:
> gksudo gedit /etc/default/pulseaudio

Change **PULSEAUDIO_SYSTEM_START** from 0 to **1** and **DISALLOW_MODULE_LOADING** from 1 to **0**.

Save the file and close the editor.

[*]
(Since Ubuntu 10.04 Lucid Lynx, this step is no longer required. Instead download the attached *system.pa* file and place it in your */etc/pulse* folder.)
Press Alt+F2 and type:
> gksudo gedit /etc/pulse/system.pa
Find this section:
```

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

```
Change it to:
```

### Automatically load driver modules depending on the hardware available
.ifexists module-**udev**-detect.so
load-module module-**udev**-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

```

Save the file and close the editor.

[*] 
Install the MPD daemon and a MPD [client]("http://mpd.wikia.com/wiki/Clients") of your choice.
Open Synaptic Package Manager (System --> Administration --> Synaptic Package Manager) and find the **mpd** package and the client of your choice (my recommendation is the **[GMPC]("http://gmpc.wikia.com/wiki/Gnome_Music_Player_Client")** client). Mark the packages for installation and click Apply.

[*]
Press Alt+F2 and type:
> gksudo gpasswd -a mpd pulse-access

[*]
Press Alt+F2 and type:
> gksudo gedit /etc/mpd.conf
Find the following section:
```

audio_output {
	type		"alsa"
	name		"My ALSA Device"
	device		"hw:0,0"	# optional
	format		"44100:16:2"	# optional
	mixer_device	"default"	# optional
	mixer_control	"PCM"		# optional
	mixer_index	"0"		# optional
}

```
Make sure it is all _commented out_, by putting a **#** symbol in front of each line, so that it looks like this:
```

**#**audio_output {
**#**	type		"alsa"
**#**	name		"My ALSA Device"
**#**	device		"hw:0,0"	# optional
**#**	format		"44100:16:2"	# optional
**#**	mixer_device	"default"	# optional
**#**	mixer_control	"PCM"		# optional
**#**	mixer_index	"0"		# optional
**#**}

```
Then in the same file, add the following:
```

audio_output {
	type		"pulse"
	name		"MPD PulseAudio Stream"
}

```

Save the file and close the editor.

[*] Make sure MPD gets started **after** PulseAudio on boot time! Do this by properly renaming the *S30mpd* (it could have a different number) file in */etc/rc2.d*, */etc/rc3.d*, */etc/rc4.d* and */etc/rc5.d* to one with a number higher than that of *S50pulseaudio*. I suggest *S60mpd*.

[*] Reboot your computer and you should be able to use MPD via PulseAudio without any interferences when switching TTYs or when killing the whole X server.
[/LIST]

[SIZE="5"]_Additional Information:_[/SIZE]
[LIST]
[*][http://wiki.archlinux.org/index.php/PulseAudio#System-wide_daemon]("http://wiki.archlinux.org/index.php/PulseAudio#System-wide_daemon")
[*][http://mpd.wikia.com/wiki/PulseAudio]("http://mpd.wikia.com/wiki/PulseAudio")
[*][https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/192735]("https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/192735")
[/LIST]

---

### Post by cIIIz on 2010-02-07
wow good stuff mate :) keep up the good work :D

---

### Post by unimatrix on 2010-02-08
> **cIIIz said:**
> wow good stuff mate :) keep up the good work :D
Thanks! :)

On a side note:
It would be nice if someone was willing to test everything just to confirm it works everywhere.

---

### Post by tekknokrat on 2010-03-06
Hi,

thank you for the howto. 
The first steps works great to make pulseaudio running independently.

For running mpd with pulseaudio (listed in pavucontrol) it was neccessary to enable network access to local audio devices. This can be done via paprefs or with editing /etc/pulseaudio/system.pa

Put in this line in system.pa somewhere beneath ### Load several protocols:
```

load-module module-native-protocol-tcp

```

For authentication you can choose to either copy the .pulse-cookie in mpd's home dir afterwards or enable unauthorized access (in paprefs a setting beyond network access or with editing system.pa again).

copy cookie (recommended):
```
cp ~/.pulse-cookie /var/lib/mpd/
```
(Btw. the article In Arch's wiki also describes how to define a global cookie place in /etc/pulse/client.conf as an alternative.)

change to unauthorized access in system.pa (unsafe, not recommended):
```

load-module module-native-protocol-tcp auth-anonymous=1

```

Optionally, you can configure the sink in mpd.conf
Use ```
pactl stat
``` to determine the sink and put it in the config:
> Default Sink: alsa_output.pci-0000_00_14.2.analog-stereo

mpd.conf:
```
audio_output {
        type    "pulse"
        name    "My MPD PulseAudio Output"
        server  "127.0.0.1"   # optional
#       sink    "alsa_output" # optional
        sink    "alsa_output.pci-0000_00_14.2.analog-stereo"
}

```

Best,
tekknokrat

---

### Post by unimatrix on 2010-03-06
Thank you for the much needed additional information and details, tekknokrat.

I just have one comment. You talk about editing default.pa. Are you sure about that? Since pulse will be running in system wide mode, shouldnt you be editing system.pa?

---

### Post by tekknokrat on 2010-03-07
> **unimatrix said:**
> Thank you for the much needed additional information and details, tekknokrat.

I just have one comment. You talk about editing default.pa. Are you sure about that? Since pulse will be running in system wide mode, shouldnt you be editing system.pa?

Hi unimatrix,
you're absolutely right. I did revert the settings from systemmode to usermode again after testing your instruction, that's why I was putting my config in default.pa all the time. 

Just saw that system.pa still has the the load-module module-hal-detect. I did misread the conffile in your instructions. Will edit my comments, thank you for pointing that out!

---

### Post by lancerocke on 2010-05-10
> **tekknokrat said:**
> Hi,

thank you for the howto. 
The first steps works great to make pulseaudio running independently.

For running mpd with pulseaudio (listed in pavucontrol) it was neccessary to enable network access to local audio devices. This can be done via paprefs or with editing /etc/pulseaudio/system.pa

Put in this line in system.pa somewhere beneath ### Load several protocols:
```

load-module module-native-protocol-tcp

```

For authentication you can choose to either copy the .pulse-cookie in mpd's home dir afterwards or enable unauthorized access (in paprefs a setting beyond network access or with editing system.pa again).

copy cookie (recommended):
```
cp ~/.pulse-cookie /var/lib/mpd/
```
(Btw. the article In Arch's wiki also describes how to define a global cookie place in /etc/pulse/client.conf as an alternative.)

change to unauthorized access in system.pa (unsafe, not recommended):
```

load-module module-native-protocol-tcp auth-anonymous=1

```

Optionally, you can configure the sink in mpd.conf
Use ```
pactl stat
``` to determine the sink and put it in the config:


mpd.conf:
```
audio_output {
        type    "pulse"
        name    "My MPD PulseAudio Output"
        server  "127.0.0.1"   # optional
#       sink    "alsa_output" # optional
        sink    "alsa_output.pci-0000_00_14.2.analog-stereo"
}

```

Best,
tekknokratmy '/etc/pulseaudio/system.pa' was blank

---

### Post by unimatrix on 2010-05-10
> **lancerocke said:**
> my '/etc/pulseaudio/system.pa' was blank

Was that on Lucid?

---

### Post by lancerocke on 2010-05-10
> **unimatrix said:**
> Was that on Lucid?yes

---

### Post by unimatrix on 2010-05-10
> **lancerocke said:**
> yes

I've uploaded *system.pa* to the main post.

---

### Post by Atermoon on 2010-05-11
Thanks **a lot** for this howto! It's the only thing that worked for me in Lucid after hours of trying this and that with zero success.

---

