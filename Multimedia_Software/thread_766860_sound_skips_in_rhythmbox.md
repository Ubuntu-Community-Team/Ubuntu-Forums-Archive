---
title: "sound skips in rhythmbox"
date: 2008-04-25
forum: Multimedia Software
---

### Post by markp1989 on 2008-04-25
when listening to music in rhythmbox, if i open a new program the music skips. or if i unminimise a window the music skips

is there a way to stop this happening? 

thankyou

---

### Post by SveinT on 2008-04-25
I have the same problem, except it only occours when scrolling webpages. Only appears with rhythmbox. Anyone knows how to fix it? Didn't have this problem in gutsy.

-edit-

Spoke too soon, I have this problem playing music in totem aswell. I guess it applies to all sound playing on my system. Rather annoying.

-edit2-
Switched from nv to nvidia video driver and problem is gone. I guess the scrolling took too much resources somehow.

---

### Post by markp1989 on 2008-04-25
i disabled Evolution alarm notifier in sessions preferences and it stoped music skipping, and made scrolling more smooth

---

### Post by lonewolf72 on 2008-04-27
> **SveinT said:**
> I have the same problem, except it only occours when scrolling webpages. Only appears with rhythmbox. Anyone knows how to fix it? Didn't have this problem in gutsy.

-edit-

Spoke too soon, I have this problem playing music in totem aswell. I guess it applies to all sound playing on my system. Rather annoying.

-edit2-
Switched from nv to nvidia video driver and problem is gone. I guess the scrolling took too much resources somehow.


I am using the nvidia driver, yet every time i switch windows or tabs I get a skip in the music playback.  Seems to only happen in some players (prefer amarok, tried exaile, both skip).  No skips in Rhythmbox... very strange...

edit: after further review, Rhythmbox skips as well... very annoying... this didn't happen when i had upgraded from kubuntu gutsy to hardy and then switched to ubuntu hardy.  this has happened after i did a full clean install of Ubuntu Hardy...


Specs:
Motherboard: ASUS A8V
CPU: AMD Athlon(tm) 64 Processor 3200+
Memory: PC3200 1GB
Video: GeForce FX 5200
Audio VT8233/A/8235/8237 AC97 Audio Controller

Hard Drive: System is installed on a Western Digital ATA 100
		Music is playing off a Western Digital SATA Drive

---

### Post by obbe on 2008-04-27
i've the same problem since i've upgraded from gusty to hardy.. any way to fix it? :cry:

---

### Post by psyke83 on 2008-04-27
[COLOR="Red"]EDIT: The information in this post is obsolete. Please take a look at my PulseAudio HOWTO here: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

This HOWTO provides information on most of the issues surrounding PulseAudio in Hardy and offers possible fixes, or failing that, links to the relevant bug reports. Please see if it helps.

----------------------------
[/COLOR]

I have a possible solution.

Make sure Rhythmbox is closed, then open a terminal. Then, pkill the "pulseaudio" process and launch Rhythmbox again, and see if the skipping stops. So:

```
$ pkill pulseaudio
$ rhythmbox
```

If the above worked, then this next part will allow you to use PulseAudio without annoying skips:

Make a backup and then edit /etc/pulse/daemon.conf, and replace the lines at the end of your config with the following in red:

```
; default-sample-format = s16le
[COLOR="Red"]default-sample-rate = 48000[/COLOR]
; default-sample-channels = 2

[COLOR="Red"]default-fragments = 8[/COLOR]
[COLOR="Red"]default-fragment-size-msec = 10[/COLOR]
```

Now, log out and log back in, then run Rhythmbox normally. If this works, please let me know the name of your sound card, i.e. the output of:

```
lspci | grep audio
```

Thanks!

---

### Post by meanburrito920 on 2008-04-27
I've had this problem too, but it generally occurs when a process spikes the CPU, such as when I am changing desktops or opening firefox and such. I think the issue is just simply that rhythmbox is not getting enough processor cycles to play smoothly. Unfortunately, rhythmbox uses about 16% of my CPU so it doesnt take much to make it skip. Unlike windoze, Linux processes cant grab the cycles they need away from other programs, which is good in most cases, except for real-time programs.

---

### Post by psyke83 on 2008-04-27
> **meanburrito920 said:**
> I've had this problem too, but it generally occurs when a process spikes the CPU, such as when I am changing desktops or opening firefox and such. I think the issue is just simply that rhythmbox is not getting enough processor cycles to play smoothly. Unfortunately, rhythmbox uses about 16% of my CPU so it doesnt take much to make it skip. Unlike windoze, Linux processes cant grab the cycles they need away from other programs, which is good in most cases, except for real-time programs.

If users are noticing skipping audio that never previously occurred (i.e. in Gutsy or prior versions), it's 99% certain to be due to the new PulseAudio system in place that most applications use to output sound.

---

### Post by meanburrito920 on 2008-04-27
I'm using Gusty still though. (at least on the comp I'm noticing the problems on)

---

### Post by ssander on 2008-04-28
> **psyke83 said:**
> I have a possible solution.

Make sure Rhythmbox is closed, then open a terminal. Then, pkill the "pulseaudio" process and launch Rhythmbox again, and see if the skipping stops. So:

```
$ pkill pulseaudio
$ rhythmbox
```

If the above worked, then this next part will allow you to use PulseAudio without annoying skips:

Make a backup and then edit /etc/pulse/daemon.conf, and replace the lines at the end of your config with the following in red:

```
; default-sample-format = s16le
[COLOR="Red"]default-sample-rate = 48000[/COLOR]
; default-sample-channels = 2

[COLOR="Red"]default-fragments = 8[/COLOR]
[COLOR="Red"]default-fragment-size-msec = 10[/COLOR]
```

Now, log out and log back in, then run Rhythmbox normally. If this works, please let me know the name of your sound card, i.e. the output of:

```
lspci | grep audio
```

Thanks!


Thank you, that did the trick in my case!

my sound card: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)

---

### Post by obbe on 2008-04-28
thanks psyko83, it's better now but i still got that sound skips, that's my sound card tho
C-Media Electronics Inc CM8738 (rev 10)

---

### Post by elfgoh on 2008-04-28
Hi I had similar problems and this thread may help:

[http://ubuntuforums.org/showthread.php?p=4823123#post4823123](http://ubuntuforums.org/showthread.php?p=4823123#post4823123)

---

### Post by jimix on 2008-04-28
this worked for me!  here is the output from lspci

edit: ok its not fixed entirely, but much better

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

---

### Post by abds on 2008-04-28
Killing the process worked for me... But editing the file does not help... When I rebooted, it just got back to where it was. Maybe I should just kill the process every time I boot?

Output of "lspci | grep audio"

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)

---

### Post by markp1989 on 2008-04-28
> **psyke83 said:**
> I have a possible solution.

Make sure Rhythmbox is closed, then open a terminal. Then, pkill the "pulseaudio" process and launch Rhythmbox again, and see if the skipping stops. So:

```
$ pkill pulseaudio
$ rhythmbox
```

If the above worked, then this next part will allow you to use PulseAudio without annoying skips:

Make a backup and then edit /etc/pulse/daemon.conf, and replace the lines at the end of your config with the following in red:

```
; default-sample-format = s16le
[COLOR="Red"]default-sample-rate = 48000[/COLOR]
; default-sample-channels = 2

[COLOR="Red"]default-fragments = 8[/COLOR]
[COLOR="Red"]default-fragment-size-msec = 10[/COLOR]
```

Now, log out and log back in, then run Rhythmbox normally. If this works, please let me know the name of your sound card, i.e. the output of:

```
lspci | grep audio
```

Thanks!

seemed the stop skiping here aswell, thanks 

```
mark@mark-desktop:~$ lspci | grep audio
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
mark@mark-desktop:~$ 

```

---

### Post by ssander on 2008-04-29
Tweaked it a little and I don't notice even the tiniest skips anymore.

1) sudo apt-get install --reinstall pulseaudio (don't know if absolutely necesary)
2) gksudo gedit /etc/pulse/daemon.conf
3) replace the lines containing "high-priority" and "nice-level" with
```
high-priority = yes
nice-level = -15
```
and the lines containing "default-sample-rate", "default-fragments" and "default-fragment-size-msec" with
```
default-sample-rate = 48000
default-fragments = 8
default-fragment-size-msec = 10
```
4) reboot? (re log in)

---

### Post by psyke83 on 2008-04-29
> **ssander said:**
> Tweaked it a little and I don't notice even the tiniest skips anymore.

Thanks for the new information. The settings that work for you seem to increase skipping for me; it seems the optimal fragment values depend on your sound card.

Can you paste your soundcard information here ("lspci | grep audio")? It will be useful to get a picture of what values work best for various cards.

---

### Post by ssander on 2008-04-29
> **psyke83 said:**
> Can you paste your soundcard information here ("lspci | grep audio")? It will be useful to get a picture of what values work best for various cards.

Here you go:
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)

---

### Post by mgmiller on 2008-04-29
> **ssander said:**
> Tweaked it a little and I don't notice even the tiniest skips anymore.

1) sudo apt-get install --reinstall pulseaudio (don't know if absolutely necesary)
2) gksudo gedit /etc/pulse/daemon.conf
3) replace the lines containing "high-priority" and "nice-level" with
```
high-priority = yes
nice-level = -15
```
and the lines containing "default-sample-rate", "default-fragments" and "default-fragment-size-msec" with
```
default-sample-rate = 48000
default-fragments = 8
default-fragment-size-msec = 10
```
4) reboot? (re log in)

This worked perfectly for me.  Thank you.

Here is my lspci:
```
marty@tux:~$ lspci | grep audio
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
```

---

### Post by momist on 2008-05-03
> **ssander said:**
> Tweaked it a little and I don't notice even the tiniest skips anymore.

1) sudo apt-get install --reinstall pulseaudio (don't know if absolutely necesary)
2) gksudo gedit /etc/pulse/daemon.conf
3) replace the lines containing "high-priority" and "nice-level" with
```
high-priority = yes
nice-level = -15
```
and the lines containing "default-sample-rate", "default-fragments" and "default-fragment-size-msec" with
```
default-sample-rate = 48000
default-fragments = 8
default-fragment-size-msec = 10
```
4) reboot? (re log in)

Thanks for the tip - this seems to have worked OK for me too.  Rather than reboot, I just stopped Rythmbox and then did
pkil pulseaudio
and restarted Rythmbox.  No more clicks and pops so far . . .

~$ lspci | grep audio
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
:)

Edit:  Pops and clicks have come back :-(  Not as bad, but still ruins the music.

---

### Post by psyke83 on 2008-05-03
> **momist said:**
> Edit:  Pops and clicks have come back :-(  Not as bad, but still ruins the music.

The step to kill PulseAudio was *only* to check if PulseAudio was causing the skips. When PulseAudio is killed, most applications will use ALSA directly instead. You're mixing up the diagnostic step with the solution.

The solution is through editing /etc/pulse/daemon.conf and then testing sound *with* PulseAudio to see if it helps. It's obvious then that the modification you made to daemon.conf does not prevent PulseAudio skipping for you.

---

### Post by 4Orbs on 2008-05-03
The pops and clicking on my system stopped once I removed VLC Player.

---

### Post by abds on 2008-05-04
So i edited my file to /etc/pulse/daemon.conf and added the following lines

default-sample-rate = 48000
default-fragments = 8
default-fragment-size-msec = 10

high-priority = yes
nice-level = -15


output of lspci | grep audio:

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)

It doesnt help at all... The skipping is as bad as it was... 

Anyone please suggest something. Right now i just kill pulseaudio on starting a session.

---

### Post by Crusty Juggler on 2008-05-05
> **psyke83 said:**
> I have a possible solution.

Make sure Rhythmbox is closed, then open a terminal. Then, pkill the "pulseaudio" process and launch Rhythmbox again, and see if the skipping stops. So:

```
$ pkill pulseaudio
$ rhythmbox
```

If the above worked, then this next part will allow you to use PulseAudio without annoying skips:

Make a backup and then edit /etc/pulse/daemon.conf, and replace the lines at the end of your config with the following in red:

```
; default-sample-format = s16le
[COLOR="Red"]default-sample-rate = 48000[/COLOR]
; default-sample-channels = 2

[COLOR="Red"]default-fragments = 8[/COLOR]
[COLOR="Red"]default-fragment-size-msec = 10[/COLOR]
```

Now, log out and log back in, then run Rhythmbox normally. If this works, please let me know the name of your sound card, i.e. the output of:

```
lspci | grep audio
```

Thanks!

Works for ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02).  Thanks!

---

### Post by Cyclops_ on 2008-05-08
Hi!

Seems I am having the same problem... skipping with a bluetooth headset.

My headset is a Jabra BT620s.
I get the following outputs:
```

user@compy:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
user@compy:~$ lspci |grep audio
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

```

I tried pkill pulseaudio, and then starting rhythmbox, with no luck.  I've tried the steps indicated... still, it skips.  There doesn't seem to be much logic to the skipping, either, other than that I know that it will skip when the CPU usage gets high.  Although, it will often skip when the CPU is at 0%, and I am touching nothing.

What else can I do to test stuff?

Thanks for any help.

---

### Post by lonewolf72 on 2008-05-09
Killing pulseaudio temporarily fixes my problem.  The "fixes" do nothing.

VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

---

### Post by Harlon Nayl on 2008-05-09
Killing pulseaudio worked for me. Editing the daemon file reduced the popping and skipping a fair bit, but it's still there. My skipping issue is most prevalent when changing window focus; I have no issue with scrolling.

```
lspci | grep audio
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
```

---

### Post by MerrickB on 2008-05-11
> **ssander said:**
> Tweaked it a little and I don't notice even the tiniest skips anymore.

1) sudo apt-get install --reinstall pulseaudio (don't know if absolutely necesary)
2) gksudo gedit /etc/pulse/daemon.conf
3) replace the lines containing "high-priority" and "nice-level" with
```
high-priority = yes
nice-level = -15
```
and the lines containing "default-sample-rate", "default-fragments" and "default-fragment-size-msec" with
```
default-sample-rate = 48000
default-fragments = 8
default-fragment-size-msec = 10
```
4) reboot? (re log in)

Thanks for the added lines; this definitely cleared up the slight skip that I had after putting in the sample-rate, fragment and size-msec.  

~$ lspci | grep audio

02:02.0 Multimedia audio controller: Creative Labs SB Audigy LS

---

### Post by curiousdannii on 2008-05-11
> **psyke83 said:**
> I have a possible solution.

Make sure Rhythmbox is closed, then open a terminal. Then, pkill the "pulseaudio" process and launch Rhythmbox again, and see if the skipping stops. So:

```
$ pkill pulseaudio
$ rhythmbox
```

If the above worked, then this next part will allow you to use PulseAudio without annoying skips:

Make a backup and then edit /etc/pulse/daemon.conf, and replace the lines at the end of your config with the following in red:

```
; default-sample-format = s16le
[COLOR="Red"]default-sample-rate = 48000[/COLOR]
; default-sample-channels = 2

[COLOR="Red"]default-fragments = 8[/COLOR]
[COLOR="Red"]default-fragment-size-msec = 10[/COLOR]
```

Now, log out and log back in, then run Rhythmbox normally. If this works, please let me know the name of your sound card, i.e. the output of:

```
lspci | grep audio
```

Thanks!

This seems to have fixed most of the skipping, however it now takes 10 seconds or more to change songs. [Edit, changing songs is fine once I've logged back in.]
As with Harlon Nayl it skips when changing window focus, I haven't noticed it skip when scrolling.

VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

---

### Post by psyke83 on 2008-05-11
> **curiousdannii said:**
> This seems to have fixed the skipping, however it now takes 10 seconds or more to change songs.

VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

That's pretty odd. Does anyone else notice this?

I created a HOWTO aimed at fixing common PulseAudio problems and adding EQ support, can you try following Step A and C? Notably I want to know if the updated libasound2/libasound2-plugins packages help your problem. Here it is: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Edit: I just saw your edited reply, glad the 10 second delay is gone, but Part C of the HOWTO may yet reduce the skipping.

---

### Post by zero_koop on 2008-05-11
My symptoms are sound skipping using Amarok.  I also have skipping while playing Miro videos and also the sound is speed up (to make up for the lost time when it skipped) and so voices are higher pitched than normal.  The video does not stutter at all, only audio.  I do not however, have audio skipping while playing a few videos from my harddrive, including the Ubuntu example video (strange).
The ```
pkill pulseaudio
``` command works but the fixes do not.
The output of ```
lspci | grep audio
``` is:
```
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
```
Thanks for the temporary fix though. :-?

---

### Post by Delenir on 2008-05-13
My problem seemed to be entirely related to the system monitor taking huge amounts of CPU. Once I took that off my mt top toolbar, the problem went away 100%

---

### Post by psyke83 on 2008-05-13
> **Delenir said:**
> My problem seemed to be entirely related to the system monitor taking huge amounts of CPU. Once I took that off my mt top toolbar, the problem went away 100%

Yes, but was that a symptom or the cause? GNOME System Monitor has a reputation for taking a lot of CPU to draw graphs, etc. This is not a good thing, but it does not mean PulseAudio should be expected to stutter when your system is under CPU load. You will probably continue to notice stuttering when your system is under load from other applications besides the System Monitor.

Check this HOWTO, paying special attention to Part C, including the linked bug reports: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by snl2587 on 2008-05-20
Worked for me! Here us the output of lspci | grep audio:

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)

Now I can finally say for sure if the skips I was hearing in those progressive metal tunes were intentional or not.

EDIT: I take that back. Restarting pulseaudio even with the new conf file results in skipping, albeit less frequently.

---

### Post by snl2587 on 2008-05-20
> **snl2587 said:**
> Worked for me! Here us the output of lspci | grep audio:

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)

Now I can finally say for sure if the skips I was hearing in those progressive metal tunes were intentional or not.

EDIT: I take that back. Restarting pulseaudio even with the new conf file results in skipping, albeit less frequently.
I fixed my problem by setting default-fragment-size-msec to 5...the skipping is still there but nearly imperceptable. Hopefully there will be a nicer fix in the future, but for now I suppose it works fine.

---

### Post by psyke83 on 2008-05-21
> **snl2587 said:**
> I fixed my problem by setting default-fragment-size-msec to 5...the skipping is still there but nearly imperceptable. Hopefully there will be a nicer fix in the future, but for now I suppose it works fine.

As I said, those tweaks are obsolete. Please see this thread instead, Part A & Part C: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by gaspard.leon on 2008-05-26
> **psyke83 said:**
> 
```
[COLOR="Red"]default-fragments = 8[/COLOR]
[COLOR="Red"]default-fragment-size-msec = 10[/COLOR]
```

Now, log out and log back in, then run Rhythmbox normally. If this works, please let me know the name of your sound card, i.e. the output of:

```
lspci | grep audio
```

Thanks!

Well the new .17 kernel sped things up quite a bit, but pidgin notification sounds still popped/cracked so following the directions in your [updated post]("http://ubuntuforums.org/showthread.php?p=4928900"), everything seems ok... a few pops in pidgin at first but now it's smooth as.

So here you go:
```

gaspard@crystal:~$ lspci | grep audio
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

```

---

### Post by Jeanpaul145 on 2008-06-14
> **markp1989 said:**
> i disabled Evolution alarm notifier in sessions preferences and it stoped music skipping, and made scrolling more smooth

This helped somewhat for me as well, though it did not eliminate the problem.

> **psyke83 said:**
> [COLOR="Red"]EDIT: The information in this post is obsolete. Please take a look at my PulseAudio HOWTO here: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

This HOWTO provides information on most of the issues surrounding PulseAudio in Hardy and offers possible fixes, or failing that, links to the relevant bug reports. Please see if it helps.

----------------------------
[/COLOR]

I have a possible solution.

Make sure Rhythmbox is closed, then open a terminal. Then, pkill the "pulseaudio" process and launch Rhythmbox again, and see if the skipping stops. So:

```
$ pkill pulseaudio
$ rhythmbox
```

If the above worked, then this next part will allow you to use PulseAudio without annoying skips:

Make a backup and then edit /etc/pulse/daemon.conf, and replace the lines at the end of your config with the following in red:

```
; default-sample-format = s16le
[COLOR="Red"]default-sample-rate = 48000[/COLOR]
; default-sample-channels = 2

[COLOR="Red"]default-fragments = 8[/COLOR]
[COLOR="Red"]default-fragment-size-msec = 10[/COLOR]
```

Now, log out and log back in, then run Rhythmbox normally. If this works, please let me know the name of your sound card, i.e. the output of:

```
lspci | grep audio
```

Thanks!

This AND disabling some unneeded services seems to have done the trick for me. Audio card info:

```

j@znote:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```

I can say that it is a RealTek ALC268 chip.

Thanx a lot! :guitar:

---

### Post by Roti78 on 2008-07-15
Hi!

 My problem solved by adding myself to the pulse-rt group by entering:

```
sudo usermod -a -G pulse-rt $USER 
``` 

Afterthat: log out and log in.

My soundcard:

```
$lspci | grep audio

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

```

Roti

---

### Post by ramiro on 2008-09-01
I tried all this, and the skipping doesn't happen regularly, I still have issues with skipping when I browse Ajax heavy sites such as Facebook or Last.fm

it's not like my computer is ancient (Pentium M 2GHz) and although I'm running Compiz, I've got a Nvidia 6600, so it shouldn't be too much of an issue. It's really frustrating, because I can't browse and listen to music at the same time

anyone else who's sound was "fixed" have this issue?

---

### Post by Malcolm on 2008-10-31
I'm having this problem after installing Ubuntu 8.10 (installed from scratch, not upgraded). When I'm listening to music in Rhythmbox, every now and then it skips - and not at regular intervals or in a predictable way. Sometimes it happens while loading web pages, sometimes it skips even when I'm not doing anything.

---

### Post by Malcolm on 2008-10-31
Update: the problem seems to affect all the players that use gstreamer. If anyone knows of a possible solution or is experiencing the same issue, please let me know.

---

### Post by Malcolm on 2008-10-31
The problem seems to be fixed now, or at least I hope so. I'll report back in case it isn't.

All I did was selecting "PulseAudio Server" for all the devices in the Preferences -> Sound settings utility. By default it was set to ALSA. Is that the way it's supposed to be?

EDIT: After a reboot, the skipping restarted... it got more and more frequent until Rhythmbox just froze :/

---

### Post by exXP on 2008-11-02
This is a problem I have for the first with 8.10.  I get about 1 sec of music followed by 1 sec of silence and this is repeated ad nauseum.  My system monitor shows a CPU load of only 30 - 50% during this time. I wonder if the streaming function isn't working?  Maybe I'll need to download a few extra files for this to work.  ALSA or PulseAudio are treated exactly the same.
exXP

---

### Post by exXP on 2008-11-02
This is a problem I have for the first with 8.10.  I get about 1 sec of music followed by 1 sec of silence and this is repeated ad nauseum.  My system monitor shows a CPU load of only 30 - 50% during this time. I wonder if the streaming function isn't working?  Maybe I'll need to download a few extra files for this to work.  ALSA or PulseAudio are treated exactly the same.
exXP

---

### Post by endesign on 2008-11-02
> **markp1989 said:**
> i disabled Evolution alarm notifier in sessions preferences and it stoped music skipping, and made scrolling more smooth
Markp1989's advice to disable Evolution Alarm Notifier worked for me - obviously not for everyone but as a thunderbird/lightning man no problem for me and now I can surf with non-skipping music. Ta mark!

---

### Post by odelay on 2009-02-05
> **endesign said:**
> Markp1989's advice to disable Evolution Alarm Notifier worked for me - obviously not for everyone but as a thunderbird/lightning man no problem for me and now I can surf with non-skipping music. Ta mark!

I disabled Evolution Alarm Notifier, but it didn't help.  This is extremely annoying, considering my life consists of listening to music and scrolling through research papers.  :D

---

### Post by spazz135 on 2009-02-05
Dude That works for the sound skiping and Using skype While listening to music if any body uses skpe and cant listen to rythmbox while using it you have to get pulseadio it works the kinks out of many sound problems you will have in the future;)

---

### Post by odelay on 2009-03-20
Rhythmbox still skips.  I've switched to Banshee because of this, but I miss having album artwork I can actually see.

---

### Post by markp1989 on 2009-03-23
i gave up on rhythmbox, i use mpd and gmpc now, and i love it:D

---

### Post by amor0fati on 2009-05-19
The fix didn't work for me.

Output:
```
lspci | grep audio
05:07.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
```

For some reason, my mouse stopped working through the ps/2 adapter after the reboot.  Jaunty and Rhythmbox cause me so much pain.  Anyone have any idea why this is happening?

---

### Post by maclaurg on 2009-09-04
> **psyke83 said:**
> [COLOR=Red]EDIT: The information in this post is obsolete. Please take a look at my PulseAudio HOWTO here: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

This HOWTO provides information on most of the issues surrounding PulseAudio in Hardy and offers possible fixes, or failing that, links to the relevant bug reports. Please see if it helps.

----------------------------
[/COLOR]

I have a possible solution.

Make sure Rhythmbox is closed, then open a terminal. Then, pkill the "pulseaudio" process and launch Rhythmbox again, and see if the skipping stops. So:

```
$ pkill pulseaudio
$ rhythmbox
```If the above worked, then this next part will allow you to use PulseAudio without annoying skips:

Make a backup and then edit /etc/pulse/daemon.conf, and replace the lines at the end of your config with the following in red:

```
; default-sample-format = s16le
[COLOR=Red]default-sample-rate = 48000[/COLOR]
; default-sample-channels = 2

[COLOR=Red]default-fragments = 8[/COLOR]
[COLOR=Red]default-fragment-size-msec = 10[/COLOR]
```Now, log out and log back in, then run Rhythmbox normally. If this works, please let me know the name of your sound card, i.e. the output of:

```
lspci | grep audio
```Thanks!



This worked for me to an extent. I can still skip the music if I scroll up and down ridiculously fast in firefox. Increasing the default-sample-rate to 48000 seemed to alleviate the problem so that it doesn't bother me.  I'm curious if increasing the sample rate even more, say to 60000, would help or cause other problems. I don't know enough about it.

Running Jaunty, AMD 64 X2 +5200, Asus MB M4A78 plus (integrated sound), 4gb ram, Nvidia 9800gt 1gb.

---

### Post by Andysan on 2009-09-11
Hi all,

Have read through all posts from cover to cover.  Thanks to those who offered help but I have tried all methods mentioned and none have worked.  My skips occur seemingly at random and regardless of whether I am scrolling/changing windows etc... even under seemingly no CPU load the audio seems to skip.

Can anyone offer a solution please?  Thanks.

lspci | grep audio
```
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
```

Running Jaunty on Athlon 2400.

---

### Post by mumbles6869 on 2009-11-19
Hey i'm new to the whole linux how did you change that? i'm using Ubuntu Jaunty 9.04..

---

### Post by Andysan on 2009-11-20
> **mumbles6869 said:**
> Hey i'm new to the whole linux how did you change that? i'm using Ubuntu Jaunty 9.04..

Hi,

These commands need to be entered from a Terminal; I suggest you read through the post first and read up on the Terminal before you start copying and pasting stuff in that you dont understand.  When you're happy go to Applications>Accessories>Terminal.  Now paste the following and hit return.  It will kill pulseaudio:

```
pkill pulseaudio
```

Now copy and paste again the following command to launch Rhymthmbox to see if it now works any better:

```
rhythmbox
```

If so, quit Rhythmbox.  Now, to make a backup and then edit /etc/pulse/daemon.conf, enter the following commands in sequence.

This makes a copy of the daemon.conf file called daemon.conf.bak in case we mess up:

```
sudo cp /etc/pulse/daemon.conf /etc/pulse/daemon.conf.bak
```

This opens the daemon.conf file in a the gedit text editor with root privilleges:

```
gksudo gedit /etc/pulse/daemon.conf
``` 

Now, replace the lines in red as instructed in the previous post:
```

; default-sample-format = s16le
[COLOR="Red"]default-sample-rate = 48000[/COLOR]
; default-sample-channels = 2

[COLOR="Red"]default-fragments = 8
default-fragment-size-msec = 10 [/COLOR]

```

Now, log out and log back in, then run Rhythmbox normally.  Read through the post and try and understand what each command does before you actually execute any of them.  The [following link]("https://help.ubuntu.com/community/UsingTheTerminalhttps://help.ubuntu.com/community/UsingTheTerminal") may be of interest.

Shout back with any problems!

---

### Post by mbuller10 on 2009-11-22
After I disabled track number times played and date added i played couple of songs with no skipping, i know this sounds retarded

---

### Post by Mspirit on 2010-06-06
Welcome to the future:

```
sudo apt-get remove  pulseaudio
```

what's the use of it anyway...XD

My problem is gone, "I have a dream" - Connie Talbot
this is the life

edit: and while you at it try this fix [http://ubuntuforums.org/showthread.php?t=1165082](http://ubuntuforums.org/showthread.php?t=1165082) which allows you to use keyboard Fn control keys once again..

---

### Post by Mspirit on 2010-06-09
> **psyke83 said:**
> 

I have a possible solution.

Make sure Rhythmbox is closed, then open a terminal. Then, pkill the "pulseaudio" process and launch Rhythmbox again, and see if the skipping stops. So:

```
$ pkill pulseaudio
$ rhythmbox
```

If the above worked, then this next part will allow you to use PulseAudio without annoying skips:

Make a backup and then edit /etc/pulse/daemon.conf, and replace the lines at the end of your config with the following in red:

```
; default-sample-format = s16le
[COLOR="Red"]default-sample-rate = 48000[/COLOR]
; default-sample-channels = 2

[COLOR="Red"]default-fragments = 8[/COLOR]
[COLOR="Red"]default-fragment-size-msec = 10[/COLOR]
```

Now, log out and log back in, then run Rhythmbox normally. If this works, please let me know the name of your sound card, i.e. the output of:

```
lspci | grep audio
```



Found out the exact cause hopefully it will work for you guys...

```
sudo gedit /etc/pulse/daemon.conf
```

near the end you would find:
**; default-sample-rate = [COLOR="Red"]16000[/COLOR] [COLOR="DarkGreen"]#44100[/COLOR]**

The value in Red is that for the sound quality..setting it higher will only worse skipping

Set it as low as possible, then increase it gradually till it reach a value where there is no skipping. You can always add # symbol before previous value so it's easy to compare

The values applicable are:

8000
16000
22050
32000
44100
48000

Read more at Wikipedia: *[Bitrates in multimedia]("http://en.wikipedia.org/wiki/Bit_rate#Bitrates_in_multimedia")*

Please post some feedback..it's a widely spread problem. So hope it would be solved for good isa XD

---

### Post by chrone on 2010-07-20
> **Mspirit said:**
> Found out the exact cause hopefully it will work for you guys...

```
sudo gedit /etc/pulse/daemon.conf
```

near the end you would find:
**; default-sample-rate = [COLOR="Red"]16000[/COLOR] [COLOR="DarkGreen"]#44100[/COLOR]**

The value in Red is that for the sound quality..setting it higher will only worse skipping

Set it as low as possible, then increase it gradually till it reach a value where there is no skipping. You can always add # symbol before previous value so it's easy to compare

The values applicable are:

8000
16000
22050
32000
44100
48000

Read more at Wikipedia: *[Bitrates in multimedia]("http://en.wikipedia.org/wiki/Bit_rate#Bitrates_in_multimedia")*

Please post some feedback..it's a widely spread problem. So hope it would be solved for good isa XD

I've changed it to 44100. It reduces the skipping much, but sometimes it still gets the skipping part. :(

I'm using AMD Chipset: Gigabyte GA-MA78GM-US2H.

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

```

the funny thing, using Intel Chipset, there's no hiccup in sound.

---

