---
title: "Realtek ALC272. Empathy kills microphone"
date: 2010-08-08
forum: Multimedia Software
---

### Post by uaaquarius on 2010-08-08
Hi,

I'm running Ubuntu 10.04 (i686) on Acer Aspire 5551G. This laptop has Realtek ALC272 sound chip. Both sound and microphone work fine. But, when I start video/audio call in Empathy the microphone dies until I reboot the laptop (sound continues to work). The same happens with Pidgin and Ekiga. So, I can't make video/audio calls.

Any ideas? :)

I believe this is pulse/alsa bug.

Thanks in advance

---

### Post by simosx on 2010-08-09
> **uaaquarius said:**
> Hi,

I'm running Ubuntu 10.04 (i686) on Acer Aspire 5551G. This laptop has Realtek ALC272 sound chip. Both sound and microphone work fine. But, when I start video/audio call in Empathy the microphone dies until I reboot the laptop (sound continues to work). The same happens with Pidgin and Ekiga. So, I can't make video/audio calls.

Any ideas? :)

I believe this is pulse/alsa bug.

Thanks in advance

It sounds like a PulseAudio bug, which might be caused by issues with Alsa.
The workaround would be to restart PulseAudio to get the mic working.
Of course, this should not happen it is would be good to figure out who is at fault, so that we inform either Alsa or PulseAudio.

There is a tool to retrieve the full Alsa details, with alsa-info.sh.
To run alsa-info.sh,
[FONT="Courier New"]
wget [www.alsa-project.org/alsa-info.sh](www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh[/FONT]

You are prompted to send the details to the alsa-project.org website; select Yes and write down the URL you will be given. This URL has your soundcard information; reply here with this URL.

---

### Post by uaaquarius on 2010-08-09
> **simosx said:**
> This URL has your soundcard information; reply here with this URL.

Hi, simosx!

Here is the URL:
[http://www.alsa-project.org/db/?f=1672f44b944fa429fff596e54048907c77fc340c](http://www.alsa-project.org/db/?f=1672f44b944fa429fff596e54048907c77fc340c)

---

### Post by simosx on 2010-08-09
> **uaaquarius said:**
> Hi, simosx!

Here is the URL:
[http://www.alsa-project.org/db/?f=1672f44b944fa429fff596e54048907c77fc340c](http://www.alsa-project.org/db/?f=1672f44b944fa429fff596e54048907c77fc340c)

Your Alsa settings look fine. You specify the Alsa model 'toshiba', probably following some instructions from other sources.

According to 
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt#91](http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt#91)
the ALC272 does not have a 'toshiba' model.
Does sound work for you if you unset the model? Setting it to 'toshiba' might be an issue.

I think Ekiga does not support Pulseaudio yet and I am not sure about Pidgin.

What I would recommend (after fixing the 'toshiba') is to kill PulseAudio and run it again as

pulseaudio -vvvv

which will show lots of debugging information. Try to perform a recording with the sound recorder and observe the output.

Then, try out empathy. You can try with voice-only call, to eliminate any video interactions.

---

### Post by uaaquarius on 2010-08-09
Hi, simosx!

Yes, "toshiba" was added by me when I tried to fix the microphone :)

OK, I commented it out and restarted pulseaudio. Not sure if I restarted it correctly, I used those commands:
```
gksu /etc/init.d/pulseaudio stop
gksu killall pulseaudio
gksu /etc/init.d/pulseaudio start
```Then I run 
```
pulseaudio -vvvv
```which resulted in
```
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 084cdccf7136c823047702a34c4b9a8e.
I: main.c: Session ID is 084cdccf7136c823047702a34c4b9a8e-1281390582.698301-1463995618.
I: main.c: Using runtime directory /home/batky/.pulse/084cdccf7136c823047702a34c4b9a8e-runtime.
I: main.c: Using state directory /home/batky/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
```Then I tested Sound Recorder. It was it was working like a charm.
Then I tested audio call with Empathy. It was quite bad: a lot of clunking like "chuk-chuk" on another computer (also running Ubuntu), some disruption, in general it was very hard to understood. The sound from another computer was heard excellently on this Acer.
Then I tried video call with Empathy. Which killed the microphone again. It does not work (e.g. in Sound Recorder) until I reboot :( 

Here is my updated result of alsa-info.sh:
[http://www.alsa-project.org/db/?f=31743a8765b799bce5b1438c744b2e63c45e0ff3](http://www.alsa-project.org/db/?f=31743a8765b799bce5b1438c744b2e63c45e0ff3)

Any ideas? :)
Thanks

---

### Post by lidex on 2010-08-09
I would start with an alsa upgrade using the link in my sig. You'll probably still need to specify a model in alsa-base.conf, but it looks like a generic one. How many analog audio jacks are there? Digital? Number of sound channels supported?

---

### Post by uaaquarius on 2010-08-10
Hi, lidex!

I'll try to upgrade after work. Then I'll also provide the number of jacks.
> **lidex said:**
> Number of sound channels supported?
How can I check this?

Thanks!

---

### Post by uaaquarius on 2010-08-12
Checked the problem on clean installation of 10.10 alpha 3. The problem is still present. So, I've reported a [bug]("https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/617001").

---

### Post by uaaquarius on 2010-09-01
This is definitely not a old-alsa problem. There is the latest alsa 1.0.23 present in 10.10-alpha-3, but the problem is still there. So, I believe upgrading alsa on 10.04 wont help.

---

### Post by lidex on 2010-09-01
How many audio jacks on the motherboard?

---

### Post by uaaquarius on 2010-09-02
> **lidex said:**
> How many audio jacks on the motherboard?

There are 2 analogue audio jacks: for microphone and for speakers.
There is aslo HDMI port from ATI 5470.

Another interesting point is that *HD-Audio-Models.txt* does not lists any Acer model for ALC272, so I tried "auto" but with no success.

---

### Post by lidex on 2010-09-02
Try 3stack-dig:
```
options snd-hda-intel model=3stack-dig
```
Reboot.

Also 3stack-6ch, 3stack-6ch-dig

---

### Post by uaaquarius on 2010-09-02
> **lidex said:**
> Try 3stack-dig:
```
options snd-hda-intel model=3stack-dig
```Reboot.

Also 3stack-6ch, 3stack-6ch-dig

Thanks for quick reply, lidex!

I've tried 3stack-dig, 3stack-6ch and 3stack-6ch-dig. Each provided the choice if input source: Mic and Front Mic. I've tried both of them for each model. But the problem is still present: 

[LIST=1]
[*]There is a "chucklink" during audio call, so the other person can hardly understand you;
[*]Videocall kills the microphone.
[/LIST]
Ubuntu developers confirmed [this bug]("https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/617001").

---

### Post by lidex on 2010-09-02
I'm thinking it may have something to do with the fact that snd-hda-intel is being used by both devices. Are you using hdmi and if not can it be disabled? What profile are you using in 'Sound Preferences'?

---

### Post by uaaquarius on 2010-09-04
> **lidex said:**
> I'm thinking it may have something to do with the fact that snd-hda-intel is being used by both devices. Are you using hdmi and if not can it be disabled? What profile are you using in 'Sound Preferences'?

I don't use HDMI and I've tried disabling it. I've even tried to remove proprietary ATI driver, but with no success :)

Here are screenshots of my sound configuration:
[[IMG]http://xmages.net/storage/10/1/0/1/2/upload/b89c63b4.png[/IMG]]("http://xmages.net/storage/10/1/0/1/2/upload/b89c63b4.png")

[IMG]http://xmages.net/storage/10/1/0/6/9/upload/4ebf7f1b.png[/IMG]

---

### Post by uaaquarius on 2010-11-21
I've managed to solve the problem with following workaround:

[LIST=1]
[*]replace Empathy with Skype
[*]delete pulseaudio (this removes some things like sound indicator)
[/LIST]

---

