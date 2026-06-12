---
title: "Problem with playing a Moonlight-stream"
date: 2010-10-04
forum: Multimedia Software
---

### Post by orrie on 2010-10-04
I've having a problem with (probably) Moonlight.
After my understandings, TV2 is using Silverlight.

[i]System-info:
Linux laptop 2.6.32-24-generic-pae #42-Ubuntu SMP Fri Aug 20 15:37:22 UTC 2010 i686 GNU/Linux
Description:	Ubuntu 10.04.1 LTS[/i]

I'm trying to play [this](http://www.tv2sporten.no/fotball/tippeligaen/husker-du-denne-andresen-3305732.html) without any results.
Have also installed the Mozilla/VLC-plugin and this is just saying "waiting for video..".

And I've also tried to install the plugin on go-mono.com without any positive results.

How can I get this video to play?

---

### Post by directhex on 2010-10-04
Try running your browser in a terminal - watch for errors from Moonlight

---

### Post by SeijiSensei on 2010-10-04
If it's from a television network, chances are good it won't play at all in Moonlight.  It probably requires authentic MS Silverlight with its built-in digital rights management features.  Does the network's web site say they support anything other than MS Silverlight?  What does it say about Mac users?

---

### Post by orrie on 2010-10-04
> **SeijiSensei said:**
> If it's from a television network, chances are good it won't play at all in Moonlight.  It probably requires authentic MS Silverlight with its built-in digital rights management features.  Does the network's web site say they support anything other than MS Silverlight?  What does it say about Mac users?

This stream will be available for everyone, without any authentication.
I'm suspecting that just the Windows-platform is supported, but I'm not sure.


> **directhex said:**
> Try running your browser in a terminal - watch for errors from Moonlight
Attempting to load libmoonloaderxpi 
Moonlight: no audio capture service available
Moonlight: Installing signal handlers for crash reporting.
Moonlight: Enabling MONO_DEBUG=keep-delegates,reverse-pinvoke-exceptions and MOONLIGHT_ENABLE_CONSOLE=1
Using the ff3 bridge
Moonlight: Plugin AppDomain Creation: OK
Moonlight: setting option emulatekeycodes to 0
Moonlight: setting option clipping to 0
Moonlight: setting option bbox to 0
Moonlight: setting option textbox to 0
Moonlight: setting option occlusion-culling to 1
Moonlight: setting option cache to 0
Moonlight: setting option backend to 1
Moonlight: setting option keepmedia to 0
Moonlight: setting option effects to 1
Moonlight: setting option projections to 1
Moonlight: setting option curlbridge to 0
Moonlight: setting option ooblauncher to 0
&#65279;trying to load: /System.Windows;component/themes/generic.xaml
Created ClipPlayerViewModel: 04.10.10 23.52.14 +2
Shutting down
NOTE: child process received `Goodbye', closing down

---

### Post by directhex on 2010-10-04
Hm, try filing a bug with the Novell bugzilla

---

### Post by littlepeon on 2010-10-05
unfortunately moonlight is NOT 100% compatible with MS silverlight..but it is getting closer and closer with every release. too bad silverlight is a knockoff of flash and has its own problems on windows computers.
all i can tell you is to update to the most recent ppa of moonlight and keep ur fingers crossed and it might work. i've had many problems with silverlight on windows platform, but you might need a windows computer to work with your tv site as orrie suggested.

good luck
-Peon

---

### Post by Old_Man_Unix on 2010-10-05
Moonlight is the open-source free  application based on  Microsoft Silverlight.  The current stable release of Moonlight, and the one that is available in the repositories,  tracks ***Silverlight 2***.

The current release from Microsoft is ***Silverlight 3***. 

See a potential problem there?  I do.

---

### Post by rattskjelke on 2010-10-12
A few months ago I somehow got 10.04 to play the Silverlight content on tv2.no. I followed the instructions in this outdated thread: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) several times and it started working. Unfortunately I did not doucument what I did to enable it. This week I upgraded to 10.10 and it broke. If I figure this out I will post it here.

---

### Post by rattskjelke on 2010-10-13
Today I fixed my problem. I did a clean install of ubuntu 10.10, installed ubuntu-restricted-extras and gecko-mediaplayer. The streaming video on tv2.no now works.

---

### Post by orrie on 2010-10-15
> **rattskjelke said:**
> Today I fixed my problem. I did a clean install of ubuntu 10.10, installed ubuntu-restricted-extras and gecko-mediaplayer. The streaming video on tv2.no now works.

Yeah. That did solve the problem. Cheers.


```

sudo apt-get install ubuntu-restricted-extras gecko-mediaplayer

```

---

