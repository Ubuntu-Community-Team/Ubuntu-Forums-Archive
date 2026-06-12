---
title: "Yet another Jack problem"
date: 2015-09-29
forum: Multimedia Software
---

### Post by DeRobyJ on 2015-09-29
Hello, I know there are several topics about Jack not starting, I read them and the error messages are different, so all those solutions don't work for me. (I tried several fixes)

I installed Ubuntu Studio 14 LTS on a Lenovo Flex 2 in dual boot.
This problem occurs both in normal mode and in low-latency mode (that came built in), and both jack1 and jack2 won't work (with different errors)
I updated all my audio software to kxstudio repository, and I'm running Jack from QjackCtl 0.4.0

Errors: with jack2:
on sturtup, it sometimes shows this

 ```
Cannot connect to server socket err = File o directory non esistente (translation: missing file or directory)

 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 [COLOR=#66cc99]09:54:14.038 Cambiamento nel grafico delle connessioni di ALSA. (translation: graphical change in ALSA connections)[/COLOR]

 (qjackctl:2427): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed

 (qjackctl:2427): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed

 (qjackctl:2427): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed

 (qjackctl:2427): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed


```



Clickin on Sart will reurn these messages:
```

 (qjackctl:2427): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed

 (qjackctl:2427): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed

 [COLOR=#ff0000]10:34:52.343 D-BUS: il server JACK non può essere avviato. Mi dispiace (ts: Jack server can't be started.)[/COLOR]

 Tue Sep 29 10:34:52 2015: Starting jack server...

 Tue Sep 29 10:34:52 2015: JACK server starting in realtime mode with priority 10

 Tue Sep 29 10:34:52 2015: self-connect-mode is "Don't restrict self connect requests"

 Tue Sep 29 10:34:52 2015: Acquired audio card Audio0

 Tue Sep 29 10:34:52 2015: creating alsa driver ... hw:0|hw:0|512|2|44100|0|0|nomon|swmeter|soft-mode|32bit

 Tue Sep 29 10:34:52 2015: Using ALSA driver HDA-Intel running on card 0 - HDA Intel HDMI at 0xe0610000 irq 46

 Tue Sep 29 10:34:52 2015: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode

 Tue Sep 29 10:34:52 2015: ERROR: Cannot initialize driver

 Cannot connect to server socket err = File o directory non esistente (translation: missing file or directory)

 Cannot connect to server request channel

 jack server is not running or cannot be started

 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock

 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlockt

Tue Sep 29 10:34:53 2015: Saving settings to "/home/roberto/.config/jack/conf.xml" ...

 [COLOR=#ff0000]10:35:09.206 Non sono riuscito ad avviare JACK come client. - Operazione fallita. - Impossibile connettersi al server JACK. Controlla la finestra dei messaggi per maggiori informazioni. (ts: I couldn't start Jack client. Can't connect to JACK server)[/COLOR]

 Cannot connect to server socket err = File o directory non esistente (translation: missing file or directory)

 Cannot connect to server request channel

 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock

```


From what I read around, it could be an audio drive problem, but I tried all the possible configurations about hw and none of them did work.

Do I need too use a professional audio drive to run jack? I do own one, that is said to work, but I don't know how to set it up so that the system runs it  (audio settings don't show it).

I'd really like to use all the different audio softwares with jack and patchage. I was able to do that on my desktop PC with ubuntu studio 11, now I just can't because of this OOTB crash.



Thank you in advance!

---

### Post by DeRobyJ on 2015-10-21
Bump.
I still can't fix this.
Thanks

---

