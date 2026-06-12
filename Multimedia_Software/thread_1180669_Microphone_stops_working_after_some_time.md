---
title: "Microphone stops working after some time"
date: 2009-06-07
forum: Multimedia Software
---

### Post by TheKrokodil on 2009-06-07
I'm currently using Ubuntu on my Thinkpad R51e, and got nearly everything to work after some time. But there is still something quite annoying: I'm using PulseAudio (which I, by the way, had to run in system instance mode, as otherwise the sound was all splitted into 1sec parts combined with 0,5sec part freezes) and can use the microphone in the gnome sound recorder, team speak, ... without any problems just after starting the system.

But after some random time, which can be from 5min to 2 hours, the microphone suddendly stops working. The PulseAudio volume meter just won't display anything anymore; in the PulseAudio sink properties the latency of the microphone sink shows the time since the microphone didn't work (in sec..); Every newly started recording program will just freeze. If I press the record button in the gnome sound recorder, It will initiate recording but freeze at 0 sec without any sound level activity; and if pressed again it will freeze entirely.

Anyone any idea? Restarting Pulseaudio via /etc/init.d/pulseaudio hasn't helped; and the same error occured just when removing pulseaudio completly and using alsa. Would be glad for any help.

Thinkpad R51e
Soundcard: 00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
Modem is blacklisted.

lsmod:
```

snd_atiixp             24204  8 
snd_ac97_codec        112292  1 snd_atiixp
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83204  6 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  5 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  20 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_atiixp,snd_pcm

```

---

### Post by TheKrokodil on 2009-06-07
Anyone able to help?

---

### Post by TheKrokodil on 2009-06-10
*push*

---

### Post by TheKrokodil on 2009-06-11
Yet another *bump*..

..no one?

---

### Post by BinaryMn on 2010-04-13
bump. i'm having the same problem.

---

### Post by JoWi on 2010-05-09
I'm having the same problem:
Hardware: Laptop hp 6735s

```
$ lspci | grep -i audio 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
```

Running Ubuntu Lucid (10.04), PulseAudio. The problem was equally present with 9.10.

Right after booting, the microphone works nice. I'm usually using it with Skype. 

When making a "Skype Test Call", then Skype asks me to record a message for 10 seconds, afterwards, it plays a "bing", then it plays my message back to me and continues with another "bing".

After some time skyping, the microphone stops working.

When the mic does not work, and I make a "Skype Test Call", then Skype asks me to record my message, afterwards I hear the "bing", and instantly afterwards the second "bing" - there is NO 10-seconds-break between the "bing"s. :o In this state, if opening the "Audio Settings" window from the volume control icon, the "recording level" meter is frozen. Any audio recording software doesn't work neither.

Most of the times, I can repair the mic by closing all apps and performing ```
sudo alsa force-reload
```
However, after repairing, the first "Skype Test Call" will always end up with the following: After recording my message, I hear the first "bing", then I hear my voice, but totally scrambled, not understandable and reduced to approx 2 seconds, then the second "bing" as normal. The second "Skype Test Call" afterwards then works perfectly and I can use the mic normally. 

Here are some programs which usually make the microphone stop working:
[LIST]
[*]Any program causing high cpu usage
[*]Thunderbird
[*]Firefox, having a site with a Flash animation open
[*]Ubuntu update manager
[/LIST]
(90% reproducibility to make the mic stop working. However, if not starting any program during talking, the microphone will work for hours without problems. With Update manager 100% reproducibility.)

(The procedures I have explained with "Skype Test Call" have been confirmed by talking to real persons, thus this is NOT a "Skype Test Call" specific problem.)

Can someone out there please give an advice or help fixing this?

---

### Post by JoWi on 2010-06-13
Any ideas?

---

### Post by lidex on 2010-06-13
> **TheKrokodil said:**
> Anyone able to help?

Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=thinkpad 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by Stay on 2010-08-30
The same problem here on my desktop Acer aspire T660:

```
$ lspci | grep -i audio 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
```

I tried to add proposed option to /etc/modprobe.d/alsa-base.conf like:

```
options snd-hda-intel model=acer
or
options snd-hda-intel model=acer-aspire

```

but after adding it and rebooting, micro didn't work at all.

Any input on this matter is very appreciated!

---

### Post by lidex on 2010-08-30
If this is happening with skype, make sure to disable skype preference to allow it to change mixer levels.

---

### Post by Stay on 2010-08-31
No, it's not related to Skype. It stops working after few minutes after boot even without using any sound apps. I keep open Sound Preferences window to see the input level indicator and it just freezes after some time.

---

### Post by lidex on 2010-08-31
Can you provide this output please:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

### Post by Stay on 2010-08-31
here is the output:

```

:~$ pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is e66716ea8bee1e1f3886f5654bed4b67.
I: main.c: Session ID is e66716ea8bee1e1f3886f5654bed4b67-1283236311.336009-1521717348.
I: main.c: Using runtime directory /home/aaa/.pulse/e66716ea8bee1e1f3886f5654bed4b67-runtime.
I: main.c: Using state directory /home/aaa/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

```

---

### Post by Stay on 2010-09-06
So any ideas? Is it a driver problem or PulseAudio? Is there any way to detect & resolve it?

---

### Post by lidex on 2010-09-15
Kinda at a loss here. I would report a bug. Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```

---

### Post by elzear on 2010-11-18
> **JoWi said:**
> I'm having the same problem:
Hardware: Laptop hp 6735s

```
$ lspci | grep -i audio 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
```Running Ubuntu Lucid (10.04), PulseAudio. The problem was equally present with 9.10.

Right after booting, the microphone works nice. I'm usually using it with Skype. 

When making a "Skype Test Call", then Skype asks me to record a message for 10 seconds, afterwards, it plays a "bing", then it plays my message back to me and continues with another "bing".

After some time skyping, the microphone stops working.

When the mic does not work, and I make a "Skype Test Call", then Skype asks me to record my message, afterwards I hear the "bing", and instantly afterwards the second "bing" - there is NO 10-seconds-break between the "bing"s. :o In this state, if opening the "Audio Settings" window from the volume control icon, the "recording level" meter is frozen. Any audio recording software doesn't work neither.

Most of the times, I can repair the mic by closing all apps and performing ```
sudo alsa force-reload
```However, after repairing, the first "Skype Test Call" will always end up with the following: After recording my message, I hear the first "bing", then I hear my voice, but totally scrambled, not understandable and reduced to approx 2 seconds, then the second "bing" as normal. The second "Skype Test Call" afterwards then works perfectly and I can use the mic normally. 

Here are some programs which usually make the microphone stop working:
[LIST]
[*]Any program causing high cpu usage
[*]Thunderbird
[*]Firefox, having a site with a Flash animation open
[*]Ubuntu update manager
[/LIST]
(90% reproducibility to make the mic stop working. However, if not starting any program during talking, the microphone will work for hours without problems. With Update manager 100% reproducibility.)

(The procedures I have explained with "Skype Test Call" have been confirmed by talking to real persons, thus this is NOT a "Skype Test Call" specific problem.)

Can someone out there please give an advice or help fixing this?

I have working solution:

loock on: [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

I have hp nx 6325 and setting describe there for my mic dont work but i check other solution (from this post) and its working!!! I have Ubuntu 10.10

what I do:
terminal
sudo gedit /etc/modprobe.d/alsa-base

At the end of file I add:
options snd-hda-intel model=toshiba position_fix=1
save and reboot. 

After reboot your card could be auto check in alsa (icon in statos bars is inactive)
go to terminal
alsamixer
click F6 mark your device
and:
killall pulseaudio

sudo alsa force-reload


If used standard don't work for you please chech other lines (for other noteboock).

---

### Post by misiu369 on 2010-11-20
> **JoWi said:**
> I'm having the same problem:
Hardware: Laptop hp 6735s

```
$ lspci | grep -i audio 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) [/CODE

I've got the exact same problem on HP6735b running 10.10 (Maverick Meerkat).
[CODE]$ lspci | grep -i audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices AD1984A
Codec: LSI ID 1040
```

According to help.ubuntu.com ([link]("https://help.ubuntu.com/community/HdaIntelSoundHowto")), I've added "options snd-hda-intel model=laptop" to alsa-base.conf, but no change. Also tried adding "enable_msi=1" or "enable_msi=0", but neither helped.

After ~10min since reboot I've noticed mic stopped working again and I've checked syslog. I found about 20 events suppressed by ratelimit.c (see below), and none of them in the next 15min, so it's possibly related to the mic problem.
```
Nov 20 19:40:32 <reboot>
Nov 20 19:40:40 mylaptop pulseaudio[2200]: core-util.c: Home directory /etc/timidity not ours.
Nov 20 19:40:40 mylaptop pulseaudio[2200]: lock-autospawn.c: Cannot access autospawn lock.
Nov 20 19:40:40 mylaptop pulseaudio[2200]: main.c: Failed to acquire autospawn lock
Nov 20 19:40:55 <I've logged in>
Nov 20 19:42:08 mylaptop pulseaudio[2431]: ratelimit.c: 3 events suppressed
Nov 20 19:42:14 mylaptop pulseaudio[2431]: ratelimit.c: 1 events suppressed
Nov 20 19:42:20 mylaptop pulseaudio[2431]: ratelimit.c: 2 events suppressed
Nov 20 19:42:26 mylaptop pulseaudio[2431]: ratelimit.c: 1 events suppressed
Nov 20 19:42:32 mylaptop pulseaudio[2431]: ratelimit.c: 1 events suppressed
Nov 20 19:42:56 mylaptop pulseaudio[2431]: ratelimit.c: 1 events suppressed
Nov 20 19:43:26 mylaptop pulseaudio[2431]: ratelimit.c: 1 events suppressed
Nov 20 19:43:32 mylaptop pulseaudio[2431]: ratelimit.c: 1 events suppressed
Nov 20 19:43:38 mylaptop pulseaudio[2431]: ratelimit.c: 2 events suppressed
Nov 20 19:43:56 mylaptop pulseaudio[2431]: ratelimit.c: 1 events suppressed
Nov 20 19:44:32 mylaptop pulseaudio[2431]: last message repeated 2 times
Nov 20 19:45:01 mylaptop pulseaudio[2431]: last message repeated 3 times
Nov 20 19:45:14 mylaptop pulseaudio[2431]: ratelimit.c: 1 events suppressed
```

The only way I can make mic working again is to reboot. Neither killing pulseaudio nor running "alsa force-reload" helps.

Is there any way to debug pulseaudio to see what the exact problem is?

Any help would be greatly appreciated...

---

### Post by lidex on 2010-11-20
> **misiu369 said:**
> I've got the exact same problem on HP6735b running 10.10 (Maverick Meerkat).
```
$ lspci | grep -i audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices AD1984A
Codec: LSI ID 1040
```

According to help.ubuntu.com ([link]("https://help.ubuntu.com/community/HdaIntelSoundHowto")), I've added "options snd-hda-intel model=laptop" to alsa-base.conf, but no change. Also tried adding "enable_msi=1" or "enable_msi=0", but neither helped.

After ~10min since reboot I've noticed mic stopped working again and I've checked syslog. I found about 20 events suppressed by ratelimit.c (see below), and none of them in the next 15min, so it's possibly related to the mic problem.
```
Nov 20 19:40:32 <reboot>
Nov 20 19:40:40 mylaptop pulseaudio[2200]: core-util.c: Home directory /etc/timidity not ours.
Nov 20 19:40:40 mylaptop pulseaudio[2200]: lock-autospawn.c: Cannot access autospawn lock.
Nov 20 19:40:40 mylaptop pulseaudio[2200]: main.c: Failed to acquire autospawn lock
Nov 20 19:40:55 <I've logged in>
Nov 20 19:42:08 mylaptop pulseaudio[2431]: ratelimit.c: 3 events suppressed
Nov 20 19:42:14 mylaptop pulseaudio[2431]: ratelimit.c: 1 events suppressed
Nov 20 19:42:20 mylaptop pulseaudio[2431]: ratelimit.c: 2 events suppressed
Nov 20 19:42:26 mylaptop pulseaudio[2431]: ratelimit.c: 1 events suppressed
Nov 20 19:42:32 mylaptop pulseaudio[2431]: ratelimit.c: 1 events suppressed
Nov 20 19:42:56 mylaptop pulseaudio[2431]: ratelimit.c: 1 events suppressed
Nov 20 19:43:26 mylaptop pulseaudio[2431]: ratelimit.c: 1 events suppressed
Nov 20 19:43:32 mylaptop pulseaudio[2431]: ratelimit.c: 1 events suppressed
Nov 20 19:43:38 mylaptop pulseaudio[2431]: ratelimit.c: 2 events suppressed
Nov 20 19:43:56 mylaptop pulseaudio[2431]: ratelimit.c: 1 events suppressed
Nov 20 19:44:32 mylaptop pulseaudio[2431]: last message repeated 2 times
Nov 20 19:45:01 mylaptop pulseaudio[2431]: last message repeated 3 times
Nov 20 19:45:14 mylaptop pulseaudio[2431]: ratelimit.c: 1 events suppressed
```

The only way I can make mic working again is to reboot. Neither killing pulseaudio nor running "alsa force-reload" helps.

Is there any way to debug pulseaudio to see what the exact problem is?

Any help would be greatly appreciated...

Try this. ```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

### Post by misiu369 on 2010-11-26
> **lidex said:**
> Try this. ```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

I'm not pasting the whole result, since I have my system is Polish and itwouldn't tell you much, but "Daemon already running." is the important part, I guess. Pulseaudio autospawns everytime I kill it and I don't know how to stop it.

I'm running Ubuntu 10.10 x64, if that changes anything..

---

### Post by lidex on 2010-11-27
> **misiu369 said:**
> I'm not pasting the whole result, since I have my system is Polish and itwouldn't tell you much, but "Daemon already running." is the important part, I guess. Pulseaudio autospawns everytime I kill it and I don't know how to stop it.

I'm running Ubuntu 10.10 x64, if that changes anything..
The whole idea was to restart pulse in the terminal with verbose output so we could see the error messages.

PA is configured to respawn so that is normal behavior.

This info would be useful as well. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by misiu369 on 2010-11-28
> **lidex said:**
> The whole idea was to restart pulse in the terminal with verbose output so we could see the error messages.

Here's the info in Polish - if you need any part translated, let me know which:
```
$ pkill pulseaudio; sleep 2; pulseaudio -vvI: main.c: setrlimit(RLIMIT_NICE, (31, 31)) nie powiod&#322;o si&#281;: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) nie powiod&#322;o si&#281;: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: To jest PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Komputer kompilacji: x86_64-pc-linux-gnu
D: main.c: CFLAGS kompilacji: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Uruchamianie na komputerze: Linux x86_64 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010
D: main.c: Odnaleziono 2 procesorów.
I: main.c: Rozmiar strony to 4096 bajtów
D: main.c: Skompilowano z obs&#322;ug&#261; Valgrind: nie
D: main.c: Uruchamianie w trybie Valgrind: no
D: main.c: Running in VM: no
D: main.c: Budowanie optymalizowane: tak
D: main.c: Wszystkie asercje s&#261; w&#322;&#261;czone.
I: main.c: Identyfikator komputera to eeb531ebfee115047ab2524f4ac8c62e.
I: main.c: Identyfikator sesji to eeb531ebfee115047ab2524f4ac8c62e-1290810117.60339-1276142297.
I: main.c: U&#380;ywanie katalogu wykonywania /home/arv/.pulse/eeb531ebfee115047ab2524f4ac8c62e-runtime.
I: main.c: U&#380;ywanie katalogu stanu /home/arv/.pulse.
I: main.c: U&#380;ywanie katalogu modu&#322;ów /usr/lib/pulse-0.9.21/modules.
I: main.c: Uruchamianie w trybie systemowym: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
```

> **lidex said:**
> Choose the upload option and provide a link for the output.
[Here it is, made after some time, when mic wasn't working any more.]("http://www.alsa-project.org/db/?f=5841f53ea1ae42ca14b7fbce1f2f56e11db133d8")
If you need it made right after reboot when everything works or after restarting pa, let me know.

Btw, thanks for your help! ;)

---

### Post by lidex on 2010-11-28
Pulse output looks fine (Google Translate;))
How much have you fiddled with alsa-base.conf? Have you tried without the MSI switch, or setting it to 0? How about 'mobile' or 'touchsmart' model?

---

### Post by misiu369 on 2010-11-28
> **lidex said:**
> Pulse output looks fine (Google Translate;))
How much have you fiddled with alsa-base.conf? Have you tried without the MSI switch, or setting it to 0? How about 'mobile' or 'touchsmart' model?
Tried only "options snd-hda-intel model=laptop" and adding "enable_msi=1" or "enable_msi=0" to it. So I should try with model=mobile and modol=touchsmart, instead of laptop? (can't today, but I'll try tommorow)

Btw, lately I had to skype, so after reboot I didn't run anything else and mic worked for a long time. Twice I did that actually - once I've killed mic by running world of warcraft through wine+winepulse. second time I tried different browsers (chrome, opera, ff) with and without flash but that didn't kill the mic - however running thunderbird did. That was unexpected.

Is there any way to take a closer look at what happens when the mic dies? Syslog is no help, but maybe there's some debug mode in pulseaudio?

---

### Post by lidex on 2010-11-28
Probably the easiest thing is to use the 'log file viewer'. It may not be in the default install:```

sudo apt-get install gnome-system-log
```
You can launch it from the administration menu.
Another thing to try is the pulse command posted previously. Simply leave the terminal open. It should report any errors (for pulse) when it re-occurs.

---

### Post by F i L on 2012-09-13
Hey guys, I have exact the same problem.
I have a webcam, microsoft LX-3000 headset and motherboard's sound card. If I select an input from either of the above, it works ONLY for 3-4 seconds and then it stops! Really strange! Any ideas ?

---

