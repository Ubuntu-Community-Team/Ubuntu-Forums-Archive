---
title: "Numerous weird issues with Rhythmbox"
date: 2013-05-24
forum: Multimedia Software
---

### Post by Sprakle on 2013-05-24
I've had many weird possibly related issues with Rhythmbox. I created a bug report for one, but I figure that with so many, I must simply have something wrong on my end.
These problems did not occur in Ubuntu 12.04 (Except for one, and then very rarely). After fresh installing 13.04, all these issues manifested immediately.

List of issues:
[LIST]
[*]If the music is paused and resumed, Rhythmbox will skip ahead for the exact amount of time that music had been playing previously. This happens every time. Example: 1) Play music for 10 minutes. 2) Pause music. 3) Resume music. 4) Rhythmbox will seek through exactly 10 minutes of music, possibly over multiple tracks. I have the debug output of this happening here: [https://gist.github.com/Sprakle/5522966](https://gist.github.com/Sprakle/5522966)
[*]Often, after pressing next, Rhythmbox will play the next track, but not stop the first one. This results in many tracks playing at once. (This would vary rarely happen on 12.04) Debug output: [https://gist.github.com/Sprakle/2fcfdb883567ccc65448](https://gist.github.com/Sprakle/2fcfdb883567ccc65448)
[*]Often, after manually seeking to a part of a track (this includes pressing previous), the seconds and seek head will advance, but no audio will play. Pausing and resuming will fix this.
[*]Constant freezing up after user input. Using xkill usually leaves the Rhythmbox process running, so it must be terminated manually using kill
[/LIST]

Apport Info:
[COLOR=#333333][FONT=Ubuntu Mono]DistroRelease: Ubuntu 13.04[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Package: rhythmbox 2.98-0ubuntu5[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]ProcVersionSign[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]ature: Ubuntu 3.8.0-19.30-generic 3.8.8[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Uname: Linux 3.8.0-19-generic x86_64[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]NonfreeKernelMo[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]dules: fglrx[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]ApportVersion: 2.9.2-0ubuntu8[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Architecture: amd64[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Date: Sun May 5 18:06:03 2013[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]InstallationDate: Installed on 2013-05-03 (2 days ago)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]InstallationMedia: Ubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]MarkForUpload: True[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]SourcePackage: rhythmbox[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]UpgradeStatus: No upgrade log present (probably fresh install)


[/FONT][/COLOR]

---

### Post by mojo636 on 2013-07-05
I get the pausing / resuming bug and found this bug report here - [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1133968](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1133968). Frustrating as I cant seem to find much information about it or any fixes and bug has been present for a long time.

---

