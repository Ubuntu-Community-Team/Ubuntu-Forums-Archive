---
title: "Shared memory error in zoneminder"
date: 2011-06-04
forum: Multimedia Software
---

### Post by deadtom on 2011-06-04
New to zone minder. I have it installed on Kubuntu 10.04.2 LTS, kernel 2.6.32-32.

I'm getting the black screen and these errors in my logs:

```
zma_m2[22871]: ERR [Shared data not initialised by capture daemon]
zmdc[22798]: ERR ['zma -m 2' exited abnormally, exit status 255]
zmc_m2[22872]: INF [Starting Capture]
zmc_m2[22872]: ERR [Invalid response status 401: Unauthorized]
zmc_m2[22872]: ERR [Unable to get response]
zmc_m2[22872]: ERR [Failed to capture image from monitor 2 (0/1)]
zmdc[22798]: ERR ['zmc -m 2' exited abnormally, exit status 255]
zmwatch[22830]: ERR [Can't get shared memory id '7a6d0002', 2: No such file or directory]
zmwatch[22830]: last message repeated 5 times
zmwatch[22830]: ERR [Can't get shared memory id '7a6d0002', 2: No such file or directory]
zmwatch[22830]: ERR [Can't get shared memory id '7a6d0002', 2: No such file or directory]
zmdc[22798]: INF [Starting pending process, zma -m 2]
zmdc[22798]: INF ['zma -m 2' starting at 11/06/04 13:32:28, pid = 22909]
zmdc[22798]: INF [Starting pending process, zmc -m 2]
zmdc[22798]: INF ['zmc -m 2' starting at 11/06/04 13:32:28, pid = 22910]
zmdc[22910]: INF ['zmc -m 2' started at 11/06/04 13:32:28]
zmdc[22909]: INF ['zma -m 2' started at 11/06/04 13:32:28]
zmc_m2[22910]: INF [Debug Level = 0, Debug Log = <none>]
zma_m2[22909]: INF [Debug Level = 0, Debug Log = <none>]
zma_m2[22909]: ERR [Shared data not initialised by capture daemon]
zmdc[22798]: ERR ['zma -m 2' exited abnormally, exit status 255]
zmc_m2[22910]: INF [Starting Capture]
zmc_m2[22910]: ERR [Invalid response status 401: Unauthorized]
zmc_m2[22910]: ERR [Unable to get response]
zmc_m2[22910]: ERR [Failed to capture image from monitor 2 (0/1)]
zmdc[22798]: ERR ['zmc -m 2' exited abnormally, exit status 255]
zmwatch[22830]: ERR [Can't get shared memory id '7a6d0002', 2: No such file or directory]
zmwatch[22830]: ERR [Can't get shared memory id '7a6d0002', 2: No such file or directory]
```I've found a lot of posts here and on other forums about setting the shared memory, I've done that with a variety of different memory settings.

/etc/sysctl.conf currently reads:

```
kernel.shmall = 167772160
kernel.shmmax = 335544320
```output of ipcs -l:

```
------ Shared Memory Limits --------
max number of segments = 4096
max seg size (kbytes) = 327680
max total shared memory (kbytes) = 671088640
min seg size (bytes) = 1

------ Semaphore Limits --------
max number of arrays = 128
max semaphores per array = 250
max semaphores system wide = 32000
max ops per semop call = 32
semaphore max value = 32767

------ Messages: Limits --------
max queues system wide = 1705
max size of message (bytes) = 8192
default max size of queue (bytes) = 16384

```
Another forum suggested adding these lines to /usr/bin/zmdc.pl:

$ENV{LD_PRELOAD} = '/usr/lib/libv4l/v4l1compat.so';
$ENV{LD_PRELOAD} = '/usr/lib/libv4l/v4l2convert.so';

Still no good.

I've added the www-data user to the video group as suggested on one forum but no luck.

I've been over the zoneminder wiki and nothing has been helpful.

I'm completely stuck now. Any help is greatly appreciated.

---

### Post by deadtom on 2011-06-04
The problem was this right here:

```
zmc_m2[22872]: ERR [Invalid response status 401: Unauthorized]

```

I had a mistake in the credentials line in the source.

---

### Post by Todamont on 2011-07-25
so how did you fix it?

---

### Post by bbiandov on 2011-12-28
> **Todamont said:**
> so how did you fix it?

I can confirm that the way I fixed this was as follows:


```
 sudo echo 167772160 > /proc/sys/kernel/shmall
```

Then to make the change permanent I did the reqisite:

[http://www.zoneminder.com/wiki/index.php/Debian_Squeeze]("http://www.zoneminder.com/wiki/index.php/Debian_Squeeze")

My errors were as follows prior to making that change:


```
12/27/11 21:56:23.038492 zmwatch[11908].ERR [Can't get shared memory id '7a6d0002', 2: No such file or directory]
12/27/11 21:56:23.039668 zmwatch[11908].ERR [Can't get shared memory id '7a6d0003', 3: No such file or directory]
12/27/11 21:56:43.042803 zmwatch[11908].ERR [Can't get shared memory id '7a6d0002', 2: No such file or directory]
12/27/11 21:56:53.044723 zmwatch[11908].ERR [Can't get shared memory id '7a6d0002', 2: No such file or directory]
12/27/11 21:57:03.046334 zmwatch[11908].ERR [Can't get shared memory id '7a6d0002', 2: No such file or directory]
12/27/11 21:57:13.047480 zmwatch[11908].ERR [Can't get shared memory id '7a6d0002', 2: No such file or directory]
12/27/11 21:57:23.048562 zmwatch[11908].ERR [Can't get shared memory id '7a6d0002', 2: No such file or directory]
12/27/11 21:57:33.049663 zmwatch[11908].ERR [Can't get shared memory id '7a6d0002', 2: No such file or directory]

```

After the change my devices showed up in GREEN and finally the black screen in Monitor started displaying the correct streams in stead of that black fake background.

One indication that it worked right away was that Monitor streams started displaying the date/time stamp.

Prior to that the face black screen DID NOT display the date/time stamp in the upper left-hand corner.

---

