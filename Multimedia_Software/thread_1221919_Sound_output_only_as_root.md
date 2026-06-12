---
title: "Sound output only as root"
date: 2009-07-24
forum: Multimedia Software
---

### Post by modemuser on 2009-07-24
Hi,

Recently I tried to upgrade Ubuntu (8.04 to 9.04) and had problems during the upgrade, resulting in a broken grub and the PC wouldn't boot anymore. It's fixed now, upgraded to 9.04.

The one thing that doesn't work though, is sound. I have a M-Audio Audiophile 2496 PCI soundcard, which worked well before the upgrade.

I tried a lot to fix it, but without success, until today. If I'm logged in as root (not just sudo), sound works!

tom@K7:~$ mocp
FATAL_ERROR: Layout3 is malformed
tom@K7:~$ sudo mocp
[sudo] password for tom: 
FATAL_ERROR: Layout3 is malformed
tom@K7:~$ sudo su
root@K7:/home/tom# mocp
Running the server...
Trying JACK...
Trying ALSA...
[And now, miraculously, it's working...]

Does anybody have an idea how to fix this, so that sound works for all users? I hate to surf the web as root ;)

---

### Post by igorzwx on 2009-07-24
**[COLOR=#980101][B][ubuntu]**[/COLOR] alsamixer not opening device  [/B]
[http://ubuntuforums.org/showthread.php?t=1219650](http://ubuntuforums.org/showthread.php?t=1219650)

---

### Post by modemuser on 2009-07-24
Thanks for your reply, that sort of helped.

Now some programs run as normal user have sound, but others don't. I cannot find a pattern there, yet.
I also tried what's described [in this thread]("http://ubuntuforums.org/showthread.php?t=816159"), namely killing, starting and checking pulseaudio, but doing that as the normal user fails. Here is the message:

tom@K7:~$ pulseaudio -k
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.

tom@K7:~$ sudo !!
sudo pulseaudio -k
E: core-util.c: Home directory /home/tom not ours.
E: main.c: Failed to kill daemon: Permission denied

root@K7:/home/tom# pulseaudio -k
E: main.c: Failed to kill daemon: No such process


Then I added my user name to the 'pulse-rt' group as advised, but that didn't help either.

What am I doing wrong?

---

### Post by igorzwx on 2009-07-24
you may ask Martin,
but he is busy, perhaps.

I removed both pulse and alsa,
and installed OSS4.
It works well, but life became boring.
no problems, everything works, nothing to fix.

check if you hardware is supported by OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by martinbaselier on 2009-07-24
could you paste the output of:
**ls /dev/snd -al**
and
**groups `whoami`**

---

### Post by modemuser on 2009-07-24
> OSS4.
It works well, but life became boring.
no problems, everything works, nothing to fix.

My hardware seems supported by OSS4, so if my current attempts  keep failing, I might try that.

Here is the output, I hope that helps:

tom@K7:~$ ls /dev/snd -al
total 0
drwxrwxrwx   2 root root     160 2009-07-12 13:00 .
drwxr-xr-x  15 root root    4440 2009-07-24 03:12 ..
crw-rw-rw-+  1 root audio 116, 7 2009-07-12 13:00 controlC0
crw-rw-rw-+  1 root audio 116, 4 2009-07-12 13:00 midiC0D0
crw-rw-rw-+  1 root audio 116, 6 2009-07-24 19:06 pcmC0D0c
crw-rw-rw-+  1 root audio 116, 5 2009-07-24 19:59 pcmC0D0p
crw-rw-rw-+  1 root audio 116, 3 2009-07-12 13:00 seq
crw-rw-rw-+  1 root audio 116, 2 2009-07-12 13:00 timer
tom@K7:~$ groups `whoami`
tom adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin pulse-rt sambashare

---

### Post by igorzwx on 2009-07-24
in both cases Martin may help better than I.

---

### Post by martinbaselier on 2009-07-24
OSS is definitely an advisor (I found the difference in sound quality amazing)

about your settings: 
You're in the audio group, so that's ok. It's a bit strange all devices are in the audio group, normally they are in the root group. I doubt that will make much difference though. 

I don't know much about pulse, I never saw any use for it. I can tell you how to kill any process though:
**ps -e | grep pulse -i**
This will show you al processes (ps -e) with the name pulse (grep) in it, case insensitive (-i)

Then use **killall** with the process name or **kill** with the pid to kill the process. You might need **sudo** or the option **-KILL** to kill it.

---

### Post by igorzwx on 2009-07-24
If you feel very experimental,
you may try to compile the latest version of OSS4

Install another Ubuntu 9.04 in dual boot.
info is here:
[http://www.4front-tech.com/forum/viewtopic.php?t=3237](http://www.4front-tech.com/forum/viewtopic.php?t=3237)

---

### Post by modemuser on 2009-07-24
In that case, I will look into OSS4, once i find the time.

Thanks a lot for your help!

---

### Post by markbuntu on 2009-07-24
All you need to do is add youself and root to the following groups

pulse
pulse-access
pulse-rt

That is what that message is telling you to do.

---

### Post by igorzwx on 2009-07-24
Mark!

I have a question about security
(root privileges)

[http://www.remote-exploit.org/backtrack.html](http://www.remote-exploit.org/backtrack.html)

---

### Post by markbuntu on 2009-07-24
WHat pulseaudio does is use root priveleges to gain hardware control and then immediately drops the root priveleges before starting the daemon so this is not as bad as it looks.

If Policykit was working properly with pulseaudio all this would not be necessary.

Bug reports on this have been filed since Jaunty alphas but no progress seems to have been made

---

### Post by igorzwx on 2009-07-24
Thanks!

Why not then give Firefox root privileges too?
It is also buggy

---

### Post by markbuntu on 2009-07-24
> **igorzwx said:**
> Thanks!

Why not then give Firefox root privileges too?
It is also buggy

Why does OSS4 allow applications into the kernel space?
OSS4 is a huge security danger which is a big reason why so many distros do not even let it in their repositories.

---

### Post by igorzwx on 2009-07-24
This is really an interesting question.

But this does not mean, however, that security can be ignored.

Do you know how DDOS can be applied to buggy things?
[http://en.wikipedia.org/wiki/Denial-of-service_attack](http://en.wikipedia.org/wiki/Denial-of-service_attack)

---

### Post by martinbaselier on 2009-07-24
What do you mean with OSS allowing applications into the kernel space? Could you give any more information about that? Maybe an article describing how it's done?

---

### Post by igorzwx on 2009-07-25
"OSS allowing applications into the kernel space?"

Why not ask this on OSS4 forum?

Another question: "If Mark's magic solution with root privileges is so good,
why not implement it as default settings of Ubuntu?"
Nobody would have problems with sound then, 
but Ubuntu botnets may become possible.

[http://en.wikipedia.org/wiki/Botnet](http://en.wikipedia.org/wiki/Botnet)

---

### Post by markbuntu on 2009-07-25
It is supposed to be default and pulseaudio privileges were defaulted to what I suggested in previous versions. The bug is that it is not default anymore, a problem with policykit that needs to be remedied. 

Anyway, future versions of pulseaudio will be dropping this requirement.

---

### Post by bootdoc on 2009-07-25
try system>administration>users&groups. Unlock and type password then choose manage groups.  find pulse, pulse access and pulsert click on properties and add yourself and any other users to the group.

---

### Post by igorzwx on 2009-07-25
Genererally speaking, security is a matter of belief.
If you believe, you feel secure.

---

### Post by igorzwx on 2009-07-25
[http://oreilly.com/catalog/9781565921481/](http://oreilly.com/catalog/9781565921481/)

                                                                                                       
      **  Practical UNIX and Internet Security, Second Edition   **

          By [Simson Garfinkel]("http://www.oreillynet.com/pub/au/355"), [Gene Spafford]("http://www.oreillynet.com/pub/au/65")
        April 1996      
                  Pages: 1000 
                             ISBN 10: 1-56592-148-8 |  ISBN 13: 9781565921481


**The latest edition is also available on [Safari Books Online]("http://safari.oreilly.com/0596003234").**
Description  
This second edition of the classic *Practical UNIX Security* is a complete rewrite of the original book. It's packed with twice the pages and offers even more practical information for UNIX users and administrators. It covers features of many types of UNIX systems, including SunOS, Solaris, BSDI, AIX, HP-UX, Digital UNIX, Linux, and others. Contents include UNIX and security basics, system administrator tasks, network security, and appendixes containing checklists and helpful summaries. 
[Full Description]("http://oreilly.com/catalog/9781565921481/#top")

---

### Post by igorzwx on 2009-07-27
Mark!
I do not trust you!
**[Root exploit for *Linux kernel* published - News - The H Security [B]...**]("http://www.h-online.com/security/Root-exploit-for-Linux-kernel-published--/news/113791")[/B]

17 Jul 2009 **...** *Brad Spengler*, the developer behind the Grsecurity project, has published an exploit for a *vulnerability* in the Tun interface in *Linux kernel* 2.6.30 **...** The exploit uses loadable modules from *PulseAudio* which are set as **...**
[www.h-online.com/security/Root](www.h-online.com/security/Root)...**Linux**-**kernel**.../113791 - [Cached]("http://209.85.135.132/search?q=cache:_Xm8cw6--XkJ:www.h-online.com/security/Root-exploit-for-Linux-kernel-published--/news/113791+vulnerability+linux+kernel+PulseAudio+Brad+Spengler&cd=1&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:www.h-online.com/security/Root-exploit-for-Linux-kernel-published--/news/113791")

[http://www.h-online.com/security/Root-exploit-for-Linux-kernel-published--/news/113791](http://www.h-online.com/security/Root-exploit-for-Linux-kernel-published--/news/113791)
17 July 2009, 18:47
     **      Root exploit for Linux kernel published **

     Brad Spengler, the developer behind the [Grsecurity project]("http://www.grsecurity.net/"), has published an exploit for a vulnerability in the Tun interface in Linux kernel 2.6.30 and 2.6.18, used in Red Hat Enterprise Linux 5 (RHEL5), which can be exploited by attackers to obtain root privileges. Of particular interest is the fact that the exploit is even able to circumvent security extensions such as SELinux. According to Spengler's report, the vulnerability is only found in these two versions of the kernel. The core of the problem is a normally non-exploitable null pointer dereference, which becomes exploitable due to the GCC's optimisation function.
  The interplay between the vulnerability and the trick for getting past SELinux is a little fiddly. The Internet Storm Center (ISC) has taken a brief look at the vulnerability and has identified the following code as being responsible for the problem:


 static unsigned int tun_chr_poll(struct file *file, poll_table * wait)

struct sock *sk = tun->sk;  // initialize sk with tun->sk
…
if (!tun)
   return POLLERR; // if tun is NULL return error
According to this, if (!tun) should return an error is it is 0 (null), but the compiler optimises the 'if' block out of existence, because the variable has already been assigned/dereferenced. As a result, the kernel may try to access the address 0x00000000, which an attacker can direct to their own code. Marcus Meissner from SUSE has confirmed to heise Security, The H's associated publication in Germany, that the problem exists in principle.
  Meissner points out, however, that two other conditions must be met for the exploit to work. The code must be able to open the /dev/net/tun device. The exploit uses loadable modules from PulseAudio which are set as SUID in some distributions, to do this. The code must also be able to disable the "mmap_min_addr" exploit protection function, something which Spengler achieves by taking advantage of an error in the implementation of ['personalities']("http://linux.about.com/library/cmd/blcmdl2_personality.htm").
  The solution to the problem is, by unanimous agreement, very simple – to prevent the test from being optimised to oblivion, the value must be tested before the pointer is assigned. The bug is reported to be fixed in kernel version 2.6.30.2.
  Future kernel versions will be compiled using the "fno-delete-null-pointer-checks" option, so that the compiler no longer eliminates checks for null pointers. A debate on lwn.net shows a split in opinion on whether this is GCC optimising code to breaking point, or a programming error.
  *See also:*
 
[LIST]
[*][Linux 2.6.30+/SELinux/RHEL5 test kernel 0day, exploiting the unexploitable]("http://lists.grok.org.uk/pipermail/full-disclosure/2009-July/069714.html"), advisory from Brad Spengler
[*][A new fascinating Linux kernel vulnerability]("http://isc.sans.org/diary.html?storyid=6820&rss"), advisory from ISC.
[*][Linux 2.6.30 exploit posted]("http://lwn.net/Articles/341773/"), advisory from lwn.
[/LIST]

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.[/B]

---

