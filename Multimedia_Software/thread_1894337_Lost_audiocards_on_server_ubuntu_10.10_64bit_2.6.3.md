---
title: "Lost audiocards on server ubuntu 10.10 64bit 2.6.32 need help!"
date: 2011-12-12
forum: Multimedia Software
---

### Post by dj--alex on 2011-12-12
i setup server for video retranslation local tv-channel for local net 
i lost 2 months to select correct OS and installing MythTv 0.23

3-4months computers works excellent,and now sound card just gone.

2-3 days back , i reboot computer and soundcard returns.
and now reboot not return any sound card but  logs seem like soundcards is alive

screenshot
[http://wow.chg.su/inside/?c=421d](http://wow.chg.su/inside/?c=421d)

for work used SAA7134 for get sound from tuner
and for write using internal soundcard.  

tuner Beholder 507 connected to soundcard with cable from sound out to sound in jack


server requires a GUI for normally controls MythTV and just for normal work.
no one have access to server  except webadmin (not having rights for sudo or e.t.c.)

please help!!
after 3 days i must start retranslation or write of channel but i don't know todo(((

i trying reinstall  pulseaudio, alsa and tries restart it (sudo service alsa restart, sudo service pulseaudio restart) but nothing ....
](*,)

Full data from "Hardware checking" [http://pastebin.com/nrbYT66C](http://pastebin.com/nrbYT66C)

[spoiler]

user@user-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
user@user-desktop:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe9f0000 irq 20
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7133[0] at 0xfeaff800 irq 18
user@user-desktop:~$ 
user@user-desktop:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 1- 0]: digital audio capture
  5: [ 1]   : control
  6: [ 0- 2]: digital audio capture
  7: [ 0- 1]: digital audio playback
  8: [ 0- 1]: digital audio capture
  9: [ 0- 0]: digital audio playback
 10: [ 0- 0]: digital audio capture
 11: [ 0- 0]: hardware dependent
 12: [ 0]   : control

user@user-desktop:~$ cat /proc/asound/oss-devices
cat: /proc/asound/oss-devices: &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
user@user-desktop:~$ cat /proc/asound/timers
G0: system timer : 10000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE
P0-1-1: PCM capture 0-1-1 : SLAVE
P0-2-1: PCM capture 0-2-1 : SLAVE
P1-0-1: PCM capture 1-0-1 : SLAVE
user@user-desktop:~$ cat /proc/asound/pcm
00-00: ALC883 Analog : ALC883 Analog : playback 1 : capture 1
00-01: ALC883 Digital : ALC883 Digital : playback 1 : capture 1
00-02: ALC883 Analog : ALC883 Analog : capture 1
01-00: SAA7134 PCM : SAA7134 PCM : capture 1
[/spoiler]

PS winamp is not used, installed just for test shoutcast and removed day tomorrow.

---

### Post by dj--alex on 2011-12-12
found how to restart ALSA, don't know correct or not

still not working sound...


ser@user-desktop:~$ sudo /sbin/alsa reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/user/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 1598(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
user@user-desktop:~$ sudo /sbin/alsa resume
user@user-desktop:~$
user@user-desktop:~$ alsamixer
\u041d\u0435 \u0443\u0434\u0430\u0451\u0442\u0441\u044f \u043e\u0442\u043a\u0440\u044b\u0442\u044c \u043c\u0438\u043a\u0448\u0435\u0440: \u041d\u0435\u0442 \u0442\u0430\u043a\u043e\u0433\u043e \u0444\u0430\u0439\u043b\u0430 \u0438\u043b\u0438 \u043a\u0430\u0442\u0430\u043b\u043e\u0433\u0430
(russian unicode from NX nomachine - english translation   cannot open mixer - no file or dir)
user@user-desktop:~$

trying  purging and reinstall - nothing 

user@user-desktop:~$ lsmod | grep snd
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_hda_codec_realtek   279040  1 
snd_hda_intel          25677  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm                87882  4 snd_pcm_oss,saa7134_alsa,snd_hda_intel,snd_hda_codec
snd_timer              23649  2 snd_seq,snd_pcm
snd                    71187  19 snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_hda_codec_realtek,saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
user@user-desktop:~$ sudo apt-get remove alsa
E: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100; &#1076;&#1086;&#1089;&#1090;&#1091;&#1087; &#1082; &#1092;&#1072;&#1081;&#1083;&#1091; &#1073;&#1083;&#1086;&#1082;&#1080;&#1088;&#1086;&#1074;&#1082;&#1080; /var/lib/dpkg/lock - open (11: &#1056;&#1077;&#1089;&#1091;&#1088;&#1089; &#1074;&#1088;&#1077;&#1084;&#1077;&#1085;&#1085;&#1086; &#1085;&#1077;&#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1077;&#1085;)
E: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1080;&#1090;&#1100; &#1073;&#1083;&#1086;&#1082;&#1080;&#1088;&#1086;&#1074;&#1082;&#1091; &#1091;&#1087;&#1088;&#1072;&#1074;&#1083;&#1103;&#1102;&#1097;&#1077;&#1075;&#1086; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; (/var/lib/dpkg/); &#1086;&#1085; &#1091;&#1078;&#1077; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1089;&#1103; &#1076;&#1088;&#1091;&#1075;&#1080;&#1084; &#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089;&#1086;&#1084;?
user@user-desktop:~$ sudo apt-get remove alsa
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081;       
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080; &#1086; &#1089;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1080;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1047;&#1072;&#1084;&#1077;&#1090;&#1100;&#1090;&#1077;, &#1074;&#1084;&#1077;&#1089;&#1090;&#1086; alsa &#1074;&#1099;&#1073;&#1080;&#1088;&#1072;&#1077;&#1090;&#1089;&#1103; alsa-base
&#1057;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099; &#1091;&#1089;&#1090;&#1072;&#1085;&#1072;&#1074;&#1083;&#1080;&#1074;&#1072;&#1083;&#1080;&#1089;&#1100; &#1072;&#1074;&#1090;&#1086;&#1084;&#1072;&#1090;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080; &#1080; &#1073;&#1086;&#1083;&#1100;&#1096;&#1077; &#1085;&#1077; &#1090;&#1088;&#1077;&#1073;&#1091;&#1102;&#1090;&#1089;&#1103;:
  mythmusic mytharchive mythbrowser twolame fftw2 libclass-factory-util-perl
  transcode-doc libmath-round-perl dbconfig-common python-lxml mythgallery
  libmpich1.0gf mythgame dvdauthor mythmovies libimage-size-perl
  libdatetime-format-builder-perl libdatetime-format-iso8601-perl
  python-chardet transcode python-utidylib mythnetvision libcarp-clan-perl sox
  wwwconfig-common mythweather mythvideo libgfortran3 mythnews
  pulseaudio-module-raop perlmagick python-feedparser javascript-common
  pulseaudio-module-zeroconf libtidy-0.99-0 python-imdbpy libjs-mootools
&#1044;&#1083;&#1103; &#1080;&#1093; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1080;&#1103; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1081;&#1090;&#1077; 'apt-get autoremove'.
&#1055;&#1072;&#1082;&#1077;&#1090;&#1099;, &#1082;&#1086;&#1090;&#1086;&#1088;&#1099;&#1077; &#1073;&#1091;&#1076;&#1091;&#1090; &#1059;&#1044;&#1040;&#1051;&#1045;&#1053;&#1067;:
  alsa-base ubuntu-desktop
&#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0, &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0 &#1085;&#1086;&#1074;&#1099;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1076;&#1083;&#1103; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1080;&#1103; &#1086;&#1090;&#1084;&#1077;&#1095;&#1077;&#1085;&#1086; 2 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1080; 1357 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1085;&#1077; &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086;.
&#1055;&#1086;&#1089;&#1083;&#1077; &#1076;&#1072;&#1085;&#1085;&#1086;&#1081; &#1086;&#1087;&#1077;&#1088;&#1072;&#1094;&#1080;&#1080;, &#1086;&#1073;&#1098;&#1105;&#1084; &#1079;&#1072;&#1085;&#1103;&#1090;&#1086;&#1075;&#1086; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074;&#1086;&#1075;&#1086; &#1087;&#1088;&#1086;&#1089;&#1090;&#1088;&#1072;&#1085;&#1089;&#1090;&#1074;&#1072; &#1091;&#1084;&#1077;&#1085;&#1100;&#1096;&#1080;&#1090;&#1089;&#1103; &#1085;&#1072; 590kB.
&#1061;&#1086;&#1090;&#1080;&#1090;&#1077; &#1087;&#1088;&#1086;&#1076;&#1086;&#1083;&#1078;&#1080;&#1090;&#1100; [&#1044;/&#1085;]? 
(&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1073;&#1072;&#1079;&#1099; &#1076;&#1072;&#1085;&#1085;&#1099;&#1093; ... &#1085;&#1072; &#1076;&#1072;&#1085;&#1085;&#1099;&#1081; &#1084;&#1086;&#1084;&#1077;&#1085;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 209135 &#1092;&#1072;&#1081;&#1083;&#1086;&#1074; &#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1086;&#1074;.)
&#1059;&#1076;&#1072;&#1083;&#1103;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; ubuntu-desktop ...
&#1059;&#1076;&#1072;&#1083;&#1103;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; alsa-base ...
user@user-desktop:~$ sudo apt-get purge alsa-base
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081;       
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080; &#1086; &#1089;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1080;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1057;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099; &#1091;&#1089;&#1090;&#1072;&#1085;&#1072;&#1074;&#1083;&#1080;&#1074;&#1072;&#1083;&#1080;&#1089;&#1100; &#1072;&#1074;&#1090;&#1086;&#1084;&#1072;&#1090;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080; &#1080; &#1073;&#1086;&#1083;&#1100;&#1096;&#1077; &#1085;&#1077; &#1090;&#1088;&#1077;&#1073;&#1091;&#1102;&#1090;&#1089;&#1103;:
  mythmusic mytharchive mythbrowser twolame fftw2 libclass-factory-util-perl
  transcode-doc libmath-round-perl dbconfig-common python-lxml mythgallery
  libmpich1.0gf mythgame dvdauthor mythmovies libimage-size-perl
  libdatetime-format-builder-perl libdatetime-format-iso8601-perl
  python-chardet transcode python-utidylib mythnetvision libcarp-clan-perl sox
  wwwconfig-common mythweather mythvideo libgfortran3 mythnews
  pulseaudio-module-raop perlmagick python-feedparser javascript-common
  pulseaudio-module-zeroconf libtidy-0.99-0 python-imdbpy libjs-mootools
&#1044;&#1083;&#1103; &#1080;&#1093; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1080;&#1103; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1081;&#1090;&#1077; 'apt-get autoremove'.
&#1055;&#1072;&#1082;&#1077;&#1090;&#1099;, &#1082;&#1086;&#1090;&#1086;&#1088;&#1099;&#1077; &#1073;&#1091;&#1076;&#1091;&#1090; &#1059;&#1044;&#1040;&#1051;&#1045;&#1053;&#1067;:
  alsa-base*
&#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0, &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0 &#1085;&#1086;&#1074;&#1099;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1076;&#1083;&#1103; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1080;&#1103; &#1086;&#1090;&#1084;&#1077;&#1095;&#1077;&#1085;&#1086; 1 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1080; 1357 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1085;&#1077; &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086;.
&#1055;&#1086;&#1089;&#1083;&#1077; &#1076;&#1072;&#1085;&#1085;&#1086;&#1081; &#1086;&#1087;&#1077;&#1088;&#1072;&#1094;&#1080;&#1080;, &#1086;&#1073;&#1098;&#1105;&#1084; &#1079;&#1072;&#1085;&#1103;&#1090;&#1086;&#1075;&#1086; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074;&#1086;&#1075;&#1086; &#1087;&#1088;&#1086;&#1089;&#1090;&#1088;&#1072;&#1085;&#1089;&#1090;&#1074;&#1072; &#1074;&#1086;&#1079;&#1088;&#1072;&#1089;&#1090;&#1105;&#1090; &#1085;&#1072; 0B.
&#1061;&#1086;&#1090;&#1080;&#1090;&#1077; &#1087;&#1088;&#1086;&#1076;&#1086;&#1083;&#1078;&#1080;&#1090;&#1100; [&#1044;/&#1085;]? 
(&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1073;&#1072;&#1079;&#1099; &#1076;&#1072;&#1085;&#1085;&#1099;&#1093; ... &#1085;&#1072; &#1076;&#1072;&#1085;&#1085;&#1099;&#1081; &#1084;&#1086;&#1084;&#1077;&#1085;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 209092 &#1092;&#1072;&#1081;&#1083;&#1086;&#1074; &#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1086;&#1074;.)
&#1059;&#1076;&#1072;&#1083;&#1103;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; alsa-base ...
&#1042;&#1099;&#1095;&#1080;&#1097;&#1072;&#1102;&#1090;&#1089;&#1103; &#1092;&#1072;&#1081;&#1083;&#1099; &#1085;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1080; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; alsa-base ...
user@user-desktop:~$ sudo apt-get install alsa alsa-base
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081;       
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080; &#1086; &#1089;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1080;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1047;&#1072;&#1084;&#1077;&#1090;&#1100;&#1090;&#1077;, &#1074;&#1084;&#1077;&#1089;&#1090;&#1086; alsa &#1074;&#1099;&#1073;&#1080;&#1088;&#1072;&#1077;&#1090;&#1089;&#1103; alsa-base
&#1057;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099; &#1091;&#1089;&#1090;&#1072;&#1085;&#1072;&#1074;&#1083;&#1080;&#1074;&#1072;&#1083;&#1080;&#1089;&#1100; &#1072;&#1074;&#1090;&#1086;&#1084;&#1072;&#1090;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080; &#1080; &#1073;&#1086;&#1083;&#1100;&#1096;&#1077; &#1085;&#1077; &#1090;&#1088;&#1077;&#1073;&#1091;&#1102;&#1090;&#1089;&#1103;:
  mythmusic mytharchive mythbrowser twolame fftw2 libclass-factory-util-perl
  transcode-doc libmath-round-perl dbconfig-common python-lxml mythgallery
  libmpich1.0gf mythgame dvdauthor mythmovies libimage-size-perl
  libdatetime-format-builder-perl libdatetime-format-iso8601-perl
  python-chardet transcode python-utidylib mythnetvision libcarp-clan-perl sox
  wwwconfig-common mythweather mythvideo libgfortran3 mythnews
  pulseaudio-module-raop perlmagick python-feedparser javascript-common
  pulseaudio-module-zeroconf libtidy-0.99-0 python-imdbpy libjs-mootools
&#1044;&#1083;&#1103; &#1080;&#1093; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1080;&#1103; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1081;&#1090;&#1077; 'apt-get autoremove'.
&#1055;&#1088;&#1077;&#1076;&#1083;&#1072;&#1075;&#1072;&#1077;&#1084;&#1099;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099;:
  apmd alsa-oss oss-compat
&#1053;&#1054;&#1042;&#1067;&#1045; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099;, &#1082;&#1086;&#1090;&#1086;&#1088;&#1099;&#1077; &#1073;&#1091;&#1076;&#1091;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1099;:
  alsa-base
&#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0, &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 1 &#1085;&#1086;&#1074;&#1099;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1076;&#1083;&#1103; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1080;&#1103; &#1086;&#1090;&#1084;&#1077;&#1095;&#1077;&#1085;&#1086; 0 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1080; 1357 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1085;&#1077; &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086;.
&#1053;&#1077;&#1086;&#1073;&#1093;&#1086;&#1076;&#1080;&#1084;&#1086; &#1089;&#1082;&#1072;&#1095;&#1072;&#1090;&#1100; 0B/140kB &#1072;&#1088;&#1093;&#1080;&#1074;&#1086;&#1074;.
&#1055;&#1086;&#1089;&#1083;&#1077; &#1076;&#1072;&#1085;&#1085;&#1086;&#1081; &#1086;&#1087;&#1077;&#1088;&#1072;&#1094;&#1080;&#1080;, &#1086;&#1073;&#1098;&#1105;&#1084; &#1079;&#1072;&#1085;&#1103;&#1090;&#1086;&#1075;&#1086; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074;&#1086;&#1075;&#1086; &#1087;&#1088;&#1086;&#1089;&#1090;&#1088;&#1072;&#1085;&#1089;&#1090;&#1074;&#1072; &#1074;&#1086;&#1079;&#1088;&#1072;&#1089;&#1090;&#1105;&#1090; &#1085;&#1072; 528kB.
&#1042;&#1099;&#1073;&#1086;&#1088; &#1088;&#1072;&#1085;&#1077;&#1077; &#1085;&#1077; &#1074;&#1099;&#1073;&#1088;&#1072;&#1085;&#1085;&#1086;&#1075;&#1086; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; alsa-base.
(&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1073;&#1072;&#1079;&#1099; &#1076;&#1072;&#1085;&#1085;&#1099;&#1093; ... &#1085;&#1072; &#1076;&#1072;&#1085;&#1085;&#1099;&#1081; &#1084;&#1086;&#1084;&#1077;&#1085;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 209088 &#1092;&#1072;&#1081;&#1083;&#1086;&#1074; &#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1086;&#1074;.)
&#1056;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1099;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; alsa-base (&#1080;&#1079; &#1092;&#1072;&#1081;&#1083;&#1072; .../alsa-base_1.0.24+dfsg-0ubuntu1_all.deb)...
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; alsa-base (1.0.24+dfsg-0ubuntu1) ...
user@user-desktop:~$ sudo /sbin/alsa reload



Doing modprobing  ....NONE

&#1076;&#1077;&#1083;&#1072;&#1083; Modprobe snd_hda_intel - &#1085;&#1077; &#1087;&#1086;&#1084;&#1086;&#1075;&#1083;&#1086; - &#1079;&#1074;&#1091;&#1082; &#1085;&#1077; &#1087;&#1086;&#1103;&#1074;&#1080;&#1083;&#1103;&#1089;

user@user-desktop:~$ lspci -v | grep snd
    Kernel modules: snd-hda-intel
user@user-desktop:~$ lspci -v | grep realtek
user@user-desktop:~$ lspci -v | grep intel
    Kernel modules: snd-hda-intel
user@user-desktop:~$ lsmod | grep intel
snd_hda_intel          25677  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm                87882  4 snd_pcm_oss,saa7134_alsa,snd_hda_intel,snd_hda_codec
snd                    71187  19 snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_hda_codec_realtek,saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
user@user-desktop:~$ modprobe snd_hda_intel
user@user-desktop:~$


Looking backports...none

user@user-desktop:~$ sudo apt-get install linux-headers-`uname -r` linux-backports-modules-alsa-`uname -r` linux-backports-modules-alsa-maverick-generic
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081;       
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080; &#1086; &#1089;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1080;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
E: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1085;&#1072;&#1081;&#1090;&#1080; &#1087;&#1072;&#1082;&#1077;&#1090; linux-backports-modules-alsa-2.6.32-24-generic
E: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1085;&#1072;&#1081;&#1090;&#1080; &#1087;&#1072;&#1082;&#1077;&#1090; &#1087;&#1086; &#1088;&#1077;&#1075;&#1091;&#1083;&#1103;&#1088;&#1085;&#1086;&#1084;&#1091; &#1074;&#1099;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1102; linux-backports-modules-alsa-2.6.32-24-generic

---

### Post by BicyclerBoy on 2011-12-12
Your alsa looks ancient ..(1.0.21)
What did you try doing to alsa ?
purge/remove & then install alsa backport modules (kernel driver) ?
Can't believe you need to update alsa.

This probably fails because your kernel is old & the matching backports package is missing..

Does your card not support internal digital audio ?
Be aware that later kernels have dropped legacy v4l support (2.6.38).

Check
dmesg | grep saa713

---

