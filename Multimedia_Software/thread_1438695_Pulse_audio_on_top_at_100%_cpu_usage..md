---
title: "Pulse audio on top at 100% cpu usage."
date: 2010-03-25
forum: Multimedia Software
---

### Post by Laxman_prodigy on 2010-03-25
I have Intel core 2 duo machine running Ubuntu Karmic 64-bit.

Whenever I play a mp3 on rythmbox and use the "top" command, the pulse audio is at top at 100%. WTF?

Is it trying to break my system just by running a mp3?


Is my system not able to detect two cores? or Whatever?

Please help me. It's just unbearable.

Here is the output of top command:
```
laxman@Cray-Jaguar:~$ top

top - 20:36:50 up  2:00,  2 users,  load average: 0.71, 0.45, 0.45
Tasks: 162 total,   2 running, 160 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.0%us, 48.4%sy,  0.0%ni, 48.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2055676k total,  1778616k used,   277060k free,   100396k buffers
Swap:  4883720k total,        0k used,  4883720k free,  1232852k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2081 laxman    20   0  322m 9360 7136 S  100  0.5  37:51.67 pulseaudio         
 3505 laxman    20   0  814m  54m  25m S    2  2.7   0:03.70 rhythmbox          
   78 root      15  -5     0    0    0 R    0  0.0   0:00.38 kondemand/1        
 1306 root      20   0 22180 1244 1040 S    0  0.1   0:01.17 hald-addon-stor    
    1 root      20   0 19452 1808 1204 S    0  0.1   0:00.54 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:04.07 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:17.53 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.01 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.07 events/1    
```


**Also, if it helps; the output of the following command:**
```
laxman@Cray-Jaguar:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz
stepping    : 6
cpu MHz        : 1596.000
cache size    : 3072 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm
bogomips    : 5067.08
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz
stepping    : 6
cpu MHz        : 2527.000
cache size    : 3072 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm
bogomips    : 5066.86
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

---

### Post by Laxman_prodigy on 2010-03-25
Anybody has the same issue? Please suggest me. There is no such thing in Windows.

Why the hell does something related to sound use 100% cpu. I am very frustrated.

Please help me.

---

### Post by Laxman_prodigy on 2010-03-25
Members please help me.:(

---

### Post by Laxman_prodigy on 2010-03-25
Is it only me who is facing this problem? I think it's can't be.

Please do reply.

Members please do reply. I know I am crying.

---

### Post by Laxman_prodigy on 2010-03-25
Let me repeat the question:

"Pulse audio is on top at 100% on running the top command and this happens when I do anything related to sound i.e. playing music, videos, etc.

I am using Karmic Koala 64-bit. What is the problem exactly?

Please suggest me any workarounds.

---

### Post by RedSingularity on 2010-03-25
Well you can remove pulseaudio.

---

### Post by gordintoronto on 2010-03-25
If you run Administration/System Monitor one of the tabs should show the usage of both CPUs.  I've never run anything which pegged either CPU on my AMD Phenom II X2.  Does it happen with every MP3?

---

### Post by Laxman_prodigy on 2010-03-26
> **gordintoronto said:**
> If you run Administration/System Monitor one of the tabs should show the usage of both CPUs.  I've never run anything which pegged either CPU on my AMD Phenom II X2.  Does it happen with every MP3?


Yes, it happens everytime something related to sound is invoked.

---

### Post by Laxman_prodigy on 2010-03-26
> **RedSingularity said:**
> Well you can remove pulseaudio.


What should I do for it then?

---

### Post by RedSingularity on 2010-03-26
Remove it like this in a terminal

sudo apt-get purge pulseaudio

After that see if you still have sound.

---

### Post by Laxman_prodigy on 2010-03-27
> **RedSingularity said:**
> Remove it like this in a terminal

sudo apt-get purge pulseaudio

After that see if you still have sound.


But "pulseaudio" is something by default in Ubuntu 9.10 as I understand.

What would I do after uninstalling it?

---

### Post by RedSingularity on 2010-03-27
After uninstalling it your applications will use ALSA directly without filtering through the pulse sound server.  When you uninstall it try some sound apps to make sure they work.

---

### Post by Laxman_prodigy on 2010-03-28
> **RedSingularity said:**
> After uninstalling it your applications will use ALSA directly without filtering through the pulse sound server.  When you uninstall it try some sound apps to make sure they work.


Hi.

I got it but I don't understand why does this happen. Please help me . Here is the exact case:

"I have Creative sound card. Now whenever, I play something through it, the pulse audio pumps up and shows "100%" cpu usage. Now if I change the Hardware through right clicking the volume on the top right and select Internal audio, its all right.

Now the problem is that I have a 4.1 Creative of which one of the front speaker doesn't work. Also, the rear speakers don't work with "Internal audio"(Tell me if I need to change something)."


Now, please suggest me.

---

### Post by RedSingularity on 2010-03-28
I am not sure what would cause the CPU to spike so much with pulseaudio installed.  You said that you had a workaround though.

"Now if I change the Hardware through right clicking the volume on the  top right and select Internal audio, its all right."

If this workaround was acceptable to you then you can always revert back to that setup by reinstalling pulseaudio.

---

### Post by christer.holmer on 2010-04-28
Hi!

Sometimes my pulseaudio spikes like that, but most of the time it's ok. I also have Karmic 64-bit. 

[LIST]
[*]I run Spotify under Wine
[*]I run Windows in VirtualBox
[/LIST]
I use pulseaudio to allow me to get sound both in Spotify and VirtualBox at the same time. 

So, when do I get a problem? I think I have narrowed it down to the following scenario:

[LIST=1]
[*]Thunderbird hangs (probably tries to play sound or something)
[*]I kill thunderbird-bin
[*]pulseaudion goes to 100% on one cpu core
[*]Spotify still plays
[*]I run 'pulseaudio --kill' and cpu gets back to normal
[/LIST]
I guess this doesn't help you, but try 'pulseaudio --kill'

---

### Post by Girindor on 2010-04-28
I struggled for ages, getting Spotify to work on Ubuntu, it breaking, re-installing, etc. -until I discovered We7.com which is basically like Spotify but web-based, works like a charm, and has less annoying ads.

You're welcome :-)

---

### Post by slouse on 2010-05-13
I had the same problem and it seems to have disappeared by getting rid of some custom settings I put in to make it work in Hardy. I just did in the terminal:
mv ~/.pulse/daemon.conf ~/.pulse/daemon_old.conf
After a reboot, pulseaudio reads the standard daemon.conf from /etc/pulse, which I assume is adapted to lucid.
Hope this helps others, too.

---

### Post by fermulator on 2010-10-17
> **slouse said:**
> I had the same problem and it seems to have disappeared by getting rid of some custom settings I put in to make it work in Hardy. I just did in the terminal:
mv ~/.pulse/daemon.conf ~/.pulse/daemon_old.conf
After a reboot, pulseaudio reads the standard daemon.conf from /etc/pulse, which I assume is adapted to lucid.
Hope this helps others, too.

I'm having the EXACT same scenario as christer.holmer is having with thunderbird.

interesting thought slouse.  When I read your post, I immediately thought, oh good point, I did this back in the day too, my settings must also be old from hardy.  Yet, when I checked, I don't have that custom daemon.conf file in my home directory, so I must have not kept it on purpose on my last upgrade.

How else can we diagnose the problem here?  It's so frustrating that thunderbird locks up due to inaccessibility to pulseaudio.  (I'm guessing that my situation is similar to others' in that I'm using Amarok to play audio ... so it must be causing similar behaviour as spotify/wine/windows/virtualbox.

---

### Post by fermulator on 2010-10-17
See [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/410418](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/410418)

---

