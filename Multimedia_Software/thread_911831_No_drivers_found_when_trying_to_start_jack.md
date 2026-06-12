---
title: "No drivers found when trying to start jack"
date: 2008-09-06
forum: Multimedia Software
---

### Post by ARam1024 on 2008-09-06
I'm trying to install and configure jack for the first time, but when I try to start jack from the jack audio connection kit, I get the following message:

02:17:58.028 Patchbay deactivated.
02:17:58.053 Statistics reset.
02:17:58.118 ALSA connection graph change.
02:17:58.423 ALSA connection change.
02:18:04.310 Startup script...
02:18:04.311 artsshell -q terminate
02:18:04.737 Startup script terminated with exit status=256.
02:18:04.738 JACK is starting...
02:18:04.739 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p64 -n3 -m
could not open driver .so '/usr/lib/jack/jack_freebob.so': /usr/lib/jack/jack_freebob.so: undefined symbol: jack_driver_nt_init
could not open driver .so '/usr/lib/jack/jack_dummy.so': /usr/lib/jack/jack_dummy.so: undefined symbol: jack_driver_nt_init
could not open driver .so '/usr/lib/jack/jack_oss.so': /usr/lib/jack/jack_oss.so: undefined symbol: jack_driver_init
could not open driver .so '/usr/lib/jack/jack_alsa.so': /usr/lib/jack/jack_alsa.so: undefined symbol: jack_driver_nt_init
02:18:04.757 JACK was started with PID=12059.
could not open driver .so '/usr/lib/jack/jack_firewire.so': /usr/lib/jack/jack_firewire.so: undefined symbol: jack_driver_nt_init
could not find any drivers in /usr/lib/jack!
jackd: no drivers found; exiting
02:18:04.766 JACK was stopped with exit status=1.
02:18:04.766 Post-shutdown script...
02:18:04.767 killall jackd
jackd: no process killed
02:18:05.173 Post-shutdown script terminated with exit status=256.
02:18:06.822 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

contents of /usr/lib/jack
inprocess.la
intime.la
jack_alsa.la
jack_dummy.la
jack_firewire.la
jack_freebob.so
jack_oss.so
inprocess.so
intime.so
jack_alsa.so
jack_dummy.so
jack_firewire.so
jack_oss.la

I tried:
sudo apt-build install --rebuild --reinstall jackd
which was suggested in a forum, but with the same results.

Any help would be appreciated.

Andrew

---

### Post by vehka on 2008-10-11
This happens to me too, when I try to start jackd from the qjackctl. After that, it happens when I try to start jackd from the command line as well. I can fix the problem by running the uninstall script (sudo make uninstall) from the jack source folder, and installing again (sudo make install). After that, the "jackd -dfirewire" works again. Strange.

I'll report back, if I find out what's wrong here.

Oh, and I'm running the latest jack installed from the subversion repository, and the latest version of qjackctl from sourceforge, and I don't have the ubuntu packages installed.

---

### Post by ARam1024 on 2008-10-11
Thanks vehka.  I'll try your suggestion as soon as my laptop gets back from the shop.  Monitor broke off...second time in 3 years.

---

