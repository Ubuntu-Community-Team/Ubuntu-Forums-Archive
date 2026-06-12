---
title: "dvd::rip - make test error - 0/2 for tonight"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by Crash90 on 2008-03-03
Wow first I can't install Mplayer and now I can't install dvd::rip - all that time checking dependcies and I can't install either one. 


Either way, here is the output I get when using the make test command. It should be noted that my  perl makefile.pl command worked fine

```
cp lib/Video/DVDRip.pm blib/lib/Video/DVDRip.pm
cp lib/Video/DVDRip/GUI/Icons/dvdrip-scan-volume.png blib/lib/Video/DVDRip/GUI/Icons/dvdrip-scan-volume.png
cp lib/Video/DVDRip/splash.de.png blib/lib/Video/DVDRip/splash.de.png
cp lib/Video/DVDRip/PSU.pm blib/lib/Video/DVDRip/PSU.pm
cp lib/Video/DVDRip/GUI/Cluster/Control.pm blib/lib/Video/DVDRip/GUI/Cluster/Control.pm
cp lib/Video/DVDRip/GUI/FormFactory/SubtitlePreviews.pm blib/lib/Video/DVDRip/GUI/FormFactory/SubtitlePreviews.pm
cp lib/Video/DVDRip/Cluster/Node.pm blib/lib/Video/DVDRip/Cluster/Node.pm
cp lib/Video/DVDRip/splash.en.png blib/lib/Video/DVDRip/splash.en.png
cp lib/Video/DVDRip/GUI/Filters.pm blib/lib/Video/DVDRip/GUI/Filters.pm
cp lib/Video/DVDRip/Cluster/Pipe.pm blib/lib/Video/DVDRip/Cluster/Pipe.pm
cp lib/LocaleData/fr/LC_MESSAGES/video.dvdrip.mo blib/lib/LocaleData/fr/LC_MESSAGES/video.dvdrip.mo
cp lib/Video/DVDRip/SrtxFile.pm blib/lib/Video/DVDRip/SrtxFile.pm
cp lib/Video/DVDRip/Cluster/Scheduler.pm blib/lib/Video/DVDRip/Cluster/Scheduler.pm
cp lib/Video/DVDRip/Convert.pm blib/lib/Video/DVDRip/Convert.pm
cp lib/LocaleData/es/LC_MESSAGES/video.dvdrip.mo blib/lib/LocaleData/es/LC_MESSAGES/video.dvdrip.mo
cp lib/Video/DVDRip/Logger.pm blib/lib/Video/DVDRip/Logger.pm
cp lib/Video/DVDRip/Subtitle.pm blib/lib/Video/DVDRip/Subtitle.pm
cp lib/Video/DVDRip/license.txt blib/lib/Video/DVDRip/license.txt
cp lib/Video/DVDRip/Depend.pm blib/lib/Video/DVDRip/Depend.pm
cp lib/Video/DVDRip/GUI/Project/Transcode.pm blib/lib/Video/DVDRip/GUI/Project/Transcode.pm
cp lib/Video/DVDRip/GUI/Project/Logging.pm blib/lib/Video/DVDRip/GUI/Project/Logging.pm
cp lib/Video/DVDRip/Audio.pm blib/lib/Video/DVDRip/Audio.pm
cp lib/Video/DVDRip/GUI/Context.pm blib/lib/Video/DVDRip/GUI/Context.pm
cp lib/Video/DVDRip/Term/Main.pm blib/lib/Video/DVDRip/Term/Main.pm
cp lib/Video/DVDRip/Term/ExitTask.pm blib/lib/Video/DVDRip/Term/ExitTask.pm
cp lib/LocaleData/it/LC_MESSAGES/video.dvdrip.mo blib/lib/LocaleData/it/LC_MESSAGES/video.dvdrip.mo
cp lib/Video/DVDRip/Project.pm blib/lib/Video/DVDRip/Project.pm
cp lib/Video/DVDRip/GUI/Preferences.pm blib/lib/Video/DVDRip/GUI/Preferences.pm
cp lib/Video/DVDRip/translators.txt blib/lib/Video/DVDRip/translators.txt
cp lib/Video/DVDRip/TranscodeRC.pm blib/lib/Video/DVDRip/TranscodeRC.pm
cp lib/Video/DVDRip/Content.pm blib/lib/Video/DVDRip/Content.pm
cp lib/Video/DVDRip/FilterSettings.pm blib/lib/Video/DVDRip/FilterSettings.pm
cp lib/Video/DVDRip/Preset.pm blib/lib/Video/DVDRip/Preset.pm
cp lib/Video/DVDRip/splash.it.png blib/lib/Video/DVDRip/splash.it.png
cp lib/Video/DVDRip/CPAN/Scanf.pm blib/lib/Video/DVDRip/CPAN/Scanf.pm
cp lib/Video/DVDRip/BitrateCalc.pm blib/lib/Video/DVDRip/BitrateCalc.pm
cp lib/Video/DVDRip/Base.pm blib/lib/Video/DVDRip/Base.pm
cp lib/Video/DVDRip/GUI/Base.pm blib/lib/Video/DVDRip/GUI/Base.pm
cp lib/Video/DVDRip/GUI/FormFactory/ClipImage.pm blib/lib/Video/DVDRip/GUI/FormFactory/ClipImage.pm
cp lib/LocaleData/sr/LC_MESSAGES/video.dvdrip.mo blib/lib/LocaleData/sr/LC_MESSAGES/video.dvdrip.mo
cp lib/Video/DVDRip/Term/Progress.pm blib/lib/Video/DVDRip/Term/Progress.pm
cp lib/Video/DVDRip/Cluster/Title.pm blib/lib/Video/DVDRip/Cluster/Title.pm
cp lib/Video/DVDRip/GUI/Project/Title.pm blib/lib/Video/DVDRip/GUI/Project/Title.pm
cp lib/Video/DVDRip/Cluster/PSU.pm blib/lib/Video/DVDRip/Cluster/PSU.pm
cp lib/Video/DVDRip/splash.sr.png blib/lib/Video/DVDRip/splash.sr.png
cp lib/Video/DVDRip/Config.pm blib/lib/Video/DVDRip/Config.pm
cp lib/Video/DVDRip/GUI/Icons/dvdrip-audio-matrix.png blib/lib/Video/DVDRip/GUI/Icons/dvdrip-audio-matrix.png
cp lib/Video/DVDRip/GUI/Project/Subtitle.pm blib/lib/Video/DVDRip/GUI/Project/Subtitle.pm
cp lib/Video/DVDRip/GUI/Preview.pm blib/lib/Video/DVDRip/GUI/Preview.pm
cp lib/Video/DVDRip/Cluster/Master.pm blib/lib/Video/DVDRip/Cluster/Master.pm
cp lib/Video/DVDRip/splash.ca.png blib/lib/Video/DVDRip/splash.ca.png
cp lib/Video/DVDRip/Cluster/JobPlanner.pm blib/lib/Video/DVDRip/Cluster/JobPlanner.pm
cp lib/LocaleData/cs/LC_MESSAGES/video.dvdrip.mo blib/lib/LocaleData/cs/LC_MESSAGES/video.dvdrip.mo
cp lib/Video/DVDRip/Cluster/Project.pm blib/lib/Video/DVDRip/Cluster/Project.pm
cp lib/Video/DVDRip/splash.es.png blib/lib/Video/DVDRip/splash.es.png
cp lib/Video/DVDRip/Title.pm blib/lib/Video/DVDRip/Title.pm
cp lib/Video/DVDRip/Cluster/Webserver.pm blib/lib/Video/DVDRip/Cluster/Webserver.pm
cp lib/Video/DVDRip/GUI/Icons/dvdrip-play-movie.png blib/lib/Video/DVDRip/GUI/Icons/dvdrip-play-movie.png
cp lib/Video/DVDRip/icon.xpm blib/lib/Video/DVDRip/icon.xpm
cp lib/LocaleData/sr@Latn/LC_MESSAGES/video.dvdrip.mo blib/lib/LocaleData/sr@Latn/LC_MESSAGES/video.dvdrip.mo
cp lib/Video/DVDRip/GUI/Icons/dvdrip-clip-move.png blib/lib/Video/DVDRip/GUI/Icons/dvdrip-clip-move.png
cp lib/Video/DVDRip/GUI/BitrateCalc.pm blib/lib/Video/DVDRip/GUI/BitrateCalc.pm
cp lib/Video/DVDRip/GUI/Cluster/Node.pm blib/lib/Video/DVDRip/GUI/Cluster/Node.pm
cp lib/Video/DVDRip/GUI/Icons/dvdrip-calc-width.png blib/lib/Video/DVDRip/GUI/Icons/dvdrip-calc-width.png
cp lib/Video/DVDRip/splash.sr@Latn.png blib/lib/Video/DVDRip/splash.sr@Latn.png
cp lib/Video/DVDRip/GUI/Cluster/Title.pm blib/lib/Video/DVDRip/GUI/Cluster/Title.pm
cp lib/LocaleData/de/LC_MESSAGES/video.dvdrip.mo blib/lib/LocaleData/de/LC_MESSAGES/video.dvdrip.mo
cp lib/Video/DVDRip/GUI/Depend.pm blib/lib/Video/DVDRip/GUI/Depend.pm
cp lib/Video/DVDRip/GUI/Icons/dvdrip-calc-height.png blib/lib/Video/DVDRip/GUI/Icons/dvdrip-calc-height.png
cp lib/Video/DVDRip/Probe.pm blib/lib/Video/DVDRip/Probe.pm
cp lib/Video/DVDRip/GUI/MultiAudio.pm blib/lib/Video/DVDRip/GUI/MultiAudio.pm
cp lib/Video/DVDRip/FilterList.pm blib/lib/Video/DVDRip/FilterList.pm
cp lib/Video/DVDRip/InfoFile.pm blib/lib/Video/DVDRip/InfoFile.pm
cp lib/Video/DVDRip/GUI/Main.pm blib/lib/Video/DVDRip/GUI/Main.pm
cp lib/Video/DVDRip/GUI/Project/ClipZoom.pm blib/lib/Video/DVDRip/GUI/Project/ClipZoom.pm
cp lib/Video/DVDRip/GUI/Progress.pm blib/lib/Video/DVDRip/GUI/Progress.pm
cp lib/Video/DVDRip/Cluster/ExecFlowFrontend.pm blib/lib/Video/DVDRip/Cluster/ExecFlowFrontend.pm
cp lib/Video/DVDRip/GUI/Pipe.pm blib/lib/Video/DVDRip/GUI/Pipe.pm
cp lib/Video/DVDRip/GUI/Rules.pm blib/lib/Video/DVDRip/GUI/Rules.pm
cp lib/Video/DVDRip/GUI/ExecFlow.pm blib/lib/Video/DVDRip/GUI/ExecFlow.pm
cp lib/Video/DVDRip/GUI/ZoomCalculator.pm blib/lib/Video/DVDRip/GUI/ZoomCalculator.pm
cp lib/Video/DVDRip/GUI/Project/Storage.pm blib/lib/Video/DVDRip/GUI/Project/Storage.pm
cp lib/Video/DVDRip/JobPlanner.pm blib/lib/Video/DVDRip/JobPlanner.pm
cd src && make
make[1]: Entering directory `/home/peter/Desktop/dvdrip-0.98.8/src'
cc  -o dvdrip-splitpipe dvdrip-splitpipe.c && mv dvdrip-splitpipe ../bin
dvdrip-splitpipe.c:10:20: error: stdlib.h: No such file or directory
dvdrip-splitpipe.c:11:19: error: stdio.h: No such file or directory
dvdrip-splitpipe.c:12:20: error: unistd.h: No such file or directory
dvdrip-splitpipe.c:13:23: error: sys/types.h: No such file or directory
dvdrip-splitpipe.c:14:22: error: sys/stat.h: No such file or directory
dvdrip-splitpipe.c:15:19: error: fcntl.h: No such file or directory
dvdrip-splitpipe.c:25: error: expected declaration specifiers or ‘...’ before ‘size_t’
dvdrip-splitpipe.c:26: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
dvdrip-splitpipe.c: In function ‘usage’:
dvdrip-splitpipe.c:30: warning: incompatible implicit declaration of built-in function ‘printf’
dvdrip-splitpipe.c:32: warning: incompatible implicit declaration of built-in function ‘exit’
dvdrip-splitpipe.c: In function ‘fatal’:
dvdrip-splitpipe.c:37: warning: incompatible implicit declaration of built-in function ‘fprintf’
dvdrip-splitpipe.c:37: error: ‘stderr’ undeclared (first use in this function)
dvdrip-splitpipe.c:37: error: (Each undeclared identifier is reported only once
dvdrip-splitpipe.c:37: error: for each function it appears in.)
dvdrip-splitpipe.c:38: warning: incompatible implicit declaration of built-in function ‘exit’
dvdrip-splitpipe.c: In function ‘main’:
dvdrip-splitpipe.c:57: error: ‘optarg’ undeclared (first use in this function)
dvdrip-splitpipe.c:67: error: ‘optind’ undeclared (first use in this function)
dvdrip-splitpipe.c:69: warning: incompatible implicit declaration of built-in function ‘sscanf’
dvdrip-splitpipe.c: In function ‘split_pipe’:
dvdrip-splitpipe.c:89: error: ‘FILE’ undeclared (first use in this function)
dvdrip-splitpipe.c:89: error: ‘tcdemux_fd’ undeclared (first use in this function)
dvdrip-splitpipe.c:90: error: ‘size_t’ undeclared (first use in this function)
dvdrip-splitpipe.c:90: error: expected ‘;’ before ‘bytes_read’
dvdrip-splitpipe.c:91: error: expected ‘;’ before ‘bytes_written’
dvdrip-splitpipe.c:92: error: expected ‘;’ before ‘bytes_this_chunk’
dvdrip-splitpipe.c:93: error: expected ‘;’ before ‘bytes_next_chunk’
dvdrip-splitpipe.c:105: error: ‘bytes_read’ undeclared (first use in this function)
dvdrip-splitpipe.c:107: warning: incompatible implicit declaration of built-in function ‘fprintf’
dvdrip-splitpipe.c:107: error: ‘stderr’ undeclared (first use in this function)
dvdrip-splitpipe.c:116: warning: incompatible implicit declaration of built-in function ‘fwrite’
dvdrip-splitpipe.c:119: warning: incompatible implicit declaration of built-in function ‘fprintf’
dvdrip-splitpipe.c:119: error: ‘bytes_written’ undeclared (first use in this function)
dvdrip-splitpipe.c:123: error: ‘bytes_this_chunk’ undeclared (first use in this function)
dvdrip-splitpipe.c:124: error: ‘bytes_next_chunk’ undeclared (first use in this function)
dvdrip-splitpipe.c:126: error: too many arguments to function ‘write_split_file’
dvdrip-splitpipe.c:133: error: too many arguments to function ‘write_split_file’
dvdrip-splitpipe.c:137: error: too many arguments to function ‘write_split_file’
dvdrip-splitpipe.c:148: warning: incompatible implicit declaration of built-in function ‘fprintf’
dvdrip-splitpipe.c: At top level:
dvdrip-splitpipe.c:152: error: expected declaration specifiers or ‘...’ before ‘size_t’
dvdrip-splitpipe.c: In function ‘write_split_file’:
dvdrip-splitpipe.c:155: error: ‘cnt’ undeclared (first use in this function)
dvdrip-splitpipe.c: In function ‘open_split_file’:
dvdrip-splitpipe.c:174: warning: incompatible implicit declaration of built-in function ‘sprintf’
dvdrip-splitpipe.c:179: warning: incompatible implicit declaration of built-in function ‘fprintf’
dvdrip-splitpipe.c:179: error: ‘stderr’ undeclared (first use in this function)
dvdrip-splitpipe.c: At top level:
dvdrip-splitpipe.c:187: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
dvdrip-splitpipe.c: In function ‘open_vob_nav_file’:
dvdrip-splitpipe.c:205: warning: incompatible implicit declaration of built-in function ‘fprintf’
dvdrip-splitpipe.c:205: error: ‘stderr’ undeclared (first use in this function)
make[1]: *** [../bin/dvdrip-splitpipe] Error 1
make[1]: Leaving directory `/home/peter/Desktop/dvdrip-0.98.8/src'
make: *** [bin/dvdrip-progress] Error 2

```

---

### Post by sanddgroper on 2008-03-03
Hi
once again why not use synaptic

Cheers
Sandy

---

### Post by Crash90 on 2008-03-03
Sandy

I tried using synaptic for this program. When I click on dvd::rip, it tells me I need to refresh the list. I do so and click again and get the same message.

EDIT: Looks like I can't read very well. I didn't right click to mark for install. Sorry, I had a tard moment.

---

