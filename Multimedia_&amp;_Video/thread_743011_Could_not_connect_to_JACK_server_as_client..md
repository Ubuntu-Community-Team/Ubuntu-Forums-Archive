---
title: "Could not connect to JACK server as client."
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by AndreasTR on 2008-04-02
Hi,

Every time I start JACK Control I get this following error message :

14:38:58.001 Patchbay deactivated.
14:38:58.021 Statistics reset.
JACK tmpdir identified as [/dev/shm]
14:38:58.099 MIDI connection graph change.
14:38:58.239 MIDI connection change.
14:39:07.889 Startup script...
14:39:07.890 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
sound server terminated
14:39:08.195 Startup script terminated successfully.
14:39:08.195 JACK is starting...
14:39:08.196 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p128 -n2
14:39:08.201 JACK was started with PID=6830 (0x1aae).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|128|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
14:39:08.233 JACK was stopped successfully.
14:39:08.235 Post-shutdown script...
14:39:08.235 killall jackd
jackd: no process killed
14:39:08.463 Post-shutdown script terminated with exit status=256.
14:39:10.225 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
14:39:24.142 Startup script...
14:39:24.143 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:39:24.424 Startup script terminated with exit status=256.
14:39:24.425 JACK is starting...
14:39:24.425 jackstart -dalsa -dhw:0 -r44100 -p128 -n2
14:39:24.431 Could not start JACK. Sorry.
14:39:25.310 JACK was stopped successfully.
14:39:25.312 Post-shutdown script...
14:39:25.314 killall jackd
jackd: no process killed
14:39:25.532 Post-shutdown script terminated with exit status=256.
14:39:36.300 Startup script...
14:39:36.300 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:39:36.580 Startup script terminated with exit status=256.
14:39:36.580 JACK is starting...
14:39:36.581 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p128 -n2
14:39:36.586 JACK was started with PID=6848 (0x1ac0).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|128|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
14:39:36.602 JACK was stopped successfully.
14:39:36.603 Post-shutdown script...
14:39:36.603 killall jackd
jackd: no process killed
14:39:36.812 Post-shutdown script terminated with exit status=256.
14:39:38.609 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
14:39:51.522 Startup script...
14:39:51.523 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:39:51.796 Startup script terminated with exit status=256.
14:39:51.797 JACK is starting...
14:39:51.797 jackd -dalsa -dhw:0 -r44100 -p128 -n2
14:39:51.802 JACK was started with PID=6859 (0x1acb).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|128|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
14:39:51.832 JACK was stopped successfully.
14:39:51.833 Post-shutdown script...
14:39:51.833 killall jackd
jackd: no process killed
14:39:52.056 Post-shutdown script terminated with exit status=256.
14:39:53.823 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
14:40:01.201 Startup script...
14:40:01.201 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:40:01.481 Startup script terminated with exit status=256.
14:40:01.482 JACK is starting...
14:40:01.482 jackd-realtime -dalsa -dhw:0 -r44100 -p128 -n2
14:40:01.488 Could not start JACK. Sorry.
14:40:02.104 JACK was stopped successfully.
14:40:02.107 Post-shutdown script...
14:40:02.109 killall jackd
jackd: no process killed
14:40:02.327 Post-shutdown script terminated with exit status=256.
14:40:21.742 Startup script...
14:40:21.742 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:40:22.021 Startup script terminated with exit status=256.
14:40:22.022 JACK is starting...
14:40:22.022 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p128 -n2 -s -S
14:40:22.025 JACK was started with PID=6877 (0x1add).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|128|2|44100|0|0|nomon|swmeter|soft-mode|16bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
14:40:22.065 JACK was stopped successfully.
14:40:22.065 Post-shutdown script...
14:40:22.065 killall jackd
jackd: no process killed
14:40:22.274 Post-shutdown script terminated with exit status=256.
14:40:24.046 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
14:40:58.680 Startup script...
14:40:58.681 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:40:58.951 Startup script terminated with exit status=256.
14:40:58.951 JACK is starting...
14:40:58.952 /usr/bin/jackd -R -p128 -t200 -dalsa -dhw:0 -r22050 -p32 -n2 -s -S
14:40:58.956 JACK was started with PID=6889 (0x1ae9).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 22050
creating alsa driver ... hw:0|hw:0|32|2|22050|0|0|nomon|swmeter|soft-mode|16bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
14:40:59.044 JACK was stopped successfully.
14:40:59.045 Post-shutdown script...
14:40:59.045 killall jackd
jackd: no process killed
14:40:59.268 Post-shutdown script terminated with exit status=256.
14:41:00.979 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
14:41:11.094 Startup script...
14:41:11.094 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:41:11.370 Startup script terminated with exit status=256.
14:41:11.370 JACK is starting...
14:41:11.370 /usr/bin/jackd -R -p128 -t200 -dalsa -dhw:0 -r22050 -p32 -n2 -s -S -zr
14:41:11.372 JACK was started with PID=6900 (0x1af4).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 22050
creating alsa driver ... hw:0|hw:0|32|2|22050|0|0|nomon|swmeter|soft-mode|16bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
14:41:11.410 JACK was stopped successfully.
14:41:11.410 Post-shutdown script...
14:41:11.410 killall jackd
jackd: no process killed
14:41:11.619 Post-shutdown script terminated with exit status=256.
14:41:13.423 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
14:41:39.522 Startup script...
14:41:39.523 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:41:39.795 Startup script terminated with exit status=256.
14:41:39.796 JACK is starting...
14:41:39.796 /usr/bin/jackd -R -p128 -t200 -dalsa -dhw:0 -r22050 -p32 -n2 -m -S -zr
14:41:39.801 JACK was started with PID=6911 (0x1aff).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 22050
creating alsa driver ... hw:0|hw:0|32|2|22050|0|0|nomon|swmeter|-|16bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
14:41:39.894 JACK was stopped successfully.
14:41:39.895 Post-shutdown script...
14:41:39.896 killall jackd
jackd: no process killed
14:41:40.119 Post-shutdown script terminated with exit status=256.
14:41:41.827 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
14:42:12.917 Startup script...
14:42:12.918 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:42:13.190 Startup script terminated with exit status=256.
14:42:13.190 JACK is starting...
14:42:13.191 /usr/bin/jackd -R -p128 -t200 -dalsa -dhw:0 -r22050 -p32 -n2 -P -S -o1 -O1
14:42:13.196 JACK was started with PID=6922 (0x1b0a).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 22050
creating alsa driver ... hw:0|-|32|2|22050|0|1|nomon|swmeter|-|16bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
14:42:13.286 JACK was stopped successfully.
14:42:13.287 Post-shutdown script...
14:42:13.287 killall jackd
jackd: no process killed
14:42:13.510 Post-shutdown script terminated with exit status=256.
14:42:15.385 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
14:43:23.657 Startup script...
14:43:23.658 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:43:23.927 Startup script terminated with exit status=256.
14:43:23.928 JACK is starting...
14:43:23.928 /usr/bin/jackd -R -p128 -t200 -dalsa -dhw:0 -r22050 -p32 -n2 -P -S -o1 -O1
14:43:23.933 JACK was started with PID=6939 (0x1b1b).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 22050
creating alsa driver ... hw:0|-|32|2|22050|0|1|nomon|swmeter|-|16bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
14:43:24.020 JACK was stopped successfully.
14:43:24.021 Post-shutdown script...
14:43:24.021 killall jackd
jackd: no process killed
14:43:24.246 Post-shutdown script terminated with exit status=256.
14:43:26.083 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
14:43:32.409 Startup script...
14:43:32.409 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:43:32.688 Startup script terminated with exit status=256.
14:43:32.689 JACK is starting...
14:43:32.689 /usr/bin/jackd -R -P1 -p128 -t200 -dalsa -dhw:0 -r22050 -p32 -n2 -P -S -o1 -O1
14:43:32.694 JACK was started with PID=6950 (0x1b26).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 22050
creating alsa driver ... hw:0|-|32|2|22050|0|1|nomon|swmeter|-|16bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
14:43:32.742 JACK was stopped successfully.
14:43:32.742 Post-shutdown script...
14:43:32.742 killall jackd
jackd: no process killed
14:43:32.952 Post-shutdown script terminated with exit status=256.
14:43:34.718 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
14:44:21.946 Startup script...
14:44:21.946 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:44:22.218 Startup script terminated with exit status=256.
14:44:22.219 JACK is starting...
14:44:22.219 /usr/bin/jackd -R -P1 -p128 -t200 -m -dalsa -dhw:0 -r22050 -p32 -n2 -P -s -m -S -o1 -O1
14:44:22.224 JACK was started with PID=6962 (0x1b32).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 22050
creating alsa driver ... hw:0|-|32|2|22050|0|1|nomon|swmeter|soft-mode|16bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
14:44:22.254 JACK was stopped successfully.
14:44:22.255 Post-shutdown script...
14:44:22.255 killall jackd
jackd: no process killed
14:44:22.478 Post-shutdown script terminated with exit status=256.
14:44:24.248 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
14:44:55.610 Startup script...
14:44:55.610 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:44:55.840 Startup script terminated with exit status=256.
14:44:55.840 JACK is starting...
14:44:55.840 /usr/bin/jackd -p128 -t200 -dalsa -dhw:0 -r22050 -p32 -n2 -P -S -o1 -O1
14:44:55.842 JACK was started with PID=6973 (0x1b3d).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 22050
creating alsa driver ... hw:0|-|32|2|22050|0|1|nomon|swmeter|-|16bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
14:44:55.856 JACK was stopped successfully.
14:44:55.857 Post-shutdown script...
14:44:55.857 killall jackd
jackd: no process killed
14:44:56.067 Post-shutdown script terminated with exit status=256.
14:44:57.926 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
14:45:13.137 Startup script...
14:45:13.137 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:45:13.411 Startup script terminated with exit status=256.
14:45:13.412 JACK is starting...
14:45:13.412 /usr/bin/jackd -p128 -t200 -dalsa -dhw:0 -r22050 -p32 -n2 -P -S -o1 -O1
14:45:13.417 JACK was started with PID=6984 (0x1b48).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 22050
creating alsa driver ... hw:0|-|32|2|22050|0|1|nomon|swmeter|-|16bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
14:45:13.447 JACK was stopped successfully.
14:45:13.449 Post-shutdown script...
14:45:13.449 killall jackd
jackd: no process killed
14:45:13.672 Post-shutdown script terminated with exit status=256.
14:45:15.497 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
14:47:43.675 Startup script...
14:47:43.675 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:47:43.950 Startup script terminated with exit status=256.
14:47:43.951 JACK is starting...
14:47:43.951 /sbin/modprobe snd-seq-oss -p128 -t200 -dalsa -dhw:0 -r22050 -p32 -n2 -P -S -o1 -O1
14:47:43.956 JACK was started with PID=6998 (0x1b56).
/sbin/modprobe: invalid option -- p
Usage: /sbin/modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o ] [ --dump-modversions ]  [parameters...]
/sbin/modprobe -r [-n] [-i] [-v]  ...
/sbin/modprobe -l -t  [ -a  ...]
14:47:43.961 JACK was stopped with exit status=1.
14:47:43.961 Post-shutdown script...
14:47:43.962 killall jackd
jackd: no process killed
14:47:44.186 Post-shutdown script terminated with exit status=256.
14:47:46.102 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
14:51:02.914 Startup script...
14:51:02.914 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:51:03.145 Startup script terminated with exit status=256.
14:51:03.145 JACK is starting...
14:51:03.145 /usr/bin/jackd -p128 -t200 -dalsa -dhw:0 -r22050 -p32 -n2 -P -S -o1 -O1
14:51:03.147 JACK was started with PID=7037 (0x1b7d).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 22050
creating alsa driver ... hw:0|-|32|2|22050|0|1|nomon|swmeter|-|16bit
control device hw:0
configuring for 22050Hz, period = 32 frames, buffer = 2 periods
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: cannot set channel count to 1 for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
no message buffer overruns
14:51:03.162 JACK was stopped successfully.
14:51:03.162 Post-shutdown script...
14:51:03.162 killall jackd
jackd: no process killed
14:51:03.372 Post-shutdown script terminated with exit status=256.
14:51:05.279 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
15:03:36.945 Startup script...
15:03:36.946 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
15:03:37.221 Startup script terminated with exit status=256.
15:03:37.221 JACK is starting...
15:03:37.222 /usr/bin/jackd -p128 -t200 -dalsa -dhw:0 -r22050 -p32 -n2 -P -S -o1 -O1
15:03:37.227 JACK was started with PID=7084 (0x1bac).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 22050
creating alsa driver ... hw:0|-|32|2|22050|0|1|nomon|swmeter|-|16bit
control device hw:0
configuring for 22050Hz, period = 32 frames, buffer = 2 periods
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: cannot set channel count to 1 for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
no message buffer overruns
15:03:37.259 JACK was stopped successfully.
15:03:37.260 Post-shutdown script...
15:03:37.260 killall jackd
jackd: no process killed
15:03:37.484 Post-shutdown script terminated with exit status=256.
15:03:39.250 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
15:14:09.070 Startup script...
15:14:09.070 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
15:14:09.302 Startup script terminated with exit status=256.
15:14:09.302 JACK is starting...
15:14:09.302 /usr/bin/jackd -p128 -t200 -dalsa -dhw:0 -r22050 -p32 -n2 -P -S -o1 -O1
15:14:09.305 JACK was started with PID=7114 (0x1bca).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 22050
creating alsa driver ... hw:0|-|32|2|22050|0|1|nomon|swmeter|-|16bit
control device hw:0
configuring for 22050Hz, period = 32 frames, buffer = 2 periods
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: cannot set channel count to 1 for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
no message buffer overruns
15:14:09.320 JACK was stopped successfully.
15:14:09.320 Post-shutdown script...
15:14:09.320 killall jackd
jackd: no process killed
15:14:09.530 Post-shutdown script terminated with exit status=256.
15:14:11.385 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
 
I hava a HP Pavilion dv9000. 

And I´m not so good with computers.

See the problem:confused:

AndreasTR

---

### Post by jakupl on 2008-04-04
bump:KS

---

### Post by jakupl on 2008-04-04
I think you mean this:

```
14:43:32.409 Startup script...
14:43:32.409 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
14:43:32.688 Startup script terminated with exit status=256.
14:43:32.689 JACK is starting...
14:43:32.689 /usr/bin/jackd -R -P1 -p128 -t200 -dalsa -dhw:0 -r22050 -p32 -n2 -P -S -o1 -O1
14:43:32.694 JACK was started with PID=6950 (0x1b26).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 22050
creating alsa driver ... hw:0|-|32|2|22050|0|1|nomon|swmeter|-|16bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
14:43:32.742 JACK was stopped successfully.
14:43:32.742 Post-shutdown script...
14:43:32.742 killall jackd
jackd: no process killed
14:43:32.952 Post-shutdown script terminated with exit status=256.
14:43:34.718 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
```

It is basically the same over and over again.... mostly ;)

---

### Post by jakupl on 2008-04-14
one last bump

---

