---
title: "Default application for microphone"
date: 2018-10-12
forum: Multimedia Software
---

### Post by ikebastuz on 2018-10-12
Hello there!
I'm struggling already for several days with microphone input on linux. I developed a web application running on chrome browser, which uses microphone input (from webcam). On MAC or Windows it works stable. But we really have to run it on ubuntu. And here - micro works sometimes rarely (between reboots), sometimes never (on different PCs).
I managed it working on 1 machine pretty stable, like 100% times.
I'm not sure if i was right, but here is what i did:
I added this to /etc/systemd/system/pulseaudio.service
[Unit]
Description=PulseAudio system server

[Install]
WantedBy=multi-user.target

[Service]
Type=simple
ExecStart=/usr/bin/pulseaudio --system --realtime --disallow-exit --no-cpu-limit
Then i ran
systemctl --system enable pulseaudio.service
systemctl --system start pulseaudio.service
There were a few errors which i fixed with here /etc/pulse/system.pa adding this:
load-module module-native-protocol-unix auth-anonymous=1
And it started working well.
The thing is - its working only on 1 PC, but they are all pretty much the same. Hardware may vary a bit, but OS is identical (installed from the same iso using same scripts, like hand-make docker)
Recently I found out this. I connect via SSH to PC with not-working mic. And run this
arecord -vv -f dat /dev/null 
And it shows, that mic is fine, volume showing as it should be. But Chrome application not seeing mic.
I checked the same command on PC with working mic - and volume was 0.
It looks like any app takes control over mic and not letting it to use by the others. Logic, but is there any way to force browser to take control over mic at the first place? Maybe route mic somehow...
Also tried to run pulseaudio as a daemon, set default-source from sources-list. But this did nothing.
Any ideas?

---

### Post by ikebastuz on 2018-10-12
One more strange activity. I open up mic settings, and closing it (not changing anything) - and it starts working.
What the heck...

---

### Post by oldos2er on 2018-10-14
Can you clarify which distro/version you're running?

---

### Post by ikebastuz on 2018-10-15
Sure, that is Ubuntu 17.04

---

### Post by oldos2er on 2018-10-16
All right, I've moved the thread to Multimedia subforum.

Support for 17.04 ended this past January, and 17.10 is EOL as well, so it's time to install 18.04.

---

### Post by ikebastuz on 2018-10-17
I dont really think that it will vary between 17.04, 17.10 and 18.04. Also there lots of client's computers running this complex build and upgrading it may crush everything up(

---

