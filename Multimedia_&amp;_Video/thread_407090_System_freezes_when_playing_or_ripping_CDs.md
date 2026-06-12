---
title: "System freezes when playing or ripping CDs"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by sav2005 on 2007-04-11
Yesterday Sound Juicer stopped working! When I put an Audio CD in my machine and try to play or rip it my entire system freezes and I have to power down.

My kernel is 2.6.17-11-386. The problem started after my last system update. Is this a coincidence? I also tried to manage files on my iPod via Rhythmbox and Rhythmbox crashed.

I have renamed my gnome2/rhythmbox, gconf/soundjuicer and gconf/rhythmbox folders.

---

### Post by teddmeister2 on 2007-04-11
Did your problem begin immediately after the kernel update?  This same sort of thing happened to me when trying to use soundjuicer to play a cd after the the most recent update of the kernel, which I guess I should have waited on...
But, anyway, the first thing you should probably do is to make sure that you're not having the sound issue that a lot of people are having after the kernel update, or at least that this isn't the cause (which I'm not sure how to do).

However, I DO have the same exact problem as you with soundjuicer bricking my system...but my sound has been working fine since the kernel update (at least, I have been able to hear the previews of my .ogg files nicely--moving my mouse over a few having been my quick check of this).
Specifically, what happens is, I put in the cd, sound juicer comes up... I hit play and the cd slows down, and the program becomes unresponsive.  Now, no matter whether I kill soundjuicer or not, the cd rpms then go up again and get the frozen cursor on screen/unresponsive keyboard/have to lean on power button for a few seconds to do anything again...  now I have hardly experienced this sort of thing (this badly/consistently) since leaving the grip of the evil empire in Redmond, I would naturally like to know what could be the cause of this and how I can deal with/fix this problem.

Can anyone help us?  Or suggest ways we can find more information about this so that we can make it so someone can more easily help us/diagnose the issue?

---

### Post by teddmeister2 on 2007-04-11
I was just looking through the forums and it has been confirmed to be desktop environment independent, as the person [here]("http://ubuntuforums.org/showthread.php?t=406802") having a similar sort of problem from the default ripper (I think) in kde confirms it.
So it's almost definitely related to the recent kernel update.
The questions are:
1) Is this problem related to the kernel update audio problems, which I'm not sure of (since my sound is working fine)?
2) Possible workarounds/fixes?

Thanks bunches!  :-D

---

### Post by getglenn on 2007-04-12
i run Edgy and Feisty and BOTH now have this problem...

edgy was working until i updated 20 minutes ago...

feisty has NOT been updated [since install] but it too freezes...

sorry but i dont have a solution, but after checking the ubuntu forums it seems to be a huge problem

---

### Post by getglenn on 2007-04-12
further to this...

System Monitor shows sound juicer as "sleeping" 

if i quit sounde juicer it responds with "... not responding - force quit" dialog box

---

### Post by getglenn on 2007-04-12
i CAN play mp3's with RythmBox, so the sound is o.k.

but System Monitor also shows "esd" as sleeping...

i thought "esd" was the sound daemon in ubuntu, so that doesnt seem to be correct???

---

### Post by michael95060 on 2007-04-12
I am having same symptoms, immediately following kernel update. so far all other sound/video okay.

---

### Post by getglenn on 2007-04-12
got mine working by following the details at [http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

briefly...

check that the following are installed:
gstreamer0.10-pitfdll
gstreamer0.10-ffmpeg
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
  gxine
libxine-main1
libxine-extracodecs
ogle
ogle-gui

and then

- Open Juicer
- Edit ---> Preferences
- Edit Profiles
- New (give the new profile a name, e.g. mp3) ---> Create
- Highlight the new profile and click Edit
- Enter a profile name, and description
- Enter the following below for Gstreamer pipeline...

   audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001 ! xingmux ! id3v2mux
NB: this was different to the actual line that i had previously

- Enter mp3 as File Extension
- Check Active box
- Click OK

Close all boxes and go back to Edit ---> Preferences in Juicer and select your new mp3 format as Output Format. 

for me, this enabled mp3 ripping... i hope you have the same luck!!!

---

### Post by sav2005 on 2007-04-12
Thanks for the feedback. It seems the issue is in one of the recent upgrades. 

I've just spent the morning reinstalling Dapper - sound juicer works - then upgraded to Edgy with all the gstreamers(0.10_*, bad and ugly plugins). Sound Juicer is dead again! OGG and MP3 preview works in Nautilus, Rhythmbox plays MP3, OGG but NOT CDs (Audio CDs are freezing the system). Data CDs are opening fine.

I'm not sure if it's the kernel because I have tried booting with earlier kernels and the problem won't go away. I'm wondering if it is the new cdparanoia that got updated on my machine yesterday?

---

### Post by sav2005 on 2007-04-12
To GetGlenn: That was how Sound juicer was set up and working before the update!

---

### Post by getglenn on 2007-04-12
it is annoying isnt it?

it seems as if there a couple of possibilities, but im not an expert, and you may have other/more thoughts...

1. it is a "dependency" thing i.e. you update one package and it changes something else as well
2. actually i cant think of another, says me scratching me head

---

### Post by sav2005 on 2007-04-12
> **getglenn said:**
> it is annoying isnt it?

it seems as if there a couple of possibilities, but im not an expert, and you may have other/more thoughts...

1. it is a "dependency" thing i.e. you update one package and it changes something else as well
2. actually i cant think of another, says me scratching me head
Don't do an upgrade!

---

### Post by charles.figura on 2007-04-12
I'm running kubuntu edgy on a dell D620, and I've seen the exact same behavior y'all have already noted - when I try to rip a cd with kaudiocreator, the program stops responding, and in about a minute the system bricks - no response at all.

What's interesting is that if kaudiocreator is running w/ no cd in the drive, nothing happens.  But when I put a cd in the drive, kaudiocreator seizes up in about the time it takes to do CDDB lookup.  I haven't even *gotten* to ripping it yet.

Just offering more information.  Has anyone posted a bug report on launchpad?

---

### Post by teddmeister2 on 2007-04-12
For those of you who are experts out there, here's the last chunk of the output I got from running strace with soundjuicer before the program hung.  I'm not sure, but I think the interesting stuff is at the bottom.

```
mmap2(0x47727000, 372356, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 20, 0) = 0xb5e12000
mmap2(0xb5e57000, 81920, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 20, 0x45) = 0xb5e57000
mmap2(0xb5e6b000, 7812, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb5e6b000
close(20)                               = 0
munmap(0xb5e6d000, 65584)               = 0
rt_sigaction(SIGSEGV, {0x48932690, [], 0}, NULL, 8) = 0
time(NULL)                              = 1176406467
rt_sigaction(SIGILL, {0xb5e23719, [], 0}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGILL, {SIG_DFL}, NULL, 8) = 0
rt_sigaction(SIGILL, {0xb5e23719, [], 0}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGILL, {SIG_DFL}, NULL, 8) = 0
rt_sigaction(SIGSEGV, {SIG_DFL}, NULL, 8) = 0
stat64("/usr/lib/gstreamer-0.10/libgstvolume.so", {st_mode=S_IFREG|0644, st_size=12608, ...}) = 0
stat64("/usr/lib/gstreamer-0.10/libgstvolume.so", {st_mode=S_IFREG|0644, st_size=12608, ...}) = 0
open("/usr/lib/gstreamer-0.10/libgstvolume.so", O_RDONLY) = 20
read(20, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320\22"..., 512) = 512
fstat64(20, {st_mode=S_IFREG|0644, st_size=12608, ...}) = 0
mmap2(NULL, 15504, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 20, 0) = 0xb5f4b000
mmap2(0xb5f4e000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 20, 0x2) = 0xb5f4e000
close(20)                               = 0
open("/etc/ld.so.cache", O_RDONLY)      = 20
fstat64(20, {st_mode=S_IFREG|0644, st_size=65584, ...}) = 0
mmap2(NULL, 65584, PROT_READ, MAP_PRIVATE, 20, 0) = 0xb5e6d000
close(20)                               = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgstcontroller-0.10.so.0", O_RDONLY) = 20
read(20, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0\37\0"..., 512) = 512
fstat64(20, {st_mode=S_IFREG|0644, st_size=29208, ...}) = 0
mmap2(NULL, 32096, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 20, 0) = 0xb5e0a000
mmap2(0xb5e11000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 20, 0x6) = 0xb5e11000
close(20)                               = 0
munmap(0xb5e6d000, 65584)               = 0
rt_sigaction(SIGSEGV, {0x48932690, [], 0}, NULL, 8) = 0
rt_sigaction(SIGSEGV, {SIG_DFL}, NULL, 8) = 0
stat64("/usr/lib/gstreamer-0.10/libgstgconfelements.so", {st_mode=S_IFREG|0644, st_size=24448, ...}) = 0
stat64("/usr/lib/gstreamer-0.10/libgstgconfelements.so", {st_mode=S_IFREG|0644, st_size=24448, ...}) = 0
open("/usr/lib/gstreamer-0.10/libgstgconfelements.so", O_RDONLY) = 20
read(20, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\27\0\000"..., 512) = 512
fstat64(20, {st_mode=S_IFREG|0644, st_size=24448, ...}) = 0
mmap2(NULL, 27368, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 20, 0) = 0xb5e77000
mmap2(0xb5e7d000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 20, 0x5) = 0xb5e7d000
close(20)                               = 0
rt_sigaction(SIGSEGV, {0x48932690, [], 0}, NULL, 8) = 0
rt_sigaction(SIGSEGV, {SIG_DFL}, NULL, 8) = 0
writev(11, [{"GIOP\1\2\1\0`\0\0\0", 12}, {"@\200\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354\240"..., 96}], 2) = 108
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1$\0\0\0", 12)     = 12
read(11, "@\200\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1"..., 36) = 36
writev(11, [{"GIOP\1\2\1\0`\0\0\0", 12}, {"@\200\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354\240"..., 96}], 2) = 108
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1$\0\0\0", 12)     = 12
read(11, "@\200\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1"..., 36) = 36
writev(11, [{"GIOP\1\2\1\0`\0\0\0", 12}, {"@\200\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354\240"..., 96}], 2) = 108
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1$\0\0\0", 12)     = 12
read(11, "@\200\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1"..., 36) = 36
writev(11, [{"GIOP\1\2\1\0`\0\0\0", 12}, {"@\200\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354\240"..., 96}], 2) = 108
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1$\0\0\0", 12)     = 12
read(11, "@\200\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1"..., 36) = 36
writev(11, [{"GIOP\1\2\1\0`\0\0\0", 12}, {"@\200\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354\240"..., 96}], 2) = 108
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1$\0\0\0", 12)     = 12
read(11, "@\200\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1"..., 36) = 36
writev(11, [{"GIOP\1\2\1\0\325\1\0\0", 12}, {"\200\200\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354"..., 44}, {"\35\0\0\0add_listener_with_properties"..., 36}, {"\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1\0\1\5\t\1\1\0\0\0\0"..., 389}], 4) = 481
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1(\0\0\0", 12)     = 12
read(11, "\200\200\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1"..., 40) = 40
writev(11, [{"GIOP\1\2\1\0o\0\0\0", 12}, {"p\200\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354\240"..., 111}], 2) = 123
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1>\0\0\0", 12)     = 12
read(11, "p\200\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1"..., 62) = 62
writev(11, [{"GIOP\1\2\1\0\230\0\0\0", 12}, {"\340\177\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354"..., 44}, {"\35\0\0\0all_entries_with_schema_name"..., 36}, {"\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1\0\1\5\t\1\1\0\0\0\0"..., 72}], 4) = 164
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\0018\0\0\0", 12)   = 12
read(11, "\340\177\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1"..., 56) = 56
writev(11, [{"GIOP\1\2\1\0\240\0\0\0", 12}, {"\340\177\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354"..., 44}, {"\35\0\0\0all_entries_with_schema_name"..., 36}, {"\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1\0\1\5\t\1\1\0\0\0\0"..., 80}], 4) = 172
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\0018\0\0\0", 12)   = 12
read(11, "\340\177\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1"..., 56) = 56
writev(11, [{"GIOP\1\2\1\0u\0\0\0", 12}, {"p\200\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354\240"..., 117}], 2) = 129
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1A\0\0\0", 12)     = 12
read(11, "p\200\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1"..., 65) = 65
writev(11, [{"GIOP\1\2\1\0\250\0\0\0", 12}, {"\260\177\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354"..., 44}, {"\35\0\0\0all_entries_with_schema_name"..., 36}, {"\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1\0\1\5\t\1\1\0\0\0\0"..., 88}], 4) = 180
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\0018\0\0\0", 12)   = 12
read(11, "\260\177\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1"..., 56) = 56
writev(11, [{"GIOP\1\2\1\0~\0\0\0", 12}, {"@\200\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354\240"..., 126}], 2) = 138
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1f\0\0\0", 12)     = 12
read(11, "@\200\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1"..., 102) = 102
writev(11, [{"GIOP\1\2\1\0\264\0\0\0", 12}, {"\200\177\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354"..., 44}, {"\35\0\0\0all_entries_with_schema_name"..., 36}, {"\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1\0\1\5\t\1\1\0\0\0\0"..., 100}], 4) = 192
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1\311\2\0\0", 12)  = 12
read(11, "\200\177\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1"..., 713) = 713
writev(11, [{"GIOP\1\2\1\0\214\0\0\0", 12}, {"\20\200\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354\240"..., 140}], 2) = 152
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1(\0\0\0", 12)     = 12
read(11, "\20\200\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1"..., 40) = 40
writev(11, [{"GIOP\1\2\1\0\264\0\0\0", 12}, {"\200\177\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354"..., 44}, {"\35\0\0\0all_entries_with_schema_name"..., 36}, {"\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1\0\1\5\t\1\1\0\0\0\0"..., 100}], 4) = 192
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1\375\2\0\0", 12)  = 12
read(11, "\200\177\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1"..., 765) = 765
writev(11, [{"GIOP\1\2\1\0\211\0\0\0", 12}, {"\20\200\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354\240"..., 137}], 2) = 149
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1(\0\0\0", 12)     = 12
read(11, "\20\200\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1"..., 40) = 40
writev(11, [{"GIOP\1\2\1\0\260\0\0\0", 12}, {"\200\177\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354"..., 44}, {"\35\0\0\0all_entries_with_schema_name"..., 36}, {"\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1\0\1\5\t\1\1\0\0\0\0"..., 96}], 4) = 188
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1\355\2\0\0", 12)  = 12
read(11, "\200\177\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1"..., 749) = 749
writev(11, [{"GIOP\1\2\1\0\206\0\0\0", 12}, {"\20\200\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354\240"..., 134}], 2) = 146
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1(\0\0\0", 12)     = 12
read(11, "\20\200\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1"..., 40) = 40
writev(11, [{"GIOP\1\2\1\0\264\0\0\0", 12}, {"\200\177\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354"..., 44}, {"\35\0\0\0all_entries_with_schema_name"..., 36}, {"\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1\0\1\5\t\1\1\0\0\0\0"..., 100}], 4) = 192
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1\261\2\0\0", 12)  = 12
read(11, "\200\177\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1"..., 689) = 689
writev(11, [{"GIOP\1\2\1\0\211\0\0\0", 12}, {"\20\200\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354\240"..., 137}], 2) = 149
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1(\0\0\0", 12)     = 12
read(11, "\20\200\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1"..., 40) = 40
writev(11, [{"GIOP\1\2\1\0\244\0\0\0", 12}, {"\260\177\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354"..., 44}, {"\35\0\0\0all_entries_with_schema_name"..., 36}, {"\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1\0\1\5\t\1\1\0\0\0\0"..., 84}], 4) = 176
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1\355\0\0\0", 12)  = 12
read(11, "\260\177\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1"..., 237) = 237
writev(11, [{"GIOP\1\2\1\0|\0\0\0", 12}, {"@\200\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354\240"..., 124}], 2) = 136
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1(\0\0\0", 12)     = 12
read(11, "@\200\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1"..., 40) = 40
writev(11, [{"GIOP\1\2\1\0\240\0\0\0", 12}, {"\340\177\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354"..., 44}, {"\35\0\0\0all_entries_with_schema_name"..., 36}, {"\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1\0\1\5\t\1\1\0\0\0\0"..., 80}], 4) = 172
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\0017\5\0\0", 12)   = 12
read(11, "\340\177\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1"..., 1335) = 1335
writev(11, [{"GIOP\1\2\1\0w\0\0\0", 12}, {"p\200\363\277\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0K\354\240"..., 119}], 2) = 131
poll([{fd=6, events=POLLIN}, {fd=11, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}], 4, -1) = 1
read(11, "GIOP\1\2\1\1(\0\0\0", 12)     = 12
read(11, "p\200\363\277\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1"..., 40) = 40
stat64("/usr/lib/gstreamer-0.10/libgstalsa.so", {st_mode=S_IFREG|0644, st_size=76864, ...}) = 0
stat64("/usr/lib/gstreamer-0.10/libgstalsa.so", {st_mode=S_IFREG|0644, st_size=76864, ...}) = 0
open("/usr/lib/gstreamer-0.10/libgstalsa.so", O_RDONLY) = 20
read(20, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0<\0\000"..., 512) = 512
fstat64(20, {st_mode=S_IFREG|0644, st_size=76864, ...}) = 0
mmap2(NULL, 75740, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 20, 0) = 0xb5df7000
mmap2(0xb5e09000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 20, 0x12) = 0xb5e09000
close(20)                               = 0
rt_sigaction(SIGSEGV, {0x48932690, [], 0}, NULL, 8) = 0
rt_sigaction(SIGSEGV, {SIG_DFL}, NULL, 8) = 0
clone(child_stack=0xb47d04e4, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID|CLONE_DETACHED, parent_tidptr=0xb47d0be8, {entry_number:6, base_addr:0xb47d0ba0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}, child_tidptr=0xb47d0be8) = 5247
futex(0x8112a84, FUTEX_WAIT, 1, NULL)   = 0
futex(0x8112a60, FUTEX_WAIT, 2, NULL)   = 0
futex(0x8112a60, FUTEX_WAKE, 1)         = 0
gettimeofday({1176406468, 34251}, NULL) = 0
stat64("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=7640, ...}) = 0
open("/usr/share/alsa/alsa.conf", O_RDONLY) = 20
fstat64(20, {st_mode=S_IFREG|0644, st_size=7640, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7e36000
read(20, "#\n#  ALSA library configuration "..., 4096) = 4096
read(20, "surround50 cards.pcm.surround50\n"..., 4096) = 3544
read(20, "", 4096)                      = 0
read(20, "", 4096)                      = 0
close(20)                               = 0
munmap(0xb7e36000, 4096)                = 0
access("/etc/asound.conf", R_OK)        = -1 ENOENT (No such file or directory)
access("/home/bapps/.asoundrc", R_OK)   = -1 ENOENT (No such file or directory)
open("/usr/share/alsa/cards/aliases.conf", O_RDONLY) = 20
fstat64(20, {st_mode=S_IFREG|0644, st_size=1277, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7e36000
read(20, "#\n#  Define aliases for various "..., 4096) = 1277
open("/usr/share/alsa/pcm/default.conf", O_RDONLY) = 21
fstat64(21, {st_mode=S_IFREG|0644, st_size=507, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5fe0000
read(21, "#\n# Default output\n#\n\npcm.!defau"..., 4096) = 507
read(21, "", 4096)                      = 0
close(21)                               = 0
munmap(0xb5fe0000, 4096)                = 0
open("/usr/share/alsa/pcm/dmix.conf", O_RDONLY) = 21
fstat64(21, {st_mode=S_IFREG|0644, st_size=1192, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5fe0000
read(21, "#\n# dmix output\n#\n\npcm.!dmix {\n\t"..., 4096) = 1192
read(21, "", 4096)                      = 0
close(21)                               = 0
munmap(0xb5fe0000, 4096)                = 0
open("/usr/share/alsa/pcm/dsnoop.conf", O_RDONLY) = 21
fstat64(21, {st_mode=S_IFREG|0644, st_size=1194, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5fe0000
read(21, "#\n# dsnoop\n#\n\npcm.!dsnoop {\n\t@ar"..., 4096) = 1194
read(21, "", 4096)                      = 0
close(21)                               = 0
munmap(0xb5fe0000, 4096)                = 0
read(20, "", 4096)                      = 0
read(20, "", 4096)                      = 0
close(20)                               = 0
munmap(0xb7e36000, 4096)                = 0
open("/dev/snd/controlC0", O_RDONLY)    = 20
close(20)                               = 0
stat64("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=7640, ...}) = 0
open("/dev/snd/controlC0", O_RDONLY)    = 20
close(20)                               = 0
open("/dev/snd/controlC0", O_RDWR)      = 20
ioctl(20, USBDEVFS_CONTROL, 0xbff37bb4) = 0
ioctl(20, UI_DEV_CREATE, 0xbff37bc0)    = 0
close(20)                               = 0
access("/usr/share/alsa/cards/ICH4.conf", R_OK) = 0
open("/usr/share/alsa/cards/ICH4.conf", O_RDONLY) = 20
fstat64(20, {st_mode=S_IFREG|0644, st_size=2891, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7e36000
read(20, "#\n# Configuration for the Intel "..., 4096) = 2891
open("/usr/share/alsa/pcm/front.conf", O_RDONLY) = 21
fstat64(21, {st_mode=S_IFREG|0644, st_size=596, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5fe0000
read(21, "#\n# Hardware output from front s"..., 4096) = 596
read(21, "", 4096)                      = 0
close(21)                               = 0
munmap(0xb5fe0000, 4096)                = 0
open("/usr/share/alsa/pcm/surround40.conf", O_RDONLY) = 21
fstat64(21, {st_mode=S_IFREG|0644, st_size=749, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5fe0000
read(21, "#\n#  Hardware output from 4.0 sp"..., 4096) = 749
read(21, "", 4096)                      = 0
close(21)                               = 0
munmap(0xb5fe0000, 4096)                = 0
open("/usr/share/alsa/pcm/surround41.conf", O_RDONLY) = 21
fstat64(21, {st_mode=S_IFREG|0644, st_size=893, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5fe0000
read(21, "#\n#  Hardware output from 4.1 sp"..., 4096) = 893
read(21, "", 4096)                      = 0
close(21)                               = 0
munmap(0xb5fe0000, 4096)                = 0
open("/usr/share/alsa/pcm/surround50.conf", O_RDONLY) = 21
fstat64(21, {st_mode=S_IFREG|0644, st_size=896, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5fe0000
read(21, "#\n#  Hardware output from 5.0 sp"..., 4096) = 896
read(21, "", 4096)                      = 0
close(21)                               = 0
munmap(0xb5fe0000, 4096)                = 0
open("/usr/share/alsa/pcm/surround51.conf", O_RDONLY) = 21
fstat64(21, {st_mode=S_IFREG|0644, st_size=783, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5fe0000
read(21, "#\n#  Hardware output from 5.1 sp"..., 4096) = 783
read(21, "", 4096)                      = 0
close(21)                               = 0
munmap(0xb5fe0000, 4096)                = 0
open("/usr/share/alsa/pcm/iec958.conf", O_RDONLY) = 21
fstat64(21, {st_mode=S_IFREG|0644, st_size=1030, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5fe0000
read(21, "#\n#  Hardware output from iec958"..., 4096) = 1030
read(21, "", 4096)                      = 0
close(21)                               = 0
munmap(0xb5fe0000, 4096)                = 0
read(20, "", 4096)                      = 0
read(20, "", 4096)                      = 0
close(20)                               = 0
munmap(0xb7e36000, 4096)                = 0
open("/dev/snd/controlC1", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC1", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC2", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC2", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC3", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC3", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC4", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC4", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC5", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC5", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC6", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC7", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC7", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC8", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC8", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC9", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC9", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC10", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC10", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC11", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC11", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC12", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC12", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC13", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC13", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC14", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC14", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC15", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC15", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC16", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC16", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC17", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC17", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC18", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC18", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC19", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC19", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC20", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC20", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC21", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC21", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC22", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC22", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC23", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC23", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC24", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC24", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC25", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC25", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC26", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC26", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC27", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC27", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC28", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC28", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC29", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC29", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC30", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC30", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC31", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC31", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC0", O_RDONLY)    = 20
close(20)                               = 0
stat64("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=7640, ...}) = 0
open("/dev/snd/controlC0", O_RDONLY)    = 20
close(20)                               = 0
open("/dev/snd/controlC0", O_RDWR)      = 20
ioctl(20, USBDEVFS_CONTROL, 0xbff37734) = 0
ioctl(20, UI_DEV_CREATE, 0xbff37740)    = 0
close(20)                               = 0
open("/dev/snd/controlC0", O_RDONLY)    = 20
close(20)                               = 0
stat64("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=7640, ...}) = 0
open("/dev/snd/controlC0", O_RDONLY)    = 20
close(20)                               = 0
open("/dev/snd/controlC0", O_RDWR)      = 20
ioctl(20, USBDEVFS_CONTROL, 0xbff37214) = 0
ioctl(20, UI_DEV_CREATE, 0xbff37220)    = 0
close(20)                               = 0
open("/dev/snd/controlC0", O_RDONLY)    = 20
close(20)                               = 0
stat64("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=7640, ...}) = 0
open("/dev/snd/controlC0", O_RDONLY)    = 20
close(20)                               = 0
open("/dev/snd/controlC0", O_RDWR)      = 20
ioctl(20, USBDEVFS_CONTROL, 0xbff37214) = 0
ioctl(20, UI_DEV_CREATE, 0xbff37220)    = 0
close(20)                               = 0
open("/dev/snd/controlC0", O_RDONLY)    = 20
close(20)                               = 0
stat64("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=7640, ...}) = 0
open("/dev/snd/controlC0", O_RDONLY)    = 20
close(20)                               = 0
open("/dev/snd/controlC0", O_RDWR)      = 20
ioctl(20, USBDEVFS_CONTROL, 0xbff37214) = 0
ioctl(20, UI_DEV_CREATE, 0xbff37220)    = 0
close(20)                               = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 20
fcntl64(20, F_GETFL)                    = 0x2 (flags O_RDWR)
fcntl64(20, F_SETFL, O_RDWR|O_NONBLOCK) = 0
connect(20, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(20)                               = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 20
fcntl64(20, F_GETFL)                    = 0x2 (flags O_RDWR)
fcntl64(20, F_SETFL, O_RDWR|O_NONBLOCK) = 0
connect(20, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(20)                               = 0
open("/etc/group", O_RDONLY)            = 20
fcntl64(20, F_GETFD)                    = 0
fcntl64(20, F_SETFD, FD_CLOEXEC)        = 0
_llseek(20, 0, [0], SEEK_CUR)           = 0
fstat64(20, {st_mode=S_IFREG|0644, st_size=819, ...}) = 0
mmap2(NULL, 819, PROT_READ, MAP_SHARED, 20, 0) = 0xb7e36000
_llseek(20, 819, [819], SEEK_SET)       = 0
munmap(0xb7e36000, 819)                 = 0
close(20)                               = 0
semget(5678293, 1, IPC_CREAT|0660)      = 65536
semctl(65536, 0, IPC_64|IPC_STAT, 0xbff37758) = 0
semctl(65536, 0, IPC_64|IPC_SET, 0xbff37758) = 0
semop(65536, 0xbff3783e, 2)             = 0
shmget(5678293, 384, IPC_CREAT|0660)    = 1114135
shmat(1114135, 0, 0)                    = 0xb7e36000
mlock(0xb7e36000, 384)                  = 0
shmctl(1114135, IPC_64|IPC_STAT, 0xbff37778) = 0
shmctl(1114135, IPC_64|IPC_SET, 0xbff37778) = 0
open("/dev/snd/controlC0", O_RDONLY)    = 20
close(20)                               = 0
open("/dev/snd/controlC0", O_RDWR)      = 20
ioctl(20, USBDEVFS_CONTROL, 0xbff37494) = 0
ioctl(20, 0x40045532, 0xbff374b4)       = 0
open("/dev/snd/pcmC0D0p", O_RDWR|O_NONBLOCK) = 21
close(20)                               = 0
ioctl(21, AGPIOC_ACQUIRE or APM_IOC_STANDBY, 0xbff37314) = 0
fcntl64(21, F_GETFL)                    = 0x802 (flags O_RDWR|O_NONBLOCK)
ioctl(21, AGPIOC_INFO, 0xbff37310)      = 0
ioctl(21, AGPIOC_RELEASE or APM_IOC_SUSPEND, 0xbff37308) = 0
mmap2(NULL, 4096, PROT_READ, MAP_SHARED, 21, 0x80000) = 0xb5fe0000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_SHARED, 21, 0x81000) = 0xb5f4a000
ioctl(21, 0xc25c4110, 0xbff37520)       = 0
ioctl(21, 0xc25c4110, 0xbff37520)       = 0
ioctl(21, 0xc25c4110, 0xbff37520)       = 0
ioctl(21, 0xc25c4110, 0xbff37520)       = 0
ioctl(21, 0xc25c4110, 0xbff37520)       = 0
ioctl(21, 0xc25c4110, 0xbff37520)       = 0
ioctl(21, 0xc25c4110, 0xbff37520)       = 0
ioctl(21, 0xc25c4110, 0xbff37520)       = 0
ioctl(21, 0xc25c4111, 0xbff37520)       = 0
ioctl(21, 0xc0684113, 0xbff373e0)       = 0
ioctl(21, 0x80104132, 0xbff3732c)       = 0
ioctl(21, 0x80104132, 0xbff3732c)       = 0
mmap2(NULL, 65536, PROT_READ|PROT_WRITE, MAP_SHARED, 21, 0) = 0xb5de7000
ioctl(21, 0x4140, 0)                    = 0
ioctl(21, 0xc0684113, 0xbff374a0)       = 0
ioctl(21, 0x4142, 0xbff37458)           = 0
gettimeofday({1176406468, 71928}, NULL) = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 20
unlink("/tmp/alsa-dmix-5195-1176406468-71928") = -1 ENOENT (No such file or directory)
bind(20, {sa_family=AF_FILE, path="/tmp/alsa-dmix-5195-1176406468-71928"}, 38) = 0
chmod("/tmp/alsa-dmix-5195-1176406468-71928", 0660) = 0
chown32("/tmp/alsa-dmix-5195-1176406468-71928", -1, 29) = 0
listen(20, 4)                           = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7f649e8) = 5248
--- SIGCHLD (Child exited) @ 0 (0) ---
waitpid(5248, NULL, 0)                  = 5248
shmget(5678294, 131072, IPC_CREAT|0660) = 1146904
shmctl(1146904, IPC_64|IPC_STAT, 0xbff37778) = 0
shmctl(1146904, IPC_64|IPC_SET, 0xbff37778) = 0
shmat(1146904, 0, 0)                    = 0xb5dc7000
mlock(0xb5dc7000, 131072)               = 0
ioctl(21, AGPIOC_ACQUIRE or APM_IOC_STANDBY, 0xbff37600) = 0
stat64("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=7640, ...}) = 0
open("/dev/snd/controlC0", O_RDONLY)    = 22
close(22)                               = 0
open("/dev/snd/timer", O_RDONLY|O_NONBLOCK) = 22
ioctl(22, 0x80045400, 0xbff37360)       = 0
ioctl(22, SNDCTL_TMR_START or TCSETS, 0xbff3735c) = 0
ioctl(22, TIOCSPGRP, 0xbff37364)        = 0
ioctl(22, 0x80045400, 0xbff37744)       = 0
open("/proc/cpuinfo", O_RDONLY)         = 23
fstat64(23, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5f49000
read(23, "processor\t: 0\nvendor_id\t: Genuin"..., 1024) = 440
read(23, "", 1024)                      = 0
close(23)                               = 0
munmap(0xb5f49000, 4096)                = 0
semop(65536, 0xbff3784a, 1)             = 0
open("/dev/snd/controlC0", O_RDONLY)    = 23
close(23)                               = 0
stat64("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=7640, ...}) = 0
open("/dev/snd/controlC0", O_RDONLY)    = 23
close(23)                               = 0
open("/dev/snd/controlC0", O_RDWR)      = 23
ioctl(23, USBDEVFS_CONTROL, 0xbff37904) = 0
ioctl(23, USBDEVFS_CONNECTINFO, 0xbff37930) = 0
close(23)                               = 0
clone(child_stack=0xb3fcf4e4, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID|CLONE_DETACHED, parent_tidptr=0xb3fcfbe8, {entry_number:6, base_addr:0xb3fcfba0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}, child_tidptr=0xb3fcfbe8) = 5250
stat64("/dev/scd0", {st_mode=S_IFBLK|0660, st_rdev=makedev(11, 0), ...}) = 0
stat64("/dev/scd0", {st_mode=S_IFBLK|0660, st_rdev=makedev(11, 0), ...}) = 0
lstat64("/dev/scd0", {st_mode=S_IFBLK|0660, st_rdev=makedev(11, 0), ...}) = 0
lstat64("/dev", {st_mode=S_IFDIR|0755, st_size=13660, ...}) = 0
lstat64("/dev/scd0", {st_mode=S_IFBLK|0660, st_rdev=makedev(11, 0), ...}) = 0
open("/dev/scd0", O_RDWR|O_NONBLOCK)    = 23
ioctl(23, SG_IO, 0xbff37aac)            = -1 EINVAL (Invalid argument)
close(23)                               = 0
open("/dev/scd0", O_RDWR|O_NONBLOCK)    = 23
brk(0x8494000)                          = 0x8494000
dup(23)                                 = 24
ioctl(23, CDROMAUDIOBUFSIZ or SCSI_IOCTL_GET_IDLUN, 0xbff37c1c) = 0
ioctl(23, SCSI_IOCTL_GET_BUS_NUMBER, 0xbff37c24) = 0
ioctl(23, SG_IO
```


I'll probably try doing the same with vlc player, since I know that it does the same thing as sound-juicer in this situation.  Would this then be a problem in the ioctl calls?
Or what?  I'm not sure exactly what to look for in these.  do the places where something outputs =-1 EINVAL (Invalid argument) mean trouble necessarily?

Should I post this as a bug in launchpad, and if so should I post it as a sound-juicer bug, or as something else?  Also, any ideas on a workaround from this?

---

### Post by charles.figura on 2007-04-12
> **teddmeister2 said:**
> I'll probably try doing the same with vlc player, since I know that it does the same thing as sound-juicer in this situation.  Would this then be a problem in the ioctl calls?
Or what?  I'm not sure exactly what to look for in these.  do the places where something outputs =-1 EINVAL (Invalid argument) mean trouble necessarily?

Should I post this as a bug in launchpad, and if so should I post it as a sound-juicer bug, or as something else?  Also, any ideas on a workaround from this?

No, don't just post it as a sound-juicer bug.  I've tested cd playing as well, and I get the same result - program hang followed by system hang - with both Amarok and KsCD (the KDE cd player).

---

### Post by charles.figura on 2007-04-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/105981](https://bugs.launchpad.net/ubuntu/+bug/105981) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've posted a bug report on launchpad.

---

### Post by teddmeister2 on 2007-04-12
update:
Okay, so, I guess I was wrong about one thing.
VLC Media Player WILL play a cd AND not brick the system.
However, I also found out the Rhythmbox bricks the system when trying to read a cd (although the program doesn't hang until the whole system hangs).
I've also got an strace file for it that I can neither make heads nor tails of, so here's the last chunk of that:

```
events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409788, 125320}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409788, 125452}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 187) = 0
gettimeofday({1176409788, 312753}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409788, 312890}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409788, 313161}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 112) = 0
gettimeofday({1176409788, 424708}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409788, 424844}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409788, 425048}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409788, 425179}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 87) = 0
gettimeofday({1176409788, 512991}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409788, 513145}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 199) = 0
gettimeofday({1176409788, 712905}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409788, 713055}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409788, 713331}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 11) = 0
gettimeofday({1176409788, 727954}, NULL) = 0
gettimeofday({1176409788, 728294}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409788, 729002}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 184) = 0
gettimeofday({1176409788, 912882}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409788, 913032}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409788, 913355}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 115) = 0
gettimeofday({1176409789, 29053}, NULL) = 0
gettimeofday({1176409789, 29136}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 29274}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 19) = 0
gettimeofday({1176409789, 48754}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 48896}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409789, 49099}, NULL) = 0
gettimeofday({1176409789, 49159}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 49291}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 63) = 0
gettimeofday({1176409789, 112821}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 112957}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 113227}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 199) = 0
gettimeofday({1176409789, 312844}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 312983}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 313254}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 15) = 0
gettimeofday({1176409789, 328760}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 328894}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409789, 329100}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 329230}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 183) = 0
gettimeofday({1176409789, 513056}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 513264}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 115) = 0
gettimeofday({1176409789, 628787}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 628925}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409789, 629131}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 629263}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 83) = 0
gettimeofday({1176409789, 712838}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 712974}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 713243}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 199) = 0
gettimeofday({1176409789, 912857}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 912996}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 913267}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 15) = 0
gettimeofday({1176409789, 928849}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 928983}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409789, 929188}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409789, 929320}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 120) = 0
gettimeofday({1176409790, 48946}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409790, 49090}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409790, 49294}, NULL) = 0
gettimeofday({1176409790, 49356}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409790, 49488}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 63) = 0
gettimeofday({1176409790, 112916}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409790, 113053}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409790, 113323}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 115) = 0
gettimeofday({1176409790, 228910}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409790, 229046}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409790, 229252}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409790, 229384}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 83) = 0
gettimeofday({1176409790, 312931}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409790, 313067}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409790, 313337}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 199) = 0
gettimeofday({1176409790, 513255}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409790, 513410}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 15) = 0
gettimeofday({1176409790, 528832}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409790, 528968}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409790, 529172}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409790, 529303}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 183) = 0
gettimeofday({1176409790, 712902}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409790, 713039}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409790, 713344}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 115) = 0
gettimeofday({1176409790, 831677}, NULL) = 0
gettimeofday({1176409790, 837568}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409790, 837731}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 75) = 0
gettimeofday({1176409790, 912969}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409790, 913110}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409790, 913384}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 136) = 0
gettimeofday({1176409791, 48934}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 49081}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409791, 49286}, NULL) = 0
gettimeofday({1176409791, 49348}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 49479}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 63) = 0
gettimeofday({1176409791, 112944}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 113080}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 113350}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 24) = 0
gettimeofday({1176409791, 136876}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 137011}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409791, 137217}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 137347}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 175) = 0
gettimeofday({1176409791, 312993}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 313135}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 313406}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 123) = 0
gettimeofday({1176409791, 436899}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 437035}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409791, 437240}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 437372}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 75) = 0
gettimeofday({1176409791, 513165}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 513320}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 199) = 0
gettimeofday({1176409791, 712972}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 713110}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 713379}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 23) = 0
gettimeofday({1176409791, 736972}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 737108}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409791, 737312}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 737443}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 175) = 0
gettimeofday({1176409791, 912977}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 913113}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409791, 913382}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 124) = 0
gettimeofday({1176409792, 37073}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 37217}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409792, 37429}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 37561}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 11) = 0
gettimeofday({1176409792, 49226}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 49360}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409792, 49561}, NULL) = 0
gettimeofday({1176409792, 49621}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 49751}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 63) = 0
gettimeofday({1176409792, 113019}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 113156}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 113426}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 199) = 0
gettimeofday({1176409792, 313003}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 313140}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 313410}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 24) = 0
gettimeofday({1176409792, 336946}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 337082}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409792, 337287}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 337418}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 175) = 0
gettimeofday({1176409792, 513267}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 513422}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 123) = 0
gettimeofday({1176409792, 636974}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 637110}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409792, 637315}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 637447}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN, revents=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 75) = 1
ioctl(3, FIONREAD, [32])                = 0
read(3, "\241 \316\223\'\0\0\3\24\1\0\0\33\1\0\0-\0\0\0\'\0\0\3"..., 32) = 32
gettimeofday({1176409792, 677888}, NULL) = 0
write(3, "\31\0\v\0M\0\0\0\0\0\30\0! \0\0M\0\0\0\24\1\0\0\33\1\0"..., 44) = 44
ioctl(3, FIONREAD, [0])                 = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 678470}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 34) = 0
gettimeofday({1176409792, 713039}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 713175}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 713445}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 199) = 0
gettimeofday({1176409792, 913040}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 913178}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 913449}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 23) = 0
gettimeofday({1176409792, 937640}, NULL) = 0
gettimeofday({1176409792, 937725}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409792, 937866}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 112) = 0
gettimeofday({1176409793, 49179}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 49332}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409793, 49586}, NULL) = 0
gettimeofday({1176409793, 49650}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 49783}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 63) = 0
gettimeofday({1176409793, 113100}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 113237}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 113508}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 124) = 0
gettimeofday({1176409793, 237014}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 237150}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409793, 237357}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 237489}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 75) = 0
gettimeofday({1176409793, 313067}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 313204}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 313473}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 199) = 0
gettimeofday({1176409793, 513327}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 513482}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 23) = 0
gettimeofday({1176409793, 537085}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 537221}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409793, 537425}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 537556}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 175) = 0
gettimeofday({1176409793, 713123}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 713259}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 713529}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 123) = 0
gettimeofday({1176409793, 837047}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 837183}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
gettimeofday({1176409793, 837388}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 837519}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 75) = 0
gettimeofday({1176409793, 913119}, NULL) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 913255}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=10, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}], 9, 0) = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1176409793, 913526}, NULL) = 0
poll(
```


(because of post size limits, this is like the last 2% of the strace output
I guess same questions as before, as well as:
What sort of bug should I post it as?
What is the problem?
Thanks.

---

### Post by yopnono on 2007-04-12
It it the fault of *cdparanoia* i rolled back to the earlier version and now everything work.

---

### Post by teddmeister2 on 2007-04-12
Confirmed!  cdparanoia is where the bug is!  Thanks for posting!
Is this cdparanoia backport bug posted to launchpad?

---

### Post by charles.figura on 2007-04-12
> **yopnono said:**
> It it the fault of *cdparanoia* i rolled back to the earlier version and now everything work.

Whoa - I see that my cdparanoia updated on april 12 as well.  How do you roll back a version?

---

### Post by teddmeister2 on 2007-04-12
> **charles.figura said:**
> Whoa - I see that my cdparanoia updated on april 12 as well.  How do you roll back a version?

Go into synaptic, search for cdparanoia, find it and select from the menu:
Packages >> Force Version, and change it from the debian backport to the 3.98a... whatever it is version.
Do the same for libcdparanoia0

---

### Post by teddmeister2 on 2007-04-12
and, if you want to keep it from updating, I think you can just go to Packages >> Lock version after that, although I've found that it's easier to keep from doing that, so that you can continue looking to see if they've updated to fix the bug yet.

---

### Post by charles.figura on 2007-04-12
> **teddmeister2 said:**
> Go into synaptic, search for cdparanoia, find it and select from the menu:
Packages >> Force Version, and change it from the debian backport to the 3.98a... whatever it is version.
Do the same for libcdparanoia0
I can support that.  I downgraded cdparanoia, libcdparanoia0 to 3a9.8-13 from 3.10, and the problem disappeared.

---

### Post by michael95060 on 2007-04-12
ditto, the downgrade worked. Thank you.

---

### Post by Pikka on 2007-04-13
Via Synaptic: Force version, then Apply...

---

### Post by yopnono on 2007-04-13
> **teddmeister2 said:**
> Confirmed!  cdparanoia is where the bug is!  Thanks for posting!
Is this cdparanoia backport bug posted to launchpad?

[https://bugs.launchpad.net/ubuntu/+source/cdparanoia/+bug/106000](https://bugs.launchpad.net/ubuntu/+source/cdparanoia/+bug/106000)

Vote/add more info

---

### Post by Earl108 on 2007-04-14
Just to let you all know this worked for me. sound juicer is working fine. Thanks for the post. Earl:D :guitar:

---

### Post by clconway on 2007-04-14
I concur. Saw the problem with both Sound Juicer and Grip. Downgrading fixed it.

---

### Post by richbiskit on 2007-04-18
I have this problem in Kubuntu edgy, how do i downgrade cdparanoia in Kubuntu? do i use adept? sorry, i am a bit of a novice!

---

### Post by min6nap on 2007-04-18
THanks people, this solution has worked fine for me. Finally can listen to my favourite songs again, without nasty hangups.

:guitar:

---

### Post by min6nap on 2007-04-18
RichBiscuit,

The best way to do would be with synaptic. Just open a terminal from the applications, accessories menu. Then type : 
sudo synaptic

Subsequently follow the instructions given earlier in this post.

Have a good one !

---

### Post by richbiskit on 2007-04-19
min6nap, thanks for the advice, i actually solved it by downloading the older versions from...

[http://packages.debian.org/cgi-bin/search_packages.pl?keywords=cdparanoia&searchon=names&subword=1&version=all&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=cdparanoia&searchon=names&subword=1&version=all&release=all)

and replacing the 3.10 versions with the downloaded ones. Worked great and now i have no problems!!! :guitar:

---

### Post by Darles on 2007-05-03
I have the same problem. CD ripping freezes on all three of the apps i have tried to use

Sound Juicer
Grip
K3b

Upon finding this thread i thought i would be able to fix it. However, when i go to synaptic and try to downgrade cdparanoia using force version i am unable to select this option. Force version is one of the options but i'm unable to select it or highlight it from the options under package.

Any ideas why?

Would i be able to download an earlier version as suggested in this thread? If so can i remove version 3.10 without it screwing up my system. It tells me it would have to remove ubuntu desktop if i went ahead and deleted it.

---

### Post by sav2005 on 2007-05-03
> **Darles said:**
> I have the same problem. CD ripping freezes on all three of the apps i have tried to use

Sound Juicer
Grip
K3b

Upon finding this thread i thought i would be able to fix it. However, when i go to synaptic and try to downgrade cdparanoia using force version i am unable to select this option. Force version is one of the options but i'm unable to select it or highlight it from the options under package.

Any ideas why?

Would i be able to download an earlier version as suggested in this thread? If so can i remove version 3.10 without it screwing up my system. It tells me it would have to remove ubuntu desktop if i went ahead and deleted it.

Removing the ubuntu-desktop package is harmless! It is a meta package which coordinates the installation of your desktop. If it is removed the applications it coordinated stay installed.

Are you using Edgy or Feisty? I thought you could force the downgrade in Edgy, but I'm not sure about Feisty.

---

### Post by yopnono on 2007-05-04
In all version that use synaptic you can do a force. Just mark the packaged then go to the menu *package* then down to *force version* or press CTRL+E. Then you get a popup dialog that ask which version you like to "downgrade" to

---

### Post by Darles on 2007-05-04
Thanks for getting back to me,

I still can't force version and i'm on feisty by the way. The problem only started since i upgraded to feisty, option is there and i can see it in the package menu but i just can't select it

Can i completely remove then install both cdparonoia and libcdparanoia0? 

The reason i wouldn't want to do that is removing libcdparanoia0 also removes other apps i use like mplayer, k3b, sound juicer etc. Although i would reinstall these if it were the only option. 

Any thoughts?

---

### Post by Darles on 2007-05-04
Don't worry i've sorted it.

I deleted the newest versions of both cdparanoia and libcdparanoia0 even though this meant i lost
*gnome-media
*gstreamer0.10-Plugins-base
*Mplayer/Mozilla-Mplayer
*Serpentine
*Sound Juicer
*K3b

And installed the earlier versions from [_here_]("http://packages.debian.org/cgi-bin/s...ll&release=all")

It was ok though as it meant i could just reinstall the apps that i wanted and now my system no longer freezer when ripping a cd.

Perfect.

Thanks for the advice.

Still don't know why i couldn't just force version though!

---

### Post by Darles on 2007-05-09
Jumped the gun a little early...

Thought the problem had gone away but it came back today when i was ripping a cd with K3b. Thought it may have just been K3b so tried Grip and bang, crashed again.

The screen freezes and the mouse doesn't work so i have to restart the computer manually.

Does anyone know how i can find out what's causing this problem?

---

### Post by meanmrmustard on 2007-07-26
After downgrading the two files, I was able to rip 5 out of 9 tracks from a CD before the system locked up.

---

