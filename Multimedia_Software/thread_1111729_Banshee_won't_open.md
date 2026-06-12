---
title: "Banshee won't open"
date: 2009-03-30
forum: Multimedia Software
---

### Post by deeejz on 2009-03-30
Ok so banshee has been running fine since I installed it but all the sudden, I closed it and tried to run it again..and it said "Starting Banshee Media Player" at the bottom, then it just goes away. When i try running it in terminal i get this:


** (/usr/lib/banshee-1/Nereid.exe:12313): CRITICAL **: _wapi_shm_file_open: shared file [/home/dj/.wapi/shared_data-ubuntu-Linux-x86_64-328-11-0] write error: No space left on device

** (/usr/lib/banshee-1/Nereid.exe:12313): CRITICAL **: _wapi_shm_attach: shared file [/home/dj/.wapi/shared_data-ubuntu-Linux-x86_64-328-11-0] open error
**
ERROR:shared.c:346:shm_semaphores_init: assertion failed: (tmp_shared != NULL)

** (/usr/lib/banshee-1/Nereid.exe:12313): WARNING **: Thread (nil) may have been prematurely finalized
Stacktrace:


** (/usr/lib/banshee-1/Nereid.exe:12313): WARNING **: Thread (nil) may have been prematurely finalized

Native stacktrace:

	banshee-1 [0x529d21]
	/lib/libpthread.so.0 [0x7ff64933d0f0]
	/lib/libc.so.6(gsignal+0x35) [0x7ff648d6a015]
	/lib/libc.so.6(abort+0x183) [0x7ff648d6bb83]
	/usr/lib/libglib-2.0.so.0(g_assertion_message+0x113) [0x7ff6497add63]
	/usr/lib/libglib-2.0.so.0 [0x7ff6497ae202]
	banshee-1 [0x4d65d7]
	banshee-1 [0x4c94cc]
	banshee-1(mono_once+0x63) [0x4d18e3]
	banshee-1 [0x4c9240]
	banshee-1 [0x4d5406]
	banshee-1 [0x490987]
	banshee-1(mono_runtime_init+0x25) [0x497445]
	banshee-1 [0x4f4049]
	banshee-1(mono_main+0x2eb) [0x416d5b]
	/lib/libc.so.6(__libc_start_main+0xe6) [0x7ff648d55466]
	banshee-1 [0x4164c9]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7ff64a023710 (LWP 12313)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0x00007ff648e16463 in select () from /lib/libc.so.6
  1 Thread 0x7ff64a023710 (LWP 12313)  0x00007ff648e16463 in select ()
   from /lib/libc.so.6

Thread 1 (Thread 0x7ff64a023710 (LWP 12313)):
#0  0x00007ff648e16463 in select () from /lib/libc.so.6
#1  0x00007ff6497bf5cc in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#2  0x00007ff6497bf9a8 in g_spawn_command_line_sync ()
   from /usr/lib/libglib-2.0.so.0
#3  0x0000000000529dc8 in ?? ()
#4  <signal handler called>
#5  0x00007ff648d6a015 in raise () from /lib/libc.so.6
#6  0x00007ff648d6bb83 in abort () from /lib/libc.so.6
#7  0x00007ff6497add63 in g_assertion_message () from /usr/lib/libglib-2.0.so.0
#8  0x00007ff6497ae202 in g_assertion_message_expr ()
   from /usr/lib/libglib-2.0.so.0
#9  0x00000000004d65d7 in ?? ()
#10 0x00000000004c94cc in ?? ()
#11 0x00000000004d18e3 in mono_once ()
#12 0x00000000004c9240 in ?? ()
#13 0x00000000004d5406 in ?? ()
#14 0x0000000000490987 in ?? ()
#15 0x0000000000497445 in mono_runtime_init ()
#16 0x00000000004f4049 in ?? ()
#17 0x0000000000416d5b in mono_main ()
#18 0x00007ff648d55466 in __libc_start_main () from /lib/libc.so.6
#19 0x00000000004164c9 in ?? ()
#20 0x00007fff5203d498 in ?? ()
#21 0x000000000000001c in ?? ()
#22 0x0000000000000002 in ?? ()
#23 0x00007fff5203f6e7 in ?? ()
#24 0x00007fff5203f6f1 in ?? ()
#25 0x0000000000000000 in ?? ()
#0  0x00007ff648e16463 in select () from /lib/libc.so.6


=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted



Im not to good at code but that doesn't sound good. Im running ubuntu 8.10 on a Compaq Presario C700 Notebook. If there is any more information you need please let me know.

Thanks.

---

### Post by deeejz on 2009-03-31
Update:

I restarted and opened banshee, it opened fine but after about 5 minutes I got an error that said something about fatal error, then it crashed. I tried to open it again and it flashed for a few seconds, said fatal error and crashed, and now it wont open at all. 

Also I'm using Opera web browser (was having issues with FF) and all of my websites have no themes.. if that makes sense. They are all like..source version i guess. Im installing updates right now and hopefully that fixes something...

Pidgen doesn't open either, it does the same thing as Banshee though.

Okay I restarted after updates and still everything is the same. And now every time I close out of opera, when I open it again it acts like it's the first time running it, same with firefox. All my passwords and usernames are gone. It seems Ubuntu is falling apart:(.

---

### Post by directhex on 2009-03-31
ARE you out of space on your disk?

if not, do an "rm -r /home/dj/.wapi/"

---

### Post by deeejz on 2009-03-31
> **directhex said:**
> ARE you out of space on your disk?

if not, do an "rm -r /home/dj/.wapi/"

I don't think I am. I ran rm -r /home/dj/.wapi/ and everything was still the same.

---

### Post by directhex on 2009-03-31
and "df -h" reports...?

---

### Post by deeejz on 2009-03-31
> **directhex said:**
> and "df -h" reports...?

Im not home at the moment but ill try it when i get home, thanks for the help.

---

### Post by deeejz on 2009-03-31
> **directhex said:**
> and "df -h" reports...?

dj@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G   13G     0 100% /
tmpfs                 496M     0  496M   0% /lib/init/rw
varrun                496M  212K  496M   1% /var/run
varlock               496M     0  496M   0% /var/lock
udev                  496M  2.8M  493M   1% /dev
tmpfs                 496M  104K  496M   1% /dev/shm
/dev/sda1             101G   78G   23G  78% /host
lrm                   496M  2.4M  494M   1% /lib/modules/2.6.27-11-generic/volatile
overflow              1.0M   32K  992K   4% /tmp






Thats what i got.

---

### Post by directhex on 2009-03-31
> **deeejz said:**
> dj@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G   13G     0 100% /
tmpfs                 496M     0  496M   0% /lib/init/rw
varrun                496M  212K  496M   1% /var/run
varlock               496M     0  496M   0% /var/lock
udev                  496M  2.8M  493M   1% /dev
tmpfs                 496M  104K  496M   1% /dev/shm
/dev/sda1             101G   78G   23G  78% /host
lrm                   496M  2.4M  494M   1% /lib/modules/2.6.27-11-generic/volatile
overflow              1.0M   32K  992K   4% /tmp






Thats what i got.

So when I said "ARE you out of space on your disk?" and you said "I don't think I am"?

---

### Post by deeejz on 2009-03-31
> **directhex said:**
> So when I said "ARE you out of space on your disk?" and you said "I don't think I am"?

Hence, why I said think.

Would installing a partitioner help to give ubuntu more room?

---

### Post by directhex on 2009-03-31
> **deeejz said:**
> Hence, why I said think.

Would installing a partitioner help to give ubuntu more room?

You can't edit a partition you're booted from - boot an ubuntu desktop install cd, and it has the partition editor in the system/administration menu

---

