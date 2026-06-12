---
title: "Problem with soundcard after upgrade"
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by chjustc on 2006-11-10
I use Kubuntu Edgy on a IBM T41 laptop.  I recently upgraded my system from Dapper to Edgy.  After the upgrading, I can hear sound when playing movie from YouTube.com and hear BEEP when hitting TAB in a shell, but I can not open any mp3 or other audio files on my hard disk.  For example, when I open any mp3 file by using xmms player, I get the following message:

Please check that:
Your soundcard is configured properly
You have the correct plugin selected
No other program is blocking the soundcard


When I use other players, such Kaffeine, it simply has no response.

I followed the procedure step by step from the Comprehensive Sound Problem Solutions Guide at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449), but the problem still persists.

When I type the command aplay -l
in a shell, I have the following soundcards listed
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I also unmuted everything in alsamixer.  And, I can see my sound card listed as Intel 82801DB-ICH4 in the alsamixer.

My sound card works in Windows, so it should not be a problem in BIOS.  

Please help!  Thanks in advance.

---

### Post by ReaderRat on 2006-11-10
Did you install the 'intel8x0" driver for 82810 ICH4 audio? If so, good. If not, see the Sound Solutions Guide again. It is an ALSA driver.

---

### Post by henriqueqc on 2006-11-10
To do the check list suggest by the XMMS "error":

"You have the correct plugin selected":
Go inside XMMS in (Options > Preferences > Output Plugin) And try selecting other plug-ins.

"No other program is blocking the sound card":
Try using the command "fuser /dev/dsp" to list the processes locking the sound card device (if any).

Alternatively you can change the Sound Device (Music and Movies) inside the Sound Preferences. Go to "System > Preferences > Sound"

I hope I could help.

Good Luck!

---

### Post by chjustc on 2006-11-12
> **ReaderRat said:**
> Did you install the 'intel8x0" driver for 82810 ICH4 audio? If so, good. If not, see the Sound Solutions Guide again. It is an ALSA driver.

Yes, I did install the 'intel8x0' driver for 82810 ICH4 audio if you are referring to the tips offered in section of ALSA driver Compilation of the Comprehensive Sound Problem Solutions Guide.

Actually, I have managed to solve the problem by changing the output plugin in XMMS to ALSA 1.2.10 output plugin.

Thank you for your help.

---

### Post by chjustc on 2006-11-12
> **henriqueqc said:**
> To do the check list suggest by the XMMS "error":

"You have the correct plugin selected":
Go inside XMMS in (Options > Preferences > Output Plugin) And try selecting other plug-ins.

"No other program is blocking the sound card":
Try using the command "fuser /dev/dsp" to list the processes locking the sound card device (if any).

Alternatively you can change the Sound Device (Music and Movies) inside the Sound Preferences. Go to "System > Preferences > Sound"

I hope I could help.

Good Luck!

Thanks!  This works.  I changed output plugin to ALSA 1.2.10 output plugin in XMMS, and XMMS plays any mp3 files just fine right now.

When I type the command "fuser /dev/dsp", nothing happens.

I can not find Preferences under System as you indicate.  Are you using Kubuntu too?

Thank you anyway!

---

### Post by henriqueqc on 2006-11-12
Sorry I haven't notice that you were using Kubuntu. I use Ubuntu, my mistake.

Glad I could help.

---

