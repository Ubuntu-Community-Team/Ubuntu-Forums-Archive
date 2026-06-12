---
title: "uvc-streamer"
date: 2008-04-28
forum: Multimedia Software
---

### Post by transmutated on 2008-04-28
I'm trying to build uvc-streamer and I seem to be doing something wrong. I have got to the point to were I downloaded the source from sourceforge. When I go to build it, I get a long output of errors. Here it is:
 > gcc -O2 -DLINUX -Wall   -c -o uvc_stream.o uvc_stream.c
uvc_stream.c:45:19: error: stdio.h: No such file or directory
uvc_stream.c:46:20: error: stdlib.h: No such file or directory
uvc_stream.c:47:20: error: unistd.h: No such file or directory
uvc_stream.c:48:20: error: string.h: No such file or directory
uvc_stream.c:49:28: error: linux/videodev.h: No such file or directory
uvc_stream.c:50:23: error: sys/ioctl.h: No such file or directory
uvc_stream.c:51:19: error: errno.h: No such file or directory
uvc_stream.c:52:20: error: signal.h: No such file or directory
uvc_stream.c:53:24: error: sys/socket.h: No such file or directory
uvc_stream.c:54:23: error: arpa/inet.h: No such file or directory
uvc_stream.c:55:23: error: sys/types.h: No such file or directory
uvc_stream.c:56:22: error: sys/stat.h: No such file or directory
uvc_stream.c:57:20: error: getopt.h: No such file or directory
uvc_stream.c:58:21: error: pthread.h: No such file or directory
In file included from uvc_stream.c:61:
v4l2uvc.h:26:19: error: fcntl.h: No such file or directory
v4l2uvc.h:30:22: error: sys/mman.h: No such file or directory
v4l2uvc.h:31:24: error: sys/select.h: No such file or directory
In file included from v4l2uvc.h:34,
                 from uvc_stream.c:61:
uvcvideo.h:4:26: error: linux/kernel.h: No such file or directory
In file included from uvcvideo.h:8,
                 from v4l2uvc.h:34,
                 from uvc_stream.c:61:
uvc_compat.h:4:27: error: linux/version.h: No such file or directory
uvc_compat.h:6:40: error: missing binary operator before token "("
uvc_compat.h:50:40: error: missing binary operator before token "("
In file included from uvc_stream.c:61:
v4l2uvc.h:44: error: field ‘cap’ has incomplete type
v4l2uvc.h:45: error: field ‘fmt’ has incomplete type
v4l2uvc.h:46: error: field ‘buf’ has incomplete type
v4l2uvc.h:47: error: field ‘rb’ has incomplete type
v4l2uvc.h:69: error: expected specifier-qualifier-list before ‘FILE’
v4l2uvc.h:96: error: expected declaration specifiers or ‘...’ before ‘__u32’
v4l2uvc.h:96: error: expected declaration specifiers or ‘...’ before ‘__u32’
v4l2uvc.h:96: error: expected declaration specifiers or ‘...’ before ‘__u32’
v4l2uvc.h:97: error: expected declaration specifiers or ‘...’ before ‘__u32’
uvc_stream.c:75: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘db’
uvc_stream.c:76: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘db_update’
uvc_stream.c:79: error: ‘NULL’ undeclared here (not in a function)
uvc_stream.c: In function ‘client_thread’:
uvc_stream.c:85: error: ‘fd_set’ undeclared (first use in this function)
uvc_stream.c:85: error: (Each undeclared identifier is reported only once
uvc_stream.c:85: error: for each function it appears in.)
uvc_stream.c:85: error: expected ‘;’ before ‘fds’
uvc_stream.c:86: warning: implicit declaration of function ‘calloc’
uvc_stream.c:86: warning: incompatible implicit declaration of built-in function ‘calloc’
uvc_stream.c:86: error: ‘size_t’ undeclared (first use in this function)
uvc_stream.c:86: error: expected ‘)’ before ‘cd’
uvc_stream.c:89: error: storage size of ‘to’ isn’t known
uvc_stream.c:92: warning: implicit declaration of function ‘free’
uvc_stream.c:92: warning: implicit declaration of function ‘exit’
uvc_stream.c:92: warning: incompatible implicit declaration of built-in function ‘exit’
uvc_stream.c:97: warning: implicit declaration of function ‘FD_ZERO’
uvc_stream.c:97: error: ‘fds’ undeclared (first use in this function)
uvc_stream.c:98: warning: implicit declaration of function ‘FD_SET’
uvc_stream.c:99: warning: implicit declaration of function ‘select’
uvc_stream.c:100: warning: implicit declaration of function ‘close’
uvc_stream.c:106: warning: implicit declaration of function ‘read’
uvc_stream.c:107: warning: implicit declaration of function ‘strstr’
uvc_stream.c:107: warning: incompatible implicit declaration of built-in function ‘strstr’
uvc_stream.c:112: warning: implicit declaration of function ‘sprintf’
uvc_stream.c:112: warning: incompatible implicit declaration of built-in function ‘sprintf’
uvc_stream.c:118: warning: incompatible implicit declaration of built-in function ‘sprintf’
uvc_stream.c:127: warning: implicit declaration of function ‘write’
uvc_stream.c:127: warning: implicit declaration of function ‘strlen’
uvc_stream.c:127: warning: incompatible implicit declaration of built-in function ‘strlen’
uvc_stream.c:136: error: storage size of ‘tv’ isn’t known
uvc_stream.c:136: warning: implicit declaration of function ‘nanosleep’
uvc_stream.c:136: warning: unused variable ‘tv’
uvc_stream.c:140: warning: implicit declaration of function ‘pthread_cond_wait’
uvc_stream.c:140: error: ‘db_update’ undeclared (first use in this function)
uvc_stream.c:140: error: ‘db’ undeclared (first use in this function)
uvc_stream.c:144: warning: implicit declaration of function ‘memcpy’
uvc_stream.c:144: warning: incompatible implicit declaration of built-in function ‘memcpy’
uvc_stream.c:146: warning: implicit declaration of function ‘pthread_mutex_unlock’
uvc_stream.c:149: warning: incompatible implicit declaration of built-in function ‘sprintf’
uvc_stream.c:157: warning: incompatible implicit declaration of built-in function ‘sprintf’
uvc_stream.c:89: warning: unused variable ‘to’
uvc_stream.c: In function ‘cam_thread’:
uvc_stream.c:173: warning: implicit declaration of function ‘fprintf’
uvc_stream.c:173: warning: incompatible implicit declaration of built-in function ‘fprintf’
uvc_stream.c:173: error: ‘stderr’ undeclared (first use in this function)
uvc_stream.c:174: warning: incompatible implicit declaration of built-in function ‘exit’
uvc_stream.c:178: warning: implicit declaration of function ‘pthread_mutex_lock’
uvc_stream.c:178: error: ‘db’ undeclared (first use in this function)
uvc_stream.c:181: warning: incompatible implicit declaration of built-in function ‘memcpy’
uvc_stream.c:184: warning: implicit declaration of function ‘pthread_cond_broadcast’
uvc_stream.c:184: error: ‘db_update’ undeclared (first use in this function)
uvc_stream.c:189: warning: implicit declaration of function ‘usleep’
uvc_stream.c: In function ‘help’:
uvc_stream.c:198: warning: incompatible implicit declaration of built-in function ‘fprintf’
uvc_stream.c:198: error: ‘stderr’ undeclared (first use in this function)
uvc_stream.c: In function ‘signal_handler’:
uvc_stream.c:218: warning: incompatible implicit declaration of built-in function ‘fprintf’
uvc_stream.c:218: error: ‘stderr’ undeclared (first use in this function)
uvc_stream.c:223: warning: implicit declaration of function ‘perror’
uvc_stream.c:224: warning: implicit declaration of function ‘pthread_cond_destroy’
uvc_stream.c:224: error: ‘db_update’ undeclared (first use in this function)
uvc_stream.c:225: warning: implicit declaration of function ‘pthread_mutex_destroy’
uvc_stream.c:225: error: ‘db’ undeclared (first use in this function)
uvc_stream.c:226: warning: incompatible implicit declaration of built-in function ‘exit’
uvc_stream.c: In function ‘daemon_mode’:
uvc_stream.c:233: warning: implicit declaration of function ‘fork’
uvc_stream.c:235: warning: incompatible implicit declaration of built-in function ‘fprintf’
uvc_stream.c:235: error: ‘stderr’ undeclared (first use in this function)
uvc_stream.c:236: warning: incompatible implicit declaration of built-in function ‘exit’
uvc_stream.c:239: warning: incompatible implicit declaration of built-in function ‘exit’
uvc_stream.c:242: warning: implicit declaration of function ‘setsid’
uvc_stream.c:243: warning: incompatible implicit declaration of built-in function ‘fprintf’
uvc_stream.c:244: warning: incompatible implicit declaration of built-in function ‘exit’
uvc_stream.c:249: warning: incompatible implicit declaration of built-in function ‘fprintf’
uvc_stream.c:250: warning: incompatible implicit declaration of built-in function ‘exit’
uvc_stream.c:253: warning: incompatible implicit declaration of built-in function ‘fprintf’
uvc_stream.c:254: warning: incompatible implicit declaration of built-in function ‘exit’
uvc_stream.c:257: warning: implicit declaration of function ‘umask’
uvc_stream.c:259: warning: implicit declaration of function ‘chdir’
uvc_stream.c:264: warning: implicit declaration of function ‘open’
uvc_stream.c:264: error: ‘O_RDWR’ undeclared (first use in this function)
uvc_stream.c:265: warning: implicit declaration of function ‘dup’
uvc_stream.c: In function ‘main’:
uvc_stream.c:274: error: storage size of ‘addr’ isn’t known
uvc_stream.c:276: error: ‘pthread_t’ undeclared (first use in this function)
uvc_stream.c:276: error: expected ‘;’ before ‘client’
uvc_stream.c:285: warning: implicit declaration of function ‘htons’
uvc_stream.c:289: error: array type has incomplete element type
uvc_stream.c:291: error: ‘no_argument’ undeclared (first use in this function)
uvc_stream.c:293: error: ‘required_argument’ undeclared (first use in this function)
uvc_stream.c:311: warning: implicit declaration of function ‘getopt_long_only’
uvc_stream.c:330: warning: implicit declaration of function ‘strdup’
uvc_stream.c:330: warning: incompatible implicit declaration of built-in function ‘strdup’
uvc_stream.c:330: error: ‘optarg’ undeclared (first use in this function)
uvc_stream.c:336: warning: implicit declaration of function ‘strcmp’
uvc_stream.c:341: warning: incompatible implicit declaration of built-in function ‘fprintf’
uvc_stream.c:341: error: ‘stderr’ undeclared (first use in this function)
uvc_stream.c:348: warning: implicit declaration of function ‘atoi’
uvc_stream.c:360: warning: implicit declaration of function ‘printf’
uvc_stream.c:360: warning: incompatible implicit declaration of built-in function ‘printf’
uvc_stream.c:289: warning: unused variable ‘long_options’
uvc_stream.c:388: warning: implicit declaration of function ‘signal’
uvc_stream.c:388: error: ‘SIGPIPE’ undeclared (first use in this function)
uvc_stream.c:388: error: ‘SIG_IGN’ undeclared (first use in this function)
uvc_stream.c:389: error: ‘SIGINT’ undeclared (first use in this function)
uvc_stream.c:389: error: ‘SIG_ERR’ undeclared (first use in this function)
uvc_stream.c:390: warning: incompatible implicit declaration of built-in function ‘fprintf’
uvc_stream.c:391: warning: incompatible implicit declaration of built-in function ‘exit’
uvc_stream.c:400: warning: incompatible implicit declaration of built-in function ‘calloc’
uvc_stream.c:402: warning: incompatible implicit declaration of built-in function ‘fprintf’
uvc_stream.c:405: warning: implicit declaration of function ‘ntohs’
uvc_stream.c:413: error: ‘V4L2_PIX_FMT_MJPEG’ undeclared (first use in this function)
uvc_stream.c:416: warning: incompatible implicit declaration of built-in function ‘exit’
uvc_stream.c:420: warning: implicit declaration of function ‘socket’
uvc_stream.c:420: error: ‘PF_INET’ undeclared (first use in this function)
uvc_stream.c:420: error: ‘SOCK_STREAM’ undeclared (first use in this function)
uvc_stream.c:423: warning: incompatible implicit declaration of built-in function ‘exit’
uvc_stream.c:427: warning: implicit declaration of function ‘setsockopt’
uvc_stream.c:427: error: ‘SOL_SOCKET’ undeclared (first use in this function)
uvc_stream.c:427: error: ‘SO_REUSEADDR’ undeclared (first use in this function)
uvc_stream.c:429: warning: incompatible implicit declaration of built-in function ‘exit’
uvc_stream.c:433: warning: implicit declaration of function ‘memset’
uvc_stream.c:433: warning: incompatible implicit declaration of built-in function ‘memset’
uvc_stream.c:434: error: ‘AF_INET’ undeclared (first use in this function)
uvc_stream.c:436: warning: implicit declaration of function ‘htonl’
uvc_stream.c:436: error: ‘INADDR_ANY’ undeclared (first use in this function)
uvc_stream.c:437: warning: implicit declaration of function ‘bind’
uvc_stream.c:440: warning: incompatible implicit declaration of built-in function ‘exit’
uvc_stream.c:444: warning: implicit declaration of function ‘listen’
uvc_stream.c:446: warning: incompatible implicit declaration of built-in function ‘exit’
uvc_stream.c:450: error: ‘size_t’ undeclared (first use in this function)
uvc_stream.c:450: error: expected ‘)’ before ‘cd’
uvc_stream.c:451: error: expected ‘)’ before ‘cd’
uvc_stream.c:452: warning: implicit declaration of function ‘pthread_create’
uvc_stream.c:452: error: ‘cam’ undeclared (first use in this function)
uvc_stream.c:453: warning: implicit declaration of function ‘pthread_detach’
uvc_stream.c:457: error: ‘cntrl’ undeclared (first use in this function)
uvc_stream.c:464: warning: implicit declaration of function ‘accept’
uvc_stream.c:465: error: ‘client’ undeclared (first use in this function)
uvc_stream.c:274: warning: unused variable ‘addr’
make: *** [uvc_stream.o] Error 1


It looks like I am missing a compiler or something. I checked to make sure gcc was installed and it is. I'm not sure what I might be missing. I'm pretty new to all of this so sorry if I sound ridiculous. Thanks

---

### Post by transmutated on 2008-04-28
Silly me, I didn't have build-essential installed. I used apt-get and picked it up. I was able to build it. Sorry for mucking up the threads.

---

