---
title: "zoom cpu usage"
date: 2020-05-27
forum: Multimedia Software
---

### Post by folivorax on 2020-05-27
Running zoom regularly takes very large cpu, showing as up to 200% in top. (see below a snapshot at a tamer time). This causes laptop to heat up, and fans to spin loudly.

```

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                   
 787685 xxxxx     20   0 8008108   1.0g 235656 S 133.3   6.6 376:17.55 zoom                      

``` 

This is a fairly modern laptop: 16GB ram and cpuinfo:
model name      : Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz
so a basic application should not make it overheat. Are others experiencing the same problems? Any way to fix it?

---

### Post by DuckHook on 2020-05-27
To get meaningful help you must post more info like OS, version, flavour, recent upgrades or modifications, etc. Most important is to describe how you installed it. It is not available in the standard repos, so it is either a snap, flatpak or something you've downloaded yourself (hugely risky).

I refuse to use Zoom for many reasons other than its technical demerits, so my help is of strictly limited value, but you should look at your logs, dmesg and journalctl for starters.

Any app that misbehaves that badly should also be invoked from the command line. The error messages are often quite revealing.

You can also try purging, then reinstalling Zoom (but only from a trusted source).

---

### Post by monkeybrain20122 on 2020-05-27
See if [this]("https://makandracards.com/makandra-orga/473077-how-to-avoid-100-cpu-load-when-screen-sharing-through-zoom") helps. Zoom is known to be resource demanding (apart from security issues) if you are just using it for one on one video call the suggestion is usually to switch to something else like skype. For conferencing maybe you can look into [jitsi-meet]("https://timesofindia.indiatimes.com/gadgets-news/jitsi-your-free-alternative-to-zoom-video-conferencing/articleshow/75201138.cms"), an open source and secure alternative to zoom.

---

### Post by speartip on 2020-05-28
Could the problem be Graphics card related? Have you installed a proprietary driver? More info is needed.
I use Zoom regularly on my 12 year old HP Desktop with an i3 processor, & integrated graphics. For general conferencing Zoom uses between 15-20% CPU. When I Screen Share that may go up to about 60% CPU.
I checked the link in monkeybrains post, but it seems that, that setting has been removed in later versions of Zoom.

---

### Post by folivorax on 2020-05-28
More detailed system info:

```

 % inxi -Fxz       
System:    Kernel: 5.4.0-31-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
           Desktop: KDE Plasma 5.18.4 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Laptop System: LENOVO product: 20KHCTO1WW v: ThinkPad X1 Carbon 6th 
           serial: <filter> 
           Mobo: LENOVO model: 20KHCTO1WW v: SDK0J40709 WIN serial: <filter> UEFI: LENOVO 
           v: N23ET62W (1.37 ) date: 02/19/2019 
Battery:   ID-1: BAT0 charge: 17.9 Wh condition: 46.4/57.0 Wh (81%) model: LGC 01AV494 
           status: Discharging 
CPU:       Topology: Quad Core model: Intel Core i7-8550U bits: 64 type: MT MCP 
           arch: Kaby Lake rev: A L2 cache: 8192 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31999 
           Speed: 800 MHz min/max: 400/4000 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 
           4: 800 5: 800 6: 800 7: 800 8: 800 
Graphics:  Device-1: Intel UHD Graphics 620 vendor: Lenovo driver: i915 v: kernel 
           bus ID: 00:02.0 
           Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa 
           tty: N/A 
           OpenGL: renderer: Mesa Intel UHD Graphics 620 (KBL GT2) v: 4.6 Mesa 20.0.4 
           direct render: Yes 
Audio:     Device-1: Intel Sunrise Point-LP HD Audio vendor: Lenovo driver: snd_hda_intel 
           v: kernel bus ID: 00:1f.3 
           Sound Server: ALSA v: k5.4.0-31-generic 
Network:   Device-1: Intel Ethernet I219-V vendor: Lenovo driver: e1000e v: 3.2.6-k 
           port: efa0 bus ID: 00:1f.6 
           IF: enp0s31f6 state: down mac: <filter> 
           Device-2: Intel Wireless 8265 / 8275 driver: iwlwifi v: kernel port: efa0 
           bus ID: 02:00.0 
           IF: wlp2s0 state: up mac: <filter> 
Drives:    Local Storage: total: 238.47 GiB used: 53.73 GiB (22.5%) 
           ID-1: /dev/nvme0n1 vendor: Lenovo model: LENSE30256GMSP34MEAT3TA size: 238.47 GiB 
Partition: ID-1: / size: 231.54 GiB used: 53.43 GiB (23.1%) fs: ext4 dev: /dev/dm-1 
           ID-2: /boot size: 704.5 MiB used: 202.5 MiB (28.7%) fs: ext4 dev: /dev/nvme0n1p2 
           ID-3: swap-1 size: 976.0 MiB used: 100.5 MiB (10.3%) fs: swap dev: /dev/dm-2 
Sensors:   System Temperatures: cpu: 50.0 C mobo: N/A 
           Fan Speeds (RPM): cpu: 0 
Info:      Processes: 287 Uptime: 6d 19h 29m Memory: 15.40 GiB used: 7.35 GiB (47.7%) 
           Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: zsh v: 5.8 inxi: 3.0.38 

```

A post on another forum suggested reverting to older kernels: [https://forums.linuxmint.com/viewtopic.php?t=317477](https://forums.linuxmint.com/viewtopic.php?t=317477), but it is not clear if that is the same issue. In particular, their it is a cinnamon process using CPU (when using zoom).

I appreciate the suggestion to avoid zoom, but my work these days requires me to take part in various zoom meetings, and occasionally to host large seminars over zoom. While zoom has many faults, so far alternatives we tried have not come up to the video/audio quality zoom gives in large (200+ participant) meetings. I appreciate the sentiment, but that is not a feasible solution at this time.

---

### Post by DuckHook on 2020-05-29
> **folivorax said:**
> More detailed system info…
:confused: 
> **DuckHook said:**
> To get meaningful help you must post more info like **OS, version, flavour, recent upgrades or modifications, etc. _Most important is to describe how you installed it._** It is not available in the standard repos, so it is either a snap, flatpak or something you've downloaded yourself (hugely risky).

…you should look at your logs, dmesg and journalctl for starters.

…should also be invoked from the command line. The error messages are often quite revealing.

You can also try purging, then reinstalling Zoom (but only from a trusted source).
It is not possible to help you without your cooperation. This starts simply enough with providing answers to the questions asked.

---

### Post by SeijiSensei on 2020-05-29
Are you hosting these sessions?  How many participants?  In our experience the host's bandwidth and computing power can matter quite a bit.

If you're hosting a 200+ participant meeting, I'd imagine a laptop could be pretty weak sauce, even one with an i7.  Any better in Windows?

---

### Post by folivorax on 2020-06-06
I don't have any computer with windows, so haven't tried.

The high CPU seems fairly universal: it occurs for both small meetings where I am guest and for large meetings which I sometimes also host. I have not tracked the CPU usage regularly, but notice when the fans get loud, which happened for all types of meetings.

zoom was installed by getting and installing the deb package from [https://zoom.us/download](https://zoom.us/download) (as far as I can tell the package is just an installer, but as official as it gets, I suppose).  Is there a better way to install zoom?  I recently re-installed to upgrade to a newer version of zoom. This did not seem to make a difference. (again, I have not collected data systematically, just my impression).

This is all on on kubuntu 20.04, upgraded from 19.04 originally installed.

---

### Post by DuckHook on 2020-06-06
I don't use Zoom, so can only give very general advice.

[list=1]
[*]You may want to try first removing/purging Zoom altogether. Get rid of its config files too. You will have to web&#8209;search the best way to do this. I don't know if Zoom has an auto&#8209;remover as part of its install process.
[*]Then install the snap version of Zoom. Hopefully, it has been tweaked to run more smoothly with Ubuntu: ```
sudo snap install zoom-client
```
[*]You can limit CPU usage with the following techniques: [https://scoutapm.com/blog/restricting-process-cpu-usage-using-nice-cpulimit-and-cgroups](https://scoutapm.com/blog/restricting-process-cpu-usage-using-nice-cpulimit-and-cgroups)
[*]I also use taskset to limit cpu usage. The taskset man page is useful for available options and is not too arcane.
[*]As a rule of thumb, unless you are absolutely, positively, entirely sure that the third-party site is safe, it is better to avoid installing apps using downloaded .deb files. However, you appear to be a seasoned Linux user, so you can judge what safety risks you are taking.
[/list]
Lastly, forum tip: the old&#8209;timers around here often unsubscribe from threads after X hours of inactivity. I had already unsubscribed from this one and just ran across your response by happenstance. If you won't be responding for some days, it is a good idea to state this up front so that other forum members know what to expect and don't unsubscribe the thread.

---

### Post by speartip on 2020-06-07
Just to chime in again with this. I use Zoom on Ubuntu & Windows. I've also used the .deb package from the website & the snap package. The package in snap is the same as the website version. On Windows cpu usage is considerably lower. On mine 60% on Ubuntu when screen sharing. 20-25% on Windows. Same on other Linux distros I've tried as well. So whether this is a Zoom problem or a Linux problem I don't know. Like You I need to use Zoom for the time being, so I reluctantly Installed Windows in a dual boot purely for this reason.

---

