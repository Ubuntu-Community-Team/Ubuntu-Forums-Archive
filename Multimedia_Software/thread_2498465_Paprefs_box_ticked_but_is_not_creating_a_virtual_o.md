---
title: "Paprefs box ticked but is not creating a virtual output"
date: 2024-06-14
forum: Multimedia Software
---

### Post by vidtek on 2024-06-14
[SIZE=4] I'm using Kubuntu 24.04 Noble Numbat.

Paprefs simultaneous box ticked, but no virtual output created, nothing in pavcontrol and the little speaker icon bottom right on the taskbar right-clicked and show virtual devices is activated. [/SIZE]

---

### Post by thealchemist886 on 2024-07-02
Having the same problem. Any help?

---

### Post by vidtek on 2024-07-02
> **thealchemist886 said:**
> Having the same problem. Any help?

I've had no replies at all apart from yours.    I have tried everything I can think of with no results.    In the end I had to ditch Noble Numbat and revert to a backup of Jammy until such time as the devs can sort it out, I don't even know if theyt are aware of the issue.   I have no idea how to report this to the devs,  I've never done it, if you can help there please do it for both of us.

Cheers Tony.

---

### Post by #&amp;thj^% on 2024-07-02
> **vidtek said:**
>  I don't even know if theyt are aware of the issue.   I have no idea how to report this to the devs,  I've never done it, if you can help there please do it for both of us.

Cheers Tony.

They are aware: [https://www.kubuntuforums.net/forum/currently-supported-releases/kubuntu-24-04-nitpick-noble-lts/software-support-bg/680811-paprefs-simultaneous-box-ticked-but-no-source-created](https://www.kubuntuforums.net/forum/currently-supported-releases/kubuntu-24-04-nitpick-noble-lts/software-support-bg/680811-paprefs-simultaneous-box-ticked-but-no-source-created)

To file a Bug against it works like this:
```
 ubuntu-bug paprefs

```

BTW won't "pavucontrol" help with that?

---

### Post by vidtek on 2024-07-03
> **1fallen said:**
> They are aware: [https://www.kubuntuforums.net/forum/currently-supported-releases/kubuntu-24-04-nitpick-noble-lts/software-support-bg/680811-paprefs-simultaneous-box-ticked-but-no-source-created](https://www.kubuntuforums.net/forum/currently-supported-releases/kubuntu-24-04-nitpick-noble-lts/software-support-bg/680811-paprefs-simultaneous-box-ticked-but-no-source-created)

To file a Bug against it works like this:
```
 ubuntu-bug paprefs

```

BTW won't "pavucontrol" help with that?

pavucontrol  no help as in first post.

Thanks for the links, one is obviously my own at Kubuntuforums, I will do a bug report thanks.

Tony

---

### Post by #&amp;thj^% on 2024-07-03
What we need to remember is on 24.04 pulseaudio has been replaced now:
```
apt depends paprefs
paprefs
  Depends: gnome-icon-theme
  Depends: pulseaudio-module-gsettings
  Depends: pulseaudio-module-zeroconf
  Depends: libatkmm-1.6-1v5 (>= 2.28.4)
  Depends: libc6 (>= 2.34)
  Depends: libgcc-s1 (>= 3.3.1)
  Depends: libglib2.0-0t64 (>= 2.12.0)
  Depends: libglibmm-2.4-1t64 (>= 2.66.7)
  Depends: libgtk-3-0t64 (>= 3.0.0)
  Depends: libgtkmm-3.0-1t64 (>= 3.24.8)
  Depends: libpulse0 (>= 0.99.1)
  Depends: libsigc++-2.0-0v5 (>= 2.2.0)
  Depends: libstdc++6 (>= 5.2)

```

---

### Post by vidtek on 2024-07-03
> **1fallen said:**
> What we need to remember is on 24.04 pulseaudio has been replaced now:
```
apt depends paprefs
paprefs
  Depends: gnome-icon-theme
  Depends: pulseaudio-module-gsettings
  Depends: pulseaudio-module-zeroconf
  Depends: libatkmm-1.6-1v5 (>= 2.28.4)
  Depends: libc6 (>= 2.34)
  Depends: libgcc-s1 (>= 3.3.1)
  Depends: libglib2.0-0t64 (>= 2.12.0)
  Depends: libglibmm-2.4-1t64 (>= 2.66.7)
  Depends: libgtk-3-0t64 (>= 3.0.0)
  Depends: libgtkmm-3.0-1t64 (>= 3.24.8)
  Depends: libpulse0 (>= 0.99.1)
  Depends: libsigc++-2.0-0v5 (>= 2.2.0)
  Depends: libstdc++6 (>= 5.2)

```


Replaced with what?  Why?  How do we get simultaneous/dual output now?   Sorry if I seem a bit dim, but what have they actually done, can you give me more details please?   Why have you listed the dependencies for pulseaudio?

Confused, Tony.

---

### Post by #&amp;thj^% on 2024-07-03
Replaced with Wireplumber and Pipewire:
```
apt policy pulseaudio
pulseaudio:
  Installed: (none)
  Candidate: 1:16.1+dfsg1-5.1ubuntu1
  Version table:
     1:16.1+dfsg1-5.1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
     1:16.1+dfsg1-2ubuntu10 -1
        100 /var/lib/dpkg/status

```
I listed the Deps to paprefs and not pulseaudio to show you why.

If you need  simultaneous/dual outputs use:
```
 pactl load-module module-combine-sink
```

---

### Post by vidtek on 2024-07-04
> **1fallen said:**
> Replaced with Wireplumber and Pipewire:
```
apt policy pulseaudio
pulseaudio:
  Installed: (none)
  Candidate: 1:16.1+dfsg1-5.1ubuntu1
  Version table:
     1:16.1+dfsg1-5.1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
     1:16.1+dfsg1-2ubuntu10 -1
        100 /var/lib/dpkg/status

```
I listed the Deps to paprefs and not pulseaudio to show you why.

If you need  simultaneous/dual outputs use:
```
 pactl load-module module-combine-sink
```

I already tried that command with zero results,  No sink created.  Mind you that was after trying all sorts of random ideas from Google.....EDIT.  Just tried again with a clean Noble backup - it definitely does not work.   The main issue seems to be tying the sink to the headphones, the headphones just do not show up in the audio settings, although paired correctly in bluetooth.

---

### Post by #&amp;thj^% on 2024-07-04
Something is wrong then, that command works on my systems Arch, BSD, Debian, and Ubuntu, with Wireplumber.
```
wpctl status|grep blue
 &#9474;     101. SRS-XB22                            [bluez5]
 &#9474;     109. output[COLOR="#B22222"].combined[/COLOR]_bluez_output.F8_DF_15_7F_64_73.1             [Stream/Output/Audio]
 &#9474;     102. bluez_capture_internal.F8:DF:15:7F:64:73                     [Stream/Input/Audio/Internal]
 &#9474;  *  105. bluez_input.F8:DF:15:7F:64:73                                [Audio/Source]

```
```
wpctl status|grep [COLOR="#B22222"]combined[/COLOR]
 &#9474;  *   42. combined                                                     [Audio/Sink]
 &#9474;      58. output.[COLOR="#B22222"]combined_[/COLOR]alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-surround-41 [Stream/Output/Audio]
 &#9474;      62. output.[COLOR="#B22222"]combined[/COLOR]_alsa_output.pci-0000_06_00.6.analog-stereo   [Stream/Output/Audio]
 &#9474;     109. output.[COLOR="#B22222"]combined[/COLOR]_bluez_output.F8_DF_15_7F_64_73.1             [Stream/Output/Audio]
         0. Audio/Sink    combined

```

Have you yet tried to revert to pulseaudio?

---

### Post by vidtek on 2024-07-05
Yes tried reverting to pulseaudio but still not working on Noble Numbat. I have spent too long of my life on this, and I haven't got an awful lot of it left!    I'm going to leave it there and hope that it is sorted before the demise of Jammy.

Pulse has been working well for years, why oh why do they have to change it for something that doesn't quite work yet?   By all means if it's a drop-in replacement with more features, but this looks like change just for the sake of change.

Tony.

---

