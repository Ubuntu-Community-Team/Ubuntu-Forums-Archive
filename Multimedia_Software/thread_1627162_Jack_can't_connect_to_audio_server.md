---
title: "Jack can't connect to audio server"
date: 2010-11-21
forum: Multimedia Software
---

### Post by coelmoba on 2010-11-21
Hello,

I'mnew on linux. I try it for the first time. Befor I changed to linux I used MS Windows 7.
There I worked much with SonyVegas for video and Adobe Auditon for music. Yesterday I searched for alternatives under Linux for Audition.  And I found much. The screen shots says, that they look similar to  Auditon. I downloaded them and installed them. But they doesn't work.  One of them say they can't connect to Jack. Some of them say  nothing, and so they don't record my line in/microphone input. After a  few seconds I of search, I knew that all of these programs uses jack for  Audio. I installed it, but the situation wasn't better.
Then I found a wiki, and try that: first start jack, than start the  program. So I do. But there i get a few error messages: At first I  should copy to lines to the file lines.conf. I do it. Then I should be  member of the audio group. I do that.

Now I get this error report if I click on run:

```
 p, li { white-space: pre-wrap; } [COLOR=#999999]12:02:16.089 Steckfeld deaktiviert.[/COLOR]
 [COLOR=#999999]12:02:16.330 Statistik zurückgesetzt.[/COLOR]
 [COLOR=#66cc99]12:02:16.375 Schaubild der ALSA-Verbindungen geändert.[/COLOR]
 [COLOR=#cccc99]12:02:16.673 ALSA-Verbindung geändert.[/COLOR]
 [COLOR=#999999]12:02:27.645 Startup script...[/COLOR]
 [COLOR=#990099]12:02:27.646 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]12:02:28.047 Startup script terminated mit Rückgabewert = 32512.[/COLOR]
 [COLOR=#999999]12:02:28.047 JACK startet...[/COLOR]
 [COLOR=#990099]12:02:28.048 /usr/bin/jackd -dalsa -r48000 -p1024 -n2 -D -C(voreinst.) -P(voreinst.)[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    1542669
 [COLOR=#999999]12:02:28.059 JACK wurde mit PID = 2415 gestartet.[/COLOR]
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 48000
 creating alsa driver ... (voreinst.)|(voreinst.)|1024|2|48000|0|0|nomon|swmeter|-|32bit
 ALSA lib control.c:902:(snd_ctl_open_noupdate) Invalid CTL (voreinst.)
 control open "(voreinst.)" (No such file or directory)
 ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM (voreinst.)
 ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM (voreinst.)
 ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 cannot load driver module alsa
 [COLOR=#999999]12:02:28.414 JACK wurde angehalten erfolgreich.[/COLOR]
 [COLOR=#999999]12:02:28.415 Post-shutdown script...[/COLOR]
 [COLOR=#990099]12:02:28.415 killall jackd[/COLOR]
 jackd: Kein Prozess gefunden
 [COLOR=#999999]12:02:28.825 Post-shutdown script terminated mit Rückgabewert = 256.[/COLOR]
 [COLOR=#ff0000]12:02:30.159  Keine Verbindungsaufnahme als Client zum JACK-Server möglich. - Overall  operation failed. - Verbindungsaufnahme zum Server gescheitert. Bitte  sehen Sie im Meldungsfenster nach weiteren Informationen.[/COLOR]

```If I click on "connections" I can only see the MIDI ports. On Audio is nothing.

But if I use the ubuntu recorder, all works. I can record form Line-in  or microphone. If I click open the audio options, I can change the  source of Audio, change the level and so on. All works. Only jack won't  work.

Can anyone help me?

Michael

---

### Post by cchhrriiss121212 on 2010-11-21
Hello
Could you post the output of "aplay -l" from a terminal?

---

