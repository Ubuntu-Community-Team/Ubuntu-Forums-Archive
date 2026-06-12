---
title: "wpa_supplicant doesn't work"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by bendeguz on 2010-11-21
I am trying to get wireless working on my new Ubuntu 10.10. The wireless adapter can be enabled and I can see the WEP wireless networks in my area. However, I cannot see any WPA2 networks, including my own.

When I try to configure wpa_supplicant via the wpa_gui tool, I get an error "Could not get status from wpa_supplicant". It makes sense because I don't think it's installed properly. I cannot start wpa_supplicant at all because the service doesn't exist:

# service 
acpid                       plymouth
acpi-support                plymouth-log
alsa-mixer-save             plymouth-splash
anacron                     plymouth-stop
apparmor                    pppd-dns
apport                      procps
atd                         pulseaudio
avahi-daemon                rc
binfmt-support              rc.local
bluetooth                   rcS
bootlogd                    README
brltty                      reboot
console-setup               rsync
cron                        rsyslog
cups                        saned
dbus                        screen-cleanup
dmesg                       sendsigs
dns-clean                   single
failsafe-x                  skeleton
fancontrol                  speech-dispatcher
gdm                         stop-bootlogd
grub-common                 stop-bootlogd-single
halt                        sudo
hostname                    udev
hwclock                     udev-finish
hwclock-save                udevmonitor
irqbalance                  udevtrigger
kerneloops                  ufw
killprocs                   umountfs
lm-sensors                  umountnfs.sh
module-init-tools           umountroot
networking                  unattended-upgrades
network-interface           urandom
network-interface-security  wicd
ondemand                    x11-common
pcmciautils                 

I uninstalled Network Manager and installed wicd.

I uninstalled and reinstalled wpa_supplicant but it came back the same way: no service.

Any help would be appreciated.

---

### Post by bendeguz on 2010-11-21
Sorry, half the services were truncated. Anyway, the point is that wpa_supplicant doesn't show up on the list.

---

### Post by bendeguz on 2010-11-22
Problem solved (by myself).

---

