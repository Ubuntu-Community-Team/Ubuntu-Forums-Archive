---
title: "libva-intel-vaapi-driver @ Kubuntu 12.04 turned my system very slow"
date: 2012-05-13
forum: Multimedia Software
---

### Post by länkky on 2012-05-13
Hi all,

After installing Kubuntu 12.04 & bunch of additional packages to my i5-2500T HTPC (with integrated Intel HD Graphics 2000) my system became totally unusable slow. After boot the system was OK for a while, but then at some point KDE becomes very slow. (TTY1 & SSH connections worked normally without terrible lag)

After 2h of thinking (& rebooting several times) I realized that the problem always started after I played some video (e.g. with VLC). That gave me clue that "maybe" the package libva-intel-vaapi-driver (/usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so) had something to do with the problem.

I removed the "libva-intel-vaapi-driver" package and after that the problem went away. So I have no va-api HW video acceleration at the moment, but at least my KDE is usable.

So in case you encounter very slow Kubuntu 12.04 desktop (where mouse moves but everything else is like swimming in jam), check if you have /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so in your system. Try removing it and test if it helps.

Maybe I will give the VA-API an other try after some time, but for now I will manage without. Has anyone else encountered the same problem?


**Update: **I was too quick in my conclusion, since the problem occurred again even though there is no VA-API driver left. Next step is that I put my old ATI GPU back to my system to see if that will help.

Does someone know if it is possible to reload display driver kernel module without booting the whole machine? It would help my troubleshooting. I would like to test if restarting Intel driver would help. Log of from KDE and killing the whole X from terminal does not help. Only reboot restores the system back to normal - and only for a while.. :(

---

### Post by länkky on 2012-05-13
I checked my system log and found following error coming to the syslog very often:

[drm:i915_hangcheck_ring_idle] *ERROR* Hangcheck timer elapsed... blt ring idle [waiting on 80053, at 80053], missed IRQ?

After some Google I believe that my slow-desktop-problem could  be related to the Sandy Bridge motherboards (mine has Z68 chip set, problem also reported with H67 chip set):

[https://bugs.freedesktop.org/show_bug.cgi?id=36241](https://bugs.freedesktop.org/show_bug.cgi?id=36241)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065)

The reason why I upgraded my whole system Intel GPU was the closed source ATI driver and poor HW video acceleration. It seems that it doesn't matter which GPU I select, I always end up having loads of problems with them.. :/

---

### Post by länkky on 2012-05-14
I got the problem (hopefully) solved. I had to set following kernel parameter to /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"

(and run 'update-grub' & boot after that)

For some reason that seemd to help. I was able to watch TV and video for 2 hours tonight without problem. Before changing this parameter the system would turn extremely low only after less than a minute of video playback.

---

